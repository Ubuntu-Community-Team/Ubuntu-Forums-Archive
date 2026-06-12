---
title: "Interrupted Ubuntu 9.10 Upgrade in Virtualbox on Vista Broken"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by allend on 2009-11-21
I had 8.04 Ubuntu running for some time in a VirtualBox on a Vista machine and it ran well.  I then upgraded to 9.04.  That was OK, too.

I then began the upgrade to 9.10 in the update manager and that was proceeding nicely in the background while I did other things.

At some point, the computer either hibernated or shut down, and when I restarted VirtualBox and Ubuntu, the boot proceeded quite normally, buth then began to complain...

status: Unknown job: usplash
saned disabled; edit /etc/default/saned
status: Unknown job: usplash
  *Starting System Tools Backends system-tools-backends       [OK]
status: Unknown job: usplash
status: Unknown job: usplash
status: Unknown job: usplash
status: Unknown job: usplash
  *Starting anac(h)ronistic cron anacron                      [OK]
status: Unknown job: usplash

  *Starting deferred execution scheuler atd                   [OK]
status: Unknown job: usplash

  *Starting periodic command scheduler crond                  [OK]
status: Unknown job: usplash
  *Enabling additional executable binary formats binfmt-support [OK]
status: Unknown job: usplash
  *Checking battery state...                                       [OK]
status: Unknown job: usplash
status: Unknown job: usplash
status: Unknown job: usplash
status: Unknown job: usplash
status: Unknown job: usplash
status: Unknown job: usplash
  *Reloading system log daemon...
_

From there nothing ever happens.

Any ideas on how to get the system up and (I assume) the upgrade to complete?

Or is this installation toast?

TIA.

---

### Post by allend on 2009-12-17
Three weeks ago, I posted this request for some insight.  So far I see it has 75 views and no replies. Not one.

My Ubuntu installations sit useless and I have no idea what to do.  In the meantime, I have installed Windows 7 on three machines with no problems.

I had thought that Ubuntu might replace Windows for me, but I can see that day is a long way off.  

Over the years I have had plenty of problems with Windows, since I run many versions on many machines and also help friends with their problems, but they have always healed themselves or I have been able to easily find solutions in a short timeframe. I have NEVER had to reinstall Windows.  Not once.  

Not so with Ubuntu, so far, at least.

---

### Post by fibercode on 2009-12-17
Sorry to hear that Allend...

I just saw your post...

When you are upgrading, among other things Ubuntu will download a new kernel and will edit the grub options in the /boot/grub/menu.lst file so that it can boot up from that new kernel image the next time.

In this file there are also settings for the "usplash"... that is the splash screen that you see when Ubuntu is logging you in, right before you see your desktop.

It seems that your hibernation interrupted that process of updating the menu.lst file.

What I would do is go into the grub editor, right in the first seconds of Ubuntu booting and edit the menu.lst file to get rid of the usplash.

Follow this post that tells you how to do this:
[URL="http://ubuntuforums.org/showthread.php?t=575708"]
http://ubuntuforums.org/showthread.php?t=575708[/URL]

This is my first hunch by looking at your output...

---

### Post by allend on 2009-12-17
Thanks.  I'll try that and report back.

---

