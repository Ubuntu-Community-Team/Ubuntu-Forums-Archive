---
title: "Ubuntu on second SSD HD fails to load"
date: 2012-09-29
forum: Installation &amp; Upgrades
---

### Post by klaus7 on 2012-09-29
Hey,

after numerous attempts at fixing this issue I decided to post my problem here and would be very thankful if you could help me. 

I have a Dell Vostro 3550 with Windows 7 on it. I replaced the CD/DVD-drive with a SAMSUNG SSD and my plan was to install Ubuntu 12.04 on it and have a dual-boot system. 

First thing I tried was to just install ubuntu on the SSD and also the bootloader. But then I encountered, that I can not tell the Dell BIOS to boot from the SSD, because it only has the option "harddrive" in the boot load entry menu, which is the other harddrive. 

Long story short, I tried a lot of things, almost broke my system, got it back up by installing Ubuntu and the bootloader on the first hd and here I am.. I am able to boot the Ubuntu on the first hd and I am also able to boot Windows 7. 

But what I want is to boot Ubuntu from my SSD.

GRUB2 detects it, but cannot boot it. I tells me:

hd1 cannot get C/H/S values
you should load kernel first 

here is the link from boot-repair:
[http://paste.ubuntu.com/1248673/](http://paste.ubuntu.com/1248673/)

Any ideas?

regards,
Klaus

---

### Post by darkod on 2012-09-29
I have seen the C/H/S problem in another thread. Not sure it the hdd was also a replacement of the dvd or not, but so far that problem is not solved also.

It might be the same issue. In that thread no dvd replacement is mentioned, but it might be the same case.

So, maybe it doesn't really consider the SSD as a full disk, even though it sees it as sdb. If that is the problem, it doesn't sound like you can have the OSs on separate disks when one of them is installed in the dvd tray.

Once the OS is running, can it see the ssd correctly and access data on it, or not?

---

### Post by doktorOblivion on 2012-09-29
I would strongly suspect the BIOS.  When SSD came out most had to scramble to support it and even in my old mobo, just connecting straight up to the SATA did not guarantee I could boot it.  I had to go into my BIOS settings, after upgrading it to the recommended level, and change some things, least of which was the SSD as a Primary with MBR on it.  Have you taken a look at your mobo's recommended BIOS level for SSD?

Oh, here is something oldfred appended to someone having similar problems.

Some very old drives have to have the boot at the beginning of the drive.
list of BIOS hard disk limits:
[http://members.iinet.net.au/~herman5...boot_partition](http://members.iinet.net.au/~herman5...boot_partition)

This is probably a hint:  
The boot files of [Das aktuell benutzte Betriebssystem - Ubuntu 12.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them...

---

### Post by klaus7 on 2012-09-29
thanks for your replies!

@darkod: yes, once the OS is loaded it can see the SSD and access data on it correctly. also installing ubuntu on it went without problems, I just cannot boot it ..
> maybe it doesn't really consider the SSD as a full diskyes, that's what I guess also, but I cannot think of a solution.

@doktorOblivion: BIOS version is the latest available and it also detects the SSD correctly. I just cannot set the boot order to boot from it. messed up dell bios...

---

### Post by darkod on 2012-09-29
Have you tried contacting Dell support and see what they have to say?

They do offer the option to replace the dvd with a hdd but maybe they didn't do thing all the way as necessary, who knows. Maybe they will have some idea for you.

Once the OS is loaded it does read it as a hdd to use, but the problem seems to be that the bootloader is not seeing it as a hdd (before any OS is loaded), so it refuses to boot anything on it.

---

### Post by klaus7 on 2012-09-29
no, I didn't contact Dell support until now. They are probably not too cooperative when you unmount the notebook yourself and replace hardware ;) I don't know.. I will try it though.

EDIT: or is it somehow possible to use the original harddrive for the booting process only, but everything else is loaded from the ssd?

---

### Post by darkod on 2012-09-29
Since the dvd is usually easy to remove without actually opening the whole laptop I assumed the change to install a hdd with some sort of caddy in its place is allowed.

In that case, if the product you used to install a hdd instead of dvd (they are not the same size so there must be some sort of caddy you used) is not supported very much, that could be one of the reasons for the problems you are seeing booting from there.

---

### Post by oldfred on 2012-09-29
I have seen some old Dells that would only boot from sda which was IDE and second drive was first generation SATA.

What settings do you have in BIOS. Drives should be SATA not IDE or AHCI. 
But if not already AHCI you need to install those drivers in Windows first.

Also some settings like fast boot or quick boot should be off if you have those type of settings. 

Since you can boot a CD/DVD, I do not see why you should not be able to boot your new SSD but that really depends on BIOS.

You could have grub installed to sda, and create a /boot in the sda drive. Then your main install could be in the SSD. Not sure how that would work with dual booting though. Oldfred has a rule  to have an entire system on one drive that fully boots so when one drive breaks you can boot from the other, but rules can be broken. :)

---

### Post by klaus7 on 2012-09-29
AHCI is installed. I broke your rule and it works! I'm fine with that ;)

So now I just installed /boot and GRUB to sda and / to sdb and that's it. 

Thanks a lot!

---

