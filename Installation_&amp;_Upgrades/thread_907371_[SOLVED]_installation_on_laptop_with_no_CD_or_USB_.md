---
title: "[SOLVED] installation on laptop with no CD or USB support"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by OldGamer on 2008-09-01
I have an older dell inspiron laptop.  I had previously installed ubuntu on it with a completly encrypted hard drive.  I decided that I want to reinstall linux with lighter apps, but my CD drive no longer works, and my laptop does not support booting from USB.  I have another laptop which uses the same size hard drive (it's a newer latitude), so I thought I might be able to put the old hard drive in the new computer, reinstall an OS, then put it back in the old computer.  I have tried this with puppy linux, but when I put the hard drive back in the old computer, I get a kernel panic.  Does anyone know of a way I could install linux (any light version would work) in this manner?  Is it possible for this to work at all?  Thanks.

OldGamer

---

### Post by phenest on 2008-09-01
I have a Dell Latitude L400. Up to now, I was able to do it using Windows XP as the host, and do a network install of either Windows or Ubuntu. [Link]("http://www.lockstockmods.net/2008/04/26/easy-way-to-pxe-boot-windows/")

I used to dual boot Ubuntu with XP, but now my computer is pure Ubuntu. So, I would also like to know how to use Ubuntu as host. Getting a DHCP server running is the start, but I don't know how on Ubuntu.

---

### Post by phenest on 2008-09-01
Although I did find this: [Link]("http://ubuntuforums.org/showthread.php?t=453988&highlight=network+install") which I will be trying myself.

---

### Post by OldGamer on 2008-09-01
Well, I ended up installing Fluxbuntu on the hard drive with my newer laptop, then I put the hard drive back in my old laptop and it booted up fine.  I'm actually using it right now to reply to this post.

---

### Post by SR_ELPIRATA on 2009-04-20
Not sure if it helps but, I've done this many times with my Dell laptops. As long as all the drives are IDE 2.5", I just switch to another laptop, install ubuntu in default settings (I mean like install but not put drivers that work only on that machine, like if you have nvidia or ati), then turn off, swap drive to end user laptop and boot-up.

So far has worked well, even when switching between manufacturers HDDs, last time I tried this was for a Compaq that had less memory than required by Ubuntu. It worked well.

ELP

---

