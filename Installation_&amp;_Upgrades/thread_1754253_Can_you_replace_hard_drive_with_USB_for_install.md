---
title: "Can you replace hard drive with USB for install?"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by trolol on 2011-05-09
Hi, I did post a thread yesterday saying a problem I had with installation but now I know what REALLY happened. My hard drive is destroyed lol I think whenever I try to install 11.4 it says "disk failure is imminent". So maybe I was wondering if it is possible to install Ubuntu on a 4gb USB flash drive and use that as my hard drive? If not a USB then maybe an external CD drive (I am on a netbook and I dont mind having a USB inside all the time) So yeah if its possible then thats great I would like to know how. But if its not possible, or maybe it is but a bit harder I just want to know what I can do because my laptop is currently useless and I dont wanna go back to Windows coz it died on me several times already. Or maybe I can try a different version of Ubuntu?? Also someone might suggest just keeping it in "try Ubuntu" but th internet drivers arent there and I need to restart pc to get it but I cant restart without being fully installed so help would be greatly appreciated I dont want to have to share this PC for any longer D: okay thanks :popcorn:

---

### Post by ThatCoolGuy220 on 2011-05-09
You could install Puppy on a USB,

Or you can check this 

[http://www.pendrivelinux.com/usb-x-ubuntu-610/](http://www.pendrivelinux.com/usb-x-ubuntu-610/)


you can use Puppy for doing the job if you dont have windows 
(I think im new on this)
or you can use a friend PC

---

### Post by Hedgehog1 on 2011-05-09
I was given an older HP lasptop with a hard drive that was giving the same  "**disk failure is imminent**" message.  The drive smelled like burning bacon when it was powered on!

I pulled the hard drive until I got around to buying another one, and installed Ubuntu on a 16 gig USB Stick.  I did a real install from the CD to the USB.  As long as you have a reasonably fast USB stick it actually works rather well!

Now, you could get by on as little as an 8 gig USB stick, but running on a 4 gig USB stick is a little tight.

If you cannot get a larger USB stick right now, then the pen drive persistent install on your 4 gig USB stick works OK (and is faster than running from a LiveCD).

You have several options to get your system working again until you can acquire a new hard drive.


***The Hedge***

:KS

---

### Post by trolol on 2011-05-10
> **Hedgehog1 said:**
> I was given an older HP lasptop with a hard drive that was giving the same  "**disk failure is imminent**" message.  The drive smelled like burning bacon when it was powered on!

I pulled the hard drive until I got around to buying another one, and installed Ubuntu on a 16 gig USB Stick.  I did a real install from the CD to the USB.  As long as you have a reasonably fast USB stick it actually works rather well!

Now, you could get by on as little as an 8 gig USB stick, but running on a 4 gig USB stick is a little tight.

If you cannot get a larger USB stick right now, then the pen drive persistent install on your 4 gig USB stick works OK (and is faster than running from a LiveCD).

You have several options to get your system working again until you can acquire a new hard drive.


***The Hedge***

:KS

Thanks! Do you think I should just  try an older version of Ubuntu? Then maybe that way it wont be as "tight"? And also can you tell me how to install it straight to the USB and ignore the HDD please I have no idea how to do this thanks

---

### Post by Hedgehog1 on 2011-05-10
> **trolol said:**
> Thanks! Do you think I should just  try an older version of Ubuntu? Then maybe that way it wont be as "tight"? And also can you tell me how to install it straight to the USB and ignore the HDD please I have no idea how to do this thanks

Installing 10.04.02 is a good idea - it is smaller than Natty and very stable.

If you (1) remove the hard drive from your laptop (2) plug in your USB drive and then (3) Boot from the 10.04 CD, the install will default to the USB stick.

That is the easiest way.

You can leave the hard drive in and do a manual install to the USB stick (if the dying hard drive is /dev/sda, then select /dev/sdb for all your work including the boot loader).

But sense you need to pull the hard drive anyway....

***The Hedge***

:KS

---

