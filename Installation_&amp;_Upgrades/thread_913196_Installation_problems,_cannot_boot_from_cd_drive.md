---
title: "Installation problems, cannot boot from cd drive"
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by Dalston on 2008-09-07
Hello im trying to reinstall XP and then ubuntu 8.04,  both from disk.  The problem is when I restart and then press f12 to change it to boot from cd,  nothing happens it just boots up ubuntu.  I have tried using 2 different versions of xp that I have previously used to install and my original version of ubuntu, all 3 end the same way.  Can someone help me out please.
Thanks

---

### Post by father time on 2008-09-07
Message Deleted.

---

### Post by Dalston on 2008-09-07
Does someone know of a reason why it wont let me boot from start up?

---

### Post by Dalston on 2008-09-07
I've been a member of these forums for a few years and it never fails to solve my problems.

ok sorry forgot to put all the relevent info.

1. Yes I have previously installed from both copies of xp and also the 7.04 live cd.
2. I have an AMD Athlon 64 processor 3200+,  512MiB ram
3. I am using ubuntu 8.04 upgraded from 7.10 upgraded from 7.04.

---

### Post by father time on 2008-09-07
Message Deleted.

---

### Post by Dalston on 2008-09-09
Thanks for your help, I think its a Grub issue because after I press f12 it doesnt give me the option to 'press any key to boot from disk' it just goes straight to starting up Ubuntu.  Im not using the amd64 distro im using ubuntu-8.04-desktop-i386

---

### Post by lowstand on 2008-09-09
most computers you hit F2 to get to bos   an then just go in an ask it to boot from cd   or if you have the built in  restore on your drive it will give you the option under your boot from  most of the time 

hope this helps

---

### Post by oilchangeguy on 2008-09-09
> **Dalston said:**
> Thanks for your help, I think its a Grub issue because after I press f12 it doesnt give me the option to 'press any key to boot from disk' it just goes straight to starting up Ubuntu.  Im not using the amd64 distro im using ubuntu-8.04-desktop-i386

grub has nothing to do with the boot selection. when your computer is posting (Power On Self Test) the operating system is not yet involved. try entering the bios and setting the boot from there.

---

### Post by JMorg on 2008-09-09
Definitely try Oilchangeguy's option of manually/permanently altering it within the BIOS. Make your optical drive the primary boot device, and if that doesn't fix your issue then attempt to use a new  optical drive or an external optical drive because i'm venturing to say that your hardware is failing.

---

### Post by Dalston on 2008-09-12
Ok update:  I still cant boot an xp disk from boot, I have tried altering the bios but I cant boot,   sometimes I get the error 'cannot boot from cd error 5' and sometimes I get 'cannot find NTLDR' anyone got any ideas?

edit: Oh yeah I tried both disks on another pc and they both booted fine.

---

### Post by Dalston on 2008-09-14
Sorry for the bump but I am at a loss as of what to do.

---

