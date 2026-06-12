---
title: "Problem with a new installation"
date: 2013-09-17
forum: Installation &amp; Upgrades
---

### Post by a-gus493 on 2013-09-17
Hello,

First of all, apologise for my english expresion, I'll do my best, but it's not my natural lenguage and I could have problems to explain myself.

Recently, I bought a new 500GB HDD and I added it on my computer. Then, past week, I reinstall my Win 7; and yesterday, I install on my old ~300GB HDD Ubuntu 12.04 LTS. Now, when I boot my PC always starts Ubuntu automatically, not even show the Grub file. Ubuntu runs perfectly, but I can't run my Windows.

I think the problem is in my MBR. I think I have one MBR in each HDD, and both ignores the other HDD. Knowing this, I still don't know how to fix it. 

Could you recomend me any tool? Maybe I should edit somehow the file grub.conf?

Thanks for your time.

---

### Post by grahammechanical on 2013-09-17
Are you able to use the BIOS to select which hard disk to boot from? Each hard disk has a Master Boot Record (MBR). If we have one hard disc then Ubuntu calls it sda (Sata Disk a). If we have two hard disks then the second hard disk is called sdb (Sata Disk b).

When we install Ubuntu we also install a boot loader called Grub into the MBR. As part of the process an attempt is made to detect other operating systems and list them into the boot menu. When you installed Ubuntu did you have the Windows 7 hard disk disconnected? If so then Ubuntu could not detect Windows 7. The Ubuntu boot loader thinks that Ubuntu is the only OS present so it does not show a Grub boot menu. It boots straight into Ubuntu.

What you can do is open a terminal. Search for terminal in the Dash - Click the Ubuntu icon at the top of the panel on the left called the Launcher When the teminal is loaded type this command

```
sudo update-grub
```
Enter your password and press enter and watch what is printed in the terminal. Does Grub detect Windows 7? It will be good if Windows 7 is detected. Now reboot and see if you get a Grub menu that lists Windows 7.

Regards.

---

