---
title: "Installation Issue"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by mmmmmmmchips on 2007-07-27
This is my first endeavor into Linux, so this may be simple to fix but I'm stumped. 

I downloaded the CD image, burned it to a CD and tried to boot on my laptop. During the boot I get an error message and windows boots normally. The error is:

For Realtek RTL8139(X)/8130/810X PCI Fast Ethernet Controller v2.13 (020326)
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE ROM.



Any ideas?

---

### Post by merlinus on 2007-07-27
Did you burn the cd as a disk image?  When you look at the contents, are there folders and files?  If not, it is burned as a data disk and will not boot your computer.

Also, you may wish to compare the checksums.  Info on this here:

[http://www.psychocats.net/ubuntu/iso#checksum](http://www.psychocats.net/ubuntu/iso#checksum)

And make sure you burn at 4x or less.

-merlin

---

### Post by dando80 on 2007-07-27
Sounds like a bad cd. The system seems to be trying to PXE boot off the network instead of the cd.

---

### Post by mmmmmmmchips on 2007-07-27
Re-burning the CD at 4X speed worked. Thanks a bunch!

---

### Post by mmmmmmmchips on 2007-07-27
Another snag. 

"Screens found, but none have a usable configuration.

Fatal server error: 
no screens found

The X server is now disabled. Restart GDM when it is configured correctly."

Then I get some sort of command prompt.

---

### Post by dando80 on 2007-07-27
What kind of video card? Can u post the Xorg log?

---

### Post by merlinus on 2007-07-27
Try this at the command prompt:

```

sudo dpkg-reconfigure xserver-xorg

```
You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:
```

startx

```

-merlin

---

