---
title: "Ubuntu 14.04.1 (u)efi not booting"
date: 2014-08-02
forum: Installation &amp; Upgrades
---

### Post by Delec on 2014-08-02
I'm trying to install ubuntu 14.04.1 on my home server. The machine is a Dell Poweredge R410 (x64), has an hardware RAID5 and used to run windows server. I updated the bios to the latest version which comes with an UEFI option.

I installed Ubuntu (first ubuntu server, later ubuntu desktop) and both install fine, however when I reboot without the USB I am greeted by the Grub panic screen, something like this:
[IMG]http://members.iinet.net.au/~herman546/p15/fig2grub.gif[/IMG] 


Typing -ls returns (hd0). First I tried to install using the recommended partition function, later I partitioned manually during the installation, starting with a gpt partition table through gparted and during the installation choosing:
[LIST]
[*]efi-boot (1024mb)
[*]swap area (2048mb)
[*]/ (everything else)
[/LIST]

I have no clue what to do, can anyone help me?

---

### Post by Delec on 2014-08-03
Oke I made some progress. I repaired the install with the boot-repair utility, I downloaded the x64 version and created a bootable USB through unetbootin. After the boot-repair finishes I get message stating to point the UEFI bios to /EFI/ubuntu/grubx64.efi. I also confirmed the installation was in uefi mode with [COLOR=#333333][FONT=monospace][ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"

[/FONT][/COLOR]After a reboot I get a grub rescue screen with Disk " ,gpt2" not found.

Any ideas what to do next?

---

### Post by oldfred on 2014-08-03
Boot-Repair runs or you can just run the BootInfo report. Post the link it gives.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I do not know RAID, actually Boot-Repair knows it better.
There are just too many types of RAID, and I only run desktop. Linux has drivers for most hardware RAID, fakeRAID(BIOS based) and its own software RAID.

      
 Hardware RAID drivers
[https://wiki.debian.org/LinuxRaidForAdmins](https://wiki.debian.org/LinuxRaidForAdmins)

 [http://ubuntuforums.org/showthread.php?t=2022679](http://ubuntuforums.org/showthread.php?t=2022679)
[https://raid.wiki.kernel.org/index.php/Linux_Raid](https://raid.wiki.kernel.org/index.php/Linux_Raid)
[http://askubuntu.com/questions/43036/how-do-i-install-grub-on-a-raid-system-installation](http://askubuntu.com/questions/43036/how-do-i-install-grub-on-a-raid-system-installation)

---

### Post by Delec on 2014-08-09
The issue was solved. It turned out to be a bug in Grub2 that has issues with a (RAID) drive >2TB. The workaround is to create a /boot partition, this points grub to the beginning of the RAID array and solves the problem.

---

