---
title: "Do I still need boot loader?"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by grubbybiker on 2010-03-21
Hi,

I have just changed from a dual boot system with windows 7 and Ubuntu 9.10.
when I boot up it still gives me the option of windows or Ubuntu.  With only Ubuntu as my OS, how can I get it to boot directly.

---

### Post by wilee-nilee on 2010-03-21
> **grubbybiker said:**
> Hi,

I have just changed from a dual boot system with windows 7 and Ubuntu 9.10.
when I boot up it still gives me the option of windows or Ubuntu.  With only Ubuntu as my OS, how can I get it to boot directly.

Your description is very vague, what changes have you done exactly, and what is directly?

---

### Post by lindsay7 on 2010-03-21
Run the boot script

 Re: GRUB on two drives error
Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command
Code:

sudo bash ~/Desktop/boot_info_script*.sh

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.
__________________
Boot Info Script courtesy of community member meierfra


This will tell you where the boot files are for windows you need to remove them.

It will look like this,


Quote:
sdb1: _
Boot files/dirs: /bootmgr /Boot/BCD
Just deleted those files and run update-grub

Code:

sudo mount /dev/sdb1 /mnt
sudo rm /mnt/bootmgr
sudo rm -r /mnt/Boot
sudo update-grub

---

### Post by jsriz on 2010-03-21
> **grubbybiker said:**
> Hi,

I have just changed from a dual boot system with windows 7 and Ubuntu 9.10.
I guess you have removed windows 7 and have a single boot ubuntu
> 
when I boot up it still gives me the option of windows or Ubuntu.  With  only Ubuntu as my OS, how can I get it to boot directly.
i didnt get it why would it give windows7 if you have already removed it???
well you can't remove the bootloader 
refer: [http://ubuntuforums.org/showthread.php?t=1421402&page=1](http://ubuntuforums.org/showthread.php?t=1421402&page=1)
but if you don't want to see the grub you can set the time out to zero.
well if you are using 9.10 you must be probably using grub2 (unless you have not upgraded)
run 
gksudo gedit /etc/default/grub
and change the lines "GRUB_DEFAULT=10"  to "GRUB_DEFAULT=0"
and then run sudo update-grub2

---

### Post by grubbybiker on 2010-03-21
Problem solved! Removed all OS's formatted drives and reinstalled Ubuntu.

Thanks for your replies

---

