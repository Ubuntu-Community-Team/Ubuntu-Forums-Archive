---
title: "Ubuntu 18.04 only boots in recovery mode on Gigabyte motherboard"
date: 2018-06-29
forum: Installation &amp; Upgrades
---

### Post by danielixo on 2018-06-29
I have a brand new computer
Gigabyte H310M S2H
Intel i3-8100
4gb ram

When installing grub fails to install.
And "Try Ubuntu" cannot boot at all

The only way to install was through the OEM installation, but then I can only start in recovery mode, and click resume to come to desktop.
It would also give me a lot of errors every time i boot, and no hacks that i found seems to work.

---

### Post by danielixo on 2018-06-29
After browsing a lot of forum topics i found a solution by making combinations of the different threads i found:

1. edit the startup options of "Try Ubuntu" by holding shift while booting, and click "e" while on Try Ubuntu option
add the following to the line that starts with linux:```
nomodeset acpi=off
```
2. run the installer when inside ubuntu.
3. Add a EFI partition of 500mb (without this grub will not be able to install itself)
4. When ubuntu is installed, open a terminal and edit the gub settings```
sudo nano /etc/default/grub
```
look for the line that says: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
add the following inside the quotes, and save the file with ctrl-x ```
nomodeset acpi=off
```
5. Update grub by typing: ```
sudo update-grub
```
6. update and upgrade the system: ```
sudo apt-get update && sudo apt-get upgrade
```
7. Reboot

---

