---
title: "Persist USB boot works, but why must I always have to choose &quot;Try Ubuntu&quot; at startup?"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by Drunken on 2010-01-23
Hi,

I know there must be a way to fix this, but cannot find anywhere how to do it.

Problem is when I start up machine, it stops at bootloader  asking for language "English" and then "Try Ubuntu without any change to your computer" from screen as if I were running a Live CD or DVD installation.

Anyone know how to skip this step so my USB boots normally like a harddrive?

---

### Post by darkod on 2010-01-23
As long as the usb stick is created as bootable startup usb stick, it will always do that. It can't know whether you want to "use it" or install ubuntu on some computer.

For what you want, you need to install it on the actual usb stick. The procedure is the same as with internal hdd, you just specify the stick as destination for install. And in the last screen, before clicking Install, click on Advanced and make sure the bootloader (grub2) will be installed on the stick too (for example if your stick is /dev/sdb and your internal hdd /dev/sda, select /dev/sdb without a number like /dev/sdb1).
If you don't check that and grub2 goes to your internal hdd, you will not be able to boot anything without the stick because grub2 initial files will be on the internal hdd MBR but the grub2 config files will be on the stick. So you'll just get a grub error.

But for all this, you'll have to take into account that the live usb only needs 700MB like the ISO. On the other hand, the default 9.10 install is around 2.7GB so you'll need a stick of minimum 8GB and I'm not sure how it would work even on that.

---

### Post by Drunken on 2010-01-23
Yeah I used to have it directly installed on my USB like that, but I was concerned about wearing out the USB because it might think it's a real HDD.

With the usb-creator/live cd approach using the casper-rw I assumed the casper-rw volume was optimized for flash memory (thus not wearing it out as much).

Correct me if I am mistaken on this.

---

### Post by darkod on 2010-01-23
I don't know much about it, I'm not running usb installs. You might actually be right because flash memory in usb sticks is not designed for non-stop read/writes.

But I wouldn't know how to overcome initial menu selections on live usb.

---

### Post by lavezarez on 2010-01-23
> **Drunken said:**
> Hi,

I know there must be a way to fix this, but cannot find anywhere how to do it.

Problem is when I start up machine, it stops at bootloader  asking for language "English" and then "Try Ubuntu without any change to your computer" from screen as if I were running a Live CD or DVD installation.

Anyone know how to skip this step so my USB boots normally like a harddrive?

I had several successful USB installations (persistent data, acts like booting directly from a harddrive) for knoppix and linux mint at the [www.pendrivelinux.com]("http://www.pendrivelinux.com") site.  

There's one for Ubuntu 9.10 but I haven't tried it. you can check it out [here]("http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/").

---

### Post by C.S.Cameron on 2010-01-23
I have a 4GB Kingston pendrive that I have been doing Ubuntu full installs to for a couple of years now, since Feisty Fawn.
Sometimes I leave it plugged in for weeks.
I have seen no degradation.

I understand that a pendrive is good for about 10000 writes and that the writes get spread out over the media.
That would be a couple thousand hours if one was to sit down and continuously fill then delete the pendrive. That is over 50 work weeks with out coffee breaks.

However I would also like to know how to get rid of the opening screens on a persistent disk image install.

---

