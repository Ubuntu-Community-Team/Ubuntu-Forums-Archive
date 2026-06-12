---
title: "unexpected boot problem"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by Lanky Juggler on 2007-06-16
I _thought_ my problems have to do with the recent kernel upgrade to 2.6.20-16, because my symptoms seem to be similar to others that I find here and on googling my error message.  I am creating this post because, though I have searched almost everything and tried about 5-6 different solutions, nothing yet has worked!  Today has been a long story, but I will try my best to keep it quick:

I was away this previous week (9th to 16th of june) and came home to some updates.  Things were okay, except that inexplicably my sound refused to work and I got a message from the gnomepanel sound-dealie that it couldn't find any audio device, so I follow someones advice and --purge remove some alsa stuff and then reinstall it, finally rebooting.

At first it starts up normal, up through the loading bar. Then it cuts to an error message which says ```
kinit: name_to_dev_t(/dev/sda5) = sda5(8,5)
kinit: trying to resume from /dev/sda5
kinit: no resume image, doing normal boot 
```

So I've been searching ever since for a solution to that, because at current (even if I boot the 20-15 kernel, in fact i eventually even purged my computer of the 20-16 kernel) I can not get X to load.  Recently, I haven't even been getting that error message, it just brings me right to tty1 (hitting alt-ctrl-F7 does nothing) and asks me to log in.

If it would help anyone, i'd be happy to post the things i've tried already, but at this point I think i've reversed everything I could to back the way it was.  Thanks for any possible help.

---

### Post by Lanky Juggler on 2007-06-16
I hate doing this kind of thing, but at this point I am lost.  Is there a way of starting X/gnome from a TTY thing?  And then maybe worming that into my grub somehow?  Because I'm not getting any error messages anymore, even with "quiet" turned off, it just goes from the loading bar straight to TTY1 Login.

---

### Post by confused57 on 2007-06-16
> **Lanky Juggler said:**
> I hate doing this kind of thing, but at this point I am lost.  Is there a way of starting X/gnome from a TTY thing?  And then maybe worming that into my grub somehow?  Because I'm not getting any error messages anymore, even with "quiet" turned off, it just goes from the loading bar straight to TTY1 Login.
I found this on launchpad, may not help you, but might be worth reading:
[https://bugs.launchpad.net/ubuntu/+bug/103148](https://bugs.launchpad.net/ubuntu/+bug/103148)

Do you have Nvidia drivers installed?  If you do you might want to try temporarily  using "nv" or "vesa".

The newest kernel update in Feisty changed IDE hard drive designations back to hdx on some hard drive controller chipsets.  You might want to mount your root partition and check your menu.lst and fstab, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

You've probably already found this thread:
[http://ubuntuforums.org/showthread.php?t=456662](http://ubuntuforums.org/showthread.php?t=456662)

---

### Post by Lanky Juggler on 2007-06-16
Thanks!! The Launchpad link indeed did help.  Although this might not be everyones problem, this whole mess did indeed (as the second to last post suggests) happen when I was deleting an alsa driver, and for some reason my ubuntu-desktop (and a few other related components) were uninstalled as well!  At current my only problem is hooking my computer up to the internet (no wireless? I'll have to do some digging around to plug it into the wall directly) so I can download the updates.

I will post again and edit this thread to resolved if this works (Which, I think, it will)


***EDIT*** Everything Works!! Thank you very, very much for your time and helpfulness.

---

