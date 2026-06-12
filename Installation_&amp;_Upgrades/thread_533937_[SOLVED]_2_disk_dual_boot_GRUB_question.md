---
title: "[SOLVED] 2 disk dual boot GRUB question"
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by Jeff4 on 2007-08-24
I installed Ubuntu 7.04 on a spare HDD with my Win2K drive removed. Then I installed both drives in the PC, and used the BIOS setup screen to dual boot. Can I now reconfigure GRUB on the Ubutu drive to be able to choose either drive to boot? Right now, I don't think that Ubuntu or GRUB are even aware of the existance of the Win2K drive. My Win2K drive is formated NTFS, would that be a problem? 
Thanks in advance, -Jeff.
P.S. I am a Ubuntu newbie. I was very impressed at how Ubuntu was able to recognise and provide drivers for all of my PC hardware. It was much easier than installing Win2K on the same machine, which did not recognize the graphics card or sound card.

---

### Post by oilchangeguy on 2007-08-24
how do you have the drives jumpered?

---

### Post by Jeff4 on 2007-08-24
Right now the Win2K drive is the master and the Ubuntu is the slave. (The BIOS setup page lets me select either one to boot.) However, I could always swap the drives if needed.

---

### Post by Pumalite on 2007-08-24
Post: sudo fdisk -l (small L)
cat /boot/grub/menu.lst

---

### Post by Jeff4 on 2007-08-24
I will try this as soon as I get home tonight.
Thank you very much. Its great Ubuntu has such a usefull and active forum.

---

### Post by oilchangeguy on 2007-08-24
> **Jeff4 said:**
> Right now the Win2K drive is the master and the Ubuntu is the slave. (The BIOS setup page lets me select either one to boot.) However, I could always swap the drives if needed.

not sure if this makes any difference. but i've got ubuntu on the master. and windows on slave. during the install of windows, and ubuntu, both were set to master (installed one at a time). then after the install, plugged in both drives. and jumpered as previously mentioned.

---

### Post by dulbirakan on 2007-08-24
You should edit menu.lst the following article might give you some tips:

[http://www.howtogeek.com/howto/ubuntu/reinst.....-out/]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/")

---

### Post by Jeff4 on 2007-08-27
Yes! All I had to do was add a line to /boot/grub/menu.lst. I added the noverify option to eliminate an error message. Now the dual boot works great. I had no idea it would be that simple. Thanks to everyone who replied for your help.
-Jeff

---

