---
title: "Netboot Install can't find PXE file"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by fizban9 on 2007-12-15
I'm trying to install Ubuntu over the network to a friends laptop.  I've been following this guide:

[http://ubuntuforums.org/showthread.php?t=327597&highlight=ubuntu+netboot+pxe](http://ubuntuforums.org/showthread.php?t=327597&highlight=ubuntu+netboot+pxe)

My setup at the house is pretty simple.  I have a DSL modem plugged into a linksys router.  On my windows machine I set up tftpd program and I tested, with a good laptop, that my windows box assigned the IP instead of the router and I was able to get on the internet.  

The problem is that when I hook my friends laptop up to the router and boot it, I can look at the tft logs and see it's getting an IP address, but it's not finding the pxe file.  

I copied the pxelinux.0 file (as well as every other file from the i386 directory) into the directory that the tft program runs from.  I tried specifying the path using the absolute path (c:\tft\pxelinux.0) and I've tried using a relative path after checking the option to "allow '\' as virtual root" (\pxelinux.0) and it can't find it either way.

Never done a network install of an OS, can anyone give me any pointers to figure this out?

Thanks in advance.

---

### Post by fizban9 on 2007-12-17
Bump!

Hopefully I wont get in trouble for that.

---

