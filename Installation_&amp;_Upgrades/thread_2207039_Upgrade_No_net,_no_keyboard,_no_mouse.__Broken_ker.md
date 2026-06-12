---
title: "Upgrade: No net, no keyboard, no mouse.  Broken kernel?"
date: 2014-02-21
forum: Installation &amp; Upgrades
---

### Post by 1clue on 2014-02-21
Hi,

I have an xubuntu 13.10 system.  I did **sudo apt-get update** and **sudo apt-get upgrade** awhile back, and now the system is broken.  I'm just now getting to it to fix it.

For one thing, since I dist-upgraded from 13.04 the useless but prettified boot screen is there, so I can't see boot failures.  It just goes to the ubuntu splash screen with a bunch of dots on the screen, and then goes to a login screen as though nothing were wrong.

I can boot from a CD and everything works fine, I have network and keyboard and mouse.  It's not broken hardware, although a raid array isn't coming up.  I think the CD I'm booting from doesn't have raid drivers.  I'm booting from a system rescue cd from probably more than a year back.  I choose 'boot existing linux' and it boots to my xubuntu, but with a different kernel I think.  I'm getting slow network access, but it's at least network access.  I can't use X but I can get to a terminal.

This reminds me of a broken kernel, but I don't recall a kernel coming in.  I also don't see much grief about it on the forum, so I guess I'm at a bit of a loss.

This is a virtual machine host, so I don't want to just wipe it.

Since I have it up, I'm trying to update it again in hopes that fixes it.  If not I think I'll try to uninstall the kernel and install it again.

Does anyone have input as to the best approach?

Thanks.

---

### Post by jv69 on 2014-02-22
FYI:  I am having a problem with no mouse functionality. Both occurred on 12.04 and 13.10.

---

### Post by 1clue on 2014-02-22
OK, so here's the deal:
[LIST=1]
[*]I booted off a system rescue cd.
[*]Boot the Linux on the hard disk.
[*]apt-get update
[*]apt-get upgrade (this installed a new kernel)
[*]unmount all the mounted filesystems
[*]run repairs on them
[*]remount
[*]eject the CD
[*]reboot.
[/LIST]

***Edit:** This fixes the problem.  I guess I didn't mention that.*

---

### Post by 1clue on 2014-02-22
In the aftermath, I think the key problem was a bad kernel.

I had to pull the plug on the box a few times.  The broken filesystems were all XFS, and it doesn't handle power failure very elegantly.

---

