---
title: "grub changes programatically?"
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by many_miles on 2008-09-08
I am trying to generate bootable hard drives from some image files I am creating.

I have an IDE drive connected to the IDE 1 channel (secondary IDE channel).  I have partitioned, formatted and distributed the files from a source directory to this secondary drive.

I then do the following to setup the environment
(Note the hdc1 - this is a Mandriva 2006 host os, as explained below)
```

mount /dev/hdc1 /mnt/part1
cp ~/show_vol /mnt/part1/root
mount -t proc none /mnt/part1/proc
mount -o bind /dev/ /mnt/part1/dev
chroot /mnt/part1 /bin/bash

```

From there, I fire up grub and enter the following:
```

root (hd1,0)
setup (hd1)

```

I then unmount everything, shut down, install said HDD into the destination hardware and voila! everything works.

My question is, how can I get the secondary HDD to have a properly installed grub loader without having to manually enter the commands above in the grub shell?

I've tried various methods, but end up with various error messages.

The PC that is doing the generating is currently a Mandriva 2006 OS, as a holdover from my former OS days, but I don't think that should matter.  Also, that PC itself boots via lilo, but, I don't think that matters.  After all, manually inputting the information gives me the desired outcome.

I'd like to call something like this:
```

echo "root (hd1,0) ^M setup (hd1)" | grub-install

```
but, I just cannot seem to find the correct documentation.

Your assistance is greatly appreciated and anticipated.

---

### Post by NetpigsBang on 2008-09-08
**[[color=magenta]Buy Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Test drive our brand new real-time traffic estimator and create your campaign. Choose text, banner, or interstitial ads. Target by site, keyword, demographic. Create or upload multiple ads. **[[color=seagreen]Sell Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Find out how we can help you generate more revenue from your ad space. Customize ads to match your site Approve and reject ads for your site Works alongside other ad programs [**[color=red]Make money online,now![/color]**[color=#0000cc][/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)

---

