---
title: "2 problems, one is modem, one is XP boot."
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by soonerborn on 2007-02-09
I have just installed amd64 and I have 2 problems that I would appreciate any assitance with.

1.  I have a USB modem, Zoom Telephonics series 06375.  Everything I saw prior to install lead me to believe that I would have no problems using an external modem.  Please help with suggestions on how to install this.  I do not have internet access with the computer, so any files I have to download will have to be put on a CD and xferred to the comp.

2.  After installing Ubuntu I cannot boot to XP.  This is not the same problem I have seen in other recent posts.  It does not matter if I boot into safe mode or normal, it does a reboot shortly after the XP splash shows.  In safe mode I get the command lines instead of a splash and it reboots when it gets to a346bus.sys, I dunno what this is or how to deal with this other than using the XP recovery which I am sure will lead to problems with my shiny new Ubuntu install.  If someone can point me to a thread (I cant find one) or guide about this I would greatly appreciate it.  I do have SATA support but I am not currently using it, only using an IDE drive.

Athlon 64 3200
Asus K8V se deluxe
Radeon 9800 Pro
XP Pro :( and Ubuntu :)

Oh and I am a Linux newb so take it easy on me. :)

---

### Post by soonerborn on 2007-02-11
Someone please help me with this modem problem.

I can understand not getting help about the XP situation, after all this is an Ubuntu forum, but I really really would appreciate some help with the modem.

---

### Post by the.phantom on 2007-02-11
i am NOT a expert !
i have a external modem but it is a serial one !
the way i understand it is you will still need drivers for a USB modem and most are just written for windows
i had a softmodem ( winmodem) 
so my solution was i got a "best data"56sx-92"modem
and it is a hardware modem that will work on about everything

of you want to try and get drivers and install a usb might look here
[https://help.ubuntu.com/community/DialupModemHowto/Which](https://help.ubuntu.com/community/DialupModemHowto/Which)

---

### Post by Herman on 2007-02-11
> 2. After installing Ubuntu I cannot boot to XP. This is not the same problem I have seen in other recent posts. It does not matter if I boot into safe mode or normal, it does a reboot shortly after the XP splash shows. In safe mode I get the command lines instead of a splash and it reboots when it gets to a346bus.sys, I dunno what this is or how to deal with this other than using the XP recovery which I am sure will lead to problems with my shiny new Ubuntu install. If someone can point me to a thread (I cant find one) or guide about this I would greatly appreciate it. I do have SATA support but I am not currently using it, only using an IDE drive. Are you using grub?
If you are, it sounds like grub is chainloading XP successfully, but there is a problem with XP after its own bootloader takes over.

I don't know what can cause a problem like that. Possibly it could be related to some kinds of partitioning or filesystem problem?

Here is a link to a how-to for making a floppy disk that can boot Windows almost no matter what. [How to make your own Windows Xp boot floppy]("http://support.microsoft.com/kb/305595/EN-US/")

Other than that, if it still won't boot, it might be a partitioning or filesystem problem, if you get yourself a [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") you should be able to boot that and be able to tell at a glance if the partition is healthy or not.
You can also sometimes tell by using sudo fdisk -lu and often partitioning errors can sometimes be seen from the output if you know what you are looking for. Partitioning errors can be caused by glitches in the partition table left over from using a non-linux partitioner at some time in the past.  ```
sudo fdisk -lu
``` You might want to do a filesytem check with GParted too, just right-click on the partition and click 'check'. I think it's pretty good, even for an NTFS filesytem, but I don't have any NTFS filesystems anyway, so I haven't tried it myself. I know it is excellent for FAT filesystems and Linux filesystems. I fixed my wife's MP3 player that way today. (FAT16).

---

### Post by soonerborn on 2007-02-11
the.phantom your plenty expert enough for me, big thank you for that link, I actually have a winmodem (PCI) that I previously just assumed wouldnt work because of the win, and its all shiny and new so it should work.

Thanks to you also Herman, yes Grub is doing its job fine, I can actually see the XP boot splash for a second or two, before it crashes, and its booting Ubuntu just fine.  Unfortunately its not as simple of a fix as using a boot floppy.  IMO I am going to have to use a XP install dvd to fix it (as I suspect there are some problems with some system files caused by the repartitioning).  Which puts me in a pickle because I have lost my original in a recent move.  I am going to borrow one from somebody, but I suspect that sucky old microsoft has some kind of key recognition that will prevent me from using it.  Even if it does let me, I further suspect that using said dvd will damage my Ubuntu.  So if I didnt need a few choice programs and games that Linux doesnt support I would just drop windows forever, oh well, someday soon perhaps.

I do have another question that perhaps one of you can answer for me without making a new thread.  I am contemplating getting satellite internet ( I am way in the boonies, so no cable/dsl available) so I can kiss all my modems goodbye.  Are there going to be any problems with this and Ubuntu?  Is there one particular service that works better on Ubuntu than the others?  It really sucks going from 500kbs download speed to 5kbs :(

---

### Post by the.phantom on 2007-02-11
still no expert ;-)

ya i was on dialup for 13 years and just went dsl 2 weeks ago, and no way could i go back 

might have to talk to the sat folks but the standard line on all of the isp's is 
we do not support linux !!!
but then you find they are using apachie (sp) servers themselves ;-D

might be able to feel them out and see do they offer dynamic or fix ip and what windows versions, and do you realy need their "magic cd" to install or can you manual do it
and that might give a hint for linux !
i went dynamic through a router, the xp came right up ready ( after i re enabled the nic)
i got tired of seeing it in the taskbar for so long. and then i just told linux that it was dynamic and off i went 
so no magic cd to install it  ;-D
i do know that sat is pretty expensive !!!!

---

