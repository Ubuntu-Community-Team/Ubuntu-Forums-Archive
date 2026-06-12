---
title: "Ubuntu 12.04 LTS stops at splash screen on HP notebook"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by rjskoko on 2012-04-29
Hardware: HP Pavilion dv1000 notebook (model DV16010US) with 1 GB RAM
OS: Windows XP with Ubuntu Desktop 12.04 LTS Precise Pangolin installed as a second operating system using Windows installer wubi from [www.ubuntu.org](www.ubuntu.org).

**Problem: Boot freezes at splash screen.**
After completing the installation and booting the machine, selecting "Ubuntu" (versus Windows) at the Microsoft multiboot screen, the Ubuntu splash screen appears and the dots start to cycle for couple minutes, then they freeze. Keyboard is unresponsive. Power cycle was necessary to reboot.

Diagnosis: After rebooting and freezing a couple times, I selected the second Ubuntu boot option (recovery console) and watched the text messages scroll during the boot process. They stopped on a section with a message about visiting wireless.kernel.org.

**Apparent cause: Broadcom wireless firmware was not installed.**

Workaround: Install Broadcom firmware package.
Process: 
[LIST]
[*]Attach notebook to router using Ethernet RJ45 cable.
[*]Boot, select Ubuntu at Microsoft multiboot, type 'e' when GRUB screen appears (acting quickly to beat the timeouts).
[*]A screen appears where you can edit the GNU GRUB boot script for this single boot.
[*]On the "linux" line (second from bottom), add "**b43.blacklist=true**" to the end of the line.
[*]Type Ctrl-X or F10 to continue booting.
[*]Wait while notebook boots. Login with password set during install.
[*]Press Ctrl-Alt-T to get a terminal window.
[*]Enter the command: **sudo apt-get install firmware-b43-installer**
[*]Wait about 10 minutes while this package installs. Be patient--there will be periods of apparent inactivity.
[*]When the terminal window returns to the prompt, enter the command: **exit**. The terminal window closes.
[*]Use the session menu (gear and 1 icon) at the right of the top bar to shutdown.
[*]Disconnect Ethernet cable.
[*]Boot into Ubuntu. Log in.
[*]Configure wireless network (empty pie wedge on the top bar)--enter SSID, passphrase, and so forth (wireless configuration not covered here).
[/LIST]

---

### Post by qtpounder on 2012-05-04
> **rjskoko said:**
> Hardware: HP Pavilion dv1000 notebook (model DV16010US) with 1 GB RAM
OS: Windows XP with Ubuntu Desktop 12.04 LTS Precise Pangolin installed as a second operating system using Windows installer wubi from [www.ubuntu.org]("http://www.ubuntu.org").

**Problem: Boot freezes at splash screen.**
After completing the installation and booting the machine, selecting "Ubuntu" (versus Windows) at the Microsoft multiboot screen, the Ubuntu splash screen appears and the dots start to cycle for couple minutes, then they freeze. Keyboard is unresponsive. Power cycle was necessary to reboot.

Diagnosis: After rebooting and freezing a couple times, I selected the second Ubuntu boot option (recovery console) and watched the text messages scroll during the boot process. They stopped on a section with a message about visiting wireless.kernel.org.

**Apparent cause: Broadcom wireless firmware was not installed.**

Workaround: Install Broadcom firmware package.
Process: 
[LIST]
[*]Attach notebook to router using Ethernet RJ45 cable.
[*]Boot, select Ubuntu at Microsoft multiboot, type 'e' when GRUB screen appears (acting quickly to beat the timeouts).
[*]A screen appears where you can edit the GNU GRUB boot script for this single boot.
[*]On the "linux" line (second from bottom), add "**b43.blacklist=true**" to the end of the line.
[*]Type Ctrl-X or F10 to continue booting.
[*]Wait while notebook boots. Login with password set during install.
[*]Press Ctrl-Alt-T to get a terminal window.
[*]Enter the command: **sudo apt-get install firmware-b43-installer**
[*]Wait about 10 minutes while this package installs. Be patient--there will be periods of apparent inactivity.
[*]When the terminal window returns to the prompt, enter the command: **exit**. The terminal window closes.
[*]Use the session menu (gear and 1 icon) at the right of the top bar to shutdown.
[*]Disconnect Ethernet cable.
[*]Boot into Ubuntu. Log in.
[*]Configure wireless network (empty pie wedge on the top bar)--enter SSID, passphrase, and so forth (wireless configuration not covered here).
[/LIST]



rjskoko I want to thank you so much for posting this. I have been searching the Internet for almost a week now trying to find a fix. I am new to ubuntu but now prefer it over windows. Your post helped me fix my Compaq nx9600 with the same broadcom chip set. I followed your exact post above and if fixed my issue. I usually do not post on forums, but I felt you deserved the credit. Again thank you!

---

