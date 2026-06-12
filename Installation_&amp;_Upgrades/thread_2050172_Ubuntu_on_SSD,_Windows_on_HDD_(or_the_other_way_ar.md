---
title: "Ubuntu on SSD, Windows on HDD (or the other way around)"
date: 2012-08-30
forum: Installation &amp; Upgrades
---

### Post by Rubykuby on 2012-08-30
Okay, I have fixed a problem I couldn't find any solution to on the internet, or merely vague directions. I thought I'd document how I fixed the problem for those who may struggle with the same issue. If you want to do this the other way around, simply imagine I say "SSD" when I say "HDD", and the other way around.

Some infos:
I have a 120GB SSD (sda, primary device)
I have a 500GB HDD (sdb)
I have UEFI

The steps to be taken are fairly easy. Go to this site and follow instructions: [http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)

The next thing you want to do is backup all your data (if you have any) and boot Ubuntu from a liveCD. Run "gparted" and wipe all partitions. This step is possibly optional, but I've found that it worked for me.

Next, shut down Ubuntu, replace the disc with the Windows installation disc and remove the power cord from your computer. Unplug the SSD cord. Put the power cord back and start your computer. Run the installation. Windows will install its two partitions exclusively onto the HDD.

Once the Windows installation is finished, shut down the computer, put the SSD plug back in and boot Ubuntu from the LiveCD. Ubuntu recognised the Windows installation for me, and clicking "install Ubuntu alongside Windows" immediately recognised the SSD as unallocated space, and installed there. Shut down the computer.

Put the boot-repair-disk CD in the tray and follow instructions displayed on the screen (if it asks you to go to the terminal, it can be found under accessories -> LXTerminal). It will sometimes show DOS-like GUIs. What worked for me is to use the "tab" key to enable the selection field, and use enter to select. At one point, it will ask you to assign the GRUB installation device. I used /dev/sda, the SSD. To pick that option, use the "space" key to select /dev/sda, and the "tab" key to jump to "OK". Hit enter. And keep following instructions.

Reboot, and make sure you have the SSD selected as the first booting device in BIOS/UEFI. It should work now. Rejoice!

---

