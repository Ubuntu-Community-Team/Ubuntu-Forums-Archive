---
title: "Ubuntu/Vista/XP install problems"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by razorfrog on 2007-04-19
Hi all-
I've had Ubuntu and Vista running happily together for quite some time now and that's been great. However, I've long had a 20gb partition left for XP pro that I've still yet to be able to install. I boot up from the XP disk, go through the first install process, but when the computer (a thinkpad T60) reboots, nothing happens (the install process should take over and finish - all I get is a blinking cursor). This happens even if I take the cd out, and to fix things I have to use the Ubuntu CD and rebuild GRUB. 

Of course this isn't an XP install forum, but I figured this would be a good place to at least get some ideas. If anyone can help me specifically - awesome; if anyone can point me elsewhere - also awesome.

Cheers!

---

### Post by IDK on 2007-04-19
You have to have Windows installed prior to installing linux.  When you try to install windows after installing linux it breaks your boot loader as you found out.  I've never successfully installed windows with an existing linux system so I always install windows first.  I would back everything up and install windows then Ubuntu again but someone here might have a way around it.

---

### Post by laughingLoki on 2007-04-19
> **IDK said:**
> You have to have Windows installed prior to installing linux.  When you try to install windows after installing linux it breaks your boot loader as you found out.  I've never successfully installed windows with an existing linux system so I always install windows first.  I would back everything up and install windows then Ubuntu again but someone here might have a way around it.

I did a clean install of Vista on my XP partition.  It worked fine.  I just had to restore grub, afterward.  A tutorial for restoring grub can be found [here](http://ubuntuforums.org/showthread.php?t=224351).

My partition set up is as follows:

```

Windows | Logical partition
        |     > Ubuntu
        |     > /home

```

Maybe it has to do with your partition layout?  If not, your guess is as good as mine.

---

### Post by razorfrog on 2007-04-19
> **IDK said:**
> You have to have Windows installed prior to installing linux.  When you try to install windows after installing linux it breaks your boot loader as you found out.  I've never successfully installed windows with an existing linux system so I always install windows first.  I would back everything up and install windows then Ubuntu again but someone here might have a way around it.

No, it's not that.. To make that work it's just a matter of fixing the GRUB. But that's easy enough. About this XP thing though - I think it's a boot issue (of course) and maybe not liking GRUB?

> **laughingLoki said:**
> 
Maybe it has to do with your partition layout? If not, your guess is as good as mine.

Probably that.. but I'm not sure how it should be set up then..

---

### Post by laughingLoki on 2007-04-22
Attached is a screen shot with my partition set up.  I hope it helps.

You can either install gparted using a package manager or you can run it from an Ubuntu live CD.

Since you're running both XP and Vista, you should probably have a second NTFS partition like the one that I have in the screen shot.

---

