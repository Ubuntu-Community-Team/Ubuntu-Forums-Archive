---
title: "CD live to login screen -- no install gui"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by rosserver on 2007-08-25
I am trying to install 7.04 server from CD.  It starts in text mode and it asks me for login before getting to the gui.  I (of course) have no idea what the login is, but I really just need to get to the server/lamp/memtest menu like before.  What's up?

---

### Post by Pumalite on 2007-08-25
You might have low memory. OTOH you might need to do md5sum on your iso, etc. Your graphics might be another problem. You might try Alternate CD or post your specs.

---

### Post by rosserver on 2007-08-25
The box is:
Tyan Thunder LE S2510
dual p3 866mhz
2 gig PC133 ECC
18 gig fujutsu Scsi

I have already put ubuntu on several dual p3 1.4 gig machines, one with ata raid and all went well.

I do get a couple of "complaints" during the booting to live process -- but nothing too fatal.

Unable to locate RSDP
timer not connected to IO-APIC
agpgart unable to determine aperture size
illegal Interupt conf (code out of date)

everything else looks normal,
it just goes:

ubuntu login:

---

### Post by Pumalite on 2007-08-25
Burn a new iso just to be sure. Torrent better than HTTP and FTP. ( I would go for the Alternate CD)

---

### Post by rosserver on 2007-08-25
I just got rid of the cable/internet and now have a T1.  Unfortunately huge downloads are much slower now.

I actually did already have 6.06 and 7.04 servers on CD as well as the desktop version and I did do a checksum with md5sum.exe and all is well -- I just burned a new copy, slowing the burner down to 32x just to make sure and all is still the same.

Tyan is horrible stuff, this mobo is old, but I have 10 of them all in 1u racks, I am determined to make them work.

Does anyone know the default login for the live CD?

---

### Post by Pumalite on 2007-08-25
It's not supposed to have a 'login'. Bur try: 'root', 'ubuntu', 'demo', etc.

---

### Post by coolbrook on 2007-11-18
I'm experiencing the same problem on a S2518.  It's the Live CD sent from Launchpad bringing up a login screen.  I'll reboot and see if I can get further.  The first time around I got a neverending list of squashfs errors.

---

