---
title: "OK buttons off screen during installation?"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by sot3 on 2007-07-09
I'm expecting that this question may make me look really stupid, but I'll ask anyway.

I've downloaded the latest ISO for amd64 and I'm attempting to install on a new system.  It boots fine from CD, then asks me what language to use, and when I selected English I noticed that there was no OK button on the screen so I just hit Enter and it continued to the next screen.

It then asks me for a timezone, and if I hit Enter I get a selection box where I can choose my timezone.  Unfortunately, I don't see any way to continue.  Is the OK button off the bottom of the screen somewhere?

---

### Post by dreadlord_chris on 2007-07-09
> **sot3 said:**
> I'm expecting that this question may make me look really stupid, but I'll ask anyway.

I've downloaded the latest ISO for amd64 and I'm attempting to install on a new system.  It boots fine from CD, then asks me what language to use, and when I selected English I noticed that there was no OK button on the screen so I just hit Enter and it continued to the next screen.

It then asks me for a timezone, and if I hit Enter I get a selection box where I can choose my timezone.  Unfortunately, I don't see any way to continue.  Is the OK button off the bottom of the screen somewhere?

you need to configure your display so you can get a higher resolution. Open up a terminal and enter the following:
```

sudo dpkg-reconfigure xserver-xorg

```
It's gonna ask you a bunch of questions - for now you are really only concerned with 2 things (you'll be doind this again later - right now we're just configuring it for installation). When it asks what *driver* to use - choose **vesa**. When it asks for what resolution to use choose only 1024x768 (uncheck everything else). Accept the defaults for everyting else. At the end say yes to save **xorg.conf**.
Once that is done hit **Control-Alt-Backspace** - this will restart X (the GUI system), You should now be able to see all....

---

