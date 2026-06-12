---
title: "Can't install Hardy on Intel D945GCLF"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by giedz on 2008-05-30
Hi all,

I've got new Intel board and can't install Hardy. There is something wrong with udevd and switches me to busybox. The strangest thing is that Gutsy works quite OK and there is now such problem at all. I know this board model is pretty new but any can point me out what to do regarding Hardy?

Thanks,
Marcin

---

### Post by Pumalite on 2008-05-30
Post your specs

---

### Post by happycube on 2008-06-04
> **giedz said:**
> Hi all,

I've got new Intel board and can't install Hardy. There is something wrong with udevd and switches me to busybox. The strangest thing is that Gutsy works quite OK and there is now such problem at all. I know this board model is pretty new but any can point me out what to do regarding Hardy?

Thanks,
Marcin

There's a bug in the rtl8169 driver in the 32-bit build.  You can either turn off LAN in the bios and put another card in, or install the 64-bit version, depending on your tastes and if you have something better to put in the PCI slot.

Yes, it's rather weird that intel put a realtek LAN chip when they have far superior ones, but this board is all about cost reduction without resorting to cheap capacitors and such... and unlike their previous SIS-based mini-ITX board the graphics actually works properly OOTB, complete with compiz. ;)

edit:  i actually just tried the amd64 version and unlike what i read the LAN still does not work, alas.  I'm just gonna shove an e100 card in my computer.

---

### Post by millhill on 2008-06-07
Is this the same problem as reported here and if so can it be fixed the same way?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/223656]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/223656")

---

### Post by kogz on 2008-06-16
Hi guys,

I'm thinking 'bout ITX solution. D945GCLF sounds good for me. My question is - do you have lots of trouble with Ubuntu 8.04 working on D945GCLF?

---

### Post by giedz on 2008-06-20
Seems like last kernel update to 2.6.24-19-generic fixes the problem.

---

### Post by giedz on 2008-06-20
kogz - you can wait for Hardy update install late July (8.04.1) or install 7.10 then do dist-upgrade. What's all ;) Have fun

---

### Post by kogz on 2008-06-21
> **giedz said:**
> kogz - you can wait for Hardy update install late July (8.04.1) or install 7.10 then do dist-upgrade. What's all ;) Have fun

Thanks. I know that. I can also download daily snapshot. ;]

But, I'm just wondering are there any other problems with ubuntu under this platform.

Thanks. :]

---

### Post by glutamate on 2008-06-23
I have just installed Ubuntu Hardy daily-live (8.04.1 from 20-Jun-2008 ) and everything works. (Not so for xubuntu 8.04.1 daily...) Gutsy also works.

---

### Post by kogz on 2008-06-23
> **glutamate said:**
> I have just installed Ubuntu Hardy daily-live (8.04.1 from 20-Jun-2008 ) and everything works. (Not so for xubuntu 8.04.1 daily...) Gutsy also works.

Good to hear that! Thanks.

---

### Post by kogz on 2008-06-28
Well..

I have a problem. I've just installed Ubuntu Server 8.04.1 from daily snapshots. Under installation stage there was network connectivity. DHCP worked. After installation, after I booted my fresh operating system, network doesn't work. DHCP and STATIC, both are not working..

Still searching for a solution..

//UPDATE:

Network from Recovery Mode works...... I don't get it...

//UPDATE:

Nah.. From Recovery Mode it was working only once.... Strange.

---

### Post by Dr John on 2008-07-04
I installed from this ISO,

30-Jun-2008 22:01  699M  Alternate install CD for PC (Intel x86) computers (standard download)

and I was able to get past the network problems.  However, it seems as if the display driver is not working correctly.  I've tried fixing it, but it seems to revert to the VESA mode and a maximum resolution of 1024 x 768 or the like.

Ubuntu Hardy still needs work to run properly on this board.  :(

---

### Post by dabone on 2008-07-23
I just installed it, had to do a little trick.
First I disabled the internal nic and added a intel gigabit I had laying around.
Did the install then rebooted, installed all the current updates.
On the next reboot I enabled the onboard nic, and after 8.04 booted it was seen.
Then I shutdown and removed the intel nic, rebooted and surfed the net.


Cute board.

I hope to sell alot of them.

(Also looking forward to the flycreek..

Later,
dabone

---

### Post by kogz on 2008-07-23
> **kogz said:**
> Well..

I have a problem. I've just installed Ubuntu Server 8.04.1 from daily snapshots. Under installation stage there was network connectivity. DHCP worked. After installation, after I booted my fresh operating system, network doesn't work. DHCP and STATIC, both are not working..

Still searching for a solution..

//UPDATE:

Network from Recovery Mode works...... I don't get it...

//UPDATE:

Nah.. From Recovery Mode it was working only once.... Strange.
BTW: Here is my solution: [http://ubuntuforums.org/showpost.php?p=5382164&postcount=10](http://ubuntuforums.org/showpost.php?p=5382164&postcount=10)

---

### Post by brecke on 2008-07-24
Hey guys,

I bought this board and i cant't even boot it. I am using a usb stick to install the latest ubuntu release and it just says "boot error." No description, no nothing.

Can someone please help me with this? What can i do to skip this?
thanks in advance,

_ brk

---

### Post by kogz on 2008-07-24
> **brecke said:**
> Hey guys,

I bought this board and i cant't even boot it. I am using a usb stick to install the latest ubuntu release and it just says "boot error." No description, no nothing.

Can someone please help me with this? What can i do to skip this?
thanks in advance,

_ brk

Be sure your USB stick is bootable. And check boot priority in BIOS.

---

### Post by brecke on 2008-07-24
I am following instructions on [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) and using UNetbootin to "build" the bootable stick. However, no luck. Still the "boot error" message... 

The strange thing is, using the same pen on my desktop works fine, so this must be a mini-itx specific thing.

Also, the priority in BIOS is set to boot usb devices first.

No clue on this one. Any help, please?

---

### Post by Frumpco on 2008-09-29
I am having the same issue with not being able to boot off USB thumb drive. I have followed the instructions set the BIOS to boot from USB, set USB to boot first, it sees it in the bios but just will not go

---

### Post by Pumalite on 2008-09-29
Check this thread:
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)

---

### Post by Frumpco on 2008-09-29
Thanks for the link.. its not an issue with the USB drive since it is able to boot off other machines..

Edit
I just created a DOS boot USB and that works so must be something with that make or isntall of the thumb drive will try again

Edit#2
Redid my thumbdrive manually from [http://www.penlinux.com](http://www.penlinux.com) and still having boot issues. It does boot of a CD with Ubuntu but just not off a USB drive

---

### Post by Pumalite on 2008-09-29
Maybe your BIOS does not allow you to boot from USB.

---

### Post by Frumpco on 2008-09-30
I am able to boot off a USB key that has DOS/WIN98boot disk on it NP so it is possible. I can boot off the Ubuntu live USB key on a different computer

---

### Post by C.S.Cameron on 2008-09-30
I have 8.04 working great on a D945GCLF.
Flash boots fine, but is recognized as another hard disk in BIOS.
Forget it though, Intel has just released the D945GCLF2.
This mITX board has a dual-core Atom and S-video.
Not sure yet how well GMA 950, S-video and Ubuntu mix though.

---

### Post by Frumpco on 2008-09-30
Got it to work.
Changed the USB setting to Fixed Disk and is able to boot off the USB Key

---

### Post by dankuoni on 2009-03-13
Thank you very much! :D

Had the same problem. After changing "USB Mass Storage Emulation Type" to "All Fixed Discs" everything works. 
Does anyone know what that actually means ?

*dankuoni

---

