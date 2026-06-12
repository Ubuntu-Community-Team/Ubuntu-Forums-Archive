---
title: "installation problem Toshiba Satellite C650D-109"
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by marck.karam on 2011-10-28
Good Day For everyone
so I've been trying all the day to get Ubuntu on my Toshiba Satellite C650D-109 lap top

i tried install 32bit as well as 64 bit on a pen-drive and DVD

tried to insatll with nomodeset as well as acpi=off

this seems to be the error i get. I cannot figure out what is wrong myself.

screenshot:

[http://i147.photobucket.com/albums/r316/mcool5/DSC02441.jpg](http://i147.photobucket.com/albums/r316/mcool5/DSC02441.jpg)
Hopefully someone will have some advice or some input into a way to resolve this as I am not the most savvy person with Ubuntu.

Any hint will be appreciated.
 Thanks in advance.
 Regards.

---

### Post by zeero_k on 2011-10-29
I had a similar problem happen when I created a bootable USB stick and then pulled it out too soon after unmounting/safely removing the drive. It seems to take several seconds to fully unmount the bootable USB drive. The result was that the casper file got corrupted.

Try erasing the drive and re-creating it. Then count to 10 after safely removing it before you pull it out of the USB socket :)

---

### Post by marck.karam on 2011-10-29
> **zeero_k said:**
> I had a similar problem happen when I created a bootable USB stick and then pulled it out too soon after unmounting/safely removing the drive. It seems to take several seconds to fully unmount the bootable USB drive. The result was that the casper file got corrupted.

Try erasing the drive and re-creating it. Then count to 10 after safely removing it before you pull it out of the USB socket :)

at the first thx 4 ur attention...!

dude this problem faced me when am try to install ubuntu from the usb and **DVD**

so i dun think it's a usb problem ..!

wait 4 u guys

please help...

---

### Post by mörgæs on 2011-10-29
When booting from USB and DVD, you will get the option of self-testing the media. Does the test give indication of anything wrong?

---

