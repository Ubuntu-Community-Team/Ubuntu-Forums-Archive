---
title: "Install Bootloader on USB"
date: 2007-07-14
forum: Installation &amp; Upgrades
---

### Post by taffy-nay on 2007-07-14
I'm just wondering if it would be possible to install a boot loader on a USB stick.


I'm think of a scenario where by 

1) User would be running a dual booted system
2) Upon boot up without USB Boot loader plugged in, Either nothing happens, or it loads a default OS
3) Upon boot up WITH USB Boot loader plugged in, User is then presented with Grub to load additional OS's


Is this in anyway feasible?? or am I thinking pie in the sky?

---

### Post by LouisvilleLIP on 2007-07-14
I like the idea, it should be possible.  I'm looking into it now, I'll let you know if I figure it out.

---

### Post by BOMBkangaroo on 2007-09-05
Not that I have a thing for bumping oldish threads, but this is relevant to my interests.

I haven't been able to find anything else about this either on these forums, or google, etc, so I was wondering if there had been any developments with regards to this?

I tried out Ubuntu with GRUB, and I got the NTOSKRNL error when trying to get back into windows.
I'd love to be able to be able to grab a new HDD and start using Ubuntu, and not have to worry about killing windows and all my funny animated GIFs I downloaded.

---

### Post by bluknight on 2007-09-05
Make sure your bios allow boot from usb
When fresh install identify your usb partition, say /dev/sdb1 (example)
When asking to install bootloader, select /dev/sdb1 root partition.

For existing install, identify your desired usb booting partition, say /dev/sdb1
As root>grub-install /dev/sdb1
Mount /dev/sdb1 to say /mnt/usb (root>mount /dev/sdb1 /mnt/usb)
Copy your current boot loader menu.lst to usb device
     root>cp /boot/grub/menu.lst /mnt/usb/boot/grub/
Identify your usb partition's UUID
    root>vol_id /dev/sdb1 | grep UUID
Copy the UUID for the booting partition to your menu.lst file to replace UUID

When trying to boot the usb device make sure bios set to boot removable devices first before internal HDs and usually the first USB slot is best (depends on your machine which usb slot boots first priority)

Good L

---

### Post by BOMBkangaroo on 2007-09-05
Thanks, I shall have to give this a go.

---

### Post by Muahdib on 2007-10-21
did this work?

I was wanting to do the same thing.. I was thinking either a usb memory stick or a memory card. in the good old days I use to do this with a floppy.. 

so anyway.. did this work?

---

### Post by Muahdib on 2007-10-22
did this work?

I was wanting to do the same thing.. I was thinking either a usb memory stick or a memory card. in the good old days I use to do this with a floppy.. 

so anyway.. did this work?

---

### Post by Muahdib on 2007-10-22
sorry dubble post

---

### Post by gregmo on 2007-11-15
I've been trying to get this to work for the past week with no luck.  I think it's because my BIOS maps the devices differently (and inconsistently) when I boot from the USB flash device.  I've tried all different combinations in device.map (and trashed my hd0 MBR in the process by mistake) with no luck at all.  The closest I get is the grub prompt and it doesn't seem to be reading my menu.lst file.  Otherwise, GRUB error 17 seems to be the consistent response.

I have gotten it to work using a USB flash drive for boot with a USB HDD (internal HDD disabled), but that's not the point of this thread.

Is there any way to determine in what order the BIOS is going to assign the drives for a USB boot without actually booting when my internal HDD are not disabled?  My understanding is that the USB boot drive is supposed to end up as (hd0), but it doesn't appear to be doing that on my machine, otherwise it should find menu.lst.

I've also tried installing the MBR, GRUB, and /boot on the flash, setting root to my HDD installation with no luck there.  I'll be thrilled if I can just get the flash drive to boot and show a splash screen with my entries, whether or not I can actually boot into one of them.

I'll keep trying and I'll post if I figure it out.

---

### Post by bulldog on 2007-11-15
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_add_Grub_to_your_USB_thumb_drive](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_add_Grub_to_your_USB_thumb_drive).

Much info :)

---

