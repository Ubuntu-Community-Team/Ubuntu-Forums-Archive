---
title: "with dual OS will . . ."
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by muka on 2007-05-20
It seems that I will have to do my upgrade to Feisty via CD.
Is there anyone with experience doing it that way?

My biggest concern is that my Grub don't muck up so that I can still get into Windows even if Feisty don't make the grade with the Upgrade.

Can someone hold my virtual hand, give it a squeeze and assure me that all will be OK?

Thanks 
Muka  :)

---

### Post by aysiu on 2007-05-20
You're doing an *upgrade* and not a *reinstall*? If you're doing an upgrade, Grub shouldn't be affected in any way.

---

### Post by tormentum on 2007-05-20
Are you able to upgrade via the internet mate?  "apt-get dist-upgrade" will work fine if you replace "edgy" (or whatever dist you're currently using) to "feisty" in your /etc/apt/sources.list file.

If you do need to use CD, it'll work fine too.  I've never seen grub get nerfed, except with multi-disk SATA setups.  Tho I think that problem got resolved ages ago.

---

### Post by muka on 2007-05-20
Like I said mate, I can't do it over the Net because I'm on dialup.

So I gave it a try, booted up my Ubuntu, slipped the CD into the drive . . .

No 'upgrade ' came up. 
Do you have the simple instructions on how to get into the upgrade mode with the CD please?

I did do gksu "sh / cdrom/cdromupgrade" and then it looked for the next command . . . I have no idea.

Thought it all going to be sort of more GUI style etc.

Thanks
Muka :)

---

### Post by aysiu on 2007-05-20
You can upgrade with only the Alternate CD. You can't use the Desktop CD to upgrade.

More details here:
[http://www.ubuntu.com/getubuntu/upgrading#head-0aee739ab0dfe9702a69ee3d316f5926d5d31807](http://www.ubuntu.com/getubuntu/upgrading#head-0aee739ab0dfe9702a69ee3d316f5926d5d31807)

---

### Post by muka on 2007-05-20
Thanks for clearing that mess up for me.
back to the drawing board  :)

Cheers 
Muka

---

