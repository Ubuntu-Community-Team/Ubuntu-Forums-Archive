---
title: "Ubuntu 11.04 does not work well with Sandisk USB stick with U3 launchpad"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Fanolian on 2011-04-29
TL;DR: If you have problem using Ubuntu 11.04 from USB, remove the U3 launchpad if you do not need it at all. It may solve your problem.
Link: [http://u3.sandisk.com/launchpadremoval.htm](http://u3.sandisk.com/launchpadremoval.htm)



I am not a Ubuntu/Linux user but I do keep a copy of Ubuntu LiveUSB in my Sandisk cruzer micro 8GB USB stick in case of system failure. It comes with the U3 lanuchpad that I never use.

The USB stick was working happily with Ubuntu 10.04 and 10.10. However when I formatted the stick and put Ubuntu 11.04 (checksum is ok) into it, it failed to boot from the stick every single time. I was getting this error even though I have disabled all(one) my physical DVD-RWs in BIOS: ```
mounting /dev/sr0 on /cdrom. failed Device or resource busy.
(I do not remember the wording...)
``` The error message appeared when I saw the Ubuntu logo and the five animating dots. So I decided to remove U3 launchpad and voilà! I could boot for the first time (and 6th time in a row without problem now).

sidenote: My physical DVD-RW drive is still blocking the bootup half of the times even if there is no discs in it. Disabling the drive in BIOS solve the problem. The error occurs before I see the five animating dots. The screen stops at ```
[*figure varying each time*] scsi 0:0:0:0: CD-ROM PIONEER DVD-RW DVR-111 1.29 PQ:0 ANSI:5 
```

---

### Post by LebLinux on 2011-04-29
Confirmed. As Fanolian said; remove launchpad and redo it. Thanks!

---

### Post by flattop1 on 2011-04-30
I have the same problem..
but I dont  use windows so how do I get rid of the u3 launchpad software using ubuntu?

---

### Post by Bao2 on 2011-04-30
So the solution to be able to use my SanDisk (that worked fine in ubuntu 10.10) is to go to the street and ask someone if has windows and let me run a tool to make my sandisk working in linux again. And this thread was marked solved??? :popcorn:

---

### Post by eks on 2011-05-01
[Wasted around 8 hours on this issue yesterday...]("http://ubuntuforums.org/showthread.php?t=1744679") My workaround was to install Kubuntu 10.10 with a SanDisk USB flash drive then upgrade it to 11.04.

Kubuntu Natty CD and DVD were crashing with the stick formatted in both fat32 or ext2. Haven't tried removing U3 launchpad, will do that next time I boot into Windows (not today).

Updated the [wiki]("https://help.ubuntu.com/community/Installation/FromUSBStick").

---

### Post by mörgæs on 2011-05-01
You can also remove U3 with **u3-tool** found in the Ubuntu repositories.

Using Killdisk as described here 
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)
is a good idea for erasing USB drives. It does not remove U3, though.

---

### Post by Cibomatto2002 on 2011-05-02
xubuntu 11.04 really did a number on my flash drive SanDisk 16 Gigs now Windows or xubuntu can not read it I can't even format it the computer does not know how big the Flash drive is anymoe :( 

I was using Linux Live USB creator version 2.7.6[B][URL="http://www.google.com/url?sa=t&source=web&cd=1&ved=0CB8QFjAA&url=http%3A%2F%2Fwww.linuxliveusb.com%2F&rct=j&q=lili%20usb&ei=DPS-TaUhg9zRAZe9idIF&usg=AFQjCNGHi-98clOd_uDJInMlbh4p2Xb4bw&cad=rja"]
[/URL][/B]

---

### Post by mörgæs on 2011-05-02
Did you try what I suggested in the post above?

---

### Post by amr2205 on 2011-05-02
I confirm that the solution provided by Fanolian worked for me.

---

### Post by Cibomatto2002 on 2011-05-02
When I use Killdisk I get Error Opening Drive Handle.

This is the driver that is installed WPD FileSystem Volume Driver.

I think somehow it installed the wrong driver after the USB key crashed.

---

### Post by mörgæs on 2011-05-03
If Killdisk can not see the USB stick, it is likely defect.

---

### Post by Cibomatto2002 on 2011-05-04
It was working just fine until I tried to install Kubuntu 11.04 I still like Kubuntu a lot :)

I think it is some kind of I/O error.

---

### Post by Bao2 on 2011-05-06
> **amr2205 said:**
> I confirm that the solution provided by Fanolian worked for me.

It works but it must not be the solution.
Imagine I am working in a shop and my customers bring me files in the USB. Some of them are SanDisks. How am I going to convince them that I must to remove the U3 Launch thing for me to be able to access their USBs??? In ubuntu 10.10 I had no problem reading all the USBs. Now I can't read SanDisks anymore in 11.04.

This is a serious problem. And please mark it as NOT SOLVED THREAD. It is not solved. I can't modify my customers USBs to read them! :(

---

### Post by mörgæs on 2011-05-07
The problem is not accessing files on the USB stick. 

Original poster is talking about booting from USB.

---

### Post by Kangarooo on 2011-05-22
Bug [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/773304](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/773304)
Cant install Ubuntu 11.04 from flash disk
It works with Xubuntu 11.04 but not Ubuntu 11.04

---

### Post by notesetter on 2011-06-01
I would bet that both issues - the boot issue and the problems using a cruzer with U3 under a HDD installation of 11.04 - are caused by [this bug]("http://www.mailrepository.com/ubuntu-bugs.lists.ubuntu.com/msg/3458458/"). Removing the U3 fake cdrom seems to be the only workaround at the moment.

---

### Post by atharfaraz on 2011-10-11
> **Fanolian said:**
> TL;DR: If you have problem using Ubuntu 11.04 from USB, remove the U3 launchpad if you do not need it at all. It may solve your problem.
Link: [http://u3.sandisk.com/launchpadremoval.htm](http://u3.sandisk.com/launchpadremoval.htm)



I am not a Ubuntu/Linux user but I do keep a copy of Ubuntu LiveUSB in my Sandisk cruzer micro 8GB USB stick in case of system failure. It comes with the U3 lanuchpad that I never use.

The USB stick was working happily with Ubuntu 10.04 and 10.10. However when I formatted the stick and put Ubuntu 11.04 (checksum is ok) into it, it failed to boot from the stick every single time. I was getting this error even though I have disabled all(one) my physical DVD-RWs in BIOS: ```
mounting /dev/sr0 on /cdrom. failed Device or resource busy.
(I do not remember the wording...)
``` The error message appeared when I saw the Ubuntu logo and the five animating dots. So I decided to remove U3 launchpad and voilà! I could boot for the first time (and 6th time in a row without problem now).

sidenote: My physical DVD-RW drive is still blocking the bootup half of the times even if there is no discs in it. Disabling the drive in BIOS solve the problem. The error occurs before I see the five animating dots. The screen stops at ```
[*figure varying each time*] scsi 0:0:0:0: CD-ROM PIONEER DVD-RW DVR-111 1.29 PQ:0 ANSI:5 
```

Hey guys i found a way to make sandisk-pendrive to work with UBUNTU, plug in to windows once format the pendrive by keeping  allocation unit size to default allocation unit size and then plug it on ubuntu.. you'll find it working :p

---

