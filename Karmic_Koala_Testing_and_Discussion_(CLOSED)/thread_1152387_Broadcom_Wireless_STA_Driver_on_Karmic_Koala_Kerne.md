---
title: "Broadcom Wireless STA Driver on Karmic Koala Kernel 2.6.30 RC4"
date: 2009-05-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by flipmatthew on 2009-05-07
First off, here is the problem. The B43 driver is limiting my bandwidth to 1mb/s (that's mega BIT.) sometimes, it will work at full speed, then it will work slow and then not work at all, this all happens in a matter of minutes. Before when I had the 2.6.28 kernel, I went into the restricted driver manager and added Broadcom Wireless STA Driver. This driver worked fine, at 54mb/s. I've searched all over and cannot find a WL (Broadcom Wireless STA Driver) for Kernel 2.6.30 RC4. I was wondering if anyone can help me :), as this means a lot to me. 
Just for comparison i was getting 6mb/s at speednet using the WL driver. Mow I am getting 1mb/s.
CHEERS! :P :guitar:
Flipmatthew

---

### Post by gradedcheese on 2009-05-07
Perhaps you should report that as a bug?
[http://wireless.kernel.org/en/users/Support](http://wireless.kernel.org/en/users/Support)

---

### Post by flipmatthew on 2009-05-07
Maybe, but I would like the community to try and help first. Isn't that what Ubuntu is all about?

---

### Post by snowpine on 2009-05-07
You'll have to compile it for your new kernel. Here it is: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Follow the steps in README.txt.

---

### Post by iggykoopa on 2009-05-07
I'm just using the old kernel until restricted-modules is built for 2.6.30, thats the package the sta driver is in. I had tried to build it for 30 before but it needs to be patched and I couldn't find a good one for it yet.

---

### Post by snowpine on 2009-05-07
Iggykoopa might be right; I haven't actually tried it with 2.6.30. ;)
Silly Broadcom...

---

### Post by flipmatthew on 2009-05-08
ty guys, but somehow, the b43 works magically lol =p.

---

### Post by Amaranth on 2009-05-09
I patched the driver for 2.6.30 locally (using the patch from gentoo) and it associates with my network but DHCP fails every single time. I tried every unsecured network in my area and my own network.

Basically I don't think a simple patch to make it build is enough, Broadcom may have to release an update for the driver.

---

### Post by ElTimo on 2009-05-10
@Amaranth: Where did you get the patch? I tried using the patch for 2.6.29, but to no avail. There is always one hunk that fails and I still get a lot of errors about incompatible pointer types. This is driving me absolutely berserk, so any help would be appreciated.

---

### Post by Amaranth on 2009-05-10
I manually applied every relevant patch from the gentoo ebuild, they wouldn't apply cleanly for me either.

Edit:
Manually means I looked at the diff in gedit and then modified the code to match.

---

### Post by plun on 2009-05-10
There is a ongoing thread within the packaging/compiling forum

[http://ubuntuforums.org/showthread.php?t=1147055](http://ubuntuforums.org/showthread.php?t=1147055)

ssb module ?

---

### Post by Amaranth on 2009-05-10
I got it working! 8)

[http://ubuntuforums.org/showpost.php?p=7252017&postcount=6](http://ubuntuforums.org/showpost.php?p=7252017&postcount=6)

---

