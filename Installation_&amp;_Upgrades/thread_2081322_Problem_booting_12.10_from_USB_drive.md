---
title: "Problem booting 12.10 from USB drive"
date: 2012-11-06
forum: Installation &amp; Upgrades
---

### Post by rickhunt on 2012-11-06
Hi, I have tried using both the Ubuntu Start up disk creator and Unetbootin, same result.

When I try to boot 12.10 from a usb stick, it loads the splash screen but then gives an error message about

Can not mount dev/sr0 no medium found.
Along with some other message about error in line 7 stdin not a typewriter...Not sure what that means.

But anyway, it sounds like its trying to boot from a CD, but its a live USB, is there a way to tell it to boot from sdb1 instead of the sr0 device?

I have 12.04 installed, just wanted to see what 12.10 is like.

Any ideas?

Thanks
Rick

---

### Post by zvacet on 2012-11-06
I know this is not direct answer to your question,but you can try [Multisystem.]("http://liveusb.info/dotclear/") It is good tool.You can install it with 

```
sudo apt-add-repository ‘deb http://liveusb.info/multisystem/depot all main’

wget -q http://liveusb.info/multisystem/depot/multisystem.asc -O- | sudo apt-key add -
```

```
sudo apt-get update

sudo apt-get install multisystem
```

I never have problem with this tool.

---

### Post by rickhunt on 2012-11-07
Ok, well problem solved. For whatever reason, my IBM Lenovo Think Centre doesn't like the flash drive I was using.

When trying to boot from a Gigaware 4GB I got from Radio Shack, I get the error saying no media found on sr0

I tried on my 2gb PNY and it goes past that point, after it says no media found on sr0, it then scans the floppy, then the USB.

Funny, the Gigaware will boot fine on my laptop, just not on the IBM.

When I hit F12 at startup, I notice my bios reads the Gigaware 4GB as a USB Hard Drive and it reads the PNY 2GB as USB Stick. So for whatever reason, the Gigaware must be configured differently and the BIOS doesn't know how to handle that one.

Anyway, 12.10 Live USB boots fine from my 2GB PNY

Thanks

---

