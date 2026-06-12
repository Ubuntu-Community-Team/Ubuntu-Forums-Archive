---
title: "Asus Infinity TF700T"
date: 2013-02-21
forum: Installation &amp; Upgrades
---

### Post by ftwlol on 2013-02-21
Hi!

how can i install ubuntu 12.10 on my Asus Infinity TF700T ?

---

### Post by ellishgibbons on 2013-02-21
> **ftwlol said:**
> Hi!

how can i install ubuntu 12.10 on my Asus Infinity TF700T ?
[LEFT][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Step by step process for install ubuntu 12.10 on my Asus Infinity TF700T[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Step 1: Download these files and save them into your computer: [COLOR=#336699]tf700-rootfs-0.7.1.tar.lzma[/COLOR] (667Mb) and [COLOR=#336699]boot_installer-0.7.1.1.zip[/COLOR] (11 Mb). Just put them in a directory you can easily find and access; there’s no need to extract them.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Step 2: Connect your device to your computer using the USB cable and copy the packages into the root directory of the device’s internal memory. After that disconnect your device and turn it off.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Step 3: Boot it into recovery mode and flash *boot_installer-0.7.1.1.zip* . You need to choose a kernel at this point. While all of them are supposed to work, the most recommended is 1.3-1.8.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Step 4: Once the installation is complete, wipe cache/dalvik.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Step 5: Turn your device off again but this time connect the keyboard dock and boot it into recovery mode. Since you have just installed a new boot loader, you must be seeing penguins while the device loads. After a short while, you will see four options: Android, Linux, Install and Shell.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Step 6: You still need to install so choose press “I” on your keyboard. The device automatically searches for *tf700-rootfs-0.7.1.tar.lzma*. You need to choose the Ubuntu image size and press “Yes” to confirm.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Step 7: It will take several minutes to complete the installation process. Refrain from touching anything on your device until everything is done to avoid messing up the process.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Step 8: Once the installation is complete, press any key on your keyboard to return to boot options. Press “1&#8243; to boot Ubuntu 12.10; the default password is “ubuntu” but you have to change it to your own password for security reason.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]This is just one of the ways to install Ubuntu on Pad Infinity TF700. We advise you to visit [COLOR=#336699]XDA devs forums[/COLOR] to learn other ways to flash this custom OS.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR][/LEFT]

---

### Post by ftwlol on 2013-02-21
THX. if it fail do you know how to factory restore

---

