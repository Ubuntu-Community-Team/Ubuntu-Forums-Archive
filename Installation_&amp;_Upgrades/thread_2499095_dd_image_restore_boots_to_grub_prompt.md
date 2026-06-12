---
title: "dd image restore boots to grub prompt"
date: 2024-07-11
forum: Installation &amp; Upgrades
---

### Post by sp40140 on 2024-07-11
So I took dd image of a thikpad laptop to a usb drive.
booted up new laptop using ubuntu live usb.
Restored the image to nvme0XX.
After reboot, the new laptop boots to grub prompt.

What am I doing wrong? 
How do I fix this?
image has ubuntu 24.04 (if it matters). The new/target laptop had windows but I formatted it before restoring dd image.

---

### Post by currentshaft on 2024-07-11
When you say you took a dd image of the laptop, what exact command was used?

---

### Post by oldfred on 2024-07-11
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

We get a lot of posts like this. And typically it can be repaired. Often with a lot of work.
But we also believe if repairs take more than about an hour, better to just reinstall & restore from you normal backup.
For another system, you can do same thing. New install & restore from backup.
Becomes good test that your backups are complete as you still have old system to find any missing data.

---

### Post by sp40140 on 2024-07-12
I didn't use any additional parameters.kept it simple:
making image
```

sudo dd if=/dev/nvme0XXXX of=/media/<user>/<usb drive>/imagefile.img

```
restoring image
```


sudo dd if=/media/<user>/<usb drive>/imagefile.img of=/dev/nvme0YYYY

```

the source disk is 500 gigs and destination is 1 TB

---

### Post by sp40140 on 2024-07-12
Thank you. 
I understand that fixing grub / boot thing is tricky.
I'd rather find out what I did wrong and re-do the restore correctly instead of trying to fix the GRUB/ UEFI thing.

---

### Post by TheFu on 2024-07-12
If the laptops aren't 100% identical with 100% identical BIOS settings, some proprietary drivers may not work.  

This is why my backup/recovery technique begins with a fresh install of the OS from a normal ISO.  Let's the installer deal with the boot issues as needed, not with a "fixed" group of settings.

BTW, dd can work in a pinch, but **ddrescue** is safer since it won't just stop at the first error. It will keep going and try to get the data from missing blocks. Also, if you need to stop in the middle for some reason, ddrescue will let you pick up exactly where you left off and continue.

---

### Post by sp40140 on 2024-07-12
Yes. the laptops are different. Both are thinkpads. But source is older model T series and destination is new P series.
I like your idea of fresh install first.
I am going to try your process. I think it will create UEFI partition and I will be able to restore the os in other.
BTW,  I am not able to locate ddrescue package. But add noerr and other flags to the image I take using dd.

---

### Post by TheFu on 2024-07-12
gddrescue

---

### Post by oldfred on 2024-07-12
If old system is BIOS/MBR and new is UEFI/gpt, you cannot restore a MBR partition to gpt drive.
And best to use UEFI/gpt if newer system.

---

### Post by currentshaft on 2024-07-12
> **sp40140 said:**
> I didn't use any additional parameters.kept it simple:
making image
```

sudo dd if=/dev/nvme0XXXX of=/media/<user>/<usb drive>/imagefile.img

```
restoring image
```


sudo dd if=/media/<user>/<usb drive>/imagefile.img of=/dev/nvme0YYYY

```

the source disk is 500 gigs and destination is 1 TB

You left out the important part, replacing it with XXXX, so we don't even know whether you copied a single partition or the entire disk.

What is so secretive about your device name that it had to be classified?

---

### Post by sp40140 on 2024-07-12
Both are UEFI

---

### Post by sp40140 on 2024-07-21
Tried a few things. Didn't work. So, to save time and get things working, I just did clean new install.

---

