---
title: "Ubuntu 11.04 will not install on new SSD?"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by ykol20 on 2011-05-20
I upgraded my nokia booklet 3g with an OCZ Onyx 1.8" SSD recently and noticed that Ubuntu 11.04 will not read/write to the new drive giving "input/output" errors.  

I think it may be related to the issue discussed on this forum
[http://www.ocztechnologyforum.com/forum/archive/index.php/t-78164.html](http://www.ocztechnologyforum.com/forum/archive/index.php/t-78164.html)  
(TRIM Command/Windows 7 related)  

After doing some research I noticed that later versions of ubuntu added TRIM function support, I'm a relative beginner with linux and do not know much more about the issue.  However, ubuntu 10.04 LTS installs and works fine, so I'm guessing "something" changed.  

Are there any workarounds available for 11.04? 

Thank you very much for any help.

---

### Post by nrundy on 2011-05-20
my understanding is that SSDs need to be installed in specific ways. It's not something a "lay person" can do. That is, it's more complicated than installing an HDD.

---

### Post by ykol20 on 2011-05-21
I think that (again from a day of googling) SSD's have some management features that help prolong life and minimize the reuse of sectors, but overall they should be as plug and play as HDD's if those features are not used.  Although, that could reduce performance/reliability. 

I was just curious if something was added to 11.04 to enable the use of SSD TRIM features since Ubuntu 10.04 installed without problems. (and if there was anyway to disable this before install from usb key)

In the linked forum post, it describes how a Windows7 install will hang when it calls the TRIM command with my particular laptop hardware.

Thanks for any help once again :)

---

### Post by oldfred on 2011-05-21
There is some discussion of trim, SSDs and kernel versions in this:
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by ykol20 on 2011-05-21
Thanks, yeah, it seems like 11.04's kernel uses the TRIM command.  

Is there any way to disable it before installing from the usb drive and trying to format the drive? Specifically just "turning off" whatever SSD support changes were made between 10.04 and 11.04.. 

According to the forum post above, the laptop's "SATA to PETA bridge" makes the hardware think that TRIM is usable, when infact it is not..causing problems.  I think that this is probably the main issue (although I could be wrong).

---

