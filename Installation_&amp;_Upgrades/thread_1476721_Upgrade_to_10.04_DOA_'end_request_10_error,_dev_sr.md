---
title: "Upgrade to 10.04 DOA: 'end_request: 1/0 error, dev sr0, sector 0'"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by christopherbalz on 2010-05-08
Pressing 'enter' makes no difference.  Stops at boot with 'n' number of these errors (big 'decimal' number shown is the last one before the hang): 

> [    64.600448] end_request: 1/0 error, dev sr0, sector 0

The message 'init: ureadahead-other main process (733) terminated with status 1'  (or sometimes 'status 4' instead of 'status 1') shows right at the bottom or the bottom few lines.

I've had X Windows problems before but never a complete nuking like this.  The last two upgrades were pretty much seamless.

I have tried 'chroot'ing from a Live USB Ubuntu 10.04 and updating my grub bootloader and adding 'nomodeset' boot command.  But so far no difference.

The machine stops completely at the black screen with the error log on it.  From there, I can make the machine respond by toggling between a purple splash screen (the loading "dot" graphics) and a terminal-type view by pressing 'esc', arrow-key, or any number of function-keys.  When I return from the splash screen (by pressing an activating key again), I see new error messages scrolling across the screen.  They say (trailing number increments):

> udevd[361] SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/45-logitechmouse.rules:16

No chance of accessing my upgraded system as a live system beyond this hang/toggle point.

Another error message that sometimes appears is:

> udevd[352]: can not read '/etc/udev/rules.d/z80_user.rules'


My hardware profile is on file here and the basic scoop is that it's an IBM ThinkPad R-51, circa 2004.  It's pretty quick still, at least with Ubuntu (when it boots!)

Any ideas to fix this nice karate-chop to my system would be appreciated.

Thank you in advance.

---

### Post by gradinaruvasile on 2010-05-08
/dev/sr0 is the cd/dvd drive... Try disabling it physically or from bios (or first remove a cd if you have something in it). Just a guess though, probably this isnt your problem.

Also, what hardware (video card/mobo) do you use? Do a "lspci" in a terminal if you can and paste the contents of it here.
More likely its a video driver related thing.

---

### Post by christopherbalz on 2010-05-08
Thanks - this machine uses an ATI Radeon card.  A couple years ago I uploaded an entire hardware profile somewhere on this site.  It was associated with my log-in through a specific category for hardware profiles.  But I can't seem to find it.   

I did have a blank CD in, and I took the CD out, but no luck. I still see the 'ATTR{}' type errors.

Will try to check it with the CD disabled from the BIOS.  

Ubuntu did seem to be getting kinder to my hardware, but maybe now it's moving away.  My whole system is stock IBM ThinkPad.

Thanks and I hope for more ideas.

---

### Post by haidoura on 2010-05-08
Iam facing the same issue but its not related to the cd its related to hp_laser jet_p1505

How is the suitable procedure to replace the  SYSFS{} with ATTR{} as the message suggested

---

### Post by christopherbalz on 2010-05-08
SOLVED The issue was old entries in fstab that I did not need.  I did not bother with the SYSFS messages, as everything works - probably a future update will clean that up.  The distros seem to leave a lot of warning messages around that are more for system developers than end users.

Here is the diff from my old fstab as it was directly after the upgrade from Ubuntu 9.10 to Ubuntu 10.04, and my current one (showing commands to get diff):

```
//cbalz-tp-r51-0/.../~ $ cd /etc
//cbalz-tp-r51-0/.../etc $ diff fstab fstab
fstab            fstab_backup     fstab.BAK        fstab-bak-may-8  fstab.pre-uuid   
//cbalz-tp-r51-0/.../etc $ diff fstab fstab-bak-may-8
8c8
< # UUID=e382a19f-c641-45d6-b353-b4498473c53b  none            swap         sw                                   0  0  
---
> UUID=e382a19f-c641-45d6-b353-b4498473c53b  none            swap         sw                                   0  0  
11c11
< # UUID=689CBBA69CBB6CE6                      /media/windows  ntfs         nls=utf8,umask=0222                  0  0  
---
> UUID=689CBBA69CBB6CE6                      /media/windows  ntfs         nls=utf8,umask=0222                  0  0  
```

Basically there was an entry for an old Windows partition which I had removed a couple years ago, and a swap partition that I was no longer using.  Not sure why that entry was there as I already had a swap partition - probably related to partition editing I did a long time ago.  And not sure why these suddenly nuke an upgrade to Ubuntu 10.04, whereas before, they were harmlessly ignored.

Thanks to tuxmaster for this post: [http://ubuntuforums.org/showpost.php?p=9256360&postcount=2](http://ubuntuforums.org/showpost.php?p=9256360&postcount=2)

---

