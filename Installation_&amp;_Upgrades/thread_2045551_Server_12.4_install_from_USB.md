---
title: "Server 12.4 install from USB"
date: 2012-08-21
forum: Installation &amp; Upgrades
---

### Post by optimator on 2012-08-21
Hey! I'm having trouble installing Ubuntu Server 12.4 from a USB stick. There is no CDROM or HD in the machine. The only drive will be USB.

I don't currently have Ubuntu installed. I d/l the iso and using xboot burned it to a partitioned USB. 

I can boot from the USB, but of course it fails when it looks from the .seed file from /cdrom.

I've spent several hours looking for solutions, and finally tried mounting the usb stick and then mounting the iso image to /cdrom. It started to work, but then failed.

Any ideas?

---

### Post by TheFu on 2012-08-21
I'm surprised that xboot doesn't work, but I've tried a few different solutions and stopped looking when yumi [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/) worked.

It will build a bootable liveCD on a flash drive. It also lets you boot lots of different OSes from the same drive - no partitioning needed.

---

### Post by optimator on 2012-08-21
Yes - Yumi worked to get the server install going. However, it now is hanging on "Select and install software"

It says "Retrieving file 1 of 29" - but then errors.

---

### Post by TheFu on 2012-08-21
You can't "install" to the same media you are running from. Is that what you are trying to accomplish?

I think you need an HDD to install to or need to run off the liveCD (on the flash drive).

Am I missing something?

---

### Post by vertago1 on 2012-10-12
I was able to install Ubuntu server from an eSATA disk using the technique you mentioned:

1) install grub2
2) copy the iso onto the disk
3) setup the grub.cfg file for booting iso
4) once booted use alt-f2 to mount the disk, and from the disk mount the iso to /cdrom
5) proceed with the installation but you cannot unmount the original disk or the installation will fail.

In my case I even had the iso on a disk I was mounting to /home in the partition setup, but without formatting it. I would guess that the installation would work for USB. If it doesn't work and you have enough ram you could mount a folder to a tmpfs and copy the iso to it, then mount the iso to /cdrom.

---

### Post by oxfordattic on 2012-10-16
Heyo,

I have been attempting to install server 12.04.1 on an acer aspire one for the past few days using a USB.

My problem arises with the /cdrom as well. I managed to work past this step using unetbootin and adding;

cdrom-detect/try-usb=true

to the initial boot options. This however only gets me 1 step farther in the instillation, it halts again while attempting to read from /cdrom.

I've attempted to mount the USB as /cdrom, however this has failed as well. My next step is to try GRUB2 to see how that goes.

I will re post if i manage to get it installed with the steps.

---

### Post by TheFu on 2012-10-16
I've installed Ubuntu 12.04 on multiple systems that don't have a CDROM or DVD at all without issues using the USB flash drive as the source and a SATA/IDE/eSATA disk as the target.

Yumi has never failed. It has worked on 2002 Celeron-based PCs and Core i7 high end laptops.

Are you trying to use a USB flash drive as the target?  I've never attempted that. Sorry.

---

