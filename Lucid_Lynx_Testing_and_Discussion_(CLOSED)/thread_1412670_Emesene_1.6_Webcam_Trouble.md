---
title: "Emesene 1.6 Webcam Trouble"
date: 2010-02-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by DoeRayMe on 2010-02-21
Well basically whenever i send or receive webcams, it hangs for like 2 minutes, then disconnects, i dont get to see anything.

Anyone know how to fix this problem, as its rather annoying now :(

Thanks
Will

---

### Post by cariboo on 2010-02-21
Are you getting any errors in the logs, to show what's happening?

---

### Post by DoeRayMe on 2010-02-21
> **cariboo907 said:**
> Are you getting any errors in the logs, to show what's happening?

Been looking around, cant see much, any specific log it would be in?

---

### Post by cariboo on 2010-02-21
Check dmesg, messages and syslog.

---

### Post by DoeRayMe on 2010-02-21
> **cariboo907 said:**
> Check dmesg, messages and syslog.

Checked, cant find anything, so you know, its a **Creative Live! Cam Vista IM** webcam

---

### Post by DoeRayMe on 2010-02-21
Well i have checked the webcam preferences, the webcam shows up there and it shows up and works with cheese

So basically its just having trouble transmitting it and receiving other peoples webcams

---

### Post by DoeRayMe on 2010-02-22
Anyone got any ideas?

---

### Post by DoeRayMe on 2010-02-22
Ok sort of solved, works on amsn, since i opened the ports, i thought emesene would use the same ports, but it still dont work, anyone know which ports it uses?

---

### Post by DoeRayMe on 2010-02-22
Here's some debug code, if it helps

```
Hosts: [('192.168.1.2', 80), ('78.149.253.189', 80)]
Starting SocketHandler thread
Could not bind to port 6892
Exception: <class 'socket.error'>
Error - [Errno 98] Address already in use
Connecting to 192.168.1.2:80
Connecting to 78.149.253.189:80
<<< MSG [TAKEN OUT] 189
<<< ACK 28
<<< ACK 29
Accepted webcam connection from: 78.149.253.189:19310
Connecting to 78.149.253.189:19310
Closing sockets except to 78.149.253.189:19310
Authentication FAILED! Got: recipientid=342&sessionid=1509580610

, but need: recipientid=170&sessionid=1509580610

!
Exception in thread Thread-6:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 527, in __bootstrap_inner
    self.run()
  File "/usr/share/emesene/emesenelib/p2p/transfers.py", line 1175, in run
    asyncore.loop(map=self.socket_map)
  File "/usr/lib/python2.6/asyncore.py", line 202, in loop
    poll_fun(timeout, map)
  File "/usr/lib/python2.6/asyncore.py", line 132, in poll
    r, w, e = select.select(r, w, e, timeout)
  File "<string>", line 1, in fileno
  File "/usr/lib/python2.6/socket.py", line 165, in _dummy
    raise error(EBADF, 'Bad file descriptor')
error: [Errno 9] Bad file descriptor
```

---

