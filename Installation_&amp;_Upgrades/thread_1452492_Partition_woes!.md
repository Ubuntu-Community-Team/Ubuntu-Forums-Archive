---
title: "Partition woes!"
date: 2010-04-12
forum: Installation &amp; Upgrades
---

### Post by fragzem on 2010-04-12
I am sure there are 100 threads out there on this already, and I admit I've only read 4 of them... I've always been a hands-on kind of learner, so no matter how many other examples I look at, I'm not going to figure this out without being shown how.. The good thing about that is, you only have to show me once!

I screwed up my last Ubuntu install, got a little ahead of myself with 10.04 and updates and messing with grub blah blah-- Long story short, I'm doing a fresh install on a new hard drive.

I bought a WD Caviar 1TB drive today.. 55GB is partitioned for Windows Server 2008 Standard x64. The other.. 876.51GB is unallocated.

What I would like to do is put Ubuntu on another 55GB partition, and then use the leftover 821.51GB for shared storage space amongst Ubuntu and Windows.

My first question is:
Is this a good idea? Am I thinking about this the right way?

My second question is:
I'm confused with manually creating the partition I need while in the Ubuntu installer. ext4, /home partition, primarys, logicals, help!? I read something about Ubuntu having a seperate partition for each userspace? I only plan to have 1 user on Ubuntu. I don't know what I'm doing! Maybe I should just create an unformatted 55gb partition in Windows and tell Ubuntu to use that, will that work?

Thanks!!

BTW, I'm using (or attempting to install) 9.10 desktop amd64
annnnd I did something wrong with grub before.. when this is all done I hope I'll be able to dual-boot properly?

---

### Post by michel. on 2010-04-12
You are looking in the right direction. I'm using dual-boot the same way you intend to.
I have one 20Gb partition for WinXP and 10Gb for Ubuntu9.10. The rest I use for storage formatted as an NTFS disk.

I stopped using (too) many partitions on Linux years ago. Now I mostly have one root partition. At the most a separate /var partition for my servers and a separate /boot partition if I really need to (when using lvm+grub1 for instance). Use as little partitions as possible, one root partition is really all you need. Using many paritions was only usefull when the disks where small or to circumvent a software problem.

Create 3 primary partitions, 1 for windows, 1 for Linux and 1 for storage. If you ever want to make a 4th partition, make sure it is a logical partition (since 4 primaries is the max). If the 4th is a logical one you can create as many logical paritions inside that one as you like. From a user standpoint there is no real difference between a primary or a logical parition. Use the Linux partition to create a '/' partition. Do not create a separate /home, /var, /usr or whatever, you really don't need it.

P.S. When you are done with installing, Ubuntu will automatically detect your windows install and add it to the bootable OS list.

---

### Post by wilee-nilee on 2010-04-12
> **michel. said:**
> You are looking in the right direction. I'm using dual-boot the same way you intend to.
I have one 20Gb partition for WinXP and 10Gb for Ubuntu9.10. The rest I use for storage formatted as an NTFS disk.

I stopped using (too) many partitions on Linux years ago. Now I mostly have one root partition. At the most a separate /var partition for my servers and a separate /boot partition if I really need to (when using lvm+grub1 for instance). Use as little partitions as possible, one root partition is really all you need. Using many paritions was only usefull when the disks where small or to circumvent a software problem.

Create 3 primary partitions, 1 for windows, 1 for Linux and 1 for storage. If you ever want to make a 4th partition, make sure it is a logical partition (since 4 primaries is the max). If the 4th is a logical one you can create as many logical paritions inside that one as you like. From a user standpoint there is no real difference between a primary or a logical parition. Use the Linux partition to create a '/' partition. Do not create a separate /home, /var, /usr or whatever, you really don't need it.

P.S. When you are done with installing, Ubuntu will automatically detect your windows install and add it to the bootable OS list.

Advising someone to forgo having a swap, using a primary partition without knowing anything about their OS is irresponsible.

---

### Post by fragzem on 2010-04-12
> **wilee-nilee said:**
> Advising someone to forgo having a swap, using a primary partition without knowing anything about their OS is irresponsible.

What should be known about my OS?


Here's some more info on my computer..

