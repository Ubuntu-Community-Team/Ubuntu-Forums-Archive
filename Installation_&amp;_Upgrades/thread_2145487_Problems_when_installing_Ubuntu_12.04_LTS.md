---
title: "Problems when installing Ubuntu 12.04 LTS"
date: 2013-05-15
forum: Installation &amp; Upgrades
---

### Post by Khazrify on 2013-05-15
Hey guys, I recently wanted to try out Ubuntu so I decided to get the Windows installer of Ubuntu 12.04 LTS. After it finished installing, it asked me to restart my computer. After it restarted it booted up Ubuntu and all I see is static all over the screen. It anyone could help me fix it, I would really appreciate it.


Picture of what my screen looks like:
[http://i.imgur.com/RpVNAhb.jpg](http://i.imgur.com/RpVNAhb.jpg)

---

### Post by papibe on 2013-05-15
Hi Khazrify. Welcome to the forum ):P

What graphic card do you have?

Are you able to get into a text mode console when you press Ctrl+Alt+F1?

Regards.

---

### Post by Khazrify on 2013-05-16
[I]Hello,
I am unable to get into text mode. When I press ctrl, alt, f1, I just get the same static on my screen. The only thing I can get to is the purple screen where I can edit the GRUB menu. Also, I have an AMD Radeon HD 6970.[/I]

---

### Post by papibe on 2013-05-16
You have a fairly new video card. and it may need to run with the nomodeset option.

You can set that option on grub before booting into Ubuntu. Here are the [instructions]("http://askubuntu.com/questions/38780/how-to-set-nomodeset-for-installation") on how to do that (top answer).

Let us know if that helps.
Regards.

---

