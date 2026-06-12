---
title: "Empty security header after ubuntu 12.10 gnome 64bit"
date: 2013-03-22
forum: Installation &amp; Upgrades
---

### Post by unconcrete on 2013-03-22
Hi all,
I have problems in dual booting ubuntu with windows 8 since two months without success.
My computer has probably gone crazy because of the series of os uninstall and reinstall. By misfortune and/or by my fault, in my former threads I've asked what to do to dual boot both win and ubuntu and how to install properly grub2. At first I've installed Precise, after Quantal. Until now Win 8 was avalaible in my /dev/sda5. Grom gparted I see that sda5 already exists with irs files and programs. But is no more avalaible.

I'd like to make a new installation of win 8 from the cd I've bought, but the system refuse to install.
 It claims for misterious drivers for my hard drive. I've never heard something so. Then I've tried another way.

I've tried to install 12.10 with gnome desktop without disable secure boot. Actually ubuntu has been installed but I've lost Windows 8. Only ubuntu now works. Grub has been installed in /dev/sda1 that is the partition Dell has created for an UEFI computer. At reboot Grub doesn't start and the computer go to ubuntu directly. 
Moreover my headache is worsen by another problem.
 At reboot, my DELL xps 8500 warns me as follows:"empty security header". Is something relaed to secure boot? Anyway I haven't disabled security boot. Very strange for me. Very little info in the internet about "empty security header". Some news concerning email, html and documents not to the system setup.
What does it mean that warning? And also, how to recover the security header (if possible)?
Please help.

If it can be useful, this my bootlog of boot-repair: 
[http://paste.ubuntu.com/5637627/](http://paste.ubuntu.com/5637627/)
Bye soon.
unconcrete

---

