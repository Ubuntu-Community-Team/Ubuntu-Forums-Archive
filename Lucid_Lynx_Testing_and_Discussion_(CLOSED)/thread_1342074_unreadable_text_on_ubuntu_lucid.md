---
title: "unreadable text on ubuntu lucid"
date: 2009-11-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by benny.kallstrom on 2009-11-30
After todays update something went wrong with my ubuntu lucid. The computer boots up fine and everything seems to be fine until the desktop shows up. When i browse around the menu the text is in an unreadable state. It is like something i´ve never seen before. And i have used Ubuntu daily since 2007.

I know Lucid is still very experimental, so this would be my first problem when testing. I will reinstall Lucid.

---

### Post by Starks on 2009-11-30
Are you using xorg-edgers?

---

### Post by godhika on 2009-11-30
Got the same problem - and yes I am using X-org edgers

---

### Post by glasen on 2009-11-30
It is a bug in the package "xorg-xserver-video-intel" aka Intel-driver. See also this git-entry :

[http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/commit/?id=cfcabc45140d19bfbfa4737c0a11cdbb042d11eb](http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/commit/?id=cfcabc45140d19bfbfa4737c0a11cdbb042d11eb)

You have three options :

1. Don't use a experimental driver together with a experimental distribution

2. Wait a few days for a new version of the driver.

3. Compile your own version of the driver.

---

### Post by Starks on 2009-11-30
Here's the bug report if you care: [https://bugs.freedesktop.org/show_bug.cgi?id=25031](https://bugs.freedesktop.org/show_bug.cgi?id=25031)

---

