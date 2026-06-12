---
title: "Installation using windows installer went awry. Multiple versions on Ubutnu now?"
date: 2013-10-08
forum: Installation &amp; Upgrades
---

### Post by mike114 on 2013-10-08
Hi, I recently used the windows installer to add ubuntu. It installed (I believe) but for some reason it doesn't work. When I start up it gives me the option to boot into ubuntu or windows 7 but when I choose ubuntu it  hangs and kicks a bunch of killing sbin/modprobe commands. 
So, I decided to try again and install 13.04 using the USB instead. It worked fine, it seems. However, now when I boot, it goes to Grub, which gives me 2 "windows 7" loaders and others (listed below). One of the windows 7 loaders loads directly to windows (sda2) while the other (sda1) takes me to a  screen (the same one I had after using windows installer) and gives me the option to select Ubutnu or Windows 7. If I select sda1 then windows starts fine, but if I select Ubuntu then it it hangs up and does the same thing it used to (killing sbin/modprob). Are there two versions of Ubuntu installed? Can I get rid of one and how can I make grub so that it only gives me the option between windows and ubuntu? Thank you!!! 

grub on boot lists the following:
Ubuntu
Adv options for Ubuntu
Memory Test
Memory Test (...)
Windows 7 (loader /dev/sda1)
Windows 7 (loader /dev/sda2)
Windows Recovery env dev/sda/3

---

### Post by mastablasta on 2013-10-09
go into windows and uninstall ubuntu. windows installer is not supported anymore i believe.

---

### Post by oldfred on 2013-10-10
It sounds like you have Windows boot in sda1 and now in sda2. Your BCD in sda1 then has the extra entry for wubi, but the BCD in sda2 does not. Normal Windows installs boot from a hidden 100MB Boot partition that usually is sda1. Boot-Repair or other tools may backup boot files to main install as many users just delete the hidden partition as they do not know what it is.
You should be able to use Windows bcdedit to remove entry in BCD in sda1 if the uninstaller for wubi does not remove that.    

New install sounds like a full partitioned install.

---

