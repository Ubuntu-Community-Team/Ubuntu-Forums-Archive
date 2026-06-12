---
title: "Ubuntu 11.04 Live CD and Live Stick not working"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by spielball on 2011-04-28
Live CD:

I dowloaded the ISO, burned it to CD, booted from this CD. It starts to load and I can see the purple background with the loading icons. Everything seems normal. But instead of ending up with the login screen, it ends up with a screen that says 'Please remove all bootup media and hit ENTER' or something like this. So I hit enter and then it shuts off my computer. That's it.


Live Stick:

So I tried another option and created a stick with 'usb-creator.exe' that is on the CD. Then I start from that stick, but all I end up is a line of 'Syslinux bla bla copyright 20xx-2011'. That's it. Then it does nothing anymore. The cursor is blinking, but no prompt or whatsoever and keyboard input doesn't do anything.

Now something weird:

When I insert Live CD and Live Stick at the same time and then boot my computer, then it boots into Ubuntu. Obviously it loads the first parts from CD and then the rest from stick. Because when I'm then in Ubuntu and try to format the stick, it says it can't do so, because there's system files from that stick in use.

What can I do? :-/

---

### Post by Hedgehog1 on 2011-04-28
This typically indicates a damaged ISO file (some sections were lost during download).  On a busy Ubuntu Server day like today, this happens more often than usual.

Please re-download the ISO using bit torrent (it does checks so nothing is missing) and make a LiveUSB from that.  If it is good, also make a LiveCD for future 'repair' work.


***The Hedge***

:KS

---

### Post by spielball on 2011-04-28
Ok, I have downloaded the ISO via torrent and checked the hash sum. I've burned another CD and checked its integrity.

As for the live stick, I have booted into Ubunu 10.04 and from there created the live stick. I found out that using the Windows version (usb-creator.exe) produces a boot stick which gets always stuck (as mentioned in my first post).

Now I can boot from CD or stick -- but still both efforts fail. Although the stick does not hang anymore, the same thing happens as with the live cd:

When I boot from either live cd or stick, the boot process seems normal. But after loading lots of stuff, at the end it displays the screen that says 'Please remove all bootable media and hit ENTER'. And when I do this, the computer is shut off.

However, I found a hint now why this might be happening:
During the boot process, just before the purple background is loaded, there is a very short glimpse of a single line that says 'Critical temperature reached (255°). Shutting down'. But this is, of course, bollocks. Because the computer is not heated up at all. I even turned it off for 20 minutes and let it cool down completely. But the same thing happened. And due to the fact that 10.04 boots fine, I wonder why it doesn't with 11.04. Strangely though this 'critical temperature' line is also displayed when 10.04 boots up, but as for 10.04 it doesn't shut down.

Is this some bug with the power management?

---

### Post by Hedgehog1 on 2011-04-28
> **spielball said:**
> However, I found a hint now why this might be happening:
During the boot process, just before the purple background is loaded, there is a very short glimpse of a single line that says 'Critical temperature reached (255°). Shutting down'. But this is, of course, bollocks. Because the computer is not heated up at all. I even turned it off for 20 minutes and let it cool down completely. But the same thing happened. And due to the fact that 10.04 boots fine, I wonder why it doesn't with 11.04. Strangely though this 'critical temperature' line is also displayed when 10.04 boots up, but as for 10.04 it doesn't shut down.

Is this some bug with the power management?

This is not a bug with Natty power management, it is a bug with 10.04 that it ignores the bad temperature reading and lets you boot anyway.

Hate to say it, but this appears to be a hardware issue that is getting you (bad temp sensor).  You may be running 10.04.02 for a while yet...


***The Hedge***

:KS

---

### Post by spielball on 2011-04-28
The temp sensor works fine. Using a hardware monitor in Windows correctly displays the temperature. Also, I don't have this issue with other Linux distros. I'm clueless :confused:

---

### Post by spielball on 2011-04-29
I have created an alternative boot stick now, using grub and loading the the whole iso. Then I was able to boot into 11.04 and start the installation from the desktop. I really don't know why I can't install it the normal way.

---

