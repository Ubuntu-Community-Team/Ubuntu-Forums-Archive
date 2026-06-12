---
title: "Linux dual boot question(grub)"
date: 2014-03-19
forum: Installation &amp; Upgrades
---

### Post by evan8 on 2014-03-19
Question. I have ubuntu/gnome installe don computer. I want to install another OS as well (Mint)

After I partition at set up and install Mint. Do I have to update grub or mess with any grub settings at all? Since they are both linux and use grub. Do, I just leave that all alone? And if I wanted to unistall one of the OS's. Do I delete the partition it is only?  in short. after installing or unistall a OS will I have any grub boot errors ? I just don't wan tot end up getting rid of one of them and then not being able to boot again because of a grub issue.

Sorry if it's been asked many times. Harder to find my answer since windows is not involved.

---

### Post by ajgreeny on 2014-03-19
The possible problem you run into when deleting a Linux partition is that it may contain all the configuration files and folders for grub, the bootloader of your system.  For example when you install Mint it will automatically install grub on the MBR of the machine, taking over from grub managed by Ubuntu.  As long as you keep Mint that will not be a problem but if you should delete the Mint partition you will get a grub error screen and be unable to progress any further until you re-install grub using a live system.

The alternative way is to choose "Something Else" when you install Mint which allows you to choose to install grub from Mint to a partition of that OS, not to the MBR, meaning that Ubuntu's grub will continue to be in charge.  It will be possible to boot to Mint once you have run **sudo update-grub** in Ubuntu, and if in future you choose to use Mint and remove the Ubuntu partition you can install Mint's grub to the MBR by first booting to Mint and running **sudo grub-install /dev/sda** assuming sda is the HDD name.

---

### Post by evan8 on 2014-03-19
I'll try to figure it out and be careful. I have 2 Hd's SSD for os and another for storage. So, that can make things a littlre more weird too I guess. When I try to make a partition. It says something like " this will remove all partitions" is that the correct path there?

Oh and luckily I just got a crapper desktop up and running and realized I can just try whatver I need to on that and not have to worry about losing anything. I mean I keep everything on my storage HD anyways. But don't feel like reinstall and themeing everything again. you know the drill heh

---

### Post by evan8 on 2014-03-19
It seems when I try to install alongside it just shows my storage HD. Is it because my boot is on ssd? I'll probably just end up installing over the ubuntu.

---

