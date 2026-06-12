---
title: "Can't boot my PC after install of Ubuntu 10.04"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by mijohans on 2010-05-08
Hi,

I have Windows Vista on PC and installed Ubuntu 10.04 with the dual boot so that I can choose which OS at startup.

Installation of Ubuntu worked fine, and when it asked me to restart the system it also worked fine.

But then when I tried to restart Windows, toogled down blue screen came up.

Tried to restart again, but then the only things that happedn is grub rescue prompt???

What can I do to save my installations ? I have alot important files from my Windows installation.

I can reboot the system from Live CD and I can see all the windows files. But what has happend to my dual boot ?


Can anybody help me fix this ?


Thanks

---

### Post by Kevanx on 2010-05-08
**Always backup your files before an upgrade.**
The good news is that if you can see your files, you can easily back them up from the live CD - you'll just need to get them onto another computer across a network, burn them onto media, or transfer them to an external hard disk.

BUT...

you should be able to fix the boot issues!

To be clear:
you can't log into either windows OR ubuntu, but after the install, you *did* sucessfully log back into ubuntu?
What does the grub rescue prompt say?

---

### Post by mijohans on 2010-05-08
Yes, firstime after installation I did sucessfully log back into Ubuntu. It worked fine.
Something happend when I tried restart windows for the firsttime. Got a bluscreen.

And when I tried to restart again, the menu were I can choose windows or Ubuntu will not appear again.
The only thing that comes up is
Grub Rescue >

Can this be fixed ?


I can see and are trying to save files via Live CD Ubuntu

---

### Post by Kevanx on 2010-05-09
I would try repairing first. if the install was successful, then you've probably got an MBR error, which is annoying, but not too tricky to fix.

Try following the instructions here:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

If you have any problems, I'll keep checking for responses.

---

