---
title: "How To Update BIOS using Linux?"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by garryconn on 2011-01-10
How do you update BIOS when manufactures such as Dell only provide the update via an .exe file? Obviously I know I can install Windows and perform the update that way. But what if I don't want to do that? What if I am totally against using Microsoft products, then what? Sensibly, it would make sense to update bios prior to installing Linux, but what happens if there is a BIOS update after the fact?

---

### Post by Grey on 2011-01-10
It's been many years since I've bothered updating my BIOS.  But the last time I did it, I did it via FreeDOS booted from a USB drive.  I would assume that most motherboard manufacturers still have a DOS version of their BIOS updater kicking around?

---

### Post by mikewhatever on 2011-01-10
Actually, Dell has a package in the repositories, firmware-addon-dell, for bios updates, though I can't vouch for it. Another way is to use a freedos live cd to run an .exe.

---

### Post by kansasnoob on 2011-01-10
> **garryconn said:**
> How do you update BIOS when manufactures such as Dell only provide the update via an .exe file? Obviously I know I can install Windows and perform the update that way. But what if I don't want to do that? What if I am totally against using Microsoft products, then what? Sensibly, it would make sense to update bios prior to installing Linux, but what happens if there is a BIOS update after the fact?

I have managed to do so using FreeDOS installed to a Flashdrive using Unetbootin:

[http://www.freedos.org/](http://www.freedos.org/)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

It was hardly straightforward though and may have added to my balding :D

---

### Post by cogier on 2011-01-10
Bootdisk.com is another option
[http://www.bootdisk.com/bootdisk.htm]("http://www.bootdisk.com/bootdisk.htm")

---

### Post by pricetech on 2011-01-10
Most of the Dell updates I've installed will work in a DOS environment, and I suspect they all will, but I can't confirm because I haven't tried with updates larger than a floppy will hold.

---

