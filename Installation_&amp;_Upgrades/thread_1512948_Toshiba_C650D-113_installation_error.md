---
title: "Toshiba C650D-113 installation error"
date: 2010-06-18
forum: Installation &amp; Upgrades
---

### Post by Tricast on 2010-06-18
When i try to boot 10.04 from cd/usb it halts almost immediately with console line: "[0.441335] [<C0104087>] kernel.thread helper+0x7/0x10".

The specs:

AMD V120 cpu
HD 4200 gpu
320 GB HD
2 GB DDR3


How can i fix this? Please help.

---

### Post by VincentTucker on 2010-06-23
Press Esc on the purple screen. F6, then press enter on acpi=off.

---

### Post by Tricast on 2010-06-27
Thanks for the help! I returned it though because of a hardware display defect.

---

### Post by bcooperb on 2010-08-15
I have this same problem with a Toshiba

kernel.thread helper+0x7/0x10

hangs there when I am booting off a 10.04 USB drive. I am trying to do a clean install. Currently has Win7 on it. This is a brand new computer. I was able to get to the Memory test one time and run the full test. Everything seemed to pass ok.

What does pressing F6 allow me to do? Can anyone explain this in a little more detail?

thanks!

---

### Post by gigi8 on 2010-10-29
Thanks VincentTucker. I have been looking for this answer for 2 days and it works like a dream. Things are really easy when you know what to do.

---

### Post by cubiks on 2010-11-16
What can I do if I get that error on boot ?

Edit: I have a Toshiba Satellite Pro, core i5 and I've just finished installing Ubuntu 10.10, after turning acpi=off as suggested because used to get same error when trying to install. Now the installation is finished and on boot "kernel.thread helper..". How do I get passed this ?

Thanks

---

### Post by cubiks on 2010-12-06
I have updated Bios to the latest version and that fixed it!

---

### Post by bejazzy on 2010-12-20
Hi everyone !

I have the same problem as you with a Toshiba Satellite L655 and I don't knwo how I can update BIOS. Do you have web links or Tips&Trick about that?

My only solution: turn off acpi (1) before installation, (2) before first restart thanks to GRUB configuration file editing and (3) edit the GRUB configuration file under Ubuntu.

I used an Ubuntu 10.10 64bits LiveCD.

(1) Before installation: F6 and tick ACPI=off as **VincentTucker** said.

(2) First restart. ESC after the Toshiba message. You can change the available linux kernel versions or start with the recovery mode. You can aslo change the GRUB configuration file temporarily. Edit it and write "acpi=off" in the line which looks like
```
linux   /boot/linux-kernel-version root=UUID=hex_message ro  splash quiet
```For instance, you can write:
```
linux   /boot/linux-kernel-version root=UUID=hex_message ro  splash quiet acpi=off
```quit and boot --- CTRL-X or CTRL-C I think.

(3) Under Ubuntu, to fix the problem, edit the file /etc/default/grub
```
sudo gedit /etc/default/grub
```and write "acpi=off" into the variable GRUB_CMDLINE_LINUX=""
```
GRUB_CMDLINE_LINUX="acpi=off"
```Then, update the GRUB configuration file with ```
sudo update-grub
``` acpi is turned off.

Unfortunately, the power management is not efficient. So, I would like to know how I can fix the problem without setting acpi=off.

---

### Post by cubiks on 2010-12-20
You can find an updated version for you laptop on toshiba's site. I also had windows installed so I've downloaded an exe version of the setup which steps were pretty much intuitive. Then rebooted and voila !
The acpi off thingie is not really a solution, means no power management - my laptop would overheat and would not last 3 seconds unplugged.

hope this helps,
cheers

---

### Post by bejazzy on 2010-12-21
My updating BIOS solutions:

  - I can install my old and dusty Vista with a dual boot and follow this "How To" [http://aps2.toshiba-tro.de/kb0/HTD9502M10000R01.htm](http://aps2.toshiba-tro.de/kb0/HTD9502M10000R01.htm) 
My Ubuntu installation is recent and the hard drive is empty, so I think it should be easy & fast.

  - If you don't have any Win*** OS, use FreeDOS with a USB flash drive or a LiveCD. See [http://www.freedos.org/](http://www.freedos.org/) 
Download the specific BIOS ([http://eu.computers.toshiba-europe.com/innovation/download_bios.jsp](http://eu.computers.toshiba-europe.com/innovation/download_bios.jsp)) and copy the *.EXE on your USB flash drive. Boot on FreeDOS, go to the USB flash drive directory (with DOS commands) and execute the *.EXE
You should read [http://liquidat.wordpress.com/2007/05/20/howto-update-bios-on-linux/](http://liquidat.wordpress.com/2007/05/20/howto-update-bios-on-linux/) and  [http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)

I think I'll choose the first one even if I don't want to reinstall Win***. It seems more safety.

Bye

---

### Post by bejazzy on 2010-12-22
Hi !

I solved my ACPI problem yesterday. I quickly installed Windows Vista, which had very big text & icons and which was not able to get the Internet because of uninstalled drivers. I launched BIOS.EXE previously downloaded from the Toshiba website. BIOS was updated. Then, I reinstalled Ubuntu 10.10 and everything is fine !

Cheers

---

### Post by Gipnokote on 2011-01-10
Hi All

I have a Toshiba T130 with the latest (v. 2.70 from 10.08.2010) BIOS update and it doesn't help this problem :(

This thread helper error emerged after installation of 10.10, 10.04 worked fine before.

Same situation: acpi=off helps but I don't like that. Memory test before booting helps but only once. I have to run it again before each boot.

Solutions or ideas would be highly appreciated. Maybe it's worth to write to Toshiba's support?

---

