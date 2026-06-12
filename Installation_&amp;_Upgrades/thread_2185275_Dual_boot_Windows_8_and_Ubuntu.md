---
title: "Dual boot Windows 8 and Ubuntu"
date: 2013-11-01
forum: Installation &amp; Upgrades
---

### Post by dcorneli on 2013-11-01
I have just purchase a Lenovo G500S laptop with Windows 8 preinstalled. I am new to Linux based operating systems and I’m attempting to make it a dual boot system with Ubuntu.

I have backed up my Windows partitions, shrank the window partition, turned off fast boot and disabled secure boot.

I then created an image file of Ubuntu v13.10 and attempted to install it. I was presented with the install menu options and selected to install Ubuntu. The disk spun for a while, and then nothing, I attempted the same with v12.04 and got the same results.

I would appreciate anyone that may have some helpful hints.

Thank you in advance.

---

### Post by craig10x on 2013-11-01
First try going in to the live session (that would be where it asks if you want to TRY ubuntu)....see if that works ok....if it does, then go to the icon on the unity dock (toward the top) where it says "install ubuntu" and then select that and see what happens....if you still have a problem installing, i'm sure some help will be along shortly...I'd try that with 13.10 first...

---

### Post by syam-nair on 2013-11-02
check for disk errors ad try again, or perhaps you can try live mode first and then install. And btw you may turn on secure boot, if you can add dual option into your windows bcd, you can easily do this using using easybcd (there is a free version) from windows.

---

### Post by coffeecat on 2013-11-02
Not an Ubuntu, Linux & OS Chat thread.

*Thread moved to **Installation & Upgrades**.*

---

### Post by dcorneli on 2013-11-04
Thank you all for the advice. Part of the problem turned out to be somewhat embarasing which is that when the Ubuntu installation program fires up on my Lenovo G500s Touch, the screen settings are somehow automaticly set to the darkest setting. So you have to adust the brightness setting every time you attempt to boot Ubuntu or Ubuntu Install! That fixed th Ubuntu boot problem.

However after getting Ubuntu to successfully boot, Windows 8 would no longer boot up claiming "**No such device: CAD28DB1D28DA1F5**"

I have finally resolved the problem by entering the bios set-up utility every time I boot and either set the Boot Mode to **UEFI** for Windows or Boot Mode to **Legacy Support** and Boot Priority to **Legacy First** for Ubuntu.

This is less than an ideal solution but it seems to work until I can figure something else out.

Once again thanks for all the help!

---

### Post by oldfred on 2013-11-06
If your system boots with secure boot off and boots something other than just the Windows efi file then you can use Boot-Repair to convert a BIOS install to a UEFI install. 
Some systems only boot the Windows efi file, but Boot-Repair also has a work around to make UEFI think it is booting Windows when it really is booting grub2's shim file by renaming files.

Best to boot live installer in UEFI mode to get Boot-Repair to update.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

This shows the purple screen you get with a BIOS boot of installer and the grub menu with black background you get with UEFI boot.

 Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Some other lenovo, may be similar issues?
 Lenovo Ideapad Y500 LiveUSB Problem, also brightness
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)

---

