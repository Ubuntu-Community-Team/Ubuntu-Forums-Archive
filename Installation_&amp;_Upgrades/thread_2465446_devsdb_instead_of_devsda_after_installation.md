---
title: "/dev/sdb instead of /dev/sda after installation"
date: 2021-08-02
forum: Installation &amp; Upgrades
---

### Post by joegiampaoli2 on 2021-08-02
Hello everyone, today I installed 20.04LTS in my wife's PC, it has only one hard drive, during install from USB I decided to do a complete deletion of all partitions on the HD and let the installer do the rest, to my surprise after booting to the freshly new install I saw that the HD was partitioned with the labels of hdb* instead of hda*,the HD is SATA and MB is not a mix of SATA/IDE as the older ones and I know this caused a lot of problems back then and the mapping and with fstab. I assume that the installation USB must of taken the hda title and labeled the main HD as hdb. My OCD will let me rest in peace with this, I do not intend to change it unless necessary if it can cause problems, so what I do need to know is if this will cause any particular problem in the future or if can it be left the way it is. I am aware you should always use UUIDs to map drives and partitions, especially if you do want to change them and to have them absolute, but all I need to know is if I can leave it the way it is before I continue to install and configure more programs and transfer all her files to the new installation, it's the first time I see this and made me doubt.

Thank you!

---

### Post by Holger_Gehrke on 2021-08-02
On modern systems the assignment of device file names to devices is not fixed. Instead of using these device files you can use either the names in /dev/disk/by-id/ (which are constructed from bus type, manufacturer, model, serial number and partition number) or you can use a label you've given a file system or you can use the UUID (a long, random looking identifier created for each file system when it is formatted; they are very likely to be unique). If you take a look in /etc/fstab you'll see it mounts file systems by UUID instead of using the device file. You can do this on the command line too using something like 'mount -U *UUID* */path/to/mount/point/'*. To find out the UUID of a file system you can use either 'lsblk --fs' or 'sudo blkid'.

Holger

---

### Post by oldfred on 2021-08-02
I often have same issue as my flash drive as sdg or sdf becomes sda on reboot which changes every drive. But UUID usually works, so system boots ok. 

If you want to review details:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I typically run Boot-Repair report just to document my configuration.

If UUIDs & drive do not match, you can just do a grub reinstall, that is the main place that I can have issues as grub relies on UEFI/BIOS for drive order as it is before Ubuntu kernel has mounted drives with fstab.

---

### Post by joegiampaoli2 on 2021-08-02
Thanks! I did check fstab and all is mapped with the UUIDs. After many repeated reboots and full shutdowns all seems to be well. I had to disable safe boot on the BIOS for this last previous installation, computer had windows before and I saw that Ubuntu would take a really long time to load and there was a huge amount of HDD activity when starting user's session, it would take almost 5 minutes to get a fully responsive desktop environment, PC is not that bad, I built it myself some good time ago with 16 GB RAM, 4 cores and additional NVIDIA card, disabling safe boot made it respond much faster and NVIDIA drivers were installed automagically. Previous installation was painfully sluggish with safe boot enabled in BIOS, I don't know why. I will leave it then the way it is, I explained to my wife to not boot it up with external drive still just in case.

Thanks again!

---

