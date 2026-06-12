---
title: "Can't get fish (ssh) kioslave to work"
date: 2009-08-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Marsolin on 2009-08-17
Has anyone successfully used fish to connect to an ssh server in Karmic? I'm using Dolphin and keep getting a message that the connection to the host is broken. I've tried upgrading from Jaunty and a fresh install with the same results.

I will get a login prompt come up, but get the connection broken message after entering it in. I also tried using a key in my .ssh directory to login without a password, but get the same results.

---

### Post by inportb on 2009-08-17
Have you tried sftp rather than fish? Some SSH servers are configured to allow file management but not remote control.

---

### Post by Marsolin on 2009-08-17
I didn't think about sftp. I just tried it and it works so that will allow me to do what I need to. It still doesn't explain why fish doesn't work anymore though. It used to on the same server with Jaunty. I guess it's not important now that I can use sftp.

Thanks for the help.

---

