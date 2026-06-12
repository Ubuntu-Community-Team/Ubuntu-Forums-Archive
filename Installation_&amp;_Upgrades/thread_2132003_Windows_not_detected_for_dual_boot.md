---
title: "Windows not detected for dual boot"
date: 2013-04-03
forum: Installation &amp; Upgrades
---

### Post by jimbobian on 2013-04-03
I've been trying, unsuccessfully for a few days to dual boot Win 7 and Ubuntu on my PC. Previously I had Vista 64-bit installed and so I decided the way to go would be to wipe the hard-drive and start all over again. Having got a Windows 7 upgrade license though, I had to leave the Vista partition intact. So I installed Windows 7 via the DVD (again 64-bit) and then booted the Ubuntu 12.10 DVD (64-bit) to see what to do. The version of GParted on the DVD flat out refuses to load the devices, it just sits at the screen saying 'scanning devices...' for at least 2 hours at which point I gave up. The install pane also doesn't detect Windows 7 which I read wasn't uncommon, but booting into a dedicated GParted CD which I also burned (not realising that the Ubuntu DVD has one) works fine and reads the device partitions no problem. Being impatient (and not really sure what I was doing) I deleted the partitions and started again with an unallocated disk - install Win 7 - get to Ubuntu - still no joy.

I read elsewhere that running sudo fdisk -l should list the partitions present, but it returns nothing on my Ubuntu DVD - the cursor drops to the line below (while I assume it's running) and then the prompt returns with absolutely no output. So I ran it again with strace as well and - although I really have no idea - I think that fact that it showed "dev/sda1            permission denied" might mean something. Anyway, thinking that I had mucked around with the partitions on my hard drive so much that Ubuntu was getting confused I decided that I would completely wipe the drive and start again. I ran DBAN to write zeroes to the whole thing and installed Windows 7 this morning. GParted on the Ubuntu DVD still doesn't work and Ubuntu still can't "see" Windows 7 installed on the drive, the only options I am given are to wipe the drive and install Ubuntu.

Has anyone got any ideas what is going on, I would be most grateful.

System: 64-bit, Q6600, 4GB RAM, "500GB (465GB)" hard drive

Cheers

---

### Post by darkod on 2013-04-03
One option could be if the disk has been used in raid so it has meta data remains. But it doesn't look like that to me. In any case, to discard the possibility, if you are NOT running raid boot ubuntu live mode, open terminal and execute:
sudo dmraid -Er /dev/sda

If that asks you to confirm removal of meta data, you had it. Confirm and try installing ubuntu again.

Another option is some error in the partition table but that also looks impossible since you deleted all partitions and started fresh. If the disk had gpt table at some point and you only used windows to manipulate it, it can create a mess because it doesn't delete the backup gpt table. You can try writing new blank msdos table in terminal with:
```
sudo parted /dev/sda
mklabel msdos
quit
```

Also, if Gparted hangs scanning it, it might mean the disk is starting to fail. Although it looks good when installing windows. This is one of the possibilities but not likely since it installs windows without errors.

---

### Post by oldfred on 2013-04-03
Also is Windows hibernated? or needing chkdsk (even with new install after a resize). 

The NTFS driver will not mount NTFS partitions with the hibernation or chkdsk flags set to avoid damage to the NTFS system.

---

