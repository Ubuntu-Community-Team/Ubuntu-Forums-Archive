---
title: "Grub cmd prompt appears on boot"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by garethinbendigo on 2010-05-11
Two days ago I decided to migrate from Fedora to Ubuntu 10.04. On the Ubuntu install I chose to format the entire disk as I do not want a dual boot system. I have three disks and have set the bios to boot from dvd, then main disk, then 2nd disk, then any other bootable drive and coming from a working Fedora I know I have my "slaves" and "Master" pin positions on the disks set correctly.
When I try to boot the fresh install of Ubuntu I do not see any menu options, no boot image nothing, I get taken immediately to a grub command window and I dont know how to fix things from there.
I have tried to fix things by booting into the "try before you 'buy'" thing on the installation cd and I can see that Ubuntu has been installed on the main disk, but all in all Im stuck.
Ive seen many posts on dual boot systems but nothing specific to my inquiry. If you have an idea on fixing through grub or via the preview on install disk please let me know. 
Thanks for any help.

Gareth

---

### Post by garethinbendigo on 2010-05-11
Ok I half solved my problem. At least I should be able to poke around the actual operating system more now that I can boot into Ubuntu.
Firstly I pulled out my IDE cable containing my other two additional hard drives and did a complete format and reinstall of my main h/drive. When I went to reboot things were even worse such that I couldnt press 'i' to bring up any boot options and I was being directed to grub command line instantly. So I inserted the install disk and pressed 'i' again and this time a list of options was presented i.e. Try....Install....Check media...etc.
I tabbed down to the Install option and noticed boot parameters near the bottom of my screen. I removed all boot parameters and enter the following parameters:

boot=(hd0,1) splash--

Ta da, Ubuntu booted up and I have since downloaded updates for 10.04 especially as it appears to be extremely buggy.
Unfortunately getting the updates hasnt helped in the slightest when I go to reboot without the install disk in. Not happy.

---

### Post by alterpinguin on 2010-05-11
check if there is a "device.map" file
in /boot/grub directory.
If it is missing, (up to now it happened one time to me with 10.04)
loading the menuentries fails.
You can recreate the device.map with grub-mkdevicemap,
after run as "root" (sudo) check the file is created
and has the right entries (its a text-file).
-
maybe a bug - dont know, if there is another harddisk
without a valid partition-table, looks like grub-update
fails to generate a device-map at the end... 
-
and if someone knows, why the timeout does not work to display
the menu in grub2.... (seems i overlooked one necessary option,
but what was it?)

if there is no devicemap, but in the grub2 console it is possible
to look for the linux-partition.
like
ls
displays known harddrives (hd0,1) ...(hd0,5)
ls (hd0,5)/boot
displays the boot directory on the linux-partition if it is the first extended one (=hd0,5)
then
a manual boot can be done like
linux (hd0,5)/boot/vm...use tab and select the correct kernel-name
then add the option for the root, like root=/dev/sda5 (!you know the partition-number?) and add the readonly: "ro" too
then the initrd is needed, same procedure
initrd (hd0,5/boot/init..use tab and select right one
after this enter:
boot
and the booting of this kernel with setting for "root" "ro" (readonly for first check in boot-sequence) and the loading of the initrd should start.

---

### Post by garethinbendigo on 2010-05-12
Thanks [alterpinguin]("http://ubuntuforums.org/member.php?u=285617") for your invaluable input in helping me to be able to boot from the grub command prompt. I noticed that my device.map file was missing and so I generated a new one. The result was (hd0) /dev/sda (and (fd0) ...) which is what I expected. Unfortunately this has not helped to solve the problem, I am still presented with grub at boot.
Additionally despite the grub.cfg warnings I edited the file under the ##BEGIN /etc/grub.d/10_linux and change the following line:

 linux   /boot/vmlinuz-2.6.32-22-generic root=UUID=e2885183-1388-40b9-98cf-9baf63b5c054 ro   quiet splash

to:

 linux   /boot/vmlinuz-2.6.32-22-generic root=/dev/sda1 ro   quiet splash

This has not worked either. After my edit I had a little trouble using vi to restore the grub.cfg back to what it was so I did: grub-update which re-generated the grub.cfg file. Still no good.
Whats getting lost in translation? Help appreciated - thanks.

---

### Post by dino99 on 2010-05-12
have a look at this mini howto:

[http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

and links below

---

