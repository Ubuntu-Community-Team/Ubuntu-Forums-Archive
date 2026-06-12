---
title: "Can't install from Dapper Live CD - screen resolution"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by zoon_unit on 2006-06-19
I'm having trouble booting up from the Dapper Live CD.  I set resolution to 1024x768 using F4 on the login screen.  And sure enough, the boot process starts off in that resolution.  But just as soon as the desktop starts to load, resolution drops back to 640x480.  That's the only option in the setting resolution screen.

I can't install ubuntu because all the install windows are too large to fit on the screen at 640x480, so I can't get to the command buttons.  But without installing, I can't make any permanent config changes, edit the config file, or download a nvidia driver.

What to do???  I have a Geforce 2 btw.

---

### Post by rcarring on 2006-06-19
Hit Esc when grub loads

Select recovery mode for the latest kernel you have

Lots of text will scroll by

You will end up at a prompt as "root".

This should allow you to configure X etc for the session you have just booted.

Then type in startx and it will load the desktop in hopefully the res you need.

---

### Post by zoon_unit on 2006-06-19
Can anybody else give this one a try?  Not sure what rcarring is talking about with configuring.  (newbie)  And since I'm booting from Live CD, will I have the ability to change configurations?

---

### Post by Mike Wilson on 2006-06-19
Search the wiki for "dapper upgrade" and note what it says about the "Desktop" ISO/CD (which is also 'live' for 6.06). I tried to use it for upgrading and it bombed; so did the strictly on-line option from the Update Manager. The only working upgrade path I could find was the "Alternate Install" ISO/CD.

---

