---
title: "got past the GRUB install and rebooted to command prompt - kernal"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by Yankees9920 on 2008-11-16
This is my first linux install and I had to do the alternative installation disk because I did not want to overwrite my MRB. After GRUB was installed it required a restart.

When the computer restarted, GRUB came up fine, and launched the Ubuntu 8.10 kernel. This prompted me for username and password, but now I do not know where to go from here.

I just see a prompt on the screen saying "ben@BenLaptopLinux:~$" and I need to finish the installation.

Thanks for you help!

---

### Post by Yankees9920 on 2008-11-16
I just tried booting to Windows XP Pro in GRUB and I got an error message "Error 21: Selected disk does not exist
Press any key to continue..."

---

### Post by Slipperyfish on 2008-11-16
Did the graphical login show up? Where it shows the Ubuntu logo?

or did you login with a black screen?

---

### Post by Yankees9920 on 2008-11-16
I logged in with the black screen, no graphical login showed up.

---

### Post by Yankees9920 on 2008-11-17
it launches in tty1 and I believe I want to switch it to tty7, but that does not work. Pressing Ctrl+Alt+ and number 1-6 works. But I am unable to press Ctrl+Alt+7 and get to tty7, which should have the graphical interface.

---

### Post by Yankees9920 on 2008-11-17
I was originally using the alternative installation which gave me errors when installing components. So I tried again using the regular installation disk and in the last step was able to select where I wanted GRUB installed, under advanced settings, and was able to choose (hd0,2).

---

