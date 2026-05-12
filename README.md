# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
```
client.py:
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
   while(i<len(l)):
    st+=s
    c.send(str(l[i:st]).encode())
    ack=c.recv(1024).decode()
    if ack:
       print(ack)
       i+=s

server.py:
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True: 
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())


```
## OUPUT:
client side:
<img width="1920" height="1140" alt="client_op" src="https://github.com/user-attachments/assets/43a82708-ef79-47a3-bf64-f03bebea1e74" />

server side:
<img width="1920" height="1140" alt="server_op" src="https://github.com/user-attachments/assets/5a20407a-8a9e-4065-86c0-7763ab22e1ad" />

## RESULT
Thus, python program to perform sliding window protocol was successfully executed
