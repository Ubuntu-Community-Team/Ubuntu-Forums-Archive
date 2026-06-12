---
title: "Installing Ubuntu with Windows on a RAID 1 system"
date: 2012-09-30
forum: Installation &amp; Upgrades
---

### Post by Techguy172 on 2012-09-30
Hi,

I just bought a Lenovo W530 laptop with Windows and two 500GB drives in a factory RAID 1 configuration, how can I dual boot Windows 7 and Ubuntu on this configuration. I've made several different attempts including Wubi, partitioning the drive in windows, partitioning in Linux, and none of these methods worked. The Linux installer doesn't seem to be able to handle this setup very well. What's the best way to do this?

Thanks.

---

### Post by darkod on 2012-09-30
You have to use the Alternate Install CD for better raid support. It should work, including installing grub correctly at the end.

If you have unallocated space (not belonging to windows), you can use that. If not, you will have to use windows Disk Management first and shrink the windows partition(s) so that you have unallocated space for ubuntu.

If there are 4 primary partitions existing you will also need to delete at least one, so that uubntu can create logical partitions for itself.

---

### Post by Techguy172 on 2012-09-30
What is the alternate CD, I downloaded the ISO and created a bootable USB drive. I have included a shot of my hard drive setup in windows It says I have 4 partitions right now, so which one am I to delete? I'm fine with splitting up space from windows.

---

### Post by darkod on 2012-09-30
By default the download is for the standard live cd. You have all images here:
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

Which partition to delete is your choice. I am not sure what that partition of 3.60GB does, it has no label.

You can also use the installed recovery software in windows and create a set of recovery DVDs. After that you don't need the recovery partition any more since you can use the DVDs if you ever need them and you can delete that partition. That way you can also use the space now taken by the recovery partition.

---

### Post by Techguy172 on 2012-09-30
I downloaded the file, put it on the USB, and started the installation and it fails on the "Selected and Install Software" step. I'm unsure of what to do now.

---

### Post by Techguy172 on 2012-09-30
So, I tried the install again, selected the free partition on my hard drive, install got farther this time but still failed and I lost Windows, my Lenovo recovery etc. Anyone who wants to install Ubuntu with a RAID 1 setup I recommend you don't it's just an enormous headache. I'm going back to Windows, I wasted my entire Sunday with this.

---

