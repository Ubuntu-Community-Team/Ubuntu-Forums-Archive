---
title: "4 sata hard drives and a boot problem"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by ikt on 2008-01-15
Hi,

I'm trying to install Ubuntu desktop on my computer at home but having some trouble.

I have a:

200GB Drive
250GB Drive
250GB Drive
500GB Drive

All of them SATA. The boot drive is set to the 200GB drive.

I have Windows XP installed on one of the 250GB drives and want to install Ubuntu on the 200GB.

The problem I have is that after installing Ubuntu onto the 200GB drive, I reboot and grub loads but then gives me the error, Grub error 17 : Cannot mount selected partition.

I can see Windows XP listed on grub as well, but if I goto that it says NTLDR is missing.

However if I reboot from that grub screen and choose to boot off the 250GB with windows on it, it loads fine and am what I'm typing from now.

Any ideas?

---

### Post by Pumalite on 2008-01-15
I think you would have better luck setting the Windos drive as first in the boot order and making space in that drive for Ubuntu with Gparted Live CD. Leave the others for a 'separate /home' and/or storage.

---

### Post by ikt on 2008-01-16
> **Pumalite said:**
> I think you would have better luck setting the Windos drive as first in the boot order and making space in that drive for Ubuntu with Gparted Live CD. Leave the others for a 'separate /home' and/or storage.

Unfortunately i'm using all of the windows drive, the other 250gb drive and 500gb drive are also being used.

I'm stuck with 1x200gb drive to try and get working. Is there any logical reason why Grub would behave this way?

---

### Post by jerrykenny on 2008-01-16
I take it you are changing the boot order in the BIOS to manage changing from one bootloader to the next ?

Is it possible that in doing so, the system map is being confused for ubuntu ?

You probably have a working ubuntu installation, you just need to find a way to boot it up so can you try booting it from the windows loader ?

If you try a google search you should find the text to add in your windows bootloader configuration.

---

### Post by Pumalite on 2008-01-16
Here it is:in case you want to try it:

You can add ubuntu to the windows boot loader:

Boot from the LiveD.

Step 1) Install Ubuntu. On the last screen click on the "advanced" button and replace (hd0) by /dev/sda3. (Here you need to replace sda3 by whatever partition Ubuntu is on)

Don't reboot immediately. Instead stay on the LiveCD.

Step 2) Mount your Windows partition:

Code:

sudo mount  -t ntfs-3g  /dev/sda2 /windows

(Here replace sda2 by whatever partition Windows is on)

Step 3) Copy the first sector of the Ubuntu partition to a file on the Windows partition:

Code:

sudo dd if=/dev/sda3 of=/windows/ubuntu.bin bs=512 count=1

(Be very careful when using "dd". Info on dd)

Step 4) Add ubuntu to the windows boot loader:

Open "boot.ini" from the Windows partition via
Code:

sudo gedit /windows/boot.ini

Add this line to the end of the file:
c:\ubuntu.bin="Ubuntu"

Save the file.

Reboot and you get should get a menu with a Windows and Ubuntu choice.
__________________

---

### Post by jerrykenny on 2008-01-16
Crikey Pumalite !  how do remember all that stuff ?  I think I'll bookmark this page for future ref :)

---

