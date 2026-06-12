---
title: "Dapper -&gt; Edgy; Problems starting X"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by yelloguy on 2006-10-26
I just finished the upgrade from Dapper to Edgy and now my X wouldn't start.

module ABI major version (0) doesn't match the server's version (1)
Failed to load module "ati" (module requirement mismatch, 0)
No drivers available.

Followed by Fatal server error yada yada...

I have been searching these forums and google for about an hour now and have tried various commands mentioned.  This is a laptop with ATI integrated video card and I have tried reconfiguring xorg (as root).  My problem is that the network is not available so most online apt-get commands fail.  The latest kernel doesn't even recognize my PCMCIA network card and when I boot to an older kernel, the network card is working (blinking lights) but network is not available.  I am guessing that is because of the wireless security (even though it was configured in Dapper correctly).

At this point, 

1. I can disable wireless security, go online and then try something (what?)
2. Download an ISO, burn a CD and do a clean re-install (getting my network card to work in Dapper was painful but other than that, this should be the shortest route and one most likely to succeed.
3. Any other ideas?

Thanks in advance.

---

### Post by taurus on 2006-10-26
Reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by martijndenerd on 2006-10-26
Had the same problem here... but I solved it!
Just install xserver-xorg-video-all (or just the ati one if you like). Then you will have all the new drivers, and it should work. (Type startx to test, or just restart, or sudo /etc/init.d/kdm start)
Apparently kubuntu-desktop does not depend on this package... is this a bug? Or were we just unlucky? 
Please confirm if you have the same problem; this is rather serious!

---

### Post by yelloguy on 2006-10-26
taurus, I tried that.  No difference.

martij, I will have to connect to the network to be able to install that.  Maybe I will hook up the laptop to the modem (wired) and try that real quick.  Thank you.

---

### Post by yelloguy on 2006-10-26
martij, that was it.  Installing xserver-xorg-video-all did the trick.

For others, boot into recovery mode and at the root prompt, do a 

aptitude install xserver-xorg-video-all

I had to connect my laptop to the router because wireless network wasn't working (still isn't) with the latest kernel (2.6.17-10-386).  Booting to the older kernel (2.6.15-27-386) however makes the network card work fine.

It wasn't easy getting my butt up and sitting it down in front of the router.  But the things I would do for this community :)

Thanks very much.  I will work on that network card problem later.

---

### Post by martijndenerd on 2006-10-26
I filed a bug: [https://launchpad.net/distros/ubuntu/+bug/68430](https://launchpad.net/distros/ubuntu/+bug/68430)

Please confirm there, if you have the same problem.

---

### Post by serlex on 2006-10-26
ahhh, just went from 6.06 to 6.10, getting error from X server tried
```

aptitude install xserver-xorg-video-all

```
(restart)just end up with black root@XXXX-laptop:~#

---

