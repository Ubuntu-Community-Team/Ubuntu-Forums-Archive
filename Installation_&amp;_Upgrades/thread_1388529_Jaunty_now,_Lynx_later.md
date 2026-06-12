---
title: "Jaunty now, Lynx later"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by AZinOH on 2010-01-23
Jaunty now, Lynx later

I am currently dual-booting Vista/Ubuntu 9.04 (32-bit) on a 2008 Dell Inspiron 530 (single hard drive). The goal is to eventually replace 9.04 with 10.04, probably 2-3 months after it is released. I am not an experienced user of either OS, and would have difficulty if I managed to somehow screw up GRUB and/or the Windows partition. Based on my current (lack of) knowledge and what I've read so far, the best hope of a clean install would be to replace 9.04 with 10.04 on /dev/sda5. Will doing this rewrite the existing GRUB and preserve Vista in the bootloader as it is now with a minimum of grief? Can this question even be answered now? I hoped someone using a 10.04 pre-release might have some input.

The other alternative would be to install 9.10 using the button in the Update Manager, and use the same method to get to 10.04 later on. What are the pros/cons of this method? I have no preference-I will use either method (or apt-get, if necessary). I just want to accomplish the change in the safest way possible without screwing anything up too seriously. 

Will I need to login as root to accomplish the change? If yes-how, as I have never done that?

Thanks for any assistance.

---

### Post by nothingspecial on 2010-01-23
I would put /home on a new partition. See [[COLOR="Magenta"]here[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome")

Then when you install 10.04, use the advanced option. Don`t touch your windows partition.

Select your new /home partition to be used as an ext3/ext4 (whatever it is) journaling file system but [COLOR="Red"][SIZE="3"]do not[/SIZE][/COLOR] check the format box. Give it a mount point of /home

Select the partition that currently has 9.04 on it for use as an ext4 journalinh file system, give it a mount point of / and select it for formatting.

This will preserve all your data and settings, but give you a clean install of 10.04.

---

### Post by AZinOH on 2010-01-23
nothingspecial, thanks for your reply. I think I understand the benefit of putting /home on a new partition but after reading that tutorial, I'm not sure that fits in my comfort zone given my abilities. I have no need or desire to preserve data and settings from 9.04 and am perfectly willing to start from scratch with 10.04. I just want to end up with a functioning 10.04 alongside a functioning Vista that will dual-boot just as it does now. If you have any further suggestions for this, I'll be pleased to hear them. Thanks again.

---

