---
title: "Installing Windows on Second Hard drive"
date: 2020-04-23
forum: Installation &amp; Upgrades
---

### Post by mhguy22 on 2020-04-23
Right now, I have ubuntu on my main hard drive but I want to install windows on this other hard drive I have that is 500gb big. I have no idea how to do this, can anyone help? I already have a bootable windows usb by the way 
Any help is appreciated.

Thanks.

---

### Post by rpessoa on 2020-04-23
The way I did (I am sure there must be better ways) on my _**desktop**_ was to install Linux on my SSD1. Then I took the SSD1 out and installed my SSD2. Then I installed Windows on this SSD2.

After having two SSDs (SSD1 and SSD2) with different OSs, I installed both SSDs on my desktop&#347; motherboard.

So, when I want to play games, I enter my boot and chose to boot from my SSD2 that contains the Windows. I only use Windows for games.

After playing, I restart the system, I enter the boot setup, change the boot order and restart with my SSD1 that has Linux.

Since I only play occasionally, my boot is always setup for Linux. 

As I said, maybe not the best solution but no other worked here. Honestly, it takes me less than a minute to change OSs. :) I have this setup for more than an year now and no problem with Windows 10 updates, Linux etc... :)

---

### Post by CelticWarrior on 2020-04-23
The first question is, as always, BIOS or UEFI?

---

### Post by mhguy22 on 2020-04-23
Bios.

---

### Post by mhguy22 on 2020-04-23
to be honest i was going to try rpessoa's methodbut i wasnt sure if it would work.

---

### Post by CelticWarrior on 2020-04-23
> **mhguy22 said:**
> Bios.

So, as suggested above, remove the drive with Ubuntu or temporarily disable it in BIOS. Also make sure the drive where Windows is to be installed is the first boot priority.
Install Windows.
Reconnect or re-enable the other one, change the boot order again to the drive with Ubuntu. At this point it should boot Ubuntu as usual, without an option to boot Windows. Then just run 'sudo update-grub' which should now detect Windows as well and add it to the Grub menu, allowing for dual-boot from that menu.

If something happens to Ubuntu you should be able to boot Windows directly simply by changing the boot order to the Windows drive.

---

### Post by mhguy22 on 2020-04-23
Okay, I'm going to try this. Thanks a lot!

---

### Post by yancek on 2020-04-23
One thing I would do is that after the install of windows, reboot to verify that there were no problems with the install and it does boot, then connect the Ubuntu drive and boot from it and update-grub to include windows.  If there is a problem with the windows install, you will know.  If there are problems later, you know that you can boot windows from the BIOS.  If you don't test this first, you may think there is a problem with Grub when it is actually a problem with the windows bootloader..

---

### Post by mhguy22 on 2020-04-24
Okay, thanks

---

### Post by mhguy22 on 2020-04-25
Looks like it worked. Thanks a million guys!

---

