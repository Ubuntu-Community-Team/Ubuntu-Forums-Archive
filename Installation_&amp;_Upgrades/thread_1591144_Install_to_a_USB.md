---
title: "Install to a USB"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by Animal0307 on 2010-10-08
I have a HP Mini 1116nr netbook and I want to use Ubuntu netbook remix on it. I've created a Live USB key but I don't want to install it to my hard drive. I would like to have it on my flash drive and still be able to save my data, drivers and installed programs like it would if I had installed it. Can I just boot with the live stick and then insert a second one and have it install to that instead of my hard drive?

---

### Post by penncon on 2010-10-08
> **Animal0307 said:**
> I have a HP Mini 1116nr netbook and I want to use Ubuntu netbook remix on it. I've created a Live USB key but I don't want to install it to my hard drive. I would like to have it on my flash drive and still be able to save my data, drivers and installed programs like it would if I had installed it. Can I just boot with the live stick and then insert a second one and have it install to that instead of my hard drive?

How did you create the bootable usb stick?  I tried writing the image to the stick using dd but it won't boot.

---

### Post by David Batty on 2010-10-08
When you created the usb, you would have had the option of creating a persistance file which allows you to save data onto the USB. If you did this you don't nead anything else.

---

### Post by Animal0307 on 2010-10-08
I followed the instructions on the Site.

[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

Worked great for me.

---

### Post by snowpine on 2010-10-08
> **Animal0307 said:**
> Can I just boot with the live stick and then insert a second one and have it install to that instead of my hard drive?

Yes, this will work fine. :) The only "gotcha!" is that, when you get to the final step of the installer, you need to click the Advanced button and choose to install the GRUB bootloader to your USB stick (instead of your internal hard drive). For example, if your USB drive is /dev/sdb, you would choose /dev/sdb (not /dev/sdb1 !) as the target for the GRUB bootloader.

If you skip this step, you might have trouble booting Windows (or whatever OS is installed on the internal drive) without the USB stick inserted, not a good thing. ;)

Also be aware that running from a  USB drive will be slower than running from an internal drive (due to USB transfer speeds) and may reduce the lifespan of your flash drive.

---

### Post by Animal0307 on 2010-10-08
Thanks. I'll give it a shot. I'm really just toying around trying to get my feet wet with Ubuntu. I'm not worried about speed. 

Thanks again. I'll post my results here soon.

---

### Post by wilee-nilee on 2010-10-08
> **Animal0307 said:**
> I followed the instructions on the Site.

[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

Worked great for me.

If you made the usb persistent you can make a larger than 4 gig ext2 this link explains.
[http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/](http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/)

---

### Post by ashfallen0 on 2010-10-09
I installed mine in the kinda-cheaty way. I loaded a live cd in Virtualbox, and installed it to the key that way.

I did encounter a problem I cant seem to find the solution for: in virtualbox, I only had the 1 virtual hard drive, so the installation was set to /dev/sdb.  my actual computer has 2 drives, so at boot time, the usb key defaults to /dev/sdc, but fstab lists it as /dev/sdb.

So, now after boot, though my OS runs and boots fine, the actual /dev/sdb cannot automount. Ubuntu seems to think that there's something in /dev/sdb already.  

:confused: Question is, can I change /etc/fstab entries without nuking my USB install?


I can see this being a bit of an issue if I plan on portable use with this OS install, as any time I plug in and run Ubuntu on any computer with more than 1 installed HDD, I'll lose the ability to use the 2nd drive(unless I terminal in and manually mount)
-------------------------------------------------------------
EDIT: Found out that if you want a "Truly" portable experience, find the UUID of the USB disk you used to install on. (use: sudo blkid)
Then edit your /etc/fstab and exchange /dev/sdb(or whatever drive is listed for /) to the UUID entry:

ORIGINAL :
/dev/sdb1       /               ext4    errors=remount-ro 0       1

NEW:
# Trying to mount the USB where it will leave everything else alone.
UUID=00000000-0000-0000-0000-000000000000       /               ext4    errors=remount-ro 0       1
NOTE: the 00000's will be the UUID unique to your USB drive

This does add a couple seconds to boot time the first time, but now all the drives in the host system will play nice.

w0rd.

---

### Post by Animal0307 on 2010-10-09
Works great. Its a bit slow but works well.

---

### Post by Animal0307 on 2010-10-11
Well That didn't last long. Its corrupted already. Not sure if my drive is shot or not.

---

