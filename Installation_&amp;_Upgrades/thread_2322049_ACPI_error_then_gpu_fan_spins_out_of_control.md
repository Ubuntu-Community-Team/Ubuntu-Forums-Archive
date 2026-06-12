---
title: "ACPI error then gpu fan spins out of control"
date: 2016-04-26
forum: Installation &amp; Upgrades
---

### Post by krickets on 2016-04-26
[COLOR=#333333]I am trying to install ubuntu 16.04 onto a Gigabyte GA-890 FXA UD5 and what happens is that the computer says ACPI then a series of numbers, then says can not map memory that high, then my monitor turns off and my graphics card starts spinning uncontrollably and I'm forced to unplug the machine.[/COLOR]

[COLOR=#333333]I have 30 gb sdd, my system has 4 gb ram, and am using usb to install Ubuntu. (couldn't even get plop boot manager to run off a cd earlier)[/COLOR]

---

### Post by krickets on 2016-04-30
[COLOR=#070F14][FONT=Verdana]Hello all, I've been having trouble installing linux onto two motherboards. I've created bootable usbs and have tried Ubuntu 15.10, 16.04, both 32 and 64 bits. What happens is that when I try to get to the grub menu, I get a black screen and my gpu fans start spinning out of control.[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]One time, I got linux to install, can't remember what version, I think it was the 15.10, then the next time I booted it up, it said [/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]Starting init: /sbin/init exists but couldn't execute it (error- 8 )[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Starting init: /bin/sh exists but couldn't execute it (error- 8 )[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Kernel panic - not syncing: No working init found. Try passing init= option to kernel.[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]The hardware I have is the ASROCK btc pro H81.[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]I have 32 gb ssd drives by bwin.[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]4 gb.[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Sapphire Nitro Sapphire 380 gpus. [/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Intel Celeron G1840 Haswell Dual-Core 2.8 GHz LGA 1150 53W BX80646G1840[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]The bootable USBs are 8gb and I'm using rufus to burn the images.[/FONT][/COLOR]


[COLOR=#070F14][FONT=Verdana]I have also had an error that said ACPI error: can not map memory that high, and then the fan spinning error thing went again[/FONT][/COLOR]

---

### Post by Bucky Ball on 2016-05-01
*Threads merged*.

Please do not post duplicate threads on the same issue and split questions into separate threads for the best chance of support. You've basically reposted the same issue with more details. :)

If your thread hasn't seen any action in 12 or more hours, simply post 'bump' in a post on the existing thread (or add further information anytime) rather than starting a new one. 

Welcome. [See here]("http://ubuntuforums.org/showthread.php?t=1613132") under the heading 'How to enable kernel options on the livecd (before install)'.

Try the 'nomodeset' option first.

---

### Post by QIII on 2016-05-01
Is this a dual boot with Windows, by chance?

---

### Post by krickets on 2016-05-01
No, these are brand new mobos with no prior OS. nomodeset option gave me a black screen that says
 boot:

---

### Post by krickets on 2016-05-09
[[IMG]http://i106.photobucket.com/albums/m253/kr4ckas/kernelpanic1_zpswzygkjqi.jpg[/IMG]](http://s106.photobucket.com/user/kr4ckas/media/kernelpanic1_zpswzygkjqi.jpg.html)

---

### Post by krickets on 2016-05-09
I got this screen after using simply the integrated graphics.

---

