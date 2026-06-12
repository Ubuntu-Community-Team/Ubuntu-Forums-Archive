---
title: "no scroll or scroll click after upgrade to 10.04"
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by ussndmac on 2010-06-19
I did some Googling to no avail and searched these forums...

I upgraded several of my pc's from 9.04 to 10.04.

On has a MS PS2 mouse, the other have usb mice.

After the upgrade, there is no response to the scroll wheel or click of the scroll wheel on the system with the ps2 mouse.

Worked fine in 8.04 & 9.04, since I just used 9.10 as a step to 10.04, never tried it there.

Regards,
Mac

---

### Post by mörgæs on 2010-06-20
Did you try a clean install of 10.04?

---

### Post by usndmac on 2010-07-06
Not sure what would indicate a fresh install.

- 5 machines, scroll was the default behavior before upgrade
- 5 upgraded machines were successful
- 4 out of 5 the scroll wheel works
- 4 out of 5 use usb rodents
- the one that doesn't uses a PS2 port mouse

I'd think this indicates that it is a device settings either changed or were overlooked for PS2 rodents.

I've looked for details on how to set this in xorg.conf, but, while there are details in the man pages, there not much info in net land about how to use the settings for specific devices. If there is, someone tell me where.

---

### Post by WinRiddance on 2010-07-06
If you're using a PS2 mouse with a PS2 to USB adapter cable simply unlug it for a moment and then plug it back in. I have the same problem with my PS2/USB keyboard adapter and as soon as I unplug/plug it in, it works. If that works for you don't forget to make the thread as solved.

---

### Post by kingbirdy on 2010-07-06
perhaps you need to install some drivers to get it to work that weren't installed by default.

---

### Post by WinRiddance on 2010-07-06
> **kingbirdy said:**
> perhaps you need to install some drivers to get it to work that weren't installed by default.


You never need to install mouse or keyboard drivers with Ubuntu ... ;)

---

### Post by kingbirdy on 2010-07-07
> **WinRiddance said:**
> You never need to install mouse or keyboard drivers with Ubuntu ... ;)
oh. rare exception? I don't really know.

---

### Post by WinRiddance on 2010-07-08
Umh, aah, I wasn't kidding!
With the somewhat rare exception to Graphic or WiFi drivers you never have to install drivers for standard input hardware such as mice or keyboards. Technically even graphic chip and WiFi drivers work out of the box too 99% of the time, or at the latest once the "hardware drivers" setting is used (under SYSTEM then ADMINISTRATION) or a replacement found in the software center (such as Wicd as opposed to the standard network manager). **But mouse or keyboard drivers?** Nope, no reason to ever install anything there ...

---

