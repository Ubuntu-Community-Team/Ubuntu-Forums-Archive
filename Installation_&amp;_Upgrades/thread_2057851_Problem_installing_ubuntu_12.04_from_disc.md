---
title: "Problem installing ubuntu 12.04 from disc"
date: 2012-09-14
forum: Installation &amp; Upgrades
---

### Post by Macca55 on 2012-09-14
I have tried installing ubuntu v12.04 from disc and after installation i get an error message saying
 
'An error occured:
 
Permission Denied
 
for more information, please see the log file'
 
I have accessed the log file and uploaded it [here]("http://pastebin.com/j8A2bn84")
 
I want to be able to dual-boot ubuntu 12.04 with my current O/S which is windows XP.
 
Any help or possible fixes would be appreciated
 
Thanks in advance
Macca55

---

### Post by micahpage on 2012-09-14
What is the process in which you install linux to dual boot?

---

### Post by oldfred on 2012-09-14
I do not know wubi.

But I see this message a few times. Is your computer 32bit? And did you try to install the 64bit version?
> 
Distro: wrong arch: i386 != amd64

There also may be issues with wubi and even if computer is 64bit, if Windows is 32bit you really need to use 32bit Ubuntu. 

How much RAM do you have? And what video card.

[https://help.ubuntu.com/12.04/installation-guide/amd64/minimum-hardware-reqts.html](https://help.ubuntu.com/12.04/installation-guide/amd64/minimum-hardware-reqts.html)

---

### Post by Macca55 on 2012-09-14
> **micahpage said:**
> What is the process in which you install linux to dual boot?
 
I insert the the original ubuntu disc and try to install via booting the disc

---

### Post by Macca55 on 2012-09-14
> **oldfred said:**
> I do not know wubi.
 
But I see this message a few times. Is your computer 32bit? And did you try to install the 64bit version?
 
 
There also may be issues with wubi and even if computer is 64bit, if Windows is 32bit you really need to use 32bit Ubuntu. 
 
How much RAM do you have? And what video card.
 
[https://help.ubuntu.com/12.04/installation-guide/amd64/minimum-hardware-reqts.html](https://help.ubuntu.com/12.04/installation-guide/amd64/minimum-hardware-reqts.html)
 
My computer is 32bit and i am attempting to install ubuntu which i believe is 32 and 64bit.

I have uploaded my pc's specs [here]("http://uploaded.net/file/9zm10evm")

---

### Post by oldfred on 2012-09-14
You can attach screenshots or text with the paperclip icon in the edit panel above the message. Or paste as code and use code tags. Highlight and click the # in the edit panel.  

Did you want to install as wubi? Or a full partitioned install?

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

