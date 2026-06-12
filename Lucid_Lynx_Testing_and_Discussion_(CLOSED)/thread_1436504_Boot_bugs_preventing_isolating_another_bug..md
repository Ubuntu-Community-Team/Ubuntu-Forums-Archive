---
title: "Boot bugs preventing isolating another bug."
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lavinog on 2010-03-22
I installed lucid beta on my laptop finally.
My laptop was having issues with sleeping in karmic...now it is having issues resuming.
So I started troubleshooting by following:
[url]
https://wiki.ubuntu.com/DebuggingKernelSuspend
[/url]

The system seems to go to sleep just fine (blinking power light)
after pressing the power button, the system attempts to resume: blank screen, no backlight, numlock key doesn't change state, ctrl-alt-del does nothing, and fan starts running at higher rpm.

After power off/on the system attempts to come up, but the boot logo just sits there animating (4 dots).  Pressing ctrl-alt-1 gives me some text about fsck complaining about inconsitancies where superblock was mounted in the future.  It claims that the current date is 1996 even though bios says 2097(going from memory...get the actual number on next attempt)

fsck prevents the boot from continuing because the date is wrong...this should be considered a bug.

So at this point, I figured I would try using booting into the recovery mode...it fails for the same reason...scary
I corrected the system date through bios, and booted normally.
Afterwards I tried booting into recovery mode again and found that I cannot.  I get a bunch of what looks like normal kernel messages, then the screen clears and displays a single blinking cursor...the system does respond thought to ctrl-alt-del and will exit normally.

So my question is what packages should these bugs be filed under?
The fsck issue may not be a bug with fsck...is upstart the problem?
Should there be a command line option to tell fsck not to look at the system date?

What about the recovery mode...in karmic there used to be a recovery menu...this menu seems to be what is broken now.

---

### Post by ShadowDragon on 2010-03-22
I was looking for the different modes as well, seems to be "simplified":

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/525966/comments/1](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/525966/comments/1)
> I removed "Safe graphics mode" as the xforcevesa option no longer had any effect anyway, and wew're trying to simplify the main menu. You can add 'nomodeset' from the F6 "Other Options" menu at CD boot time, which may help you; that was the only remaining effective part of "Safe graphics mode".

For recovery mode, you could specify "single" as bootoption under F6.

---

