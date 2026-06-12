---
title: "2 big problems"
date: 2009-08-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hgergo on 2009-08-10
i have set my laptop to dualmonitor and the log aut and i get log in back while after login is droping me back to login screen.
And i have givn an update with the terminal and i have seen that grub is no mor showing the menu list for dualbooting with windows.
i have givn update-grub2 but no menu list.
sombodi can help me?

---

### Post by wayne_cat on 2009-08-10
well .. the dual booting problem:

grub2 (1.96+20090725-1ubuntu2) karmic; urgency=low

```
* 950_hidden_timeout.diff: New patch. Add GRUB_HIDDEN_TIMEOUT support.
Move the timeout setting to the end so that the sleep comes after
terminal setup.
[COLOR=Red][B]* debian/default/grub: Default to hiding the menu with a three-second
timeout. Pressing Escape during this time will show the menu.
grub-installer will unhide it if other operating systems are installed.[/B][/COLOR]
* debian/grub.d/05_debian_theme: Set a monochromatic theme for Ubuntu.
* 951_gfxpayload_keep.diff: New patch. If gfxpayload starts with "keep" or
if GRUB_ASSUME_LINUX_HAS_FB_SUPPORT is defined, then tell Linux to use
the current video mode.

[https://lists.ubuntu.com/archives/ka...st/005911.html]("https://lists.ubuntu.com/archives/karmic-changes/2009-August/005911.html")
```And your login problem ... sorry ... I do not understand what your wrote.
Can you explain it a little bit more

---

### Post by hgergo on 2009-08-10
I have set my laptop to clone display to a monitor and a mesage aear to log out and i am loging out and i cant log back while when i am loging in i wil be dropt back to login screen

---

### Post by hgergo on 2009-08-10
Nobody can help me?

---

### Post by bacardiandwatermelon on 2009-08-11
My dual boot returned after doing a dist-upgrade, update, then upgrade :-)

---

### Post by hgergo on 2009-08-12
nobody idire for login problem or how can I disable dualmonitor from terminal?

---

