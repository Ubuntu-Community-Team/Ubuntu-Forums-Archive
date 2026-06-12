---
title: "Problems in displaying grub menu. Works only when I connect my pen drive"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by clipod on 2010-12-26
Hello I am a newbie. I have this wierd problem which I tried to find on the forum but I could not. I made a USB bootable Ubuntu 10.10 server on my pen drive for installing the OS on my system. I have installed and it started working. But the problem is every time I need to work on linux i have to connect my pen drive and boot it via usb. Or else its not showing the grub menu. It directly goes to my other operating system (win 7). Previously i have installed ubuntu 9.04 and it did not have this problem. IDK if I have done any mistake while create a bootable linux right now. Can anyone tell me what I have to do to make this grub show up directly even when I am not connecting the usb.

---

### Post by Quackers on 2010-12-26
Welcome to UF
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by garvinrick4 on 2010-12-26
> **clipod said:**
> Hello I am a newbie. I have this wierd problem which I tried to find on the forum but I could not. I made a USB bootable Ubuntu 10.10 server on my pen drive for installing the OS on my system. I have installed and it started working. But the problem is every time I need to work on linux i have to connect my pen drive and boot it via usb. Or else its not showing the grub menu. It directly goes to my other operating system (win 7). Previously i have installed ubuntu 9.04 and it did not have this problem. IDK if I have done any mistake while create a bootable linux right now. Can anyone tell me what I have to do to make this grub show up directly even when I am not connecting the usb. The install you have on HDD does not have grub installed correctly and go's straight to only OS that drive thinks is installed. On USB pen drive has a good grub in mbr (master boot record)and see's all your installs.
# Do what post #2 as Quackers asks and it will show where error lies and be able to be fixed. No user can fix without being able to examine your bootscript!! Can make a quess if that is what
you desire.

---

