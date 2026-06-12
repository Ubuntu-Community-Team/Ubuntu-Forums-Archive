---
title: "lsusb hangs 8.04"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by fishtoprecords on 2008-04-29
Hi, I'm trying to debug my LogiTech Quick Cam Chat webcam. Its a cheapie, cost $20 and seemed to work well with 7.04. (the problem is lack of color, but that's not why I'm posting)

I've just upgraded to 8.04, and most stuff is working (thanks to folks here) but I'm not having reliable luck with my webcam.

The first step in debugging it is to check the results of 'lsusb' but it hangs often. No response, the shell just freezes. checking 'top' doesn't show anything.

So first, I have to get to where I can run lsusb and change things.

Any hints or tips?
Thanks
Pat

---

### Post by Aelfric5578 on 2008-08-24
Does anyone know what could be causing this?  I am having the same problem.  The only difference is that in my case the offending device is a USB mouse, and using a GUI without a mouse is just a bit difficult.  The mouse was working the first day after I installed Hardy, then it simply stopped.  I have a suspicion that this might be a general USB issue, and lsusb hanging reinforces that suspicion.

---

### Post by krystallkitty on 2008-08-25
I am also having this problem, in that i am trying to install a Genius MousePen Tablet and i cannot get the computer to recognize the Usb that is plugged in and now lsusb has stopped working....

only i haven't ever had this device work, (it's new) but the light on it is flashing when i touch the pen to it but there is no response in my laptop

---

### Post by spiderbatdad on 2008-08-25
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260891](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260891)
Problem may be related to the above referenced bug.
Start by obtaining a dmesg log```
dmesg > ~/Desktop/dmesg.txt
```This will write a file to the desktop, useful for confirming the bug above, or posting here as an archive for possible help. To post here: right click the file and select "create an archive." Upload the file here or on launchpad as an archive.

---

### Post by krystallkitty on 2008-08-25
Well, see with mine i havent had issues with any other usb port devices at all.

I've searched the web and i've found this problem several times but no one has seemed to be able to find an answer...

The thing is, there's absolutely no problem with my tablet, i plugged it into my grandpa's vista computer and it began working in no time.

---

### Post by Aelfric5578 on 2008-08-26
Here is the output of dmesg.  I don't think it's the same bug that you directed us to, because rebooting does not restore USB functionality.  I hope someone can help me solve this problem.  Right now I'm relying primarily on synergy to control my desktop, and the controller is on somewhat flaky wireless leaving me mouseless when what I really want to do is share the wired connection using a USB ethernet adapter.  It might also be worth mentioning, often when I am completely without a mouse alt-tab locks up as well.  Though I suppose that is most likely unrelated.

---

### Post by darklordveynom on 2008-10-20
I'm having the same problem, but it's with my Kingston 2Gb flash drive. It's odd too because I have a laser optical mouse attached to the USB and it works fine. Here is my dmesg.

---

