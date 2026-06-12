---
title: "tty1-6 no login promote after recovering grub"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by chanyunkwan on 2010-03-06
Hi, I installed windows 7 and recover grub from the karmic livecd successfully. Now I can access all the OS in my machine. The only weird issue that I have is that there's no login promote in tty1-6 any more. When I switch to tty1-6, I can only see a flashing underline promote. But I can input anything in tty1-6. 
How to get tty1-6 back?

---

### Post by hansdown on 2010-03-07
Hi chanyunkwan.

This may help.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by hansdown on 2010-03-07
Hi chanyunkwan.

Edit:  

Double post.

---

### Post by chanyunkwan on 2010-03-07
Thanks man, but that doesn't work for my situation. I can get in any system through grub, just the tty1-6 in Karmic doesn't work unless I manually active them.

---

### Post by SecretCode on 2010-03-07
I don't know if it's connected to GRUB ... but it could be, via mode settings. I saw something about similar problems while fixing grub graphics modes.

Have a dig around the forums for tty login **prompt** (not promote) and /etc/init/ or /etc/init.d/ scripts.

---

