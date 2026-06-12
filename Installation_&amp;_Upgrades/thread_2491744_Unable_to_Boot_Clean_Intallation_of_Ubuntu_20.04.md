---
title: "Unable to Boot Clean Intallation of Ubuntu 20.04"
date: 2023-10-19
forum: Installation &amp; Upgrades
---

### Post by Phillip35 on 2023-10-19
I have used Ubuntu 22.04 for months in my GA-EP45-DS4 computer but my hd4850 graphics card failed. It was replaced by an Nvidia 3050 card but I was no longer able to boot the computer. I do not have more than rudimentary Linux knowledge so, for expediency, I installed Ubuntu 18.04 from a DVD that was on hand. I could not, however, get the Nvidia card to communicate with the Nvidia driver. I would have preferred to install Ubuntu 22.04 again but have not been able to because the iso does not fit on a DVD and my computer refuses to boot from a USB stick despite my many attempts to implement suggestions in these fora. 

Fortunately Ubuntu 20.04 iso just fits on a DVD so I booted from it in live-session mode. The graphics card operated correctly so I installed Ubuntu 20.04 from the DVD in BIOS mode. The process went to completion and everything appeared normal and correct but the start-up boot was not successful. It resulted in a frozen screen and the messages, "4.1691431 systemd[1]: Failed to look up module alias 'autofs4': Function implemented", then "[UNSUPP] Starting of Arbitrary Exec Automount Point not supported", then "[ 5.449562] systemd[1]:Failed to start Load Kernel Modules" then [FAILED] Failed to start Load Kernel Modules". My hdd is GPT partitioned, the mbr on dev/sda1 has bios_grub flag and /dev/sda3 is the /boot partition. I subsequently tried another install, this time following the suggestion at #5 of [https://ubuntuforums.org/showthread.php?t=2462576](https://ubuntuforums.org/showthread.php?t=2462576), but had the same outcome.

I would be grateful for help.

---

### Post by readableauthor on 2023-10-19
You can try a more lightweight Ubuntu flavor. For example, Kubuntu 22.04.3 weighs 4.0GB

---

### Post by Phillip35 on 2023-10-21
Thank you readableauthor for your information on Kubuntu 22.04.3. My  main problem at present is to get my computer working and I now have  ubuntu 20.04 installed. It will not operate with the current kernel in  either normal or recovery mode but I have been able to run it with an  old kernel by first booting in recovery mode, removing nvidia packages  and then installing the old kernel in normal mode with the Nouveau  driver, but the monitor has the wrong resolution, single screen etc.  Looking on the bright side - my knowledge of linux is improving!

---

### Post by MAFoElffen on 2023-10-21
The Ubuntu 22.04.3 Server Edition installer Live ISO image is 3.4 GB. It will fit on a DVD.

Install that. Once you have it installed, then install tasksel, where you can install any desktop on top of that from a "menu"... 
```

sudo apt install task-sel

```
Or just install ubuntu-desktop directly
```

sudo apt install ubuntu-desktop

```
With an NVidia card, until you get the graphics drivers loaded, at the Grub boot, press the <E> key to enter the edit mode, <Arrow-Down> until you get to the mine that starts with "linux", go to the end of the line and add the word  "nomodeset". Then press the <Cntrl><X> keys to boot. Once you get the desktop installed and working, then start "Software & Updates" > "Additional Drivers" tab, then install the recommended driver.

I have a BlueRay drive on my workstation were I can burn Dual Layer DVD Discs with up to 8.5GB but the cost of the discs add up.

---

### Post by guiverc on 2023-10-21
It may help if you're specific with what you actually installed.

You mentioned Ubuntu 20.04 LTS, but not if Desktop or Server, nor if 20.04, 20.04.1, 20.04.2, ... 20.04.6 etc. as this provide extra details.

Ubuntu LTS releases offer kernel stack choices (GA which is default for Servers, and HWE which is better for new graphics cards & default for recent Desktop ISO; with other OEM stack options for some hardware too). The default stack is decided at install time by your installation media, though can be changed post-install too. Ubuntu *flavors* vary the default stack on ISO; 20.04 & 20.04.1 using GA, 20.04.2 & later using HWE; just as Ubuntu Desktop did before 20.04

Thus 20.04 media exists that contain the GA kernel of 5.4, the updated HWE stacks of 5.8 (20.04.2), 5.11 (20.04.3), 5.13 (20.04.4) & 5.15 (20.04.5 & later) which is what you used when you booted & installed, but **may not** be what you had post-install if internet was available & the system thus upgraded. Your details only mentioned the release & not product (Server, Desktop) or actual installation media used (20.04, 20.04.1, .... 20.04.6). If internet was **not**available during install, you won't have upgraded your stack (ie. *versions changed as I mentioned in this paragraph*), but the subsequent boot could also differ in that an OEM kernel was used (*if available on your installation media which wasn't stated*).

Sorry I don't know your problem & thus have no solution, but I also don't know what you installed (*Server/Desktop & ISO used*), nor if it was allowed to update (*internet was available*) and thus change occurred during first boot due to lack of detail. 

If kernel did change post-install (*upgrades applied*), you should be able to select the install kernel at boot using the grub menu.

---

### Post by Phillip35 on 2023-10-24
I have just read the advice and information offered by MAFoElffen and guiverc. I appreciate very much the time and knowledge that is required in addressing my problems. Unfortunately I was unaware of the posts until today because of internet unavailability however today I have been able to get ubuntu 20.04 running correctly with the new nvidia GeForce RTX 3050 graphics card by installing a liquorix kernel, nvidia-535 graphics driver and following the installation procedure detailed in [https://www.linuxcapable.com/install-nvidia-drivers-on-ubuntu-linux](https://www.linuxcapable.com/install-nvidia-drivers-on-ubuntu-linux). I will upgrade to 22.04 later when convenient. Thank you for your help.

---

