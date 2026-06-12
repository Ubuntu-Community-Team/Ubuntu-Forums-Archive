---
title: "Using Vista boot loader, dual boot 10.10"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by rplantz on 2010-10-18
My laptop dual boots Vista and Ubuntu 10.04. I use the Vista boot loader so I can get to the Vista restore partition if need be. (It did not come with a Vista CD/DVD.)

When I've installed Ubuntu versions up through 10.04, there was an "advanced" pull down menu after partitioning that allowed me to tell the installer NOT to overwrite the Vista boot loader. I just tried to install 10.10, and I do not see this option. Is there any way to continue using the Vista boot loader with 10.10?

I understand that I can use grub. I have Ubuntu 10.10 and Windows 7 dual booting on my desktop machine. It uses grub for both systems. But, again, I'm trying to preserve the Vista boot loader on my laptop so I can get to the restore partition. I learned the hard way when I first bought the laptop that grub does not handle the restore partition at all. Took me a whole afternoon to get the laptop running again.

---

### Post by wilee-nilee on 2010-10-19
The former advanced button for grub placement is now in the manual partitioning part of the install, bottom of the screen.

---

### Post by rplantz on 2010-10-19
> **wilee-nilee said:**
> The former advanced button for grub placement is now in the manual partitioning part of the install, bottom of the screen.

Aha! I recall seeing a drop-down menu in that part of the install. I have three partitions for Ubuntu: /, /home, and swap. Am I correct that I should select the / partition for grub, then the Ubuntu installer will NOT write over the MBR, leaving the Vista boot loader as the primary loader for my machine? (The / partition shows up as something like /dev/sda3 in that drop-down menu.)

---

### Post by wilee-nilee on 2010-10-19
> **rplantz said:**
> Aha! I recall seeing a drop-down menu in that part of the install. I have three partitions for Ubuntu: /, /home, and swap. Am I correct that I should select the / partition for grub, then the Ubuntu installer will NOT write over the MBR, leaving the Vista boot loader as the primary loader for my machine? (The / partition shows up as something like /dev/sda3 in that drop-down menu.)

It is the same choice just in a different place. Sounds like your already using the manual partitioning so you should have no problems. 

As far as putting grub in other then the mbr there are others that are more familiar with this.

---

### Post by rplantz on 2010-10-19
Thank you, wilee-nilee. It worked just fine. I did manual partitioning and used to pull-down menu at the bottom to tell the installer to place grub in the "/" partition.

Actually, grub also saw both my Vista and my Recover systems. Starting with the Vista boot loader I select Ubuntu. That brings up grub, which allows me to boot into Vista. I did not try the Recover yet.

Thinking back, I think I was using grub 1 on the laptop and had been simply upgrading Ubuntu through 10.04. I suspect that grub 2 sees the Recover okay and would allow me to boot into that if necessary. In that case, I could just let grub 2 write over the MBR and control the whole thing. I don't use the laptop very much, so this isn't a big deal for me. One of these days I might give it a try. It's more likely that I will eventually get another Windows 7 install disk and upgrade from Vista, so I would not need the Recover partition any more.

---

