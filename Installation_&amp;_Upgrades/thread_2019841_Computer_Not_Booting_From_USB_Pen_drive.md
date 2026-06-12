---
title: "Computer Not Booting From USB Pen drive"
date: 2012-07-07
forum: Installation &amp; Upgrades
---

### Post by Frsutrato on 2012-07-07
I've made a bootable pen drive by way of the recommended method.  I've used the USB installer thing for Ubuntu and put the ISO file as shown in a tutorial.

It doesn't matter how I alter the boot settings in my BIOS, the computer always boots off the C: drive and loads Windows XP.

I've set the BIOS to recognise the USB drive, first and foremost, as the primary boot device and I've even tried disabling all other boot drives - but for some stupid reason all I can ever achieve is loading Windows XP.

I have made sure to save the settings (F10 - save to CMOS and exit? Y / press enter) but I cannot get the computer to boot from my USB pen drive.  All I get is Windows XP.  How can this be?

---

### Post by msammels on 2012-07-07
Can you link the tutorial please? However, I would recommend you use [Universal USB Installer](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) from within Windows.

If you know how old your BIOS is as well, this would help to diagnose the problem.

---

### Post by arkster on 2012-07-07
I had this problem before. You need to do the following.

* Make sure that the usb is recognized by your bios. It should list it in one of the menus.
* Make sure that you set the boot priority to boot off the USB.

If your bios shows your other hard drives and not your usb key, then the likely issue is how the usb key was formatted. I've found that windows/linux Fat32 formatting does not work properly for this. I almost always have to revert to using the HP storage format tool. You can download that in the link below or use Google to search for a different download location.
[http://files.extremeoverclocking.com/file.php?f=197/](http://files.extremeoverclocking.com/file.php?f=197/)

---

### Post by OM55 on 2012-07-07
Hi,

First - of course you have to make sure that the USB-Key and/or USB-Drive are listed as first in the boot order of your BIOS. To enter the BIOS settings restart your computer and press the relevant hot key (it will be listed briefly on the first boot screen, normally F2 or 'Del' key, but could also be another combination). When in the BIOS screen, switch to the 'boot' menu and make sure that all USB related items are listed first in the boot order.

Now to the important and less known part:

There are 2 'kinds' of bootable USB: One is called 'USB Key' and the other is 'USB Drive'. For some reason when the BIOS bootable USB technology was developed, they created this distinction (probably thinking that USB keys will never be used as complete USB drives). The distinction is made during the formatting of the USB device, so you can format it one way or the other.

However, not all BIOSes are created alike, and some today will no longer be able to recognize a USB bootable device as USB-Key but only as a USB-Drive, while others will have both options.

If you have completed successfully the first paragraph above but still cannot boot from the USB device, it is very possible that your USB device is formated as USB-Key and either your BIOS does not recognize a USB-Key at all or the USB-Key is listed BELOW the internal IDE drive in the boot order.

What you will need to do is re-format your USB device as a USB-Drive and not as a USB-Key. This will solve the problem and the device will be recognized by the BIOS.

As far as I know the default setting of the Ubuntu Startup Disk Creator is the 'USB Drive', but if you created your USB key using another software, that may have not been the case, and here is your culprit. 

Hope that helps.

---

### Post by Frsutrato on 2012-07-07
Thank you for the replies, everyone.

As I've said, I've gone to great pains to ensure the BIOS is set up to recognise the USB device.   What OM55 says, seems to be on the money, as far as I can tell, so thank you for explaining that, OM.

I think I understand the distinction between 'key' and 'drive' but I'm not sure how to go about making this clear in any formatting instructions.  I intend to re-build the USB boot sector using the Uinversal USB Installer (from within Windows) as I did before, while looking out for the approprite options covered in this conversation.

One other thing, perhaps I should mention... I have an external 500GB USB drive here on my desk and am wondering if this might be a fail safe device to use instead of the pen drive?

I am really beginning to wonder if my BIOS (due to the age of the motherboard) actually does support what I'm trying to achieve so, msammels, you could be right.  Trouble is, I don't really have access to that information.  It might be about five or six years old.  It's as old as the AMD Athlon 64 4000+ 988 MHz processor it came with.

I'll first address the re-formatting of the USB stick and then get back to you on the results.

That - and the bootable CD for Ubuntu, which I have also, so far, have had no success in booting from.  I got as far as the 'try first' demo stage but I can't seem to get it to install as an operating system alongside Windows.  Some advice on this would be handy.

Again, thank you very much for your speedy replies.

---

### Post by OM55 on 2012-07-07
Can you describe what issues you encountered when trying to install Ubuntu 12.04 as dual boot with Windows?

If you are able to get the "Try Ubuntu" to work off the live CD that means your hardware is sufficiently compatible and the dual boot will work fine. 

Please describe the nature of the problem when you try to install a dual boot, and I'll try to help you out.

---

### Post by tommyguns on 2012-07-07
Regards the cd and usb - did you verify the md5sum of the iso used?  Did you use the slowest speed possible for burning the cd?

I had my own problems getting ubuntu to work, tried cd and usb.  Gave up on the cd, and while I used usb installer for my first attempt and used the iso I had downloaded directly from the ubuntu site.......I then decided to try another program I'd seen mentioned called unetbootin.  And rather than using the iso image I downloaded from ubuntu (which I did verify the md5sum of) I chose for unetbootin to download an iso itself.  When I tried the usb prepped by usb installer it just froze my laptop despite all usb options being ahead of hdd and cd in bios.

Just sidetrack on to what OM mentioned, in my bios I had keyusb, drive usb, usb cdrom, and another usb option I can't recall, along with the other things like hdd & cd etc.  Do you have those multiple usb options?

Anyway, I reset my bios to default & confirmed that the usb options were still ahead of cd and hdd in the boot order.  I then reset my laptop, plugged in my usb drive & was very very happy to see the unetbootin options list, went ahead and installed perfectly.  This was after a fair bit of trial and error, a few wasted cd's due to each one of them getting no further than saying "loading bootlogo......." & a lot of frustration. 

But I got there in the end and I got my laptop back up and running after vista got corrupted and my recovery disks turned out to be totally unfit for purpose & made the problem worse.  Luckily a friend lent me their laptop so I could get it all sorted out.

---

### Post by OM55 on 2012-07-07
.

---

