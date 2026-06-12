---
title: "Unable to boot after upgrading 14.04 to 16.043"
date: 2018-02-11
forum: Installation &amp; Upgrades
---

### Post by Al-Man on 2018-02-11
Hi I wonder if any one can help me with a fstab problem I have after upgrading from 14.04 to 16.043. Some breif information about my system: Asus MV50s Laptop with 4gig memory runnning ubuntu 14.04 32bit on a 250gig Samsung SSD with Grub on its own partition a swap partition and  a / partition. My fstab loads 3 external drives and at first I thought this may be the culprit so I commented out the external entries but to no avail. Below is my fstab entry:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=dc326ebf-4a80-4779-abca-c1093aa6849f /               ext4    noatime,nodiratime,discard errors=remount-ro 10       1
# swap was on /dev/sda3 during installation
UUID=29831935-7ac8-40bd-b4d0-37b13f819ee0 none            swap    sw              0       0
UUID=03984D547DA4EA2E  /media/alex/BigNTFS  ntfs-3g permissions,auto 0 0
UUID=098AC1DD78ECB54C /media/alex/BIGNTFS  ntfs-3g permissions,auto 0 0
UUID=015e2d60-08da-45da-9aaf-60c6d5728f88 /media/alex/BIGBuntu ext4 auto 0 0
UUID=f9cba2cd-484c-4008-89dc-13e5064bbbe8 /media/alex/BigBuntu ext4 auto 0 0
UUID=0ABF87364902D21B /media/alex/WD_Data_1  ntfs-3g permissions,auto 0 0
tmpfs   /tmp          tmpfs   defaults,noatime,nodiratime,mode=1777   0       0
tmpfs   /var/spool    tmpfs   defaults,noatime,nodiratime,mode=1777   0       0
tmpfs   /var/tmp      tmpfs   defaults,noatime,nodiratime,mode=1777   0       0      


If anyone can help me boot up my system I would much appreciate it. I would do a new install but I have added many aditions over the years and have just moved so only have access to the net through a 4g usb dongle and data is not the fastest and quite expensive.

Many thanks,

Al-Man

---

### Post by ajgreeny on 2018-02-12
"Unable to boot" is not very helpful and gives us no clues at all, so tell us more about what you actually see.
Where does the boot process get to?
Do you see any error messages?

The more info we have the better we may be able to help you.

---

### Post by Impavidus on 2018-02-12
Not much to go on, but I notice you have three tempfs file systems. For /tmp this is fine, but the contents of /var/tmp are supposed to be kept during reboot. I'm not sure about /var/spool, but it may have to be non-volatile too. I don't know what errors it might cause, but probably nothing during boot.

The option list of your root partition contains a space after discard. That should cause a problem during boot.

---

### Post by Al-Man on 2018-02-15
Thanks for your help I am sorry I have not been able to reply as I have been off grid. I have managed to boot my system i was able to edit my fstab using a live usb 
This is my new fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=dc326ebf-4a80-4779-abca-c1093aa6849f /   ext4    noatime       1       1
# swap was on /dev/sda3 during installation
UUID=29831935-7ac8-40bd-b4d0-37b13f819ee0 none            swap    sw              0       0
# UUID=03984D547DA4EA2E  /media/alex/BigNTFS  ntfs-3g permissions,auto 0 0
# UUID=098AC1DD78ECB54C /media/alex/BIGNTFS  ntfs-3g permissions,auto 0 0
# UUID=015e2d60-08da-45da-9aaf-60c6d5728f88 /media/alex/BIGBuntu ext4 auto 0 0
# UUID=f9cba2cd-484c-4008-89dc-13e5064bbbe8 /media/alex/BigBuntu ext4 auto 0 0
# UUID=0ABF87364902D21B /media/alex/WD_Data_1  ntfs-3g permissions,auto 0 0
tmpfs   /tmp          tmpfs   defaults   0       0
tmpfs   /var/spool    tmpfs   defaults   0       0
tmpfs   /var/tmp      tmpfs   defaults   0       0

so far no problems if any one has any advice for making it more efficient/friendly to my ssd I would be very interested.

Many thanks again.

Cheers. Al-Man  :)

---

