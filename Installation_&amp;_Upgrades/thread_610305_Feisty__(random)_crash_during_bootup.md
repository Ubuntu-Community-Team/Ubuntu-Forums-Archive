---
title: "Feisty : (random) crash during bootup"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by dhruv001 on 2007-11-11
Feisty 64 bit (2.6.20-15-generic)  crashes  (atleast) once every 5 boots..

Appears its unable to load the hard disk, and just drops into the busybox.. 
 
WHhat it looks like is  that the disk driver, sd_mod was not loaded at all,.

/proc/modules shows scsi_mod but no sd_mod.

modprobe sd_mod failed, with a  FATAL module not found error
insmod sd_mod did succeed, but of no use when continuing with the boot.

I am now typing this after a successful reboot, where sd_mod / scsi_mod appear to have been loaded without issues.

And the funny thing is, this is  a very  random occurrence.

I am using ACER 4520...Can anyone help me out understand whats going on ?

---

### Post by vankampen92 on 2007-11-12
Ubuntu 7.10 (Gutsy Gibbon) 32 bit (2.6.22-14-generic) crashes (at least) 9 every 10 boots..

I have exactly the same problem, but with Gutsy and quite more often. Now I am also writing after a successful reboot. I have also rebooted several times in recovery mode and dropped into the BusyBox. One of them juust before that I have got:

............................................................................................................
[  sss.xxxxxx] ata3: port is slow to respond, please be patient (Status 0x80)  
[  sss.xxxxxx] ata3: COMRESET failed (errno=-16) 
[  sss.xxxxxx] ata3: SATA link up 1.5 Gbps (SStatus 113 Control 300)
[  sss.xxxxxx] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cddatray
[  sss.xxxxxx] Uniform CD-ROM driver Revision: 3.20
[  sss.xxxxxx] sr 0:0:0:0: Attached scsi generic sg0 type 5

           Check root= bootarg cat /proc/cmdline
           or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/c3022b5c-xxxx-xxxx-xxxx-xxxxxxxxxxxx does not exit. Dropping to hell!
............................................................................................................

And, then, hell is:

............................................................................................................
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built in shell (ash)
Enter 'help' for a list of built in commands

(initramsfs)
............................................................................................................
 
Note that x's above are alpha-numiric characters.

This is only one example of an unsuccessful boot.  Other examples seem to drop you into BusyBox when the system is trying to load the hard disk rather than the CD-ROM disk as in the post from dhruv0001.

Can the problem be at the SATA bus level?
Look at [http://en.wikipedia.org/wiki/SATA](http://en.wikipedia.org/wiki/SATA)

This may explain why sometimes the problem is when loading the hard disk or the CD-Rom disk. 

I am also very puzzled about the random thing. In my old post I reported that I was not able even to install the Ubuntu 7.10 live disk and that I was also being dropped into BusyBox all the time. At some point I succeeded by using first the 6.10 live disk, and I thought this had something to do, but now I guess it was because of this random failure in then SATA bus.

By the way, when I don't shut down the computer, but only hivernate it, the system recovers without failing most of the time. 

My laptop is a new lenovo T61

Any ideas?

---

### Post by ZetLAW on 2007-11-12
I have the Same problem with LAPTOP MSI m662 (MS-1034) With Intel NAPA chipset 945

---

### Post by dhruv001 on 2007-11-13
*This is only one example of an unsuccessful boot. Other examples seem to drop you into BusyBox when the system is trying to load the hard disk rather than the CD-ROM disk as in the post from dhruv0001.*

In my case, the kernel 'crashes' when it tries to mount the hard disk. The CD-ROM disk mount does go through fine all the time. 
         /proc/devices   /dev/disk/h*   /dev/disk/by-id indicate that the cd-rom driver did successfully  register and mounted the cd drive. It is always the hard disk that fails

        The reboot fails only because it is not able to load the hard disk driver ( sd_mod).l 


Another thing i just realised.

       If  i restart the system, by holding down the power button, immediately after a boot failure, the system does boot fine without any issues

    If i try to come back after a hibernate, it always fails 

    If i try to reboot after a shutdown restart 
             it usually (9 out of 10)  succeeds
  
    If i try to reboot, after a long interval past a shutdown,
           it always fails

---

### Post by dhruv001 on 2007-11-13
Now, i beginning to think that this may not be a software issue after all..

I initially tried to install 7.10 Gutsy, and it failed in a similar fashion. But that was my first ever linux install ever! .. Being new to linux, i  assumed it was due to kernel/driver issues.

But then, if this is a hardware problem, would'nt this be happening to window's installation's as well ? windows vista/xp should experience the same problem in this hardware, if this is really a hw issue.

I wonder if ACER ships this model (4520 ), with windows presintalled, after all ....

The model i had came built with with some linux version that  i am unable to recollect now, and  the hw dissue should have caused the same problems in the machine.. but ofcourse, the first thing , i did, on receiving the laptop, was to install ubuntu..

---

### Post by dontom on 2007-11-13
I'm having the exact same issues with my 4520. I think it's a kernel issue though, when I ran 7.04 it worked fine, could boot everytime. Then I upgraded to 7.10 and the problems started, however when I boot the old kernel 2.6.20-16 it works everytime. Also all sorts of other problems occured after upgrading, but I'll take them elsewhere :)

---

### Post by vankampen92 on 2007-11-13
Hi!!

This is what I have done to solve the problem of random failure at booting time. Look at this:

[https://answers.launchpad.net/ubuntu/+question/17654](https://answers.launchpad.net/ubuntu/+question/17654)

Hope it helps.
David.

---

### Post by dhruv001 on 2007-11-14
David, thanks for the link..

The problem persisted with the controller in IDE mode , which is the default bios configuration on my laptop.. 

I re-installed 7.04, 
        upgraded the kernel to 2.6.20-16-generic ,
        installed the latest nvidia drivers ( from nvidia  website)
        compiled and installed the latest alsa drivers ( from alsa website)
        installed beryl-manager

 My desktop is now 'working'  cleanly, without any of the nagging issues i had been experiencing earlier.

And most amazingly, this also seemed to have fixed the 'random crash' , during boot.. atleast so far.. :-)

---

### Post by vankampen92 on 2007-11-16
Hi,

It seems that the whole thing was an "update problem". After updating my BIOS, my  crash during bootup problem (dropping you into the BusyBox) also vanished!! :) 

Just for the record, I posted this information in the bug (which is not a bug any more!) related to the question I made:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/162536](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/162536)

---

