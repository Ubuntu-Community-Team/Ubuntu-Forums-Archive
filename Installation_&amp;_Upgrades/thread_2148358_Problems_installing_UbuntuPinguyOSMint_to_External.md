---
title: "Problems installing Ubuntu/PinguyOS/Mint to External HDD"
date: 2013-05-24
forum: Installation &amp; Upgrades
---

### Post by Thetri on 2013-05-24
On both my laptop and netbook I was able to get what I wanted. On my Laptop I've managed to get Pinguy OS 12.04 and Linux Mint 13 running in a dual boot and on my Netbook I was able to get Lubuntu 12.04 and Joli Cloud in a dual boot. However, on my desktop I've run into issues. First of all every OS I've tried installing so far does not allow me to install it along side Windows 7 like it has on the laptop and netbook. I decided to stick in a External 1TB HDD I had laying around and install Ubuntu 12.04 on to it. The installation went well then I rebooted and got "error:file not found. grub rescue>" I turned off the PC and removed the drive thinking I've failed. Then I rebooted and saw the message there again. I freaked out since I thought Windows 7 was now gone. I did some research on my laptop and found out how to fix it using a grub repair disk. I got my Windows 7 working again. Now, I've recently tried installing Linux Mint 13 and Pinguy OS to the same HDD. The same message appears but only if I try booting from the External HDD. My main OS is fine. I'm wondering if there is a way to get this to work the way I wish. I just want to have it boot the OS when I select to boot my External HDD. Why do I need this grub thing? It seems to mess up everytime I try to install it. Not sure why but on the laptop and netbook it's fine.

---

### Post by 2F4U on 2013-05-25
It seems to me as if you installed grub to the mbr of the hdd on which Windows resides. If you want to boot Ubuntu to boot only when you select to boot from the external hdd, install the boot loader on the external hdd.

---

### Post by sudodus on 2013-05-25
Please see the following links to learn about grub and to find ways to repair your current installation. I agree with the previous post and think you should ***reinstall grub into your external drive, to the drive head***, for example /dev/sdb (no digit because not a partition).[URL="https://help.ubuntu.com/community/Grub2"]

https://help.ubuntu.com/community/Grub2[/URL]

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

But if you have not done any tweaking to your Ubuntu, it might be easier to reinstall it, and when you arrive at the partitioning page, select ***Something else ***and select to overwrite your previous Ubuntu installation (format its partition).

Then at the bottom of that screen, you can select where to*** install the bootloader***. Install it ***into your external drive***, to the drive head, for example /dev/sdb (no digit because not a partition).[URL="https://help.ubuntu.com/community/Grub2"]
[/URL]

---

