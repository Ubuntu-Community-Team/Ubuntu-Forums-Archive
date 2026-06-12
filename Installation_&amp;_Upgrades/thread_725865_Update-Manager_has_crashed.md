---
title: "Update-Manager has crashed"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by yeehaw123 on 2008-03-16
Dear Ubuntu Community,

I have recently installed Ubuntu 7.10, and when it was ready it asked me if I wanted to install updates. I said yes, entered my password and it started installing updates. Until it crashed, I still need to install 48 updates, but they don't show anymore. :(

I would like to know which logfiles are needed to solve this problem, so i can post them too, and if anyone knows an solution

yeehaw123.

ps. I have searched, but only found threads that have no solutions.

---

### Post by banewman on 2008-03-16
I would try typing in a terminal - 
sudo apt-get update
and see the response - it should work if apt is ok
:)

---

### Post by yeehaw123 on 2008-03-16
Thanks for your reply! Will try when i get home:)

---

### Post by bioShark on 2008-03-17
Thanks **banewman**, it helped me with the exact same problem, however after I ran:

> sudo apt-get update

I got an error, and I needed to run:

> sudo dpkg --configure -a 

and after that again

> sudo apt-get update

Thx

---

