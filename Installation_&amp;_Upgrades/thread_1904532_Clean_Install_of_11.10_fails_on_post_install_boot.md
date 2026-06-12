---
title: "Clean Install of 11.10 fails on post install boot"
date: 2012-01-04
forum: Installation &amp; Upgrades
---

### Post by tuxman_ottawa on 2012-01-04
Hi,
 
I have a Dell GX620 with a single 320Gig SATA drive in it. I was able to boot the installer off my USB stick with no issue. While going through the installer I get to the partitioning screen. This is where things get a little wierd for me. 
 
I'm not new to installing xnix distros, but this is the first time that I've seen /dev/mapper taggings for my partitions rather than /dev/sda (on desktops anyway). So I create my single ext4 partition mounted to / and my swap partion. Eveything else seems ok but when it goes to reboot it throws me into a grub rescue prompt with the following error
 
error: no such device : ab3eb93f-109c-480c-ab60-2c51e1a981b
grub rescue>
 
if I try to access the partition in the grub resecue it tells me unknown filesystem but if I access it from the "liveUSB" boot I can see the data no issues.
 
if I look at /dev I see that the /dev/mapper/ entries are mapped to /dev/dm-0,1,2 which smells to me like it thinks its an array of some sort rather than a straight disk. 
 
if i do a fdisk /dev/sda I see the partitions sda1 and sda2 but they don't exist in /dev
 
does anyone have any suggestions? I have wiped the drive and tried this about 6 times in the last couple of days, I even tried creating the partitions manually from Fdisk and then using them for the install from the gui.
 
help ? :)
 
Thanks
 
Dave

---

### Post by Basher101 on 2012-01-04
maybe your grub entry was written wrong? try [this]("http://www.upubuntu.com/2011/08/how-to-repairreinstall-grub-boot-loader.html") to fix it in the easiest manner (done it too a few times, worked flawlessly)

---

### Post by tuxman_ottawa on 2012-01-06
Thanks for the tip, but it unfortunetly didn't work. 
 
I did finally get it working though. 
 
The problem was that although this was a fresh install, I had forgotten that the drive I was using in the machine had been in another machine prior. In that machine it was part of an NVIDIA raid. 
 
so the problem was that the ubuntu installer saw some leftover pieces that made it think it was a raid disk. It actually had 2 raid sets tucked away on it. a "nvidia" and a "ddf1"
 
I was able to remove the nvidia one by doing a 
 
[FONT=Courier New]/sbin/dmraid -E -r -f nvidia[/FONT]

[FONT=Courier New]but I couldn't remove the ddf1. I ened up having to write zeros to the drive to flush it.[/FONT]

[FONT=Courier New]dd if=/dev/zero of=/dev/sda bs=1M[/FONT]
 
[FONT=Courier New]it took time since it was a 320GB drive, but after that all was good.[/FONT]
 
[FONT=Courier New]Thanks for the help though.[/FONT]
 
[FONT=Courier New]Dave[/FONT]

---

