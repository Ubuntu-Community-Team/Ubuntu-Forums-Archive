---
title: "Ubuntu 19.10 installation freezes in blank screen after the GRUB2 screen"
date: 2019-10-20
forum: Installation &amp; Upgrades
---

### Post by tobubiyori on 2019-10-20
I downloaded Ubuntu 19.10 iso image from the official website of Ubuntu and burned it in my USB flash drive. Then,I tried to boot in live session in my computer, Dell Inspiron 3268 with Intel core i5-7400 CPU.
However, after I chose "Try Ubuntu without installing" in GRUB2 menu screen, the screen went blank in Power Saving Mode and nothing seemed to be happened. I could do nothing except turning off my computer forcibly.
I made sure that there is no problem for the USB flash drive and iso image I downloaded by booting another PC with it. I tried changing the port and USB flash drive to use, but the situation didn't change.

Please give me some suggestions to solve this problem. Sorry for my poor English, because I am not native English speaker.

---

### Post by oldfred on 2019-10-20
Dell typically needs UEFI update & if SSD, SSD firmware update.
You also need to change RAID/Intel RST to AHCI, but if dual booting with Windows install Windows AHCI driver first.
With nVidia you typically need nomodeset on boot of live installer & first boot or until nVidia driver installs. But now I believe 19.10 gives you the option to install nVidia driver as part of install.

Dell  Inspiron 3670 UEFI update & AHCI worked
[https://ubuntuforums.org/showthread.php?t=2412152](https://ubuntuforums.org/showthread.php?t=2412152)
Dell Inspiron 3567 Review i3 7100u (Works well)
[https://ubuntuforums.org/showthread.php?t=2364642](https://ubuntuforums.org/showthread.php?t=2364642)
Dell precison 3520 Turn off RAID & change to AHCI
[https://askubuntu.com/questions/1096492/installing-ubuntu-18-04-alongside-windows10-the-ssd-is-not-recognized](https://askubuntu.com/questions/1096492/installing-ubuntu-18-04-alongside-windows10-the-ssd-is-not-recognized)

At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by rbmorse on 2019-10-20
When you boot from the live installer device, select the "try Ubuntu without installing, safe graphics mode" or similar option.  

There should be two choices that indicate "safe graphics".  On my machine the first one brings up a lower screen resolution than the second one.

---

### Post by chinakook on 2019-10-20
I have this problem too, I think it's the problem with linux kernel 5.3.
My graphic card is 2080Ti and I can enter system when I choose the linux kernel 5.0 (my 19.10 is upgrade from 19.04).
I also tried newly installing, it has the same problem.
Note: My BIOS debug LED show a ```AF``` code in that case.

---

### Post by tobubiyori on 2019-10-21
Thank you for your quick reply and many hints for the solution.
This time, setting "NOMODESET" (as mentioned in post #2) in the boot option in grub2 worked fine and I succeed to boot live sessions in my Dell Inspiron PC.
It seems the problem was completely solved. Thank you very much!!

---

