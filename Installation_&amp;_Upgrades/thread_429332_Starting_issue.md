---
title: "Starting issue"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by fficsori on 2007-05-01
Hi folks, 

I have some issues running Feisty. Just installed Feisty, after booting, login name and password is required. First it didn't work with the password I provided during installation, so I changed password in command line, after which I could log in successfully. Then I thought it would run normally but it didn't. It says login was successful, writes there the time of the last login and then it says: "The programs includedwith the Ubuntu system are free software; the exactdistribution terms for each program are described in the individual files in /usr/share/doc/*/copyright. Ubuntu comes with ABSOLUTELY NO WARRANTY to the extent permitted by applicable law." Then my user name is there and my hostname and and the cursor is there waiting for something else and I have no idea what to type there in order that the system would start. What do I need to do now? How to go on?

Thanks

---

### Post by lw5 on 2007-05-01
Actually your system is started and completely functional. It just hasn't started your graphical environment. Try  giving a 'sudo startx'.

---

### Post by fficsori on 2007-05-01
I also have a feeling everything's ok its just that I miss something minute. Tried sudo startx, then since started with sudo, asks for my password. Typed password and then it says command not found.

I was thinking about running the whole thing from the live CD and install from that disk. Will it work?

---

### Post by lw5 on 2007-05-01
You mean a complete re-installation? That will probably work, yes ;)

Otherwise, are you sure you only changed your password and nothing more? 'cause it sounds like a bit more is going on..

---

