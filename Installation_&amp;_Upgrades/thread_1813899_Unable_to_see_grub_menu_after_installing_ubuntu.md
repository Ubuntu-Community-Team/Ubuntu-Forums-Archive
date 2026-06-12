---
title: "Unable to see grub menu after installing ubuntu"
date: 2011-07-28
forum: Installation &amp; Upgrades
---

### Post by ktp.kti on 2011-07-28
I installed Ubuntu 11.04 (x64) today. I use an LG LCD monitor. After installation, I am unable to see the grub menu. I get a 'D-sub out of range 92.5 kHz / 58 Hz' message on screen instead of grub menu. I know the grub menu is there because, by pressing the 'down' button 5 times and then the 'enter' button I am able to select the windows loader. If I select nothing I am able to log into ubuntu without any display problem.

Please advise me what to do...:(

---

### Post by plusnplus on 2011-07-28
hi.., 
if you press down button 5 times, then go to windows, maybe the second will be the recovery mode.
please choose the second. if you can go to recovery mode, choose again start with low resolution mode.
if you can login use low resolution mode, click hardware driver, then it will promp you graphic card driver, just activate it (download)

that what i did when i have similar problem.
I can see the grub, but after choose the normal mode, only blank screen.
Hope it help

---

### Post by ktp.kti on 2011-07-30
:-( Unable to log into recovery mode. What to do now?
It's really annoying dealing with a hidden grub!

---

### Post by dino99 on 2011-07-30
hidden grub menu is the default config for single OS; to see it you need to hold "shift" key down at bios end process

there if you select the second line (recovery mode) then you can select "repair packages" to fix some issues

or edit the boot line to either "remove splash" or "add other parameter like nomodeset/noacpi/..."

---

### Post by ktp.kti on 2011-07-30
Shift key did not work. 

My problem is that grub is there but there is a display issue with the LG monitor. I use dual boot with windows 7.

The display problem occurs only with grub but not after logging into ubuntu (Unity)

---

### Post by ktp.kti on 2011-07-30
Yipee!!!!!!!!! Did it!!!!!!! :D

I went to the folder, file system/etc/default. There, i opened the 'grub' file (which is a text file, which can be opened with gedit, which is the default text editor for ubuntu). Then, i uncommented (i.e removed the # in front of the command) #GRUB_GFXMODE=640x480. This activated this command.

But for editing this file, you have to be the root user (i.e administrator). To temporarily elevate yourself to this privelege type this on your terminal (without the quotation marks) "gksudo gedit /etc/default/grub" (don't forget to leave a space between gedit and /etc) and press enter. Give your user account password if prompted. The file will open and you can edit it. (Do not try to login as the root user. You might mess up with important files!)

After editing the file run "sudo update-grub" on the terminal. Then restart your computer. That's all.

---

