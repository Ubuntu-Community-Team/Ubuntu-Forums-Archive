---
title: "Ubuntu+Fedora+XP"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by vijaysarathy on 2009-11-27
Hi,
I have Fedora7 and Windows XP currently installed in my PC.
I need to install Ubuntu (9.04 or 9.10). Will Ubuntu take care of grub settings while installation. 
Will there be any problems regarding grub after installing Ubuntu ? 
Pls suggest me on this..

---

### Post by Bunnybugs on 2009-11-27
If everything goes well, and you choose 'Install them side by side', you'll be able to pick a OS after loading grub. It gives you all the options, including all kernels, used by Ubuntu and Fedora, and their recovery modes! The grub is installed from Ubuntu, and the ubuntu partition becomes the first partition to boot. When you remove Ubuntu, and go back to only fedora and XP, you'll need to re-initialize the boot-options, like, install the windows bootloader as primary, or the Fedora-bootloader (I guess this is grub to?)

EDIT: Grub will automatically search for new/excisting OS'

---

### Post by darkod on 2009-11-27
Grub2 will search for other OSs and add them to the grub menu regardless what method of install you choose. If you feel confident with manual partitioning (not big deal anyway) and want to have control where and what size your partition will be created, you can select the Manual Partitioning option when asked where do you want Ubuntu installed.
That shouldn't affect grub2. Only situations reported where grub2 was not able to properly create the menu and boot all of your OSs seems to be if you have some weird partitioning layout etc. In these cases some manual tweaking might be needed.

PS. Grub2 comes with 9.10. In 9.04 grub1 is still used.

---

