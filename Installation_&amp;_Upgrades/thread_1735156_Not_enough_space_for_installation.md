---
title: "Not enough space for installation?"
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by fangslayer on 2011-04-21
This is my first time trying out Ubuntu, and when I try to install it from the disc, it tells me it needs at least 2.6 GB of free space. Problem is, I've got 100GB of free space on my disc (ie space that's not in a partition), so I don't know how to resolve this.

Any help would be awesome

---

### Post by theprofessor102 on 2011-04-21
> **fangslayer said:**
> This is my first time trying out Ubuntu, and when I try to install it from the disc, it tells me it needs at least 2.6 GB of free space. Problem is, I've got 100GB of free space on my disc (ie space that's not in a partition), so I don't know how to resolve this.

Any help would be awesome

Is that just telling you that you need 2.6g or Stopping at that point, Are you picking the correct partition for the install?

---

### Post by fangslayer on 2011-04-21
> **theprofessor102 said:**
> Is that just telling you that you need 2.6g or Stopping at that point, Are you picking the correct partition for the install?

I got that message right after clicking on install Ubuntu. It's the screen that also checks that you're connected to a power source and the internet. It's before I get to pick any partitions, and the continue button is blacked out.

---

### Post by Hedgehog1 on 2011-04-21
What version of Ubuntu are you trying to install?  I ask because the 11.04 beta of Ubuntu is having some installers issues on yesterdays build.

If you are not installing 11.04, then please do this so we can see what is going on with your drive setup that might be confusing the installer:

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

---

### Post by mörgæs on 2011-04-21
Are you planning to use the entire disk for the new Ubuntu installation, or do you want to keep one or more of the existing partitions?

---

### Post by fangslayer on 2011-04-21
I'm installing 10.10, and I would like to dual boot ubuntu with win7. After running the script, the result was as follows:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================


=========================== Drive/Partition Info: =============================

no valid partition table found
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
error: block: No such file or directory
error: devices: No such file or directory
error: /dev/mapper/no: No such file or directory
error: found: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

no block devices found 

```

thank you all for your help =)

---

### Post by fangslayer on 2011-04-22
I would also like to add that when starting up, Ubuntu gives me a "too many connections" error during the orange loading screen thing. I ignored this at first since it didn't seem to do anything, but I don't know if these two things can be related.

---

### Post by Hedgehog1 on 2011-04-23
fangslayer,

Something is very wrong here.

That script sees the CD ROM; but it otherwise acts as if you have no hard drive installed (or the drive or the controller is acting up).

I believe there a few hardware combinations where this is know to happen.  The solution I have seen given (and that seems to work fine) is to use the 'alternate install' CD.  This CD does the install, but does not have the 'TRY' option.  By removing the extra overhead of the 'TRY' option, folks normally install fine.

If, however, you have been having disk errors already in Windows 7, then you have another issue that requires a new drive or controller. 

***The Hedge***

:KS

---

