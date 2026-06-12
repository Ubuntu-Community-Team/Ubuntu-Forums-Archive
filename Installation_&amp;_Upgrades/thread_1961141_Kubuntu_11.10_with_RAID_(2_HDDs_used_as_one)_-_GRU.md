---
title: "Kubuntu 11.10 with RAID (2 HDDs used as one) - GRUB install problem"
date: 2012-04-18
forum: Installation &amp; Upgrades
---

### Post by RPieter on 2012-04-18
Hello guys!

I am trying to install Kubuntu 11.10 on my Vaio AR51SU notebook, but I am having some problems with the RAID setup of the hard disks. I am not familiar with Linux kernel commands. 

I am using the alternate setup Oneiric Ocelot because I read that I would run into troubles with the RAID setup. In the beginning of the installation I selected that the install would help me with the RAID config (I didn't chose for Manual). Now I am almost at the end of the installation where th GRUB-bootloader needs to be installed on one of my hard discs. The setup gives me a screen where I have to choose where to install GRUB. Now it says "/dev/mapper"; also it gives some examples what I can choose, i.e.: '/dev/sda', '/dev/sda2' or '/dev/sdc5'. But no matter what I choose from these three I get the same error: install of grub failed, this is a fatal error. After this I can choose to skip the GRUB install and go ahead with the install without installing GRUB, but I'm guessing this will make my Kubuntu not bootable,...

What should I do to solve this problem?

Thank you in advance !

Pieter

---

### Post by darkod on 2012-04-18
Does it include the letters after the /dev/mapper/ too? It should be like /dev/mapper/XXXXXXX

You can choose not to install grub2 but you are right. It will not boot.

However, you could boot with the live cd in live mode and just add the grub2 bootloader. That is one option if it stubbornly doesn't want to install grub2 during the install.

---

### Post by strask on 2012-04-18
I had exactly this problem yesterday; I found my way out of it but haven't re-tried the install yet. 

What I think you need to do is start the install process over again, and when you get to the part where you partition the (raid) hard disk, look carefully at the volume name. It should be something like /dev/mapper/isw_somethingrandom_Volume0 if your system is like mine. Write this down and use that name when it asks where to install grub.

When I did it I tried to go back to the partitioning/formatting step to get the volume name and then jump forward to the grub install again, but that confused it, which is why I think you need to start over from the beginning.

---

### Post by RPieter on 2012-04-19
@Darkod: is it that simple to just skip GRUB2 during installation of the alternate CD, after that it won't boot, but I will boot with the live CD and install Grub2?

@strask: did you try this solution with the "isw_somethingrandom_Volume0" name? Because I didn't had the time yet to try this possible solution,...


Then an update how last night ended,... Like I said in my previous post first I tried the alternate cd which ended with the GRUB that I couldn't install. After that I tried it again but at the RAID options during installation I chose for Manual. This disabled the RAID setup of my notebook which made me able to install Kubuntu. BUT when I opened the file manager I could only see one of two hard drives (which normally with the RAID setup is seen as one disc of 500GB). So now I only have 250GB available,...   And to end yesterday night really depressed, I was doing a software update, which stalled somewhere in the middle which made me do a hard reset, which made it impossible to log in again,... so now I have a notebook without an OS again. 

So, anybody some more tips about installing the alternate CD WITH the RAID setup, AND to make it dual boot with a Win7?

What a struggle,..

---

### Post by strask on 2012-04-19
> **RPieter said:**
> 
So, anybody some more tips about installing the alternate CD WITH the RAID setup, AND to make it dual boot with a Win7?


If you want to make it dual boot with windows 7, I strongly recommend that you install windows FIRST. If you get ubuntu working and then install windows, the windows install will clobber your boot loader and cause another headache.

I am trying the alternate cd again right now, as soon as I get a successful grub install I will post here again.

---

### Post by strask on 2012-04-19
Ok, grub installed successfully this time.

1) My raid volume was already configured in bios
2) Windows 7 was already installed on the first three partitions of the raid volume (the first two are tiny recovery partitions, the third is the main windows partition)
3) When the alternate install cd offered to activate my RAID volume, I of course said YES.
4) I wrote down the name of my raid volume, /dev/mapper/isw_bhiiebfiid_Volume0
5) I created three logical partitions, for swap, /, and /home, in the free space not used by windows.
6) The install proceeded normally.
7) When it asked me at the end where to install grub, I gave the full device name from step 4.
8 )Reboot at the end of the install and grub comes up happy, ready to boot linux or windows.

Note this was done with the 12.04 beta 2 alternate install disk; but my understanding is that 11.10 should work the same way.

Also note that for some reason the alternate disk only wanted to use my wired ethernet network, I couldn't get it to use wireless.

Good luck!

---

### Post by strask on 2012-04-19
Ugh. I was premature in my statement of success.

Windows boots fine.

Ubuntu starts to boot but can't find the root volume; it's searching by UUID and says the UUID doesn't exist; if I change the grub boot command to use the /dev name of the volume it gets a lot farther in the boot process but fails when it goes to mount the actual filesystems. I don't have time for a full writeup now and it seems to be a separate issue from the installation/grub problem I was having before, so I'll make a separate post about it later tonight.

---

