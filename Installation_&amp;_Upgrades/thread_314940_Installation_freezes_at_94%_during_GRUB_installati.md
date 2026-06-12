---
title: "Installation freezes at 94% during GRUB installation"
date: 2006-12-08
forum: Installation &amp; Upgrades
---

### Post by TADsince1995 on 2006-12-08
Hi guys!

I'm trying to install ubuntu edgy eft desktop 6.10 AMD64 and I cannot manage to have it installed.

After booting from CD I launch the installer, everything goes well until it reaches 94% of the installation process, during the execution of "grub -install (hd0)". The installation process stops here.

Someone suggested me to clean up the MBR (which was containing a lilo installation of my slamd64 distro, which I'm substituting with ubuntu), I tried it and then restarted the installation, but no way. It blocks again at 94%, during grub installation. I tried several times.

This is my configuration:

AMD Athlon64 3500+
ASUS Motherboard A8N SLI
HD 120 Gb EIDE with 3 partitions: Windows (hda1) Linux (hda2) Swap (hda3)
HD 300 Gb Serial ATA with a NTFS partition for shared data storage.

Please help me, this is the first time I try to install ubuntu!

Thank you very much!

Regards,

TAD

---

### Post by bulldog on 2006-12-08
Did you check the live cd on errors?
Did you burn the Image on low speed,high speed burning delivers more often a bad install cd.
If you checked this and it's alright then disconnect the Sata disk,and try it again.
You can add this partitions manually in fstab if the installation will succeed this time.

---

### Post by TADsince1995 on 2006-12-10
OK guys, at the 7th try, GRUB installed!!! I don't know the reason of this problem. Now I'm edgy up and running.

Thank you!

TAD  :)

---

### Post by Seamyst on 2006-12-13
I'm having the exact same problem.  I'm trying to install Edgy on a MacBook with three partitions - for Tiger, Linux and Swap.  It installs just fine until it reaches 94% and tries to install GRUB in (hd0).  Then it stops and says there's a fatal error and the installation cannot be completed.  I've tried it several times and tried to see if I could change the location GRUB would be installed... no luck.  I'm a total Ubuntu/Linux newbie so I could be doing something really simple wrong.

Should I just keep trying and trying until it works for me, if it does?  Should I choose a certain place for GRUB to install?  Should I do something else?

---

### Post by bulldog on 2006-12-13
Try this from the live cd.
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

Watch for the error messages and write them down so we can have a look at them.

---

### Post by Seamyst on 2006-12-23
Okay, I did exactly as you said and got an error message right away.  I was able to get to the grub prompt, but when I typed in "find /boot/grub/stage1", it gave me an error message:  "Error 15: File not found".  I tried this several times, even closing the Terminal and opening it again, all with the same message.

---

### Post by nvurusic on 2007-01-06
I am having the same problem, too... I tried to install it a few times (4-5), and it always stops at exactly 94%?

Any hints?

Nenad

---

