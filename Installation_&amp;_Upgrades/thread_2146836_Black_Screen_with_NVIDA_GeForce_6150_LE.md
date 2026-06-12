---
title: "Black Screen with NVIDA GeForce 6150 LE"
date: 2013-05-19
forum: Installation &amp; Upgrades
---

### Post by JohnMorrow on 2013-05-19
Hello:

I've done a clean install of LinuxMint 13 MATE, which is based upon 12.04 Precise, and I can't get any proprietary drivers to work properly. The system works reasonably well with the default open-source driver with "nomodeset" added to the grub command line. If I install any of the proprietary drivers using the "Additional Drivers" tool, the system will boot to a black screen. I can boot to a command line using LM13's "recovery mode". I have been using LinuxMint 9, which is based upon Ubuntu 10.04 for years and love it, but it is now EOL. I am doing this on a HP Pavilion a1632x desktop, which uses and AMD Athlon processor. The system has 3GB of RAM. The Additional Drivers tool offers up the (version current) [Recommended] driver, which doesn't work, the version 173, which works on LM9 but not on LM13, and an updated version of 173, which doesn't work on LM13, so I'm stumped. I'm including some screen caps from LM9 so you can see what DOES work.[ATTACH=CONFIG]242793[/ATTACH][ATTACH=CONFIG]242794[/ATTACH][ATTACH=CONFIG]242795[/ATTACH][ATTACH=CONFIG]242796[/ATTACH]

---

### Post by JohnMorrow on 2013-05-26
After another clean install, running the update manager and applying all updates, then NOT attempting to use the "Additional Drivers" tool, I found the fix in the "sticky post" titled "Thread: Graphics Resolution- Upgrade /Blank Screen after reboot" at the top of this forum. Searched for "NVIDIA", and on the second hit found a section quoted below (command numbers added).
-------begin quote-------------------------------------------------------------------------------------------
Notes about nvidia cards and SLI
The "nomodeset" kernel bootline switch usually works for most nVidia cards, but now all.

Especially for nvidia cards, I usually just into a text mode by going to a text console via grub edit ('e") append " text " to the end of the kernel boot line and boot{"ctrl-x') and after a login type
Code:

(1) sudo apt-get update
(2) sudo nvidia-installer --uninstall
(3) sudo apt-get remove nvidia-*
(4) sudo apt-get install linux-headers-'uname -r'
(5) sudo apt-get install nvidia-current  
(6) sudo nvidia-xconfig
(7) sudo apt-get update
-----------------------------end quote----------------------------------------------------

Note that in my case, not all of these commands worked. For command (2), the reply was something like "command:nivida-installer not found". After the second command failed, I started Synaptic, searched for Nvidia, and only found "nvidia-common" installed, which is a tool for finding obsolete drivers. So I skipped command (3). Command (4) returned something along the lines that I already had current headers installed. I then executed commands (5), (6), and (7), which completed with some error messages which appeard to be normal. After a reboot, I started the "Addtional Drivers" tool which now showed "Nvidia-current" driver installed and activated. Web pages are now rendering correctly, which is all I was after. So from where I sit, there appears to be a bug in the LM/Ubuntu "Addtional Drivers" tool. Will mark SOLVED.

---

