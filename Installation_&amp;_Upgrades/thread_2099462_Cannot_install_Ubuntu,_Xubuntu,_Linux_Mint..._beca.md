---
title: "Cannot install Ubuntu, Xubuntu, Linux Mint... because of nouveau drivers"
date: 2012-12-29
forum: Installation &amp; Upgrades
---

### Post by GiGaZ on 2012-12-29
Hello everyone!

I wanted to start developing and porting Android, but I came to a problem.

My problem is that every time I want to install any distribution of Linux on my PC, the problem with Nouveau drivers occurs (I think that it is problem with the drivers, because on my old PC with Intel graphic everything works OK).

The system shows a desktop for a couple of seconds and then the graphical interface stops and command line shows the following messages:
[IMG]http://dl.dropbox.com/u/15803997/Ubuntu/DSC_0230.JPG[/IMG]

I was also able to get the log file:
[Xorg.0.log]("http://dl.dropbox.com/u/15803997/Ubuntu/Xorg.0.log")

My PC has:
GPU: Nvidia MSI GTX 580
CPU: Intel i7 2600K
MB: AsRock Fatal1ty P67 Professional
RAM: Crucial 1333Mhz 8GB

Is there a way to install Ubuntu or other Linux distro without nouveau drivers or do I need to wait until this is fixed by Linux kernel.

Thank you for your answers,
Ziga

---

### Post by Bashing-om on 2012-12-29
GiGaZ; Hi ! Welcome to the forum.

My suggestion: try to boot with the "nomodeset" option at the grub menu:(disables kernel mode setting)
Depress the shift key soon as bios screen clears ->grub menu:
"e"key to enter edit mode ->arrow down to the kernel boot line ('buntu versions have quiet splash in this line) arrow across to that term and insert "nomodeset" -without the quotes- in this line; -> ctl-x to continue to boot.
Once into the desktop, choose Additional Drivers and install the recommended driver.
Detailed instructions:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by GiGaZ on 2012-12-29
Thank you very much for your quick response :p

My problem was now fixed by your suggestion and now I can start learning Linux OS more seriously because my old computer with Linux lags too much.

Thank you again!

---

### Post by Bashing-om on 2012-12-29
Hey, Glad I could help. Keep learning and soon you will pay-it-forward.
Please mark this thread as solved (thread tools). This aides others in seeking solutions and saves helper's time in not looking at a solved situation.


[INDENT]happy 'buntu'n <== BDQ

[/INDENT]

---

