---
title: "Ubuntu 18.04 hanging at startup after updates"
date: 2018-06-15
forum: Installation &amp; Upgrades
---

### Post by jeebuskrise on 2018-06-15
Okay, so I have been running 18.04 on my MSI GS63 laptop since it came out with no problems whatsoever. Today I went to shut down and checked the box "Install upgrades on startup" (not exact wording but you know what I mean). Anyway, when I went to start the computer back up again, it kept hanging at at splash. After trying multiple times and getting the same result, I went into the ubuntu advanced settings. What I found there is confusing me very much. Here are the four lines that appeared: 
-Ubuntu, with Linux 4.15.0-23-generic
-Ubuntu, with Linux 4.15.0-23-generic (recovery)
-Ubuntu, with Linux 4.15.0-22-generic
-Ubuntu, with Linux 4.15.0-22-generic (recovery)
So I tried running the third line (with the 22 instead of the 23) and it booted up perfectly. However, now the only way I am able to boot into Ubuntu is by manually going into the advanced options every time and selecting that line. If I try to boot normally, splash hangs. 

I am very curious. What does the 22/23 bit represent? Why are there 4 lines instead of only 2, which is what I have seen on other ubuntu systems? I'm a total noob with this operating system stuff, but I very much want to learn and understand. But I would also like to solve this problem.

---

### Post by mrdc76 on 2018-06-16
> **jeebuskrise said:**
> 
I am very curious. What does the 22/23 bit represent? Why are there 4 lines instead of only 2, which is what I have seen on other ubuntu systems? I'm a total noob with this operating system stuff, but I very much want to learn and understand. But I would also like to solve this problem.

The 22 and 23 represent kernel versions. Kernel was upgraded. Ubuntu always saves the previous kernel version for these kind of situations. 

You can 1) keep on booting through the advanced startup option until the bug is reported and fixed or 2) remove the newest kernel and put updates for kernel on hold: [https://askubuntu.com/questions/18654/how-to-prevent-updating-of-a-specific-package]("https://askubuntu.com/questions/18654/how-to-prevent-updating-of-a-specific-package") The latter option creates a security threat if the situation persists.

---

