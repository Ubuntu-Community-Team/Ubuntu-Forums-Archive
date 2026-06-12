---
title: "(alternate install) flashing screen on boot, recovery menu non functional"
date: 2012-12-28
forum: Installation &amp; Upgrades
---

### Post by Stutz Jr on 2012-12-28
I recently installed lubuntu on an old compaq armada e500 laptop (256 mb ram).  I had to use the alternate installer in text mode.  Don't remember whether it was 12.04 or 12.10 (linux 3.5.0-17-generic).  I wasn't able to get any help on irc at the time so I left it aside until I had time to look into it.

[B]The system boots up, and after the lubuntu splash screen it shows something like:
"* Checking battery state...   [OK]"
flashing endlessly.[/B]
If I press ctrl-alt-f1 the login prompt flashes once and returns to the above text flashing endlessly.
Any other keypresses just add more text to the flashing screen.

If I hit ctrl-alt-del it says "acpid exiting", shows the splash screen again and then reboots.

If I reboot and ask grub to load the recovery menu I am able to drop to the root shell prompt, but if I do anything like run apt-get I get errors like "not using locking for read only..." and "the package lists or status file could not be parsed or opened" etc.  There does not appear to be any xorg.conf file in /etc/X11.

If I attempt to enable networking from the recovery menu I get the following:
"fsck from util-linux 2.20.1
/dev/sda5: clean, [...] blocks

" ... and the system is again nonresponsive apart from being able to type text to the screen, ctrl-alt-f1 does nothing, ctrl-alt-del begins to restart but gets stuck on a garbled recovery screen for about 2 minutes before restarting

If I load the recovery menu and choose resume it gets to the same point as above (battery etc, flashing) but at the bottom of a full screen of hardware text instead of at the top of the screen in vga text.



I want to get this lubuntu system booting correctly.
**I believe that I need the mach64 driver for the onboard video** (that's what worked previously in arch linux).  **But I don't know how to get and configure this driver as the recovery menu has problems of it's own.**

I HAVE ALREADY EXTENSIVELY SEARCHED GOOGLE AND THIS FORUM ON THIS TOPIC

...and did not find an answer, just in case you were wondering.
Could someone here please help me to get up and running?

thanks!

---

### Post by ajgreeny on 2012-12-28
Have you checked the md5sum of the .iso file you used to make the CD or USB which you used to install the system?

See [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes") 

The range of problems you are experiencing suggests perhaps a corrupt .iso or a bad burn.

---

### Post by Stutz Jr on 2012-12-28
[QUOTE=https://help.ubuntu.com/community/UbuntuHashes]
 **5dde10476ccb7fc2c6fb50d914061902**  | lubuntu-12.10-alternate-i386.iso
[/QUOTE]


```

rich0@Cerulean ~/Downloads $ md5sum lubuntu-12.10-alternate-i386.iso
5dde10476ccb7fc2c6fb50d914061902  lubuntu-12.10-alternate-i386.iso

rich0@Cerulean ~/Downloads $ ls -l lubuntu-12.10-alternate-i386.iso 
-rw-r--r-- 1 rich0 rich0 675590144 2012-10-27 21:56 lubuntu-12.10-alternate-i386.iso

rich0@Cerulean ~/Downloads $ dd if=/dev/cdrom bs=1 count=675590144 | md5sum
675590144+0 records in
675590144+0 records out
675590144 bytes (676 MB) copied5dde10476ccb7fc2c6fb50d914061902  -
, 345.354 s, 2.0 MB/s
```

I really wanted to believe it was a bad burn, but unfortunately as far as I can tell the disc is good.
Thus, I'm still after an answer on this one :(

---

### Post by Stutz Jr on 2012-12-28
So I'm still struggling to get this system working as above.

Those who are paying attention will note that I am stuck on step 3 of the vaguely unrelated sticky thread "Graphics Resolution- Upgrade /Blank Screen after reboot".  I think I can safely say that having reading over 20 pages of completely unrelated issues about "upgrades" and "nvidia" ad nauseum, that thread was not able to answer my 2 main questions.

As an aside I did learn that it is possible to force grub to boot to a text login by changing "quiet splash vt.handoff=7" to "nosplash --verbose text". Curious indeed, however again this still does not answer my 2 main questions as I will explain below.  I was under the strong impression from previous unhelpful forum warriors that one does not ever directly edit the grub config files, as grub 2 no longer allows/requires you to do this.  I didn't want to cause a total protonic reversal but I had an apparently bricked system, so I crossed the streams anyway.  So I was wrong in thinking that the decision whether to boot to a text login or graphical dm comes after grub, but why then was I not able to drop back to a login from the recovery menu?

So I can login now, hooray?  No.  Problems still not solved:

I ran sudo apt-get upgrade etc.

sudo service lightdm start - still returns to a flashing screen

glxinfo - unable to open display

lspci | gep -i vga -
01:00.1 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Rage Mobility P/M AGP 2x (rev 64)

sudo Xorg -configure - I got some error about multiple screens or displays but it did create an xorg.conf.new

So I copied xorg.conf.new to /etc/X11/xorg.conf and then removed lines about monitor, card & screen 1,2,3 (left 0) etc,
I left device card0 driver as "mach64" and BusID as PCI:1:0:0
and I added a line in screen0 subsection display of modes "1024x768".

That hasn't worked, and I do not know what to do now.

**1. system still reboots to flashing text as always**
**2. recovery mode menu still freezes at fsck**

---

### Post by Stutz Jr on 2012-12-28
Ok so we've had a win.  I've been able to solve one of the two issues as follows:

As per previous post, after a dodgy grub hack to login I wasn't able to get xorg.conf working with my mach64 graphics.  I looked at _[some old arch linux help related to my laptop issue suggesting I needed to install xf86-video-mach64](https://bbs.archlinux.org/viewtopic.php?id=67837)_.  Unfortunately apt-get informed me that "E: Unable to locate package xf86-video-mach64".
On a frustrated whim I decided to try changing the driver from "mach64" to "vesa", on the belief that I might be able to get in on a hobbled low res gui.  It actually worked - not only that, the system now boots to 24 bit 1024x768.  I didn't expect that to work, but at least I've managed to solve half of the original issue.

p.s. On first impression the lubuntu desktop is very slick and well thought out.  Once I got in I immediately had a much better experience than with arch+xfce previously.  Kudos to all involved.

Anyway I did a software update and **rebooted straight to lightdm.**  Great!

Logged in to lubuntu desktop, rebooted to the recovery menu to check issue 2.
** Recovery mode menu options "Enable networking" and "check all filesystems" still freeze on fsck**, so are still not a means to get to a proper text login.
Why is there no option on the recovery menu simply to get a regular text login rather than this readonly root prompt with no network anyway?

---

### Post by Stutz Jr on 2012-12-29
Yep.  So this issue has been a **_[confirmed bug](https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/1061239)_** since October 2012.
It would have been nice if I'd known that yesterday and hadn't wasted all this time trying to figure it out.
Thanks for the help folks...

---

