---
title: "boot Ubuntu in second SATA using Win XP GRLDR"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by mohanradhakrishnan on 2010-05-30
Hi,
I have GRLDR configured in C:\boot.ini in Windows XP in the first SATA drive. Now I also have Ubuntu in the second SATA.
 
I have two options.
 
1. Switch the SATA drives so that the Ubuntu SATA is the primary boot drive. Use grub to boot Windows XP from there.
 
2. Boot Win XP which shows the GRUB menu of GRLDR. Choose the ubuntu boot menu so that it can detect the second SATA and boot Ubuntu.
 
How can I set up the second option ? I know that everyone might recommend option 1 but I want to learn if it is possible or not.
 
 
Thanks,
Mohan

---

### Post by oldfred on 2010-05-30
I do not know about grub4dos. 

But you can install Ubuntu's grub to sdb and in BIOS or one time boot key select to boot sdb. You can leave grub4dos in sda.

It may be easier to install grub to sdb and add a chainboot entry in grub4dos to sdb. If it is like old grub chainboot entries are relatively easy to add, but have to link to another boot loader in either the MBR or PBR partition boot sector.

Old grub entry to chainboot. May be similar for grub4dos. Requires grub in sdb's MBR.
title       Ubuntu  @ sdb
root        (hd1)
chainloader +1

---

### Post by mohanradhakrishnan on 2010-06-06
Ok. I will try that. It requires me to press F2 and then it shows two menus
 
1. Windows XP
2. Grup
 
 
There is another option.
 
Actually I have plugged my Ubuntu SATA in slot 0. I have also added
 
#! /bin/sh -e
echo ""
cat << EOF
menuentry "XP"{
set root=(hd1,0)
chainloader +!
}
 
When I run sudo update-grup I see
 
"grup-probe: error: Cnnot find a GRUB drive for /dev/sdb2. Check your device.map"
 
So even though GRUB 2 shows Ubuntu and Win XP in the menu I can't choose WinXP due to this problem. It does not boot.
 
There is no problem with the drives. Win XP boots if I switch the drives in the slots.

---

### Post by oldfred on 2010-06-06
You should not have to change slots for you SATA drives and in fact that may create more problems as each drive's install thinks it is drive 0 so when in the drive 1 postition it will not work.

Put windows as first drive if that is where you originally installed it. And run this script.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by mohanradhakrishnan on 2010-06-07
This is what I did. I plugged in the Ubuntu drive in slot 0 and updated the device.map. There was no entry for /dev/sdb.
 
After that when I booted the machine with the Ubuntu drive in slot 0 and WinXP drive in slot 1 I could see the GRUB menu.
 
Now I can boot into either Ubuntu or Win XP. So device.map was the problem.
 
Update the GRLDR menu.lst with the Ubuntu chainloader did not work. So I abandoned it.

---

