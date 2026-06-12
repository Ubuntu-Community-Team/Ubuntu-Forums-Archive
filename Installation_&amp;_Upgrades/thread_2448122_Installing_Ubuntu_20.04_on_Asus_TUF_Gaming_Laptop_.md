---
title: "Installing Ubuntu 20.04 on Asus TUF Gaming Laptop FA5061H"
date: 2020-08-02
forum: Installation &amp; Upgrades
---

### Post by Hewjr100 on 2020-08-02
I can install Ubuntu 20.04 on this new laptop with Mini Iso, but when booting up all I get is xxxx_acpi and a blinking cursor.

Ryzen 5 4700/4800 Radeon graphics, GTX 1650, 16 GB ram, I upgraded from 8, 6 cores and 6 threads.

Can anyone with similar system guide me thru setting up Ubuntu.  Currently back on Windows 10 via Macrium image backup.

Henry

---

### Post by ubfan1 on 2020-08-02
First check your machine's firmware version with HP and update to the latest.  Booting takes the "nomodeset" keyword edited into the grub line starting with "linux" at the "quiet splash" words, At first successful boot, sudo apt-get update and check for Nvidia proprietary drivers -- run Software and Updates, Additional Drivers tab, and select the latest "tested" Nvidia driver.  That may fix the boot problems, but if not, acpi=0 (another linux boot option) may be the start for selecting more specific acpi options which won't degrade the system as much.

---

### Post by Hewjr100 on 2020-08-02
Gotcha, FYI this is a new Asus TUF Gaming laptop.  I need to edit my signature.

Henry

---

### Post by Hewjr100 on 2020-08-03
Got it going, but diasbling secure is not my favorite idea.  BTW Ubuntu 20.10 is still using Nvidia 440.  It's not the best, when scrolling down web pages it ripples and tears.  I hope they update Nvidia drivers for Groovy.

Henry

---

### Post by ubfan1 on 2020-08-03
The graphics-drivers ppa does list an nvidia 450 driver.  Maybe try that one.What exactly did you do to get things working? I guess you could leave secure boot on if you sign the kernels yourself, but I've never had to do that (no secure boot on my UEFI machine with Nvidia).

---

### Post by Hewjr100 on 2020-08-08
Just had to disable secure boot in Bios.  Noticed if I disabled fast boot I would get Ubuntu logo, with fast boot no logo.  With secure boot disabled Ubuntu 20.04.1 install media installed Nvidia 440 by default.

Henry

---

### Post by CelticWarrior on 2020-08-15
Add the [Graphics Drivers PPA]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa") and then you can install 450. You can just select it at Additional Drivers. It's that simple.

If you still experience screen tearing with the Nvidia card that typically can be solved by enabling the "Force full redraw" setting in Nvidia X Server Settings.

---

### Post by Hewjr100 on 2020-08-15
Changan, gonna try the ppa, but I noticed that Nvidia settings app does not start, jsut gives the option to exit.

Henry

---

### Post by CelticWarrior on 2020-08-15
> [COLOR=#000000]Nvidia settings app does not start[/COLOR]

Not good. If you don't disable Secure Boot -or- manually sign the Nvidia drivers they won't load and Nvidia X Server Settings will give all sorts of errors.

---

### Post by Hewjr100 on 2020-08-15
Got it working.  All systems are a go.

Henry

---

### Post by Hewjr100 on 2020-08-18
CHANGMAN, where can I find Nvidia X Server Settings, it's noe in the Nvidia settings app.

Henry

---

### Post by CelticWarrior on 2020-08-18
The Nvidia X Server Settings *is* the settings app.

---

