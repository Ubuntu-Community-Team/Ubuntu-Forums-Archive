---
title: "stuck at splash screen after kernel upgrade"
date: 2011-12-09
forum: Installation &amp; Upgrades
---

### Post by jabrilm on 2011-12-09
I am running Ubuntu 10.04 on an HP Pavilion dm1 laptop. I ran update manager a couple of days ago, which included a kernel upgrade. So the GRUB loader now shows:

Ubuntu, with Linux 2.6.32-36-generic
Ubuntu, with Linux 2.6.32-36-generic (recovery mode)
Ubuntu, with Linux 2.6.32-34-generic
Ubuntu, with Linux 2.6.32-34-generic (recovery mode)

(plus a Windows 7 installation)

When I select the first (default) choice "Ubuntu, with Linux 2.6.32-36-generic", it starts to boot up but then gets stuck at the splash screen where it reads "ubuntu" with 5 red dots beneath. It never gets past that point. It also does that when I select the third choice "Ubuntu, with Linux 2.6.32-34-generic" (the previous version). 

The only way I can run Ubuntu now is in recovery mode / low graphics version, which seems very limited (e.g. wi-fi doesn't work). 

Any suggested fix? In the short time that I've had this laptop (3 months) there have been two kernel upgrades, each of which completely broke Ubuntu in different ways on this laptop.

---

### Post by MAFoElffen on 2011-12-09
> **jabrilm said:**
> I am running Ubuntu 10.04 on an HP Pavilion dm1 laptop. I ran update manager a couple of days ago, which included a kernel upgrade. So the GRUB loader now shows:

Ubuntu, with Linux 2.6.32-36-generic
Ubuntu, with Linux 2.6.32-36-generic (recovery mode)
Ubuntu, with Linux 2.6.32-34-generic
Ubuntu, with Linux 2.6.32-34-generic (recovery mode)

(plus a Windows 7 installation)

When I select the first (default) choice "Ubuntu, with Linux 2.6.32-36-generic", it starts to boot up but then gets stuck at the splash screen where it reads "ubuntu" with 5 red dots beneath. It never gets past that point. It also does that when I select the third choice "Ubuntu, with Linux 2.6.32-34-generic" (the previous version). 

The only way I can run Ubuntu now is in recovery mode / low graphics version, which seems very limited (e.g. wi-fi doesn't work). 

Any suggested fix? In the short time that I've had this laptop (3 months) there have been two kernel upgrades, each of which completely broke Ubuntu in different ways on this laptop.
In low-grahics mode, go tp System > Administration > Hardware Drivers > install your driver.

---

### Post by MAFoElffen on 2011-12-09
> **jabrilm said:**
> I am running Ubuntu 10.04 on an HP Pavilion dm1 laptop. I ran update manager a couple of days ago, which included a kernel upgrade. So the GRUB loader now shows:

Ubuntu, with Linux 2.6.32-36-generic
Ubuntu, with Linux 2.6.32-36-generic (recovery mode)
Ubuntu, with Linux 2.6.32-34-generic
Ubuntu, with Linux 2.6.32-34-generic (recovery mode)

(plus a Windows 7 installation)

When I select the first (default) choice "Ubuntu, with Linux 2.6.32-36-generic", it starts to boot up but then gets stuck at the splash screen where it reads "ubuntu" with 5 red dots beneath. It never gets past that point. It also does that when I select the third choice "Ubuntu, with Linux 2.6.32-34-generic" (the previous version). 

The only way I can run Ubuntu now is in recovery mode / low graphics version, which seems very limited (e.g. wi-fi doesn't work). 

Any suggested fix? In the short time that I've had this laptop (3 months) there have been two kernel upgrades, each of which completely broke Ubuntu in different ways on this laptop.
At your Grub Menu, follow these instructions:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][**Temporalrily Booting Into a TTY Text Console**]("http://ubuntuforums.org/showpost.php?p=11383888&postcount=715")[/SIZE][/COLOR][/SIZE][/COLOR]

That will get you into a TTY Text console with newtorking.

Then do:
```

lspci -vnn | grep VGA

```If it says ATI then
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][**Installing ATI Packaged Drivers**]("http://ubuntuforums.org/showpost.php?p=11467052&postcount=798")[/SIZE][/COLOR][/SIZE][/COLOR]

If it says NVidia then
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][**Installing NVidia Packaged Drivers**]("http://ubuntuforums.org/showpost.php?p=11467050&postcount=797")[/SIZE][/COLOR][/SIZE][/COLOR]

If it says Intel, then...

---

### Post by jabrilm on 2011-12-09
I get "failed to fetch" errors when I try to active the driver listed there, since wi-fi isn't working. So I guess I have to fix the networking problem before this problem. And the solution I've followed before isn't working:

[http://ubuntuforums.org/showthread.php?t=1776880](http://ubuntuforums.org/showthread.php?t=1776880)

---

### Post by MAFoElffen on 2011-12-09
> **jabrilm said:**
> I get "failed to fetch" errors when I try to active the driver listed there, since wi-fi isn't working. So I guess I have to fix the networking problem before this problem. And the solution I've followed before isn't working:

[http://ubuntuforums.org/showthread.php?t=1776880](http://ubuntuforums.org/showthread.php?t=1776880)
So... Your wifi is not working while booted TTY Text console?  If not working, then your wifi also was hosed?

Does your wifi work when booted under the LiveCD?

---

### Post by jabrilm on 2011-12-09
Okay, I got wireless working in recovery mode again. 1 problem down, 1 to go. I will see about the ATI driver now.

---

### Post by MAFoElffen on 2011-12-09
> **jabrilm said:**
> Okay, I got wireless working in recovery mode again. 1 problem down, 1 to go. I will see about the ATI driver now.
So the LSPCI command string returned ATI as your video?

---

