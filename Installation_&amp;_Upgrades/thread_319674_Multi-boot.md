---
title: "Multi-boot"
date: 2006-12-16
forum: Installation &amp; Upgrades
---

### Post by Shriike on 2006-12-16
This may be a stupid question, or in the wrong place, if so I apologize, but I was wondering about something, I currently have Ubuntu installed on my laptop, and windows XP on a separate partition, I was wondering if I install Kubuntu would that mess stuff up (have the Grub booter that came with my Ubuntu not sure if it can handle more then 2 operating systems, not sure if I can reuse the same swap partition, etc.) if anyone could help me out I'd greatly appreciate it, I've been a longtime windows user just switching to Linux and wanted to try out a couple different distributions.

---

### Post by aysiu on 2006-12-16
Well, first of all, you don't have to install Kubuntu from scratch. You can just add it to Ubuntu by following these directions:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

If you want to install Kubuntu over Ubuntu just to get a fresh start, the Grub boot loader will be reinstalled and add Windows XP to the boot menu, just as Ubuntu did. Ubuntu and Kubuntu are the same distro underneath--it's only the appearance and superficial behaviors that are different.

If you want to do a triple-boot with Kubuntu/Ubuntu/Windows XP, you will need to create a new partition for Kubuntu, and its installed Grub will recognize both Ubuntu and XP and add them both to the boot menu. The swap space can be used by both Ubuntu and Kubuntu--you won't need two separate swap partitions.

---

### Post by Shriike on 2006-12-16
wow, that perfectly answers all my questions, thank you so much!

---

