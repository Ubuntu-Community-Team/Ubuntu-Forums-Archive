---
title: "Loss of video at boot up"
date: 2011-04-19
forum: Installation &amp; Upgrades
---

### Post by BluDawg on 2011-04-19
I installed 10.04 in stand alone on a HP 7700 slim line. On the first boot I got a blinking cursor then loss of singal msg. on the monitor and it goes blank. The OS continues to boot but I have no video. During the install I had to use nomodeset to get video. I figured I could correct this on the first boot using cntrl x and adding nomodeset in the grub screen then install the NVIDIA driver after the boo up. I did it that way when the system was dual boot with Vista. Now I don't get the grub boot screen:confused: I rebooted with the install CD and downloaded the NVIDA driver after mounting the HD and rebooted with no change :confused::confused:

---

### Post by tommcd on 2011-04-20
If Ubuntu is the only OS on the system you will not get the grub menu on bootup like you do with a dual boot system. 
To see the grub menu hold down the *shift* key when the computer boots. Then add *nomodeset* to the grub menu's kernel line, then boot the computer.
If this works, then install the nvidia driver from the Ubuntu repos and you should be good. If you have tried to install the nvidia driver from nvidia.com, you should remove that before installing the nvidia driver from the Ubuntu repos.

---

### Post by BluDawg on 2011-04-20
Thanks tommcd. I figured this out quite early this morning I think it was lack of sleep and too much coffee that jogged my memory:D  ***Problem Solved!!!***

---

