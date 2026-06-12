---
title: "Problem loading into Ubuntu"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by dean5778 on 2008-04-22
Hi there,

I'm completely new to Ubuntu so am unsure what to do here but here goes:

I've downloaded Ubuntu 8.04, then I opened the iso via daemon tools in windows vista. It gave me the option to install perfectly and I have done so on a partition. When it askes to restart I have two operating systems to pick: vista and ubuntu. When I click ubuntu all I seem to get is this:

[   54.927762] ACPI: EC: acpi_ec_wait timeout, status = 0, expect_event = 1
[   54.927810] ACPI: EC: read timeout, command = 128

after thinking maybe it needs the ISO mounted onto a cd (which is recommended I know) I followed the instructions on the ubuntu site about mounting and I downloaded and used ISOrecorder. 
So then I un-intalled my original attempt of ubuntu via the windows option. Restarted the computer with the cd in the drive. A ubuntu logo popped up and then soon gave me the option to just browse the operating system or install. I tried both and exactly the same problem happened to me like before. That code was showing. Nothing would load. I had to restart my computer without the cd in. 

Any help with this people. What am I doing wrong? 

My computer is fully up to spec as I only got it last September it's a sony vaio vgn-n38z with 140gb 2gb ram and 1.67 ghz intel processor. 

Thanks for help

---

### Post by Partyboi2 on 2008-04-22
seems to be a bug ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/191137](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/191137)) some have had sucess by removing quiet from the boot options. To try this at the ubuntu main menu screen press F6 and remove the word quiet then press enter.

---

### Post by Arabiest on 2008-10-06
u may need to see this that worked for me.

[http://ubuntuforums.org/showthread.php?p=5916216#post5916216]("http://ubuntuforums.org/showthread.php?p=5916216#post5916216")

Good luck

---

