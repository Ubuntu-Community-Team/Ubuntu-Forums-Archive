---
title: "Cant install and run ubuntu"
date: 2011-03-25
forum: Installation &amp; Upgrades
---

### Post by cartmendez on 2011-03-25
Ok, I have to say I am frustrated beyond my limit and on the verge of forgetting this OS even exists.  But Ill give this forum a shot first.  Ive spent the last 6 hours on this and Im done reading other posts, so if I post something that is already on here, oh well.

Here it goes:  I have done much more than this but this is the latest results.
I am trying to put this on my desktop computer along side windows xp.
I downloaded Ubuntu right from their website.  Followed their instructions perfectly.  Ive tried every program on their website, including downloading and running the windows installer seperate from the ubuntu download.
I used the Universal USB installed and created my USB drive with Ubuntu on it.  It is a 4gb PNY flash drive.  It is in FAT 32 format.  My only other option for that drive is NTFS.  The USB seems to work fine.  I run WUBI on it, it seems to work fine itself.  Goes through the installation process and asks me to choose the amount of the hard drive to use for it.  I chose the default value it gave me, 17gb.  I chose my password.  It ran its install and gave me the option to reboot now or later.  I hit now and it started to shut down.  Ok, so that nice image you can see on the website where it gives you the option of booting either Windows or Ubuntu, that doesn't exist on my computer.  If I choose the harddisk, it goes right to windows.  End of story.  If I disable the harddisk and try to boot from the USB is has me select my USB drive, so it obviously see's it, but this is the error i get when I hit it, "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER."   

So, Im almost done trying this and hoping that here of all places I can get USEFUL information on this.

---

### Post by Hedgehog1 on 2011-03-26
cartmendez,

When you made the CD to load Ubuntu, did you select the 'Burn CD From ISO' option in your CD burning software?

When you create a LiveUSB correctly, you will be able to boot off of it.  The  "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER"  error message indicates to me that you were not successful at creating a valid LiveUSB.

May I suggest that you try this method of creating a working LiveUSB: [**ubuntu-on-flash-drive-using-windows**]("http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/")

***The Hedge***

:KS

---

### Post by cartmendez on 2011-03-26
> **Hedgehog1 said:**
> cartmendez,

When you made the CD to load Ubuntu, did you select the 'Burn CD From ISO' option in your CD burning software?

When you create a LiveUSB correctly, you will be able to boot off of it.  The  "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER"  error message indicates to me that you were not successful at creating a valid LiveUSB.

May I suggest that you try this method of creating a working LiveUSB: [**ubuntu-on-flash-drive-using-windows**]("http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/")

***The Hedge***

:KS

I never made an actual disk.  I just did the USB drive.  Ill give that method a shot and hopefully get it to work, if not does burning to a CD make any difference over the USB method?

---

### Post by cartmendez on 2011-03-26
> **Hedgehog1 said:**
> cartmendez,

When you made the CD to load Ubuntu, did you select the 'Burn CD From ISO' option in your CD burning software?

When you create a LiveUSB correctly, you will be able to boot off of it.  The  "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER"  error message indicates to me that you were not successful at creating a valid LiveUSB.

May I suggest that you try this method of creating a working LiveUSB: [**ubuntu-on-flash-drive-using-windows**]("http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/")

***The Hedge***

:KS

Ok, should have looked at the link first, sorry.  That actually is the software I used to make my USB.  I followed those steps exactly and I get the Disk Boot Failure.

---

### Post by Hedgehog1 on 2011-03-26
The USB method is faster and easier.

By the way, you don't have to unplug you hard drives to boot off the USB, you can change th boot order in BIOS.  Many mother boards also off a '1 time boot' selection (F11 on my home PC, F12 on my work PC) that will let you select the USB or a specific hard drive.

I hope you are successful.  I enjoy Ubuntu very much.  It might be a good fit for you, too.  But only you can judge that.

***The Hedge***

:KS

p.s. The LiveUSB can also be used to boot a Windows PC where Windows has crashed and allow you to copy data off the drive.  It is worth learning the LiveUSB skill just for that - you can be a hero now and again!

---

### Post by Hedgehog1 on 2011-03-26
Perhaps burning a LiveCD (at a slow speed for best readablilty) is the way to go.

I might add - if your motherboard does not support USB boot, the error you would get would also be: "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER" 

If you used a USB 3.0 port, please boot from a USB 2.0 port instead.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-26
Also, another way to create a LiveUSB is with Unetbootin, found here: 
[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

Many folks insist this make a better LiveUSB.  I have not had a problem with either, but I am a Nerd and blessed with 'the knack'.

***The Hedge***

:KS

---

### Post by Duncan Williams on 2011-03-26
Anyone wth a cd-burner and limited knowledge of computers would be better off to just burn the cd, this can be used for emergency data recovery as well. I found it quick and easy.

boot from cd is on most bios - no configuration required.
(except user selecting this option in their bios)

---

