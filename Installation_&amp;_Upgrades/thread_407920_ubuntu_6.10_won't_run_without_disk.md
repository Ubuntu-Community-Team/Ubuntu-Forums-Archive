---
title: "ubuntu 6.10 won't run without disk"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by fenderbender on 2007-04-12
I installed ubuntu 6.10 onto a hard disk dedicated to ubuntu only.  I am running a rack mount system with two seperate hard disks, one ubuntu only and one xp only.  The disk I installed ubuntu on had an old copy of win 98 (fat32) on it and I installed ubuntu over top of the 98. 

The install seemed to go OK and ubuntu seems to be working OK so far (but I'm a linux newbie so I'm not entirely sure about that yet).  The only issue I'm having is that if I try to boot without the ubuntu install disk in the cd drive I get an error about "NTLDR is missing".  I can select the otion to "boot from 1st hard disk" and it proceeds to boot OK.

Since windows is not even in the picture when I'm booting ubuntu I have to assume that the NTLDR error message is a residual issue left on the disk from the original 98 install.  I assumed that the ubuntu install would format and overwright all of the windows crap, but I guess I was wrong.

Any ideas how to resolve this?  If I need to completely wipe the disk and re-install, could you recommend a program (freebie hopefully) that will do that for me? I want to eventually dump windows for good but I'm hesitant to do so until I know that ubuntu is going to work for me.  So far it's looking pretty impessive!

Thanks in advance for your help.

---

### Post by mac.ryan on 2007-04-13
> **fenderbender said:**
> Since windows is not even in the picture when I'm booting ubuntu I have to assume that the NTLDR error message is a residual issue left on the disk from the original 98 install.

Although it might seem so, I would be very surprised if that would be the case, as NTLDR is the "new technology loader", and it is a component of windows NT/XP/2003... but not of 98 systems.

What is not clear to me is: did you install GRUB? I.E: when you power on your system, do you have a text-menu allowing you to choose between XP and ubuntu? If yes, it would be helpful if you could post here the output of the following two commands:

```
sudo fdisk -l
```

(this will allow us to see how your HD partitions are seen from linux)

```
cat /boot/grub/menu.lst
```

(this will allow us to see how your grub thinks it has to launch the OSs...)

---

### Post by mesh_ok on 2007-04-13
**fenderbender**
I had the same problem - changing (hd1,1) to (hd0,1) helps me every time I upgrade kernel and reboot. 
(the file is /boot/grub/menu.lst)
You might need to search for correct address of your partition (what about hd0,0?). Seems that sometimes GRUB confuses itself ;)

FYI: I have hda, sda and sdb. my Ubunty boots from sda1 (windows is sda0) and in bios I've turned hda off, but grub seems to consider hda is always 1st in my boot seq and makes it (hd0) that's why I always have to manually fix the menu.lst file after any new kernel installation.

---

### Post by fenderbender on 2007-04-13
No, I don't get the text menu option for xp or ubuntu.  All I get is an error message "NTLDR is missing" if I don't use the install cd, or if I do use the cd it goes directly into the ubuntu boot options.  Don't forget, I'm not running dual boot.  I have a rack mount system so when I want use use ubuntu I'm removing the xp hard disk completely and inserting the ubuntu hard disk.

This really has me baffled.

Thanks for replying.

---

### Post by mac.ryan on 2007-04-13
> **fenderbender said:**
> Don't forget, I'm not running dual boot.  I have a rack mount system so when I want use use ubuntu I'm removing the xp hard disk completely and inserting the ubuntu hard disk.

Sorry, I misunderstood what a rack system is (I am not a native English speaker)... so, if I get you right this time:[LIST]
[*]when you have the XP HD inserted and boot, you don't have any problems: you get your XP going.
[*]when you have the ubuntu HD inserted and boot, you get the error above[/LIST]If this time i got the picture, then I would say that the problem is your master boot record (MBR), which doesn't ever get formatted, because in fact it doesn't belong to any filesystem. It probably still contains the "stage one" of some windows loader (win98 or XP it doesn't matter). Stage 1 of boot loaders - indeed - is just a "pointer" to the "real stuff", and this is why at the moment your system can't find NTLDR: the MBR "points" to somewhere that has been now formatted and overwritten.

You should be able to solve the matter just installing grub (or Lilo, or GAG...), which indeed will re-install the "stage one" of its own stage one on the MBR and its own "real stuff" on the linux partition. This should correct the issue.

In order to do that, once you are running your installed version of ubuntu (eventually launched from the liveCD) follow [this how-to]("http://ubuntuforums.org/showthread.php?t=224351").

Let us know if it works! :)

**EDIT:** just crossed my mind that if the above mentioned method should not work (i.e. because it can't locate the needed files on your HD) you might also wish to consider a fresh install of GRUB via the [Super Grub Disk]("http://supergrub.forjamari.linex.org/").

---

