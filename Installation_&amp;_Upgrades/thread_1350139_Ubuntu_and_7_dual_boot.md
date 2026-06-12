---
title: "Ubuntu and 7 dual boot"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by ravi.m.sharma1 on 2009-12-09
**[FONT=Arial]Hey Everyone[/FONT]**

**[FONT=Arial]I am a novice as far as Ubuntu is concerned.I have been banging my head in google to help myself with the dual boot.:razz: but of no use.[/FONT]**

**[FONT=Arial]My Issue Goes like this: [/FONT]**

**[FONT=Arial]Installed Ubuntu 9.04 (32 bit) with existing Vista (64 bit)  on my 320 GB hard drive.I upgraded my Jaunty to Koala as soon as it got released and then I upgraded Vista to Win 7(64 bit).As soon as I did it Win 7 wiped out MBR and therefore I can't access Ubuntu now.[/FONT]**

**[FONT=Arial]I have a Jaunty CD with me and Win 7 CD too.Also, I have a slow internet connection.I do not want to download Karmic afresh and then install it above windows 7.[/FONT]**

**[FONT=Arial]Please help me.:KS[/FONT]**

---

### Post by vidyesh on 2009-12-09
I guess you would have to install Windows 7 again and give it a try. 
Since you removed windows 7 you couldn't even repair it. thats where you messed up.
Or if you ready 2 reinstall both the OS, go  ahead do it.
Install Windows then go for Ubuntu.

---

### Post by ubhi on 2009-12-09
i recoverd my ubuntu by this way.. you can do as well...

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by johndillinger1932 on 2010-01-11
After spending 3 days and one long night trying to dual-boot my girlfriends dell studio xps1340, following instructions found on here I came up with an easy way to do it, and yes you install windows( xp, vista, 7) first.
First back up what ever you need to back up, goes without saying...
then get yourself a grub live cd...
start pc with grub live cd and creat 2 partitions, 1 ntfs and 1 ext3...
when that is done install your version of windows....
after windows is finished installing, put whatever live cd version of ubuntu you want/have ( we used studio jaunty )
install ubuntu..
when that is done, you are done.. no need to reinstall grub at all..oh and **** bill gates!

---

### Post by oldfred on 2010-01-11
If you upgraded in place you still have grub legacy not the new grub2 that comes with new/clean installs of Karmic.  If you upgraded grub to grub2 you will have to download a new liveCD as you cannot mix grubs (then you have a real mess).

Follow the instruction for 9.04 if you did not upgrade to grub2 to reinstall old grub.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by presence1960 on 2010-01-11
+1

Follow oldfred's advice. If you have GRUB 0.97 use 9.04 Live CD, if you upgraded to GRUB2 use 9.10 Live CD.

**_You don't have to reinstall anything to put GRUB back on MBR. _**

Here is what happened: When you installed windows 7 windows overwrote GRUB on the MBR and put the windows bootloader there. All you need to do to get GRUB back is put it back on the MBR.

---

