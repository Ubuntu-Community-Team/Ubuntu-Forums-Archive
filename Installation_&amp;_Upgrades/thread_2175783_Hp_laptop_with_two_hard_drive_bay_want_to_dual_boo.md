---
title: "Hp laptop with two hard drive bay want to dual boot with Win8"
date: 2013-09-21
forum: Installation &amp; Upgrades
---

### Post by jaime3 on 2013-09-21
Hello guy's. I have my laptop running super great and running quick with Ubuntu 13.04 everything basically is working. But I have a second bay I just have to get the hard drive kit and then I can install 740gb or 720gb what ever size it is that came with. Now how would I dual boot from two seperate drive? I'm thinking about having a partition for Windows Os installation on the regular hard drive on second bay. And another partition for back up. I want to enter either or os by grub instead manually butting second or first through bios. How would I do that? Thank you.

---

### Post by nerdtron on 2013-09-21
1. Ubuntu is installed on the 1st hard drive.
2. Remove the 1st drive and put the 2nd drive only.
3. Install Windows as usual on the 2nd drive. There will be no problems as you Ubuntu drive is not connected.
4. After the Windows install, put the 1st drive back. Make sure that on the BIOS, the computer is set to boot to 1st Drive (the Ubuntu Drive).
5. On Ubuntu, run "sudo update-grub" from the terminal. This will scan all hard drives on available OSes. This will put an entry on the GRUB about your Windows installation.

With this method, the second hard drive is untouched. GRUB will merely scan that there is windows on that partition and it will add an entry on the GRUB (which is installed on the 1st hard drive). The windows boot loader is still intact on the second drive.

---

### Post by jaime3 on 2013-09-21
> **nerdtron said:**
> 1. Ubuntu is installed on the 1st hard drive.
2. Remove the 1st drive and put the 2nd drive only.
3. Install Windows as usual on the 2nd drive. There will be no problems as you Ubuntu drive is not connected.
4. After the Windows install, put the 1st drive back. Make sure that on the BIOS, the computer is set to boot to 1st Drive (the Ubuntu Drive).
5. On Ubuntu, run "sudo update-grub" from the terminal. This will scan all hard drives on available OSes. This will put an entry on the GRUB about your Windows installation.

With this method, the second hard drive is untouched. GRUB will merely scan that there is windows on that partition and it will add an entry on the GRUB (which is installed on the 1st hard drive). The windows boot loader is still intact on the second drive.


That easy? Very nice! Thank you.

---

