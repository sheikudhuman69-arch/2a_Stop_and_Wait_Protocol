# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
## CLIENT.PY
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    msg = s.recv(1024).decode()
    print(msg)

    s.send("Acknowledgement Received".encode())
```
## SERVER.PY
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)

print("Waiting for connection...")

c, addr = s.accept()
print("Connected with", addr)

while True:
    i = input("Enter a data: ")

    c.send(i.encode())

    ack = c.recv(1024).decode()

    if ack:
        print(ack)
        continue
    else:
        c.close()
        break
```

## OUTPUT

server:

<img width="413" height="308" alt="Screenshot 2026-05-18 134518" src="https://github.com/user-attachments/assets/4222cdc2-22a4-40e0-bc73-14ecda8dc0fb" />

client:

<img width="316" height="170" alt="Screenshot 2026-05-18 134526" src="https://github.com/user-attachments/assets/359893d4-f52c-424f-8385-5994df2a79e7" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
