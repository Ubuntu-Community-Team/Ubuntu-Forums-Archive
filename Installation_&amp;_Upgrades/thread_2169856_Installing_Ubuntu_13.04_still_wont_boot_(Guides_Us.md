---
title: "Installing Ubuntu 13.04 still wont boot (Guides Useless)"
date: 2013-08-23
forum: Installation &amp; Upgrades
---

### Post by MJ_Nale on 2013-08-23
I have been trying to install 13.04 and it does not boot. I can boot into Windows 7 just fine. I have tried everything ( along side windows, something else with swap and primary) I have read everything I can and nothing works (EasyBCD fails) (Boot repair disk fails) I need help here is my pastebin [http://paste.ubuntu.com/6019478/](http://paste.ubuntu.com/6019478/)

I am using an Asus u36s

---

### Post by Quackers on 2013-08-23
Did you run the recommended repair from that utility? You have something odd in the MBR of the drive. Grub should be there but it's not.

---

### Post by MJ_Nale on 2013-08-24
As I said boot repair failed yes I ran the recommended repair it ask me to Run some sudo chroot commands to sda4 but when I open xterm in boot repair and tried to copy and paste the recommended commands it would not let me. I keep reading and trying everything nothing works.

---

### Post by MJ_Nale on 2013-08-25
PLEASE HELP "" I spent two days trying to get grub installed. I've tried boot repair which does not work it has me use sudo chroot command lines that doesn't work. If I try to update the grub from live CD it does not work either. I've created a swap and primary partition and no matter what I do it does not work can someone please look at my paste.bin or give me some ideas. ( Note everything I have tried from searching Ubuntu forums seems to fail) it is like grub is not there. My Ubuntu installation is but it will not boot. I do not want to use WUBI because I need more than 30gb. I never had any trouble before but this Asus u36s is got me at a loss

---

### Post by Quackers on 2013-08-25
Firstly try the quick way to install grub.
Boot from the live cd/usb and select try ubuntu.
When the desktop loads open up a terminal and enter ```
sudo mount /dev/sda4 /mnt
```
Then enter ```
sudo grub-install --root-directory=/mnt /dev/sda
```
If that completes ok reboot and take the cd/usb out.

All the above should be copy/pasted into the terminal window as this will stop typing errors.

The system should now boot into your Ubuntu installation. If it does open up a terminal and run ```
sudo update-grub
``` and watch to make sure that the Windows menu entries are picked up. If they are please reboot and try to boot Windows from the grub menu.
If that works everything is ok. If not get back to us.

---

