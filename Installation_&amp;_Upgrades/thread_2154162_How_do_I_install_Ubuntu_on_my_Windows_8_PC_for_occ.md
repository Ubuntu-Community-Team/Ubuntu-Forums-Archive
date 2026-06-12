---
title: "How do I install Ubuntu on my Windows 8 PC for occasional use?"
date: 2013-06-13
forum: Installation &amp; Upgrades
---

### Post by DanielT01 on 2013-06-13
[COLOR=#000000][FONT=verdana]I'm starting to learn Ruby on Rails to develop web apps, and this is something than can't really be done well on Windows. So I need to install Ubuntu on my current system.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]My current Windows 8 OS is installed on a 120GB SSD, and I have a 1TB HDD, which is where I'd want to install Ubuntu.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]What's the easiest way to do this? Is it possible to have Ubuntu on the HDD and Windows on the SSD, keeping Windows as the default and just using Ubuntu when I need to?[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Thanks for the help![/FONT][/COLOR]

---

### Post by mikewhatever on 2013-06-13
It's possible, but a little complex, especially if you've not done it before. I'd suggest VirtualBox instead, in other words, an Ubuntu installation in VBox.

---

### Post by oldfred on 2013-06-13
Is your Windows 8 in UEFI mode with gpt partitioning and data drive also in gpt?
 Or are both MBR(msdos) and you boot with BIOS. 
Both have to be the same to easily dual boot. And install instructions, & partitioning requirements are then different for the new UEFI than the 30 year old BIOS/MBR.

---

