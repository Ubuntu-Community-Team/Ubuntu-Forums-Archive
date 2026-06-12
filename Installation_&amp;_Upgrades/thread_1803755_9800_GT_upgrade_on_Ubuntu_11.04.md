---
title: "9800 GT upgrade on Ubuntu 11.04"
date: 2011-07-13
forum: Installation &amp; Upgrades
---

### Post by gatordude on 2011-07-13
I got my 9800 Gt today and went to install in in my 11.04 machine. I connected both of my monitors to the new card and on first power-up I went into the bios and disabled the on-board graphics. I then saved and PC rebooted. During Ubuntu load my machine keeps freezing. First two times it froze on reading battery state and then the last time it froze it said stopping backsplash. I rebooted again after connecting to the on-board graphics and enabling in the bios and it still freezes. I had to remove the 9800 GT to get my pc to run.

PLease dont tell me  have to do a fresh install.

All help would be appreciated.

---

### Post by gatordude on 2011-07-14
OK,
I fixed my problem and here is what I did.

If you are going from ATI to Nvidia before you install anything deactivate the ATI driver, then install Start up manager "sudo apt-get install startupmanager"
 
Launch the Startup Manager from "System>-Administration->Startup-Manager"
In the "Boot options" tab, change the resolution to something your monitor can handle (1024x768 is usually enough for the boot screen to look nice).
Change the color depth to "24 bits" and Press the "Close" button. Power down your PC and install your new Nvidia graphics card and power up your pc. If your lucky like I was your PC will boot into 11.04 then go into the hardware drivers and activate Nvidia then restart and adjust to your preferences.

Here is the page I used for fixing my problem.
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

