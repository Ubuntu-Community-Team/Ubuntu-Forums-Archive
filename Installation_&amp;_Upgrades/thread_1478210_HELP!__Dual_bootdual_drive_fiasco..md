---
title: "HELP!  Dual boot/dual drive fiasco."
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by rmjohnson144 on 2010-05-09
I have multiple drives on my system and I decided to put Ubuntu on my main 1TB hard drive.  I install 9.10 on my drive and it partitions half of it to Ubuntu and install is successful.  Well, on reboot I get nothing.  I switch to my secondary drive with windows on it already and the dual boot menu appears?   Apparently it installs in on SATA1 and not the drive selected as boot in the BIOS.  I decided to leave it this way until recently I needed to use the secondary drive on my other rigs failing hard drive.  

So, how do I get grub on the 1TB hard drive? I ran windows 7 BOOTREC files and recovered the Windows boot, but I couldn't get Ubuntu to recover with live CD nor the GRUB online help didn't work.

Is there a simple way to get my dual boot menu back?
-=Mark=-

---

### Post by darkod on 2010-05-09
Boot into live desktop with the 9.10 cd and in terminal do:
sudo fdisk

Post the results here and you will restore grub2 in no time. The live desktop should give you internet access, I just want to see the fdisk results to give you correct commands.

---

### Post by rmjohnson144 on 2010-05-09
OK, I removed all my drives except the 1TB so I don't end up with a huge multi-boot menu.  sudo fdisk -l report SDA. 

Here's a complete output:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb1df1280

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       61594   494647859    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           61594      121602   482011200    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5           61594      120122   470125056   83  Linux
/dev/sda6          120122      121602    11886132   82  Linux swap / Solaris

---

### Post by darkod on 2010-05-09
Again from the live desktop run:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

That will install grub2 on /dev/sda (your only hdd right now), with root partition being /dev/sda5.

Usually I don't advise to unplug disks because it might also confuse grub how many disks and which you have.
Restoring grub like this should allow you using ubuntu right now. When you plug other drives back you won't see grub unless you select the ubuntu disk to be first hdd option in BIOS. Depending how your system is set up, I can't tell what will happen.

---

### Post by rmjohnson144 on 2010-05-09
> **darkod said:**
> Again from the live desktop run:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

That will install grub2 on /dev/sda (your only hdd right now), with root partition being /dev/sda5.

Sweet, it worked great.  I don't know why it didn't work when I tried before.  It kept telling it couldn't install grub, was unavailable?  Maybe the repo was down or something.

> Usually I don't advise to unplug disks because it might also confuse grub how many disks and which you have.
Restoring grub like this should allow you using ubuntu right now. When you plug other drives back you won't see grub unless you select the ubuntu disk to be first hdd option in BIOS. Depending how your system is set up, I can't tell what will happen.

Yes, it can confuse grub if you plug the disk back in the wrong order.  otherwise it's OK.  but since this is the only drive I ewant dual booted and I always keep my main drive in first sata port, I usually have no issues.  It took me a while to figure out the SDA ports are specific SATA ports, not BIOS boot order.

Thanks a ton for your help
-=Mark=-
ps. How do I mark this thread solved?  I see no option in tread tools nor will edit won't let me change subject line.

---

### Post by darkod on 2010-05-09
> **rmjohnson144 said:**
> 
ps. How do I mark this thread solved?  I see no option in tread tools nor will edit won't let me change subject line.

Glad it worked. Above the first post in Thread Tools you should have option to mark as solved. But only if logged in. Likewise, other people don't get that option for a thread you started.

---

