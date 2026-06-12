---
title: "Ubuntu 18.04.4 with Nvidia gtx 1650 super"
date: 2020-02-17
forum: Installation &amp; Upgrades
---

### Post by nikos_gevre on 2020-02-17
I just bought a new gpu. Nvidia gtx 1650 super. Tried to run Ubuntu 18.04.4 that i already had installed. The pc freezes after i log in. Tried some stuff i found online but ended up braking the grub and generally my pc. I have now reinstalled everything in my pc. I am using one drive with Ubuntu, one drive with windows 10 and one hdd for storage. I formatted and clean installed Ubuntu in the ubuntu driver. Grub broke my windows drive as well. And now i am reinstalling windows. Even after the fresh install of Ubuntu 18.04.4 I still have the same issue. Ubuntu freezes after log in. What is wrong with Nvidia and Ubuntu? And how can i use Ubuntu without unplugging the gpu every time i want to use Ubuntu? I read about installing the 390 driver version but somehow i couldn't..? And then i tried to change something in the grub that i read in a thread and everything went south... Please help!

Update: i fixed a problem with the grub and i can boot to Windows now. My mistake was stupid... Still need help with the Ubuntu though. Still freeze after log in

---

### Post by CatKiller on 2020-02-17
> **nikos_gevre said:**
> Nvidia gtx 1650 super... I read about installing the 390 driver version but somehow i couldn't..? 

The 1650 Super needs a driver from at least the 440 branch, which you can get from the [graphics drivers PPA](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa).

"I did something and then it broke" is not at all useful in allowing people to help you.

---

### Post by nikos_gevre on 2020-02-17
> **CatKiller said:**
> The 1650 Super needs a driver from at least the 440 branch, which you can get from the [graphics drivers PPA]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa").

"I did something and then it broke" is not at all useful in allowing people to help you.

did some stuff means i searched the problem online. in different posts and answers i found it was stating to download the 390 driver. i did that but the problem was still there. i currently have the 440 driver but it still freezes after log in

---

### Post by CelticWarrior on 2020-02-17
Disable Secure Boot.

---

### Post by mastablasta on 2020-02-18
my kid has the normal GTX 1650 (not the super) and all we did was install recommended drivers via PPA to 18.04.3 (which was the latest version at the install time). 
he has Ryzen CPU with no GPU on it.  If you have AMD Ryzen or Intel CPU that has a GPU chip attached, then that might be causing issues and i would disable it.

graphics drivers do not break the grub. the only thing are boot options you can add to GRUB. however they are temporary (per boot) and do not have any effect on the OS after reboot. that is unless you took special effort in making things permanent.

also no need to reinstall windows if they can't boot due to corrupted boot loader. instead, just restore the boot loader.: [https://www.dell.com/support/article/us/en/04/sln300987/how-to-repair-the-efi-bootloader-on-a-gpt-hdd-for-windows-7-8-8-1-and-10-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln300987/how-to-repair-the-efi-bootloader-on-a-gpt-hdd-for-windows-7-8-8-1-and-10-on-your-dell-pc?lang=en)


or another version: [https://answers.microsoft.com/en-us/windows/forum/windows_10-update/how-to-restore-windows-bootloader-from-grub/4faa0e42-afc6-46cf-9dd5-13a860e62746](https://answers.microsoft.com/en-us/windows/forum/windows_10-update/how-to-restore-windows-bootloader-from-grub/4faa0e42-afc6-46cf-9dd5-13a860e62746)

---

