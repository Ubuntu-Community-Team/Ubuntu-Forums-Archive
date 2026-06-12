---
title: "Difficult one: Install Ubuntu from XP dual boot (no CD nor USB boot capable)"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by menosesmas on 2009-12-05
Let's see if there is a solution for this problem.
 
**- Objective**: A dual boot Notebook XP / Ubuntu (or Puppy Linux).
**- Reason**: Need a low RAM consuming OS for an old Notebook (183 MB RAM, 1 GHz), just for fun (XP SP3 is too clumsy for this hardware). 
 
The fact is that the Notebook is old enough to be unable to boot from a live USB, and the CD-ROM unit does not work :( (died years ago).
 
I've managed to start Ubuntu and Puppy Linux with MobaLiveCD emulation software (version 2.1) with loooooots of patience and time, but i'm unable to install Linux from that source (it gets stuck before starting installation process)...
 
I don´t see any other solution, if it is not possible to run a liveCD or liveUSB with a fresh start, maybe there is no other way to install Ubuntu... 
 
Or not? ](*,)

---

### Post by blandhrr on 2009-12-05
If I understand your question correctly, and you have internet access on the laptop, you could do a WUBI install from XP and then do a wubi-move-to-partition (see  [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)). I have not checked this link recently but I recall that the script had not been updated for the Grub2 changes in 9.10.  I worked around this with a LiveCD to fix Grub.

Perhaps the trick is to install 9.04 (it uses the 'old' Grub) via WUBI and then do an upgrade to 9.10.

---

### Post by phillw on 2009-12-05
> **menosesmas said:**
> Let's see if there is a solution for this problem.
 
**- Objective**: A dual boot Notebook XP / Ubuntu (or Puppy Linux).
**- Reason**: Need a low RAM consuming OS for an old Notebook (183 MB RAM, 1 GHz), just for fun (XP SP3 is too clumsy for this hardware). 
 
The fact is that the Notebook is old enough to be unable to boot from a live USB, and the CD-ROM unit does not work :( (died years ago).
 
I've managed to start Ubuntu and Puppy Linux with MobaLiveCD emulation software (version 2.1) with loooooots of patience and time, but i'm unable to install Linux from that source (it gets stuck before starting installation process)...
 
I don´t see any other solution, if it is not possible to run a liveCD or liveUSB with a fresh start, maybe there is no other way to install Ubuntu... 
 
Or not? ](*,)

Does said wee beastie have any operating system on it - and a working internet connection ?

Phill.

---

### Post by phillw on 2009-12-05
Actually, cancel that - there's a good thread over here on the matter --> [https://www.linuxquestions.org/questions/damnsmalllinux-42/install-dsl-onto-a-external-harddrive-then-plug-into-a-laptop-521095/](https://www.linuxquestions.org/questions/damnsmalllinux-42/install-dsl-onto-a-external-harddrive-then-plug-into-a-laptop-521095/)

If nothing else, it will let you ponder your options.

Regards,

Phill.

---

### Post by Alexis Phoenix on 2009-12-05
If I've understood you correctly, this is what I would do.

(Okay, having written everything below, maybe you could see if a network boot is possible?  Debian lets you install this way, I presume Ubuntu will.  But on with my first idea...)

Create a partition using XP which your Linux is going to live in.

Get some kind of Windows program which understands ext3 (or at least ext2) filesystem.  Format the partition.

Run your live cd image in MobaLive (sounds cool).

Copy everything from the running live cd system, into your new partition, except for /proc and /sys.  Likely it is using udev, so don't copy /dev either, but check this.  No udev means you need to copy /dev.

Okay.  You most likely have to change some things to get a bootable system.  Also, some binaries may not work if they have been compiled to run from a cd image.  This is something I don't know about so am speculating, however once it's running you may have to uninstall stuff, change your sources, and reinstall.

In the new partition, look for a folder called /boot/grub.  Here you should find a file called menu.lst.  Assuming you  have an ide hard disk, you need to make sure there is an entry which refers to the Linux installation.  I'll leave it to you to research what you need to change, or someone wiser than me to fill in the gap.

Okay, that's the easy part.  The hard part is, you need to somehow run the "update-grub" command, which means you need to have a running linux system on the computer.  I hope MobaLive would let you do this.  Otherwise, without a boot disk, I don't know.  I'm sure you can get multi-boot loaders that will install from Windows though - that would do it.  No need for grub then. Hmmm.

I hope this is of some help!

Alexis

---

### Post by menosesmas on 2009-12-06
**Thanks a lot** for your quick answers.
Fortunately, now  I have enoguh info to give it a second try. 
I'll post the results if I finally get it. 
 
Best regards !!!
:D
 
 
Additional notes:
- No LAN boot is possible with this PC (BIOS only allows HDD, 3.5" diskette and CD-ROM boot).
- Internet connection is possible through XP. (I dont know if the PCMCIA card will be compatible with Ubuntu becuse it has a TI chipset . D-Link AirplusG+ DWL-G650+)

---

### Post by menosesmas on 2009-12-06
Well, finally _it was not so difficult_.
 
**Wubi** installer did the job **surprisingly easy**.  Having XP installed and a working internet connection it was just as **easy** as installing another windows application. #-o
 
Anyway I read through the thread **phillw** wrote ( [https://www.linuxquestions.org/questions/damnsmalllinux-42/install-dsl-onto-a-external-harddrive-then-plug-into-a-laptop-521095/](https://www.linuxquestions.org/questions/damnsmalllinux-42/install-dsl-onto-a-external-harddrive-then-plug-into-a-laptop-521095/) ) and was quite interesting, but the problem was even worse as the laptop did not have ANY working OS. (Here I managed to install XP before).
 
Well for now on, I may study some performance tweaks. RAM is at 70% usage (110 MB, that is quite a good start for this laptop), I have ubuntu installed over NTFS instead of Ext3, and it doesn't recognize my wireless PCMCIA Card, and I may try Alexis solution to install Puppy Linux (which consumes only 32 MB of RAM) .... but .... that will be another story ... ;)
 
[SIZE=4]Thanks ![/SIZE]

---

