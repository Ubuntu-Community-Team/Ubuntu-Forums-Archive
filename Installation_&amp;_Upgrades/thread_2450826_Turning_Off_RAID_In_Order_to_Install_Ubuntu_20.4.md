---
title: "Turning Off RAID In Order to Install Ubuntu 20.4"
date: 2020-09-21
forum: Installation &amp; Upgrades
---

### Post by jasona7783 on 2020-09-21
[COLOR=#000000][FONT=DejaVu Sans, sans-serif]Here is my story. I purchase an HP laptop that came preinstalled with Windows 10. I did not want Windows so I installed Kubuntu in which I am currently using version 20.4. I am having all sorts of problems and I am pretty convinced that they are isolated to Kubuntu. For example, I have 3 other Acer laptops that was also having the same problems plus some while running Kubuntu. I switched them to Ubuntu and they are running awesomely. All of those problems are now gone. I would like the same for my HP laptop. However, when I try to install Ubuntu, I get a message that the installer has detected that I have RAID devices and it cannot continue. It directed me to a support page which did not help. I looked in BIOS and I have two drives, one is just under 2 TB and the other is 14 GB. For both, it says that they are Non-RAID. To me that is confusing.[/FONT][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][FONT=DejaVu Sans, sans-serif]I tried contacting HP but that was a bust since they kept pushing me to use Windows and never would tell me how to fix it. So now I am coming in hopes that I can get some help. The model name of my laptop is HP Laptop 17-by0089cl. I used Ubuntu sometime ago for awhile and it was very nice. I had to briefly go to Windows 10 before now being on Kubuntu but I would just like to go back to Ubuntu and stay put.[/FONT][/COLOR]

---

### Post by Tony_Bennett on 2020-09-23
It could be you have M.2 Optane (16gb) acting as a Disk cache for the 2TB drive.

IF THIS IS THE CASE, you will have to disable Optane in Windows (using the Intel RST app),
reboot into Windows 10, instruct Windows to boot into safe mode, reboot into the 
BIOS/UEFI and turn your SATA drives from RAID or RST mode into AHCI mode.  
Then save and exit.  You should now be able run Ubuntu install.
This [LINK]("http://triplescomputers.com/blog/uncategorized/solution-switch-windows-10-from-raidide-to-ahci-operation/") gives a step by step instruction.

I recommend you first check your BIOS/UEFI to ensure you have an option to change to
AHCI.  I have seen some models of HP Laptops that DO NOT have that option, making
installing Ubuntu impossible.

---

