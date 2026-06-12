---
title: "Computer Hangs After Install"
date: 2005-11-11
forum: Installation &amp; Upgrades
---

### Post by level_jumping on 2005-11-11
Hi, i am having problems running ubuntu on my pc, ive searched these forums, tried various suggestions for problems similar to mine, but nothing has worked so far.

anyway, ive tried installing ubuntu 5.10 from the dvd but each time, the installation suceeds, the disc is ejected, the computer is restarted (all going fine....) then the packages are installed....the progress bar gets to 68% and then thats it. computer hangs. disks stop spinning, light stops flashing on my pc, nothing!

so i decided to try ubuntu 5.04. This INSTALLS fine, but when i get to the login screen. it hangs! mouse stops moving, just hangs! when i restart the computer, same again, get to the login screen (if im fast enough i can actually log in!) but then, liek clockwork, itll hang!

ive tried installing it on my second hard drive (20GB fujitsu), with XP on my Master drive (120G Maxtor).

im running a 512mb Ram AMD Athlon 64 3200, on a gigabyte K8NSPro motherboard. i have a speedtouch 330 ADSL USB Modem, microsoft intellimouse pro, and a logitech quickcam messenger in my USB ports (in case its something to do with my devices)

anyway, any help on getting ubuntu up and running will be appreciated. 5.04, or 5.10. whichever you think you know you can help me with!

---

### Post by Xian on 2005-11-11
[QUOTE=level_jumping]i decided to try ubuntu 5.04. This INSTALLS fine, but when i get to the login screen. it hangs! mouse stops moving, just hangs! when i restart the computer, same again, get to the login screen (if im fast enough i can actually log in!) but then, liek clockwork, itll hang![/QUOTE]
If when you get to this point you can still use the keyboard to move the cursor around the login screen I'd say you might need to add "acpi=off" to the kernel line in your menu.lst.

---

### Post by bonzodog on 2005-11-11
Have you tried booting the 64 bit live CD?
The speedtouch USB modem is going to be a problem as it requires drivers to get it working. Also, quickcam won't work without a lot of configuration.Try unplugging the modem - I suspect it's hanging because it's trying to get out on the net, and you need to get the drivers by some other method (maybe in windows), do a net-less install of breezy, get X up and working, then import the drivers for the modem.

Hope this might be of help.

---

### Post by level_jumping on 2005-11-11
[QUOTE=bonzodog]Try unplugging the modem - I suspect it's hanging because it's trying to get out on the net, and you need to get the drivers by some other method (maybe in windows)[/QUOTE]

i thought that worked, just unplugged it and there was no crash. but the next time i restarted, it was hanging again. modem still unplugged.

ill try a netless install of breezy. what do u mean by "netless"? i tried a server install before, and then installed the ubuntu-desktop, but that hung the system too.

[QUOTE=Xian]If when you get to this point you can still use the keyboard to move the cursor around the login screen I'd say you might need to add "acpi=off" to the kernel line in your menu.lst.[/QUOTE]

what does that do? and how do i do that with the system crashing on startup? i pretty much know nothing about linux.

---

### Post by Xian on 2005-11-11
[QUOTE=level_jumping]what does that do? and how do i do that with the system crashing on startup? i pretty much know nothing about linux.[/QUOTE]
It's just a parameter that you can pass along at boot. You can do this on just a trial run by highlighting the Ubuntu entry in the grub login menu, press 'e' to edit, add "acpi=off" [no quotes] to the the line which mentions the kernel, and then proceed with the boot process.

---

