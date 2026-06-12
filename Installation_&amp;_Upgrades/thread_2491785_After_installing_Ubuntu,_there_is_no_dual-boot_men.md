---
title: "After installing Ubuntu, there is no dual-boot menu available."
date: 2023-10-20
forum: Installation &amp; Upgrades
---

### Post by cat82023 on 2023-10-20
My computer already had Windows XP pre-installed. After installing Ubuntu, the computer directly boots into Ubuntu without showing the dual-boot menu. I installed Ubuntu on the same SSD where Windows XP is installed, using the partitioning tool available before installing Ubuntu. I am certain that Windows XP has not been removed because I can still see the entire NT partition. What should I do now? Thank you, everyone.

---

### Post by oldfred on 2023-10-20
XP? We are telling users to stop using Windows 7 as it is not supported anymore.
Do not use XP to connect to Internet as you will be hacked in minutes.

Did you install in BIOS boot mode? 
Does this not add entry? Which runs os-prober. Some versions may turn off os-prober, but you can turn it back on in grub settings.
sudo update-grub
Most systems that would support XP, would not run Ubuntu well, you would need a lighter weight flavor.

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie
But I was able to run Kubuntu 22.04 on my old XP laptop from 2006 on an external SSD. XP long retired.

Post this:
sudo parted -l

---

### Post by cat82023 on 2023-10-20
I installed it by setting the USB drive as the boot device in the BIOS. Could you please explain how to input "sudo update grub"? This is my first time installing and using Linux, and I have no prior experience. I would greatly appreciate it if you could provide a step-by-step tutorial. Thank you so much.

---

### Post by oldfred on 2023-10-20
You need to open terminal. Do not be afraid of terminal. I still almost always copy & paste from my notes as I do not remember commands. 
[https://ubuntu.com/tutorials/command-line-for-beginners#1-overview](https://ubuntu.com/tutorials/command-line-for-beginners#1-overview)
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

sudo update-grub 

You can check of running os-prober is on or not:
cat /etc/default/grub
And then this line, I always set to true as I do not want os-prober to run, you can change to false:
[FONT=monospace][COLOR=#000000]GRUB_DISABLE_OS_PROBER=true[/COLOR]



[/FONT]

---

