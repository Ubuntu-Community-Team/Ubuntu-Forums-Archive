---
title: "After Installing Ubuntu 12 Alongside XLES 10, SLES 10 wouln't load."
date: 2013-04-11
forum: Installation &amp; Upgrades
---

### Post by ksnvarma on 2013-04-11
Hello Guys, 
    I use the SLES 10 (Suse Linux Enterprise Server 10) for the work purposes, but I don't have drivers for it, so I cannot use Internet , audio or video in SLES 10 . So I installed Ubuntu 12 alongside the SLES 10, it installed fine and everything is working, but the SLES 10 does not boot. I believe it could be fixed by making some changes to the grub. Can anyone help me solve this please . Thank you. 
Notes:
I created 3 partitions while installing SLES 10   1 boot partition (SDA 1),  1 root partition (SDA 3),  and 1 Swap Partition (SDA 2). So I believe the grub is in the boot partition. Then I installed ubuntu alongside SLES 10, I have no idea where it got installed, I was planning to create a new partition for it and install it there but it showed the option "Do you want to install Ubuntu alongside SLES 10" and I chose Yes and it installed the OS automatically , It didn't ask me to create partition or anything. Kindly help me resolve the issue. Thank you.

---

### Post by grahammechanical on 2013-04-11
> [COLOR=#000000]but the SLES 10 does not boot[/COLOR]

Please give more information. Do you get a Grub menu? If you select SLES 10 what happens? "Does not boot" does not give any clue as to what is wrong. Are there any error messages?

---

### Post by ksnvarma on 2013-04-11
> **grahammechanical said:**
> Please give more information. Do you get a Grub menu? If you select SLES 10 what happens? "Does not boot" does not give any clue as to what is wrong. Are there any error messages?

Hello, Yes I do get a grub menu showing Ubuntu 12.04 and SLES 10 options, but when I select Ubuntu, it loads fine, but when I select SLES 10 the computer just restarts and shows the grub menu again.

---

### Post by grahammechanical on 2013-04-11
Here is something that you can try. Open a terminal and enter this command

```
sudo update-grub
```

And watch the printout. Does Grub show that it has detected SLES 10? You might want to check this out

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Note this comment:

> 
[LIST]
[*=left][FONT=inherit]Then click the "Recommended repair" button. When repair is finished, note the URL (**paste.ubuntu.com/XXXXX**) that appeared on a paper, then reboot and check if you recovered access to your OSs. [/FONT]
[*=left]If the repair did not succeed, indicate the URL to people who help you by email or forum.
[/LIST]


Post the URL here. In that way some of us will be able to get a better idea of what is happening. Usually, when Grub cannot find the configuration files it needs it puts us at a Grub rescue prompt. But you are getting a re-boot.

I am wondering about the file systems for SLES 10. Is it Ext4 or btrfs by any chance? I tried experimenting with Ubuntu and btrfs and I could not get the installation to load. I think that Grub has problems with a boot partition that is btrfs. Just my opinion. Can you find out what format that /boot partition (sda1) is? Does not SUSE use the LiLo boot loader?

Regards.

---

