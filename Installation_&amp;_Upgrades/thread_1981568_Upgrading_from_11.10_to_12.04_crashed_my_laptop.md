---
title: "Upgrading from 11.10 to 12.04 crashed my laptop"
date: 2012-05-17
forum: Installation &amp; Upgrades
---

### Post by auscanstom on 2012-05-17
I recently performed an upgrade from Ubuntu 11.10 to 12.04 and the upgrade crashed my system. Now when I try to boot my Toshiba laptop, that I purchased in 2007, it goes past the Toshiba screen and stops at a command prompt that reads as:
grub rescue>
 
I really do not know how to proceed from here. I do not have a startup disk or usb. Can anyone help me to get my laptop up and running back again?
 
Other details of my laptop are:
Processor Core Duo
Motherboard chipset Intel 945PM
Processor number T2400
Centrino Yes
Processor speed 1.83G

---

### Post by carl4926 on 2012-05-17
And you are posting this from?

You put us in an impossible situation....

---

### Post by auscanstom on 2012-05-17
:D I am posting this from my ipad.
 
Are there any options for me?

---

### Post by darkod on 2012-05-17
Did the upgrade appear to finish correctly or the actual upgrade crashed and didn't finish?

---

### Post by auscanstom on 2012-05-17
The upgrade did not finish. Half way through the upgrade, the laptop stopped responding and that was it. Waited for about 5 hours and I had to turn the laptop off through the laptop power button.

---

### Post by darkod on 2012-05-17
OK.

When you boot the laptop, do you get a grub2 boot menu? If not, hold Shift until the boot menu shows.

Select the Recovery Mode entry, and boot it. It will ask you to select a language (I think) and then it will show a menu.

In this menu, select Networking first. That will activate networking and bring you back to the menu. It's better to connect it with a network cable to the internet before you do this, wireless will rarely work in recovery.

After the network is activated, from the menu select Drop to root shell.

That will bring up the command prompt. At the prompt, first try:
dpkg --configure -a

That should finish configuring all packages that weren't configured during the upgrade. It first downloads, then begins to upgrade them. Hopefully the download part should have finished OK, it only froze in the upgrading. That command should finish the configuring of the packages.

If it finishes without major errors, just type reboot and it will reboot. See if the normal mode will work now.

---

### Post by auscanstom on 2012-05-17
I have started my laptop and again after the startup toshiba screen, it directly goes to a command prompt. The first line says "error: unknown filesystem"
The second line says "grub rescue>"

Pressing the shift key on this screen does not bring up anything.

---

### Post by darkod on 2012-05-17
I'm not sure you can do this without booting from live cd/usb. :(

At the grub rescue, if you try:
ls

What does it list? It should be the hdd and partitions like:
(hd0), (hd0,msdos1), (hd0,msdos2), etc

---

### Post by auscanstom on 2012-05-17
Darko,

At grub rescue when I type ls and press enter, I get the following

(hd0), (hd0, msdos5), (hd0, msdos1)

I really appreciate the help that you are giving.

---

### Post by darkod on 2012-05-17
Do you have dual boot or only ubuntu on this machine?

---

### Post by auscanstom on 2012-05-17
Just Ubuntu Darko.

---

### Post by darkod on 2012-05-17
OK, at the grub rescue prompt, try:
insmod part_msdos
insmod ext2
set root=(hd0,msdos1)
linux /boot/vmlinuz-3.2.0 (press TAB and it will show you available files, finish the command selecting the file with greatest number, like vmlinuz-3.2.0-23-generic, then press Enter)
initrd /boot/initrd.lz-3.2.0 (press TAB and do the same)
boot

That should attempt to boot it.

Note that when trying the linux command it might report that it can't find any kernel files.

---

### Post by auscanstom on 2012-05-17
At the grub rescue prompt, I have tried the first 3 commands one by one. That is on enetering:
insmod part_msdos
I then press enter and enter the next command.
 
When I tried to enter "linux /boot/vmlinuz-3.2.0" I did press TAB after this but nothing shows or comes up. After entering "linux /boot/vmlinuz-3.2.0" and pressing enter, it shows that "linux" is an unknown command.
 
I then tried "initrd /boot/initrd.lz-3.2.0" and pressed the TAB and nothing came up again. But I then pressed enter again as I did in the previous command and it shows "initrd" is an unknown command.
 
I entered boot and I get "boot" is an unknown command.

---

### Post by darkod on 2012-05-17
Hm, lets try this. After the set root command, try what can be seen with:
ls
ls /boot

The second command, does it show anything? Anything similar to vmlinuz-3.2.0 or vmlinuz-3.0.0, etc?

---

### Post by auscanstom on 2012-05-18
I have typed in "ls /boot" in the command prompt as:grub rescue>ls /boot
 
I then pressed enter and I get the below:
error: unknown filesystem
 
And then it returns to:
grub rescue>

---

### Post by darkod on 2012-05-18
I'm out of ideas. See if you can somehow make cd or usb with 12.04 so you can boot in live mode and try things from there. There are not much options if you can't boot with a cd or usb.

---

### Post by auscanstom on 2012-05-18
Darko, thanks a lot for trying. I'm trying to get a live USB created.

---

