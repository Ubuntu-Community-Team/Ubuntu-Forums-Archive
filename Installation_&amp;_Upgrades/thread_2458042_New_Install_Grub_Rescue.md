---
title: "New Install Grub Rescue"
date: 2021-02-15
forum: Installation &amp; Upgrades
---

### Post by werth.clinton on 2021-02-15
I just got a new hard drive. Fresh install. I tried the latest server and desktop versions. After a successful install. It reboots into  grub rescue each time. I've tried to reinstall multiple times,  still grub rescue.

I've also tried the grub rescue fixes. And have no luck. Should I try a different linux version?  What am I doing wrong?

from boot-repair - [http://paste.ubuntu.com/p/cgXFrYwbfx/](http://paste.ubuntu.com/p/cgXFrYwbfx/)

I'm new to linux and just trying to start learning how to use it. I just want to set up a linux server with Samba so I can use it as a kind of NAS for my home. I also want to set up a plex server. I have a 6tb drive. Everything is blank right now, so whatever the path of least resistance is I'm all for it. I don't need to worry about saving data or anything like that at the moment. Just trying to get an install done so I can start setting up what I need to and start learning. Thank you all for your patience and help with me.

---

### Post by CelticWarrior on 2021-02-15
Check the boot order in BIOS/UEFI.

---

### Post by Impavidus on 2021-02-15
Can you install [boot-repair](https://help.ubuntu.com/community/Boot-Repair) in the live session and create a boot info summary? That may tell us what's going on. Don't run the recommended repair.

---

### Post by grahammechanical on 2021-02-15
Did you choose Erase disk & install Ubuntu or Something else. If it was something else that you chose did you select a device for the boot loader installation? Default should be sda. Do you have more than one drive in that machine?

I guess that there may be more than one reason for grub rescue but the reason I know about is that the core part of Grub cannot find the grub configuration file. It should be found at /boot/grub and is called grub.cfg. Did you set up a separate boot partition? The configuration file allows Grub to produce its menu and if there is only Linux installed it will tell grub which Linux kernel to boot. Now I come to think about it, not finding a Linux kernel where it should be is another reason for getting grub rescue.

If we knew the number of drivers and the partitions we could tell you the commands to run from a live session to reinstall grub. If you get a grub menu and select Advanced options for Ubuntu and then select a kernel with recovery mode, you can then use the recovery menu to update grub boot loader. It is one of the options.

Regards

---

### Post by werth.clinton on 2021-02-15
I was able to boot and pull up boot-rescue, here is the link it provided [http://paste.ubuntu.com/p/cgXFrYwbfx/](http://paste.ubuntu.com/p/cgXFrYwbfx/).
and this is a new disk, so whatever the path of least resistance here. I just want a clean install up and running, don't need to save any data. thank you

---

### Post by oldfred on 2021-02-15
Is system UEFI or only BIOS.
You have very large 6TB drive, so gpt partitioning required.
If drive every used in newer UEFI system better to also have ESP - efi system partition as first partition. You do need the bios_grub partition for BIOS boot. A year or two before I got my first UEFI system, I partitioned all drives with both ESP & bios_grub so I could easily convert boot mode.

You do have another 6TB drive for backups?

There used to be an issue with grub & kernel boot files that were beyond about 600GB in TB sized drives. That issue was resolved, at least with 2TB drives.  Linux randomly writes files into its partition, so kernel & boot files may be anywhere on drive. Some had working system, but then an update moved kernel to nearer the 2TB mark and it quit. You have boot files nearer the 6TB area. See line 161.

```
   5.315425873 = 5.707395072    boot/vmlinuz                                   2
   5.315425873 = 5.707395072    boot/vmlinuz-5.8.0-43-generic                  2
```

I would try install with 30 to 50GB / (root) partition and rest as /home, if you want everything on that one partition. I prefer several data partitions, but then have to manage size if one gets too full and other is nearly empty. If drive may be in UEFI system in its lifetime, I would add 500MB ESP, your 1MB bios_grub, 50GB / and rest for your use. I typically do not fully allocate a new drive until I know where I am putting data.

The Microsoft basic data partition must be because you partitioned with Microsoft tools? Microsoft requires a system reserved partition before the first NTFS partition. If later installing Windows you have to use UEFI as drive is gpt.

If not wanting to re- install, you can convert Microsoft partition to the ESP as FAT32 with esp flag, and shrink your / partition. Since not a lot of data written yet, the shrink should not take too long. But with 6TB drive and lots of data it could take a very long time to resize. Never interrupt a resize.
You can shrink / to anything less than say 500GB just to test if that is the issue.

What brand/model system? What video card/chip? Some hardware needs boot parameters to boot.

---

### Post by werth.clinton on 2021-02-15
System is bios. And this is getting a little over my head,  I have 1 6tb done I'm wanting to use. I'm new to Linux so the purpose of this is to learn.  All I'm looking to do is set up samba so I can have a kind of home NAS for storing files.  I was also wanting to set up a plex server,  which is why I went with the 6tb drive. 

So all I was trying to do was install ubuntu using a thumb drive onto this 6tb drive.  After installing i got the grub rescue on start up.

---

### Post by CelticWarrior on 2021-02-15
Regardless of the OS you're installing setting the required boot options in BIOS or UEFI, as well as other machine specific settings, cannot be over your head. So, that's the first thing to check.

Then, if really BIOS the machine must be very old and may not have proper support for a drive so big or it needs a firmware (BIOS) update. This isn't saying it can't work with that drive but this suggestion > [COLOR=#000000]try install with 30 to 50GB / (root) partition and rest as /home[/COLOR] instead of the single partition the installer gives, is sensible. Reason: Grub, the bootloader, and more specifically its second stage may end up located too far down the drive for the BIOS to boot properly.

BUT... Before anything else, again, > [COLOR=#000000]What brand/model system? What video card/chip?[/COLOR]
"System is bios" tells us nothing useful.

---

### Post by werth.clinton on 2021-02-15
It's for a Dell Poweredge T320 Xeon E5-2430L 6-Core 32GB PERC h310.
I have the option to boot with Bios or UEFI. Currently it's set to boot with BIOS.

just to keep the link going with the thread, this is my boot-repair link: [http://paste.ubuntu.com/p/cgXFrYwbfx/](http://paste.ubuntu.com/p/cgXFrYwbfx/)

---

### Post by CelticWarrior on 2021-02-15
If it's UEFI then use UEFI mode.
There is no BIOS. What you call "boot with BIOS" is actually Legacy/CSM mode. Why force it when there's no reason to?

And using a power hungry tower server for what you want to do is insanely ridiculous. A Raspberry Pi or equivalent and an external USB drive does the same while using 50x to 100x less electrical power.

---

### Post by werth.clinton on 2021-02-15
Yes, I'm sure this is way more than what is needed, but again, I'm learning. I didn't want to put a bunch of money down on stuff, so I'm using what I have at the moment.

I set the boot to UEFI but I'm guessing I need to do something to have the drive boot with UEFI instead of BIOS? looking at the start up screen, it's showing that there is 1 non-raid disk found on the host adapter and 1 non-raid disk handled by the bios. I'm guessing I need to change something so it's booted with UEFI instead?

---

### Post by Impavidus on 2021-02-16
When you set your computer to uefi mode, the installer disk will boot in uefi mode and will install your system in uefi mode. Which is really preferred for modern systems.

BTW, your boot info summary shows nothing out of the ordinary, other than using legacy mode. Normally it should work, but using such a large drive in legacy mode may be the problem. But you should consider separate partitions for OS and data anyway.

---

