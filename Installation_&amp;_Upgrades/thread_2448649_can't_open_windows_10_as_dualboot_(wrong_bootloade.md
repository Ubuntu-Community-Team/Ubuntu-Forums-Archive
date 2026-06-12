---
title: "can't open windows 10 as dualboot (wrong bootloader)"
date: 2020-08-11
forum: Installation &amp; Upgrades
---

### Post by chicanodionio on 2020-08-11
hello ,Im just new to this OS and i know maybe this is a old problem as before , i install ubuntu (dual boot ) together with windows 10 pro , and window 7 
but as i install the bootloader to the windows 10 pro , i cant access the windows 10 pro , please help me to change the bootloader to the window 7 , or help me so i can access 
my windows 10 pro , thank you , power!!!

---

### Post by slickymaster on 2020-08-11
Thread moved to **Installation & Upgrades** for a better fit

---

### Post by Bucky Ball on 2020-08-14
Can you boot into any of the other OSs and just not Win 10? Anyhow, go [here]("https://help.ubuntu.com/community/Boot-Repair"). 

Once you have Boot Repair up and running and you're looking at the home GUI, click 'Recommended repair'. When that's all done, reboot the machine. Can you boot all the installs now?

If you can't boot any of the OSs, you can create a Boot Repair USB on another machine and boot from that then run a repair. Good luck.

---

### Post by oldfred on 2020-08-14
BIOS installs?

Windows on second install, overwrites the first installs boot files in the NTFS partition with boot flag and updated BCD with first install, so Windows can boot either version.

Then grub only finds one set of Windows boot files.

Also grub only boots working Windows, so Windows 10's fast start up must be off and hibernation in both Windows must be off. And Windows 10 will turn fast start up back on with updates.

If all these systems are on one drive in BIOS boot mode with only one MBR for starting booting, Windows 10 has made dual booting a bit more difficult. Better to use UEFI or at least have two drives, to have two MBR.

If grub will not boot Windows, you have to temporarily install a Windows boot loader or a Windows type boot loader, fix Windows, then restore grub, so then grub can boot Windows again. 
Best to have both a Windows repair flash drive and Ubuntu live installer for current versions of installed systems for those regular repairs.


If both installs of Windows are in primary NTFS partitions, you can move boot flag & do repair to get boot files into both Windows. Then grub can direct boot either one.

Pictures here worth 1000+ words Older Windows but same for all BIOS versions.
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by chicanodionio on 2020-08-15
yes  ,, i think that will be the problem in boot-repair does nothing at all when i select windows 10 in grup boot loader the nothing happen , so what do i do to fix this , please help

---

### Post by CelticWarrior on 2020-08-15
Again, > [COLOR=#000000]grub only boots working Windows, so Windows 10's fast start up must be off and hibernation in both Windows must be off. And Windows 10 will turn fast start up back on with updates.[/COLOR]

So, if UEFI it should be as easy as changing the UEFI boot order back to "Windows bootloader manager", boot Windows 10 directly and proceed with the above instructions regarding Fast Startup. Then change the UEFI boot order back to Ubuntu, boot Ubuntu and run 'sudo update-grub'.

If BIOS the process is a lot more complicated. You need to boot Windows 10 installation media and follow (Windows) instructions to reinstall the Windows bootloader in MBR. This same bootloader should handle both 10 and 7. Then boot Windows 10 and follow the above instructions regarding Fast Startup. Finally reinstall Grub - you can then use Boot Repair for this -, boot Ubuntu and run 'sudo update-grub'.

The more OSes in multi-boot scenario, the more solid your knowledge must be. If you don't know what you're doing better acquire the required minimum before proceeding otherwise you'll end up wasting a lot more time correcting easily avoidable mistakes and some thing may not be correctable at all.

And why are keeping Windows 7 around? It's EoL and shouldn't be used in any internet facing computer (disconnected and only used for retro-gaming is fine though).

---

