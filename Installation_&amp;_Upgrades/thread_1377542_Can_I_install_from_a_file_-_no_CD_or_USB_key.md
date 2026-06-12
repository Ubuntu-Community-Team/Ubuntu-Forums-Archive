---
title: "Can I install from a file - no CD or USB key?"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by bit mad on 2010-01-10
Quick question (I hope) ... :)
I have played with the "Live" CD / USB before, and it's my prefered way to install.

However, I have an old lappie which won't boot from USB, and I have no blank CDs. I can get files onto it (Windows XP) via the USB keys or the network... but ... is there a way to copy an ISO onto it and force it to run as if it had booted up with it? Is there a utility to allow running the file that the Live USB is made from, with Windows no longer running?

Thanks

---

### Post by michy99 on 2010-01-10
The only thing that comes to mind at the moment is that you can do a wubi install with the iso file and then convert it to a true dual-boot system. I know that's not exactly what you asked about, but it might be a solution.

---

### Post by keithweddell on 2010-01-10
I think this is what you are looking for:

[https://help.ubuntu.com/community/Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux")

Keith

---

### Post by michy99 on 2010-01-10
After looking around, it looks like you might be able to do it with unetbootin and do what they call a "frugal install" which installs the install disk to a partition instead of a usb drive.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Sef on 2010-01-10
If you can connect to the net, you can install Ubuntu; read Ubuntu Doc's [Installation]("https://help.ubuntu.com/community/Installation").

---

### Post by bit mad on 2010-01-10
Ok thanks... I'll make a USB Key with a wubi jobbie that can be launched from Windows, and see if I can use that to do the dual-boot install. I'll let you know how it goes ... however I'm a bit tied up at the moment trying to AV scan the thing which has a worm on it, and it hasn't been Windows Updated for years, etc etc etc (all those wonderful Windows horrors!)

Cheers :)

---

### Post by underquark on 2010-01-10
While updating, it might be worthwhile seeing if there's a BIOS upgrade available that will support booting from USB.

---

### Post by bit mad on 2010-01-11
> **underquark said:**
> While updating, it might be worthwhile seeing if there's a BIOS upgrade available that will support booting from USB.

That's a darn good idea, I'll look into that - thanks.

As for the install, it seems like the Unetbootin "frugal install" and Wubi methods will get things going to some degree, but not the ultimate proper install.... you can't install to a drive that Linux is already running on...?

I'm a bit confused at this point... I need to be running on the USB stick somehow so that I can install to the harddrive, it seems.

---

### Post by KeLa on 2010-01-11
I used this [http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows](http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows)
to install ubuntu (first 9.04 and then 9.10) to Toshiba R100 laptop that have no cd-rom
and can't boot from usb-stick or usb cd-rom.

---

### Post by bit mad on 2010-01-11
Thanks, but I didn't understand enough of that webpage to get going with it :)

---

### Post by Cheesemill on 2010-01-11
If you have access to another laptop that can boot from CD or USB you could always swap the drive into that to do the install then put it back in the original machine.
 
If you do use this method then whatever you do dont attempt to boot Windows in the other machine, it will throw a massive fit!

---

### Post by bit mad on 2010-01-11
> **underquark said:**
> While updating, it might be worthwhile seeing if there's a BIOS upgrade available that will support booting from USB.

No joy yet with that one. If you can find such a thing for an ancient old Time (MiTAC) 7321 with "Insyde Software SCU" BIOS with its fullsome 37GB disk and all of 352MB memory, cranked along by a 1.5GHz AMD Athlon 1800 :D ... then you're a better Googler than I!

At the moment it... well.. it works... I can surf da web with Firefox in Windows easily thanks to the built in modem *(I refuse to pay through the nose for expensive broadband at home when I can play with it all day at the office, so dial up it is)* as and when I need to.... but I'd like the challenge of doing that with Linux, if I can, and doing it without burning a CD has become part of that challenge.

I may have bitten off more than I can chew though :)

---

### Post by bit mad on 2010-01-11
> **Cheesemill said:**
> ... dont attempt to boot Windows in the other machine, it will throw a massive fit!

Indeed. Yet times are changing ... we had a Windows 7 machine die here the other day (motherboard), and bought a new PC, popped the old drive in, Win 7 detected all the changes and was up and running in minutes. A total breeze. We wuz well impressed! :D

About time too, really :P

---

### Post by bit mad on 2010-01-11
oooh... I've just noticed a strange sized opening on the side... it's got a floppy drive! And I've got floppies to hand... that might make it easier... perhaps? :)

"plop" looks worth a try [http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

---

### Post by bit mad on 2010-01-11
Well... I've drawn a blank. I'm mystified. The "Plop" boot manager was waaaay too complicated and wanted to install something permanently, which isn't what I want. I just want to be able to boot up with a floppy, for the darn thing to detect the USB key, and then boot up the USB key. Too much to ask?!

I found DOSUSB too, but couldn't get much sense from that either. I've run out of patience for tonight.

Any bright ideas anyone? Please? :)

---

