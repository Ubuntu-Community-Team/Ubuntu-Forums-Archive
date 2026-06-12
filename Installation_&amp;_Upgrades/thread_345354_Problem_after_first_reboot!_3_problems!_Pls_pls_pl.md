---
title: "Problem after first reboot! 3 problems! Pls pls pls HELP!!!"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by adityak_28 on 2007-01-24
Hi all,
   This is almost the 10th time i'm installing Ubuntu so this is getting really frustrating! This is the third different copy of ubuntu 6.10 i'm trying. Ok, I installed ubuntu-desktop on my computer just now. The installation completed successfully. On reboot, the ubuntu logo appeared with the loading bar and after sometime the screen blanked around 5-6 times like it was changing video modes. After that, it provided with 2 pages of errors by the X server. After this the message 

"The X server has been disabled. Restart gdm when it is configured correctly." 

was displayed on the screen. I then pressed Ctrl+Alt+F1 which displayed 

"[17179820.860000] Out of Memory: Kill process 6613 (apport) score 109 and children.
 [17179820.860000] Out of Memory: Killed process 6613 (apport)."

and it wouldn't let me log on. I then pressed Ctrl+Alt+F2 and logged in with my username(aditya). On logging, the message

"-bash: /dev/null: Permission denied"

was continuously output on the screen till i intervened it by pressing Ctrl+c. I'm a linux newbie and was looking towards ubuntu to be a good and newbie friendly learning ground. I have tried installing 6.06 (2 different copies) and 6.10 (3 diferent copies). 6.06 used to boot after install only once and would give the same X server error as mentioned above on subsequent boots. 6.10 gives me the above errors. 2 other copies of 6.10 used to give me different errors on each boot so i guessed that my installation media might be bad and downloaded another copy of 6.10. I checked this particular copy by verifying md5 checksum and verified data on cd after burning it (in Nero). This is almost my 10th re-install and the hopes of learning linux seem to be fading by the moment. Does anyone know what should be done now?

NOTE: My system is Amd X2 3600+, Gigabyte GA-M51GM-S2G motherboard (nForce 430. It also has an onboard display which I've disabled through BIOS since I have an external card, 1 GB DDR2 RAM, Seagate SATA II 160 GB HDD, XFX GeForce 7300 GS. I also have WinXP installed on my computer. I do not know if information about my system would help but I provided it anyway...

---

### Post by apjone on 2007-01-24
> **adityak_28 said:**
> Hi all,
   This is almost the 10th time i'm installing Ubuntu so this is getting really frustrating! This is the third different copy of ubuntu 6.10 i'm trying. Ok, I installed ubuntu-desktop on my computer just now. The installation completed successfully. On reboot, the ubuntu logo appeared with the loading bar and after sometime the screen blanked around 5-6 times like it was changing video modes. After that, it provided with 2 pages of errors by the X server. After this the message 

"The X server has been disabled. Restart gdm when it is configured correctly." 

was displayed on the screen. I then pressed Ctrl+Alt+F1 which displayed 

"[17179820.860000] Out of Memory: Kill process 6613 (apport) score 109 and children.
 [17179820.860000] Out of Memory: Killed process 6613 (apport)."

and it wouldn't let me log on. I then pressed Ctrl+Alt+F2 and logged in with my username(aditya). On logging, the message

"-bash: /dev/null: Permission denied"

was continuously output on the screen till i intervened it by pressing Ctrl+c. I'm a linux newbie and was looking towards ubuntu to be a good and newbie friendly learning ground. I have tried installing 6.06 (2 different copies) and 6.10 (3 diferent copies). 6.06 used to boot after install only once and would give the same X server error as mentioned above on subsequent boots. 6.10 gives me the above errors. 2 other copies of 6.10 used to give me different errors on each boot so i guessed that my installation media might be bad and downloaded another copy of 6.10. I checked this particular copy by verifying md5 checksum and verified data on cd after burning it (in Nero). This is almost my 10th re-install and the hopes of learning linux seem to be fading by the moment. Does anyone know what should be done now?

NOTE: My system is Amd X2 3600+, Gigabyte GA-M51GM-S2G motherboard (nForce 430. It also has an onboard display which I've disabled through BIOS since I have an external card, 1 GB DDR2 RAM, Seagate SATA II 160 GB HDD, XFX GeForce 7300 GS. I also have WinXP installed on my computer. I do not know if information about my system would help but I provided it anyway...

go here and get envy [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) that will sort your graphics problem

---

