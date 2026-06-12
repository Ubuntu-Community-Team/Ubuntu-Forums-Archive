---
title: "uswsusp broke my swsusp"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by arfbarf on 2007-10-31
Hi all,

In the never ending quest for working suspend I have installed uswsusp on my gutsy install and not only did it not work but it also broke my prior to that working hibernate.

All I did 'sudo apt-get install uswsusp' and after trying s2disk and I removed it with 'sudo apt-get remove uswsusp'

Unfortunately something in this process broke swsusp. A unsuccessful try to hibernate results in this entry in the log:

swsusp: Cannot find swap device, try swapon -a.

So the questions are these:
1. is there some sort swsusp.conf somewhere that got modified
2. I noticed that the uswsusp install modified/generated the following files:
     /boot/initrd.img-2.6.22-12-generic 
     /boot/initrd.img-2.6.22-14-generic 
what are these files and how do I get the original copies?
3. Is there anyway to get back to the previous system state prior to installing uswsusp?

Thanks for all your help.

---

### Post by arfbarf on 2007-11-01
Ok I think I figured out what was going on. Here is a summary and steps that I had to do to fix it:

1. The main cause was installation of uswsusp, During the install uswsusp complained about swap not being available even though the partition was there. What it did and how it messed up the swap I don't know, but it for sure did it.
2. Everything looked good in '/etc/fstab' and 'fdisk -l' also returned the expected results. But in reality the swap was not active. running 'free' or swapon -s showed no swap space
3. To get the swap back I followed the swap faq, Rebuilt the kernel and rebooted.
4. Hibernate works again :-)

---

