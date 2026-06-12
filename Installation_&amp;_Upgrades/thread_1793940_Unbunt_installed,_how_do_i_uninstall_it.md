---
title: "Unbunt installed, how do i uninstall it ?"
date: 2011-06-30
forum: Installation &amp; Upgrades
---

### Post by bigvisnes on 2011-06-30
hi, wondering if anyone can help me with a litle problem i'm having with my laptop, i have installed Ubuntu and i want to go back to windows 7, but the laptop does not have a cd-rom. and i can't see the windows system in the boot menu, i have no idea on how to fix this so, if anyone could help me, it would be great :D

Thanks in advance

Sebastian Visnes aka Bigvisnes
[email]Sebastianvisnes@hotmail.com[/email]

---

### Post by YesWeCan on 2011-06-30
Windows7 and Ubuntu are installed on the same disk, right?

If so, the critical thing is to restore the MBR boot code so you can boot into Windows. Then, in Windows, you can just delete the Ubuntu partition(s) to free up space.

But first. The fact that Windows is not in your boot menu is a concern. Let's get that working so that you know Windows is bootable. Otherwise fixing the MBR will leave you unable to boot either.

In Ubuntu, run sudo update-grub and view the output and check it detects Windows. Then reboot and select and boot into Windows.

Then boot back into Ubuntu and install an MBR installer, Lilo.
sudo apt-get install lilo

Now check what the drive name is. You can look in Disk Utility or run sudo fdisk -l. It will probably be /dev/sda. Then use this command with the correct name to reinstall the MBR boot code.
sudo lilo -M /dev/sda mbr

Now when you reboot it should go straight into Windows.

---

### Post by mastablasta on 2011-06-30
first - do you have windows currently installed? if not then the above advice won't help a bit.
 
use this script and post the result here using code tags (the # icon) : [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
 
this will say how the OS is booting and also if there is anything else installed.
 
if you had windows 7 on a restore partition and you didn't back it up and then rewrote the whole disk during Ubuntu install then you're in trouble.

---

