---
title: "Dell PowerEdge 1400SC (NO RAID) w\ SCSI aic7899 wont install"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by ljerabek on 2008-04-30
Everyone,

I have been searching the internet up and down for an answer on this. I have a Dell PowerEdge 1400SC without a raid controller, but with a aic7899 SCSI controller and SCSI drives. The install starts then drops me into the (Built In Shell) Busy Box V1.1.3.

I've tried Ubuntu Version 7.10 and 8.04 with boot options:

aic7xxx=no_probe
use_generic_ide (to see what is going on)

I am about to loose my mind. As a test I installed Solaris 10 for x86 and it worked fine. I'm suspecting there is an issue with the aic7xxx driver.

Thanks again for any advice.

Regards,

Lu

---

### Post by ergosteur on 2008-07-01
I have got exactly the same problem. Adaptec AIC-7899 in a PowerEdge 1400SC with 4x Maxtor Atlas 10k. Any solutions?

---

### Post by avtolle on 2008-07-01
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) may help you.

---

### Post by chitsung.loh on 2008-09-07
Hi,

Not too sure will it help... but I manage to install xubuntu 7.10 to dell poweredge 1400sc with aic7899 scsi controller...

Try using an old CDROM drive instead of any kind of writer (e.g. CD writer or DVD writer)... I also remove the IDE drive from the dell..

Cheers

---

### Post by rjromero10 on 2008-11-11
I know this thread is a little old, but I have just installed ubuntu 8.10 server on my 1400sc and had the same problem. I would get the busybox (built in shell), I type exit and suddenly it booted up. I search for an answer all over the net and could not find one. I figured it had do with a timeout, which it did. I put "rootdelay=60" without the quotes in the grub menu.lst file located in /boot/grub/menu.lst. The line is toward the bottom and looks something like this: /boot/vmlinuz-2.6.27-7-server root=UUID=492ac531-c353-xxxx-xxxx-xxxxxxxxd913 ro rootdelay=60 quiet splash
You can edit the file like this "sudo nano /boot/grub/menu.lst"
You can also try it first by using the <esc> at bootup to view/edit the grub menu and put the "rootdelay=60" there. The example how-to is located [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I hope this will help someone else.

---

### Post by cpenner on 2008-12-15
This was EXTREMELY timely.  I've been fighting with the BusyBox message too.  Your timeout fix solved it instantly.

Much Christmas Karma your way...

---

### Post by ergosteur on 2008-12-15
sweet! I'm going to be trying this when i get home for christmas

---

### Post by movingover on 2008-12-31
rjromero10's solution did it for me as well. I had a PowerEdge 1650 with a AIC-7899 SCSI controller, based off a non-RAID 39160 controller card. Here is what I did to get everything working:

1) Installed Windows XP SP3.
2) Downloaded BIOS update for poweredge 1650 from Dell's website. Formatted a blank floppy, and let the update churn out its data to the floppy.
3) Rebooted poweredge and booted from floppy. Ran BIOS update.
4) Installed Xubuntu 8.10 from LiveCD. You may crash to a terminal, simply type "exit" and the normal GUI should boot.
5) Booted Xubuntu from hard drive, using "exit" trick. Ran all system updates, and ran these commands in a terminal:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.`date +~%b-%d-%Y~%T`
sudo mousepad /boot/grub/menu.lst

```
Then added "rootdelay=60" at the end of each of the operating systems listed (four since there are two kernals after update). 
6) Saved & closed the editor, and ran
```
sudo update-grub
```
7) Rebooted. System takes quite awhile to boot, and goes to a resolution too high for my monitor, but then behaves great.

NOTE: if you're on ubuntu, you'll need to use a different editor than mousepad, try replacing with "gkedit", or if you have a command-line fetish "nano".
NOTE2: the first command makes a copy of your ".lst" file in case you mess something up
Hope this helps anyone who runs into similar problems on Dell hardware!

---

### Post by beatgr on 2009-02-12
I have sucessfully installed Ubuntu 8.10 on the Dell PowerEdge 1400 (no RAID controller) using just the AIC7899 built-in SCSI controller.

My install documentation and notes:
[http://ubuntuforums.org/showthread.php?t=1063456](http://ubuntuforums.org/showthread.php?t=1063456)

Good luck with it !

g. beat

---

### Post by sahwan on 2011-09-24
thanks ,I have manged to install ubuntu 10.04 on powerwdage 1650 with aic7899 scsi drivers the only change i made is the above dicription for Grub but for ubuntu 10.04 it use Grub2 so the file need to be edit is 

[PHP]sudo nano /boot/grub/grub.cfg[/PHP]

---

