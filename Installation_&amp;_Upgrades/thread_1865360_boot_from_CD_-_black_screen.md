---
title: "boot from CD - black screen"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by tankmil on 2011-10-20
Hi,

I have an Acer laptop with Win 7 64 bit installed now. I wanted to install Ubuntu. Downloaded ISO. Burnt to CD.

When I tried rebooting my machine and booting from CD, the following happens:
Black screen with a single line of text (someone's name in it). Then the screen shuts off, and the machine does a lot of spinning and thinking, but nothing appears on the screen. Please, advise.

---

### Post by varunendra on 2011-10-21
That single line (with name Peter Anvin...) indicates the booting process has been initialized from the cd, but then if there is a lots of (unusually fast) disk activity with nothing but blank screen, then it may be one of the following three most prominent reasons for this:

[LIST]
[*]cd is burnt incorrectly (::**Verification:** Try booting another computer with it.:: **Solution =** try writing it at minimum possible speed, preferably on a desktop PC)
[*]your optical drive has physical problems (**Solution=** try creating a Live USB flash drive and booting from it. Preferable method to create it is either using inbuilt "Startup Disk Creator" or Unetbootin)
[*]The downloaded iso itself is corrupt. (::Verification: match md5checksum of the downloaded iso with the value provided at where you downloaded it from. [How to MD5Sum]("https://help.ubuntu.com/community/HowToMD5SUM"):: Solution=Re-Download if match fails)
[/LIST]
If the same cd is able to boot another computer, you may use its inbuilt "Startup Disk Creator" to create a Live USB drive and try booting from it.

---

