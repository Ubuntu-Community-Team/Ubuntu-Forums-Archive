---
title: "Solaris &amp; Ubuntu Dual Boot"
date: 2007-12-25
forum: Installation &amp; Upgrades
---

### Post by terets on 2007-12-25
I think I have a new and interesting problem, something not seen before.  I have installed on my PC Windows Vista Ultimate on /dev/sda1, Sun Solaris Express Developer Edition build 70 on /dev/sda2 and Ubuntu 7.10 on /dev/sda3.  When I boot up Ubuntu it stops midway with the error that fsck could not check /dev/sda2 (Solaris) and that it must be done manually and then drops into a root shell.  Also, the Ubuntu installed grub automatically recognized /dev/sda2 (Solaris) as being another Ubuntu installation.  How do I get Ubuntu to stop recognizing Solaris as another Ubuntu installation so that it boots up regularly (I can handle the grub issue myself)?  Any help will be much appreciated.

---

### Post by meierfra on 2007-12-25
Boot to ubuntu. Open "fstab" via
```
gksudo  gedit /etc/fstab
```

look at the line concerning sda2. Either put a # in front of the line  and ubuntu will  complete ignore sda2. 
Or change the last number in that line to 0, then Ubuntu will not run "fsck" at boot up. 

But why does fsck fail? Maybe there is something wrong with sda2.

---

### Post by terets on 2007-12-26
Thanks so much.  Putting 0 at the end of the /dev/sda2 line in fstab fixed the problem.  This is one thing I love about Linux, just ask and you get expert advice faster than you could anywhere else.  Did you know it costs money to ask Microsoft a question, even after you paid all that money for their software?  I think you get one free question a year and that is it, then it is $35 per question, at least for Office it is.  I know because I tried.  Here I get a better, faster answer for totally free.  And to satisfy your curiousity, I think the reason fsck failed on /dev/sda2 is because it is Solaris, not Linux.  The operating system and all programs run perfectly, so I doubt something is wrong.  Thanks for the help.

---

