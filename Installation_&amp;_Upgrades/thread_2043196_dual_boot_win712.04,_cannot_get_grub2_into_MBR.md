---
title: "dual boot win7/12.04, cannot get grub2 into MBR"
date: 2012-08-16
forum: Installation &amp; Upgrades
---

### Post by sippyCUP on 2012-08-16
Hi all,

Long time Ubuntu/Mint user, I'm trying to install 12.04 unity on my new 64 bit box. I've already got win7 installed, MBR partitions.

After spending two days reviewing internet forum posts and guides pertaining to dual booting, I am totally at wits end. This install is kicking my butt.

I have a 180GB SSD, sda, and a 2TB HDD, sdb. SDA has the 100mb windows partition, an NTFS win7 install parition, then I have a 60db logical partition for linux and 4 gb swap. My 2tb disk is hosting /home.

At first I attempted to install GRUB to an /boot partition (/boot was the grub install location) and use easyBCD in windows to load Ubuntu via the win7 bootloader, but I was met with a grub4dos prompt upon attempting to load Ubuntu. I could not resolve this issue despite playing with it for several hours.

Then I figured I would just let GRUB take over the MBR, so I reinstalled Ubuntu, specifiying /dev/sda as the GRUB install location. Well, that didn't work. Kinda ridiculous considering how often people complain about OS's inadvertently jacking their MBR, but win7 still loads its bootloader.

I then decided to forcefully insert GRUB into the MBR to the best of my ability. I booted in my Ubuntu install with rescatux, and ran grub-install followed by update-grub.

Well... my MBR must be using birth control, because by all indications it is inpenetrable.

I'm kind of wondering if this is some sort of weird UEFI thing, but windows volume manager claims my disk is MBR, not UEFI.

I really just want to get GRUB on my boot disk's MBR. Any ideas?

Thanks, Eric

Here's my parted print output:

```
Model: ATA INTEL SSDSC2CT18 (scsi)
Disk /dev/sda: 180GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  106MB  105MB   primary   ntfs            boot
 2      106MB   115GB  115GB   primary   ntfs
 3      115GB   180GB  64.8GB  extended
 5      115GB   176GB  60.8GB  logical   ext4
 6      176GB   180GB  3999MB  logical   linux-swap(v1)


Model: ATA WDC WD20EARX-00P (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ext4

```

---

### Post by darkod on 2012-08-16
So, if you boot with the ubuntu cd in live mode and try something like:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

After that restart and make sure in BIOS that the ssd is first in the boot order.

---

### Post by SJR Dorset on 2012-08-16
Trying installing EasyBCD onto your Windows 7 installation:

[http://www.softpedia.com/get/System/OS-Enhancements/EasyBCD.shtml](http://www.softpedia.com/get/System/OS-Enhancements/EasyBCD.shtml)

I have installed and used it on my dual boot Win7/12.04 system.

---

### Post by sippyCUP on 2012-08-16
> **SJR Dorset said:**
> Trying installing EasyBCD onto your Windows 7 installation:

```
At first I attempted to install GRUB to an /boot partition (/boot was the grub install location) and use easyBCD in windows to load Ubuntu via the win7 bootloader, but I was met with a grub4dos prompt upon attempting to load Ubuntu. I could not resolve this issue despite playing with it for several hours.
```

I have spent hours trying to get easyBCD to work already, changing the GRUB mode from GRUB2 to GRUB legacy, etc. I need some new methods.

---

### Post by sippyCUP on 2012-08-16
> **darkod said:**
> So, if you boot with the ubuntu cd in live mode and try something like:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

After that restart and make sure in BIOS that the ssd is first in the boot order.

Checking out the update-grub man file, this appears to pull grub from / to MBR... or the other way around, the language isn't that clear.

My last Ubuntu install I already attempted to install to /dev/sda, my boot drive. I don't think GRUB bootloader is installed at /dev/sda5, my / partition, but I'll try it anyway. I haven't broken anything yet.

---

### Post by sippyCUP on 2012-08-16
Yup, it worked! So I've run grub-install followed by update-grub several times... what is it about those arguments that allowed it to actually work this time around?

I perused the info/man pages but it isn't clear to me what it's doing.

---

### Post by drs305 on 2012-08-16
One thing to watch out for is a failure of Grub in the future. If it happens again, it could be because your BIOS can only read the first 137GB of your drive. Since your Ubuntu partition spans this area, if the GRUB files are located before 137GB it may work, but fail if the files end up moving beyond that point. 

If it fails, at the GRUB menu run "ls (hd0,5)/boot" and see if it finds the boot files. Repeat with "ls (hd0,5)/" and "ls (hd0,5)/boot/grub". If GRUB doesn't see the files during the boot process the BIOS is probably the cause. You can either update the BIOS, enable large drives is this is a BIOS option, or create a separate /boot partition within the first 130 GB or so.

I don't know if that was your issue, but it's a possibility.

---

### Post by darkod on 2012-08-16
It doesn't "pull grub from / to the MBR".

The second command installs grub2 to the destination /dev/sda (the MBR), passing in between the argument --root-directory which specifies where is your root partition. But since you can't pass /dev/sda5 as argument you first need to mount it at any temporary mount point like /mnt. The first command did that for you.

Not sure what didn't work before, but you can always install grub2 to the MBR with those commands. Unless the 137GB limitation hits you (which depends on your BIOS too) like drs305 mentioned, it should always work.

---

### Post by sippyCUP on 2012-08-16
Ya this is a brand new box, SATA disks, 48-bit LBA support. Was thinking about locking the GRUB version just so nothing is auto-broken on updates, thoughts?

---

### Post by darkod on 2012-08-16
> **sippyCUP said:**
> Ya this is a brand new box, SATA disks, 48-bit LBA support. Was thinking about locking the GRUB version just so nothing is auto-broken on updates, thoughts?

I do all the automatic updates and it has never broken grub. Don't think it's needed if the BIOS doesn't suffer from the 137GB issue.

---

