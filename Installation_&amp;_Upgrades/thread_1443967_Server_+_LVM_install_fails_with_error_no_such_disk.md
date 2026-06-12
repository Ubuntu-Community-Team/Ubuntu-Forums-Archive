---
title: "Server + LVM install fails with error: no such disk."
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by Out_Cold on 2010-03-31
So I have been trying to get 4 Sata HDDs in use with LVM. I have tried numerous releases including 9.10 alt, 9.10 server, 10.04 alt, 10.04 server. It seems that the guided lvm install does it's business but then grub cannot find what I assume to be / or /boot after reboot.

I tried the 'rescue' option and can mount /dev/mapper/root being the only LV available. /boot is empty so not sure what's happening there. Someone suggested chrooting into the drive which I thought was what the rescue did. 

When I try to manually partition, I get similar errors, But run into even more issues after I try to re-install yet again. I found a similar post about /dev/fd0 but I have disabled/enabled this in BIOS and still no luck.

[http://ubuntuforums.org/showthread.php?t=1395308&highlight=lvm+grub+error](http://ubuntuforums.org/showthread.php?t=1395308&highlight=lvm+grub+error)

I also know about the insmod lvm but I can't find anything in /boot including grub.cfg or any other sub-directories. 

I can post more info but am running out of ideas. I think i am going to try next to make a regular /, /boot and swap partition and continue on with /home, /var, /usr and /svr LVs. If anyone else has any suggestions or ideas, please toss them out here before I pull out all my hair.

---

### Post by Out_Cold on 2010-04-01
So I did as mentioned above, this time I get the same error also followed by: error: no such device: <UUID#> and again it does not want to boot. I can not for the life of me figure out why I can not do a proper guided/manual lvm installation. 

Any ideas?

I am doubting that I can accomplish what I want with a live cd due to lack of LVM support. Is it possible to edit grub before it installs? Can I install LVM with a live cd and make LV mounting points before installing? I have approx. 5 TB that I would really benefit from having in LVs. I guess if all else fails I will go back to regular partitions but what's up with this epic failure?

---

### Post by Out_Cold on 2010-04-09
Bump...

I tried to do a regular install via usb alt/live and it boots but then I get an apt error about the cd not being mounted. Well no duh, I'm not using a bloody cd. Why is this computer giving me so many headaches??

---

### Post by Out_Cold on 2010-04-13
So I finally got an install that I'm happy with. I set up a RAID-5 using 3 1.5TB disks as my storage and the 250GB for my system. I declined LVM and decided that it was more of a headache than I was wiling to deal with.

1. LVM guided/manual install failed when grub was trying to find LV partitions

2. USB install doesn't seem to realize that the apt repo is on USB and not a CD thereby not willing to install.

3. Finally installing from a server CD, I managed to get RAID-5 functioning and continued from there. 

The lesson I learned? There are still a lot of bugs to fix before this becomes a decent advanced installation OS.

---

### Post by X1R1 on 2010-05-24
I have a similar issue, Tried to setup up a RAID 1 with LVM and I get:

error: no such device <UUID>
error> no such disk

And then the system boots and everything works ok.

So I reinstalled without LVM (just RAID1) and still same problem.

what can it be?

cheers

---

### Post by intel on 2010-05-25
This is an issue with the ubuntu kernel included in the CD/ISO  you could install the upstream vanilla kernel, and you won't face such issues.

---

### Post by X1R1 on 2010-05-25
Upstream vanilla kernel? What do you mean?

---

