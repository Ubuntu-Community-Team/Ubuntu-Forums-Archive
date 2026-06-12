---
title: "Live Installer Fluorescent Green Screen"
date: 2022-06-27
forum: Installation &amp; Upgrades
---

### Post by george-b-fields on 2022-06-27
I wanted to install Ubuntu (22.04) and when I booted the live installer, the screen was a strange shade of green, with stuff still visible. Screenshot attached. I'm running a Ryzen 5 5600X and an NVIDIA RTX 3080, hardly an uncommon (or new) combination.

I did not actually proceed with the install, because I didn't want to have to deal with this later. Is this normal? Am I literally the very first person in the world to try this release on this particular hardware, and encounter this issue?

Any help would be appreciated. Someone on SO posted the same issue, the answer was something about Wayland, etc., etc., but when I go to "Additional Drivers" all the options there have X.org in the name (I did that in the live env). Obviously since I didn't install, I have no idea if installing the proprietary NVDA driver would fix the issue, but I wasn't going to be wasting my time just to find out it doesn't.

What am I doing wrong?

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290657&stc=1[/IMG]

- g

---

### Post by sudodus on 2022-06-27
Try with the [boot option](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808) **[FONT=Courier New]nomodeset[/FONT]**.

When in the grub menu, press 'e'  to edit a command. Put **[FONT=Courier New]nomodeset[/FONT]** it onto the 'linux' line (surrounded by spaces).

---

