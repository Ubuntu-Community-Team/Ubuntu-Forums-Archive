---
title: "Can't use screen or indput devices after trying to upgrade to 10.10"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by sinisterstuf on 2010-10-17
[COLOR=Red]**tl;dr: Messed up upgrading to 10.10 and can't use screen/mouse/keyboard, what can I do?!**[/COLOR]

_Right so I read the [thread at the top of this section]("http://ubuntuforums.org/showthread.php?t=1580857") but only after I tried to do an **online upgrade**, this is what happened:_

I live in Africa and my internet is pretty slow so it took me about a week to download all the packages needed for the upgrade, it must have finished overnight so by yesterday morning it was actually installing the packages and it said 4 hours remaining but I still wanted to use the computer so I just opened a few things like google chrome and nautilus and then it froze, chrome didn't even open. So I started closing the browser windows I opened and stuff but when I clicked on the update tool taskbar icon it would show.

I decided to leave it be in the hopes it would sort itself out, I returned about 5-6 hours later and nothing had changed, but in fact I could do even less, I could move the mouse but couldn't open anything or turn it off, I tried switching to one of the TTYs that didn't have X running on it and logging and rebooting but it woulnd't load, I tried using Ctrl+Alt+Backspace to restart. In the end I used Alt+SysRq+B which did restart the computer but when it came on (after scanning disks) told me: *"Ubuntu cannot detect settings for your screen or input devices"* so I can't use the mouse/keyboard and there is just a black screen with that message on it.

Someone advised me to boot into a Live Disk (which I am now) and use chroot to check it out but I'm not very familiar with it. I chroot into the disk and tried to run sudo do upgrade -d ...which didn't really work. As did any apt commands I tried.

**So... what can I do to either complete the upgrade or, failing that, revert back to 10.04 which worked nicely?**

---

### Post by sinisterstuf on 2010-10-20
bump?

---

### Post by STOIE on 2010-10-20
Hiya, did you enable SSH to the box, this may be your (like mine) saving grace.

When logged in wget the xserver-xorg-input-all and xserver-xorg-graphics-all packages (which can be got from ubuntu packages site), then, install it with dpkg -i <pkg name>

Reboot and hopefully it should work.

Else, boot off live CD, mount the filesystem, edit the SSH config (and static IP if not there too), then reboot and proceed as I said above.

---

