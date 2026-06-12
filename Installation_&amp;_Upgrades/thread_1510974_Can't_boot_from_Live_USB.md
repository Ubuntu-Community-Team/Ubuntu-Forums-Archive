---
title: "Can't boot from Live USB"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by jts1994 on 2010-06-16
[FONT=Courier New][SIZE=3]I wanted to create a Live USB device for Ubuntu 10.04[/SIZE][/FONT][FONT=Courier New][SIZE=3].[/SIZE][/FONT][FONT=Courier New][SIZE=3]  So I went to the Ubuntu website and followed their directions.  I downloaded the pendrivelinux.com Installer, downloaded Ubuntu 10.04 (32-bit) and put it on the usb.  I rebooted, but I booted into Windows (without any sort of menu or options).  The Ubuntu sit said this might happen so I changed the boot order to make USB devices first.  It still booted into Windows.  Then I erased the USB and tried the whole thing over with Ubuntu 10.04 (64-bit).  Still no success.  Could anyone help me with this?  

I may have made a mistake when I changed the boot order, because I'm not very familiar with BIOS.[/SIZE][/FONT]

---

### Post by C.S.Cameron on 2010-06-16
Not sure what your BIOS is like but sometimes you just need to make the flash drive your first HDD, (under hard drive order).
Some old old computers will not boot flash drives so you need to use a boot CD to make things work.

---

### Post by oldefoxx on 2010-06-16
> **jts1994 said:**
> [FONT=Courier New][SIZE=3]I wanted to create a Live USB device for Ubuntu 10.04[/SIZE][/FONT][FONT=Courier New][SIZE=3].[/SIZE][/FONT][FONT=Courier New][SIZE=3]  So I went to the Ubuntu website and followed their directions.  I downloaded the pendrivelinux.com Installer, downloaded Ubuntu 10.04 (32-bit) and put it on the usb.  I rebooted, but I booted into Windows (without any sort of menu or options).  The Ubuntu sit said this might happen so I changed the boot order to make USB devices first.  It still booted into Windows.  Then I erased the USB and tried the whole thing over with Ubuntu 10.04 (64-bit).  Still no success.  Could anyone help me with this?  

I may have made a mistake when I changed the boot order, because I'm not very familiar with BIOS.[/SIZE][/FONT]

What you report is very odd indeed, and contrary to the way that PCs are devised to work.  The BIOS kicks in first and does it identification of hardware and all, then depending on the settings for boot devices and order, determines which device to go to to next.  If that device is unresponsive or fails to act, it then goes to the next device.  But you decide te order and what to include.

A proper LiveCD setup only requires the CD drive, so if you were to detach or disable the hard drive, that would cut off Windows completely and you should then be forced to boot from the CD.  But this is assuming that the LiveCD was a good download and you made a good burn of it to a CD.  This is not always true, you know, and typically, for something as critical as a LiveCD, I do a couple of downloads and burn each at least twice to CDs.  You might be surprised how many digital CDs turn out to be defective, likely due to OEMs cutting cost in the making of CD blanks and CD-RW drives.  To fight back and keep costs down, I suggest you invest in and use some more CDs.  And make note of the brands that are not serving you so well, and buy something else next time.

I also invested in an external USB CD burner, which works great when I begin to distrust how an internal one might be behaving, or need that capability with something like a netbook.

Burner software is another sticky point; I find some good, some better, and some of questionable value.  If you just want to just to the point where you have a LiveCD in hand and no major investment, you can order rhe LIveCD on CD for just a few dollars,  I've even found that there are people that sell them through dBay.  There you can go by the buyers' responses as to whether you are getting a good deal or not.

All sorts of ways to work around this.  Sometimes all that is needed is to go at it from a different angle.

---

### Post by garvinrick4 on 2010-06-16
I go into BIOS and set CD,USB,HDD in that order and leave it there. Use the apps,s Ubuntu gives me such as Startup Disk Creator which gives you 4 gigs of persistence so you can make changes to Live USB and have used Unetbooten before but no persistence so is quite like a Live CD.  Every once in a while a Flash drive just does not want to become bootable.
Believe is hardware problem not software. Centon has always worked for me. Others I imagine are fine also I just prefer what has worked for me. Yes also Brasero Desk Burner if I make sure at slowest speed works just about all the time. They are in Ubuntu install and work so why fix what is not broken. 
 To not have BIOS set not to boot off of CD first when that  media is always available is sure way to make small problem into big one.

---

### Post by oldfred on 2010-06-16
On my computer USB flash drive is a choice under hard drives not USB devices. 

I originally tried USB floppy, USB CD USB this and that - It had a lot of choices but I could not get any to work. I then was changing boot order of hard drives and there was the USB flash drive.

---

### Post by jts1994 on 2010-06-16
Thanks, people who have responded so far.  
What's weird about this is that my computer is less than a year old and should boot from the USB fine.  I'm having trouble getting back into BIOS.  I don't remember what button I pressed to get into it the first time :confused:.  This probably sounds stupid, but is there a particular button to press or does it vary?

---

### Post by wilee-nilee on 2010-06-16
Use unetbootin that loader does not work all that well, and try different thumbs, and check the md5sum of the iso.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by oldfred on 2010-06-16
You should see a list of the buttons to use to get into BIOS or single boot on the initial BIOS screen. It goes by quick and is usually small print somewhere. Otherwise you have to look at your motherboard manual.

My computer uses del key for BIOS and f12 for single boot. But my portable is different.

---

### Post by jts1994 on 2010-06-17
Thanks a lot.  
I figured out the Bios button and I fixed the boot order.  I had actually put something else first and the flash drive was still last, so I fixed that and now it's working fine.

---

