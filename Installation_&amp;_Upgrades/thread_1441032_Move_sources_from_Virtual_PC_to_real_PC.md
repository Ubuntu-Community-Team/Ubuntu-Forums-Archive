---
title: "Move sources from Virtual PC to real PC"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by Fire Cat on 2010-03-28
Hey everybody,
So I need help for one thing. I am running Ubuntu Studio 9.10 on Microsoft Virtual PC. After using it a lot, I have decided to move to a real machine. The thing is, I don't have the time to reinstall ubuntu and all the programs and move my docs. So i wanted to copy/move the content of my virtual HDD to put it on a real one. But when I try copying th e OS, it says that i don't have permission to do that. 
What can I do?
 
Thanks
Fire Cat

---

### Post by labinnsw on 2010-04-04
I am taking it that you already have Ubuntu installed but do not want to do all the updates or reinstall your programs. First see the last section of the attached instructions. Then in a terminal type or copy and paste ```
sudo nautilus
``` This allows you to work as super user. After you copy the stuff across, you will also need to run the following commands in a terminal. (copy and paste)

```
sudo chown yourusername .dmrc
chmod 644 .dmrc
chmod 700 ~
```

Alternatively you could use the attached instructions to backup the virtual system and restore it on the real drive. To do this you will need either a working installation of Ubuntu or you will need to install it. (I don't believe it will take as long as you believe it will) Pay special attention to the last section of the instructions before you start the restoration process.

---