1x 1 TB WD Caviar Black 64mb Cache 7200rpm SATA 6.0gb/sec
1x 500 GB WD Caviar 7200 SATA 3.0gb/sec (full with junk that I'm slowly deleting)

8GB PC 6400 RAM
nVidia GeForce 8800GTS 640MB

Sony DRU-830A DVD-R (IDE)

MSI K9N Platnium MoBo

AMD Athlon X2 6000+ @ 3.04 Ghz


With Windows Server 2008 x64 I run no Virtual Memory at all. I'd prefer my OS use the RAM in its place.

---

### Post by wilee-nilee on 2010-04-12
That is enough ram to run a primary partition without swap. Say you were a user who had less then say a gig of ram in a 32 bit OS, then you would want the swap in there. Swap can be turned off or on and you can adjust the swappiness as well.

I am just concerned when I see a 1 post count and advice that could cause problems. I ask now what made this person start their experience with the UF with advising somebody on this sort of stuff? It is not that it was all wrong, but not everybody knows about when it is appropriate to just run a primary partition without swap.

I don't think you can create a ext4 partition in windows. Use gparted on the live CD make the partition before you install Ubuntu. When you get to the partition gui in the install hit custom then click on your pre-made partition tick change make it ext4 as it is don't tick the format box and put / in the mount line.../=root. hit the enter then tick on your pre-made partition again hit forward. On the very last gui there is a advanced button tick on it and make sure it is installing grub on the HD your installing on. NO partition numbers just sda or sdb depending on how your HD are listed. You can open gparted at any time during this process to make sure you are pointing grub at the correct HD and MBR.

---

### Post by fragzem on 2010-04-12
> **wilee-nilee said:**
> That is enough ram to run a primary partition without swap. Say you were a user who had less then say a gig of ram in a 32 bit OS, then you would want the swap in there. Swap can be turned off or on and you can adjust the swappiness as well.

I am just concerned when I see a 1 post count and advice that could cause problems. I ask now what made this person start their experience with the UF with advising somebody on this sort of stuff? It is not that it was all wrong, but not everybody knows about when it is appropriate to just run a primary partition without swap.


Point taken! I thought it odd he only had one post also..... I'm installing atm from the liveCD..  

I made mention of a lot of numbers in my first post, perhaps he thought I mentioned having a high amount of RAM in there... :confused:

Now that I'll have a "fresh" feeling computer... any suggestions as to what I should do.. to ensure that when/if I upgrade to 10.04 that Grub2 doesn't cause me nightmares trying to get back into Windows? I had that happen once already.. doh!

Also.... if anyone knows..  What's with the 10.04 live CD's not working with nvidia cards? I understood alpha 3 not working correctly when I got it.. but beta 2? What happened to the "safe graphics" mode in the F4 menu?

annnnd.. does ubuntu create any error logs someplace during an install? I noticed the icon up top just now "kernel error/crash report"...  (it happened last time too.. but without any future problems) -- I just wanna be sure everything is perfect for this install)

---

### Post by fragzem on 2010-04-12
grrr...

I can't get the new install of Ubuntu working.

I'm having this same problem:

[http://ubuntuforums.org/showthread.php?t=1325490](http://ubuntuforums.org/showthread.php?t=1325490)


flashing login prompt rather than the GUI I'm accustomed to.. never had that before..
I have a dissimilar card to the guy who made that post, and its a year old now.. any advice, anyone?

---

### Post by michel. on 2010-04-12
> **wilee-nilee said:**
> 
I am just concerned when I see a 1 post count and advice that could cause problems. I ask now what made this person start their experience with the UF with advising somebody on this sort of stuff? It is not that it was all wrong, but not everybody knows about when it is appropriate to just run a primary partition without swap.


Oops, forgot about the swap :oops:
Oh, and I only have one post because I can't find my original login anywhere anymore...Seems I used some other email adres...

Anyways, if I do create a swap partition I always try to create a swap partition the size of the total RAM. This allows you to use suspend-to-disk. On servers and if there's more than 1G of RAM I often skip a swap partition altogether. So much so I even forget to advise using a swap to other users :)

---

### Post by michel. on 2010-04-12
> **fragzem said:**
> grrr...

I can't get the new install of Ubuntu working.

I'm having this same problem:

[http://ubuntuforums.org/showthread.php?t=1325490](http://ubuntuforums.org/showthread.php?t=1325490)


flashing login prompt rather than the GUI I'm accustomed to.. never had that before..
I have a dissimilar card to the guy who made that post, and its a year old now.. any advice, anyone?

You should try to disable your X server. Pressing Ctrl-Alt-F1 at the right time should disable it (temporarily anyway). Another way would be to start in single user mode which disables starting X in the first place. After that you need to check which driver you are using. Always start with the open source drivers first. You problably also need to move /etc/Xorg.conf out of the way. X should autodetect the card automatically, especially a 8800 one!

Alternatively, you could do a reinstall and make sure you select the open source drivers, remove any TV-cards and/or just do a plain server install first. You can always add X later by 'sudo apt-get install ubuntu-desktop'

---

### Post by fragzem on 2010-04-12
> **michel. said:**
> You should try to disable your X server. Pressing Ctrl-Alt-F1 at the right time should disable it (temporarily anyway). Another way would be to start in single user mode which disables starting X in the first place. After that you need to check which driver you are using. Always start with the open source drivers first. You problably also need to move /etc/Xorg.conf out of the way. X should autodetect the card automatically, especially a 8800 one!

Alternatively, you could do a reinstall and make sure you select the open source drivers, remove any TV-cards and/or just do a plain server install first. You can always add X later by 'sudo apt-get install ubuntu-desktop'

It DID detect my card.. 3 months ago when I first tried 9.10... now on this new install... (two installs tonight)... it's not detecting it? I dunno what changed.

It's really aggravating me now, though.. I'm going for a 3rd times the charm install.. but I know i'll probably be back here crying. see you guys in 10.

---

