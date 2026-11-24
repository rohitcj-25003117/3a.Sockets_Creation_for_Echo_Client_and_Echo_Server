# 3a. CREATION OF ECHO CLIENT AND ECHO SERVER USING TCP SOCKETS

## AIM
To write and execute a Python program to create an Echo Client and Echo Server using TCP sockets.

## ALGORITHM

1. Import the socket module in Python.
2. Create a TCP socket using the socket module.
3. Bind the server to the localhost and port number 12345.
4. Make the server listen for client connections.
5. Accept the client connection.
6. Connect the client to the server.
7. Send messages from the client to the server using the `send()` function.
8. Receive messages using the `recv()` function.
9. Display the received message and send it back to the client.
10. Stop communication when the client sends "exit".
11. Close the socket connections.

## PROGRAM

### SERVER PROGRAM (SERVER3a.py)

```python
import socket

s = socket.socket()
s.bind(('localhost', 12345))
s.listen(1)

print("Server waiting...")
c, addr = s.accept()
print("Client connected")

while True:
    msg = c.recv(1024).decode()

    if msg == "exit":
        break

    print("Client:", msg)
    c.send(msg.encode())

c.close()
s.close()
```

### CLIENT PROGRAM (CLIENT3a.py)

```python
import socket

s = socket.socket()
s.connect(('localhost', 12345))

while True:
    msg = input("Enter message: ")
    s.send(msg.encode())

    if msg == "exit":
        break

    data = s.recv(1024).decode()
    print("Echo:", data)

s.close()
```

## OUTPUT

### Server Output

```text
Server waiting...
Client connected
Client: Hello
Client: Welcome
Client: How are you?
```

### Client Output

```text
Enter message: Hello
Echo: Hello

Enter message: Welcome
Echo: Welcome

Enter message: How are you?
Echo: How are you?

Enter message: exit
```
## OUTPUT
<img width="1280" height="763" alt="image" src="https://github.com/user-attachments/assets/f80bb555-015b-40a7-a711-b5318a7e7bbb" />


## RESULT

Thus, the Python program for creating an Echo Client and Echo Server using TCP sockets was successfully created and executed.
