---
title: "Unable to install Ubuntu 20.04.4 LTS"
date: 2022-07-19
forum: Installation &amp; Upgrades
---

### Post by nkellerucsd on 2022-07-19
Hello,
I am unable to install ubuntu 20.04.4 LTS (Focal Fossa) on my machine. I've created a live bootable USB (from the ubuntu website) and can run ubuntu in live mode (from my USB) on my machine. Then I  go ahead and install ubuntu and the installation process seems to be successful. After the installation completes, the system reboots and I get the following output that is printed on the screen only once after the installation: 

sd-umoun: Failed to unmount /oldroot : Device or resource busy
sd-umoun:Failed to unmount /dev/pts : Device or resource busy
sd-umoun:Failed to unmount /dev : Device or resource busy
shutdown: Could not detach loopback /dev/loop0: Device or resource busy
shutdown: Failed to finalize file systems, loop devices, ignoring
reboot: Restarting system

Then I just get a black/dark-blue screen forever (print out above only occurs once after the installation, it never occurs again). 

I've tried the following (I always select the "Erase disk and Install Ubuntu" option):

(1) Install Ubuntu in safe graphics mode
(2) In the GRUB installation screen, I press 'e' and replace "quiet splashy " with nomodeset and then press F10 to reboot
(3) Disabled Secure Boot and Optimized Boot in the BIOS settings
(4) Installed with the installed drivers checkbox checked

The fact that Ubuntu runs fine with my USB in live mode but does not run when installed on my machine suggests I have to edit the partition table when I install but I am unclear what parameters I should use. 
Is there a path or suggestion I could try to? All help is welcome!

Thank you very much,
Nick

---

### Post by grahammechanical on 2022-07-19
> The fact that Ubuntu runs fine with my USB in live mode but does not run  when installed on my machine suggests I have to edit the partition  table when I install but I am unclear what parameters I should use.

Not necessarily. The Erase disk and install Ubuntu option will do exactly that and it will set the partition table and create and format the necessary partitions. Please use the live session and open the Disks utility see what partitions are on that disks. 

Regards

---

### Post by oldfred on 2022-07-19
What brand/model system?
What video card/chip?

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

