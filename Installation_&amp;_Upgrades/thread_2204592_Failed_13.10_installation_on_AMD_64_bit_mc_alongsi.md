---
title: "Failed 13.10 installation on AMD 64 bit m/c alongside Win XP"
date: 2014-02-09
forum: Installation &amp; Upgrades
---

### Post by philromford-q on 2014-02-09
Hi,

I firstly ran the demo from the CD I burned; that was fine, everything worked properly. I then proceded to run the full install from within Ubuntu 13.10. The installation ran without hitch, it seemed; so far so good.

However, when re-booting the machine I get the window with the OS choices, I selected Ubuntu which would start to load after the 5 second delay, showing the splash screen. It halted at this screen:-

----------------------------------------------------------------

Completing the ubuntu installation
For more installation boot options, press 'ESC' 

BusyBox v1.20.2 (Ubuntu 1:1.20.0-8.1ubuntu1) built in shell (ash)

(initramfs) {flashing cursor}

----------------------------------------------------------------

It has now totally halted. I tried all the other boot options with the same result. However, when trying the DEMO option, it halts at:-

(initramfs) unable to find a medium containing a live file system


My PC has two hard drives; one with Windows XP, the other as document drive. Ubuntu automatically decided to install on the 2nd  (document) drive. I thought I would look at re-installing, but that it would appear, would not allow a re-install in the same ubuntu partition; in other words replacing the failed install. There doesn't appear to me for there to be a way of doing this.

Help please! I would be very grateful for a solution to this.

Thanks in advance

---

### Post by tfrue on 2014-02-09
Would you post the URL from the boot-info script? Here is a link to the website on how to create the boot-info script:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Thanks,
Chris

---

### Post by philromford-q on 2014-02-09
Chris,

The URL   [http://paste.ubuntu.com/6904326/](http://paste.ubuntu.com/6904326/)

Thanks

Phil

---

### Post by tfrue on 2014-02-09
What I noticed as rather strange, or things I simply noticed and mentioning just for the sake of it:
[LIST]
[*]You have 2 drives, a 320GB(/dev/sda) and an 80GB(/dev/sdb). 
[*]You have a boot flag on /dev/sda1 and on /dev/sdb1 
[*]You seem to have 3 boot loaders, one on /dev/sda1, another on /dev/sdb1, and on /dev/sdb5. 
[*]/dev/sda1 and /dev/sdb1 use a Windows boot loader, and /dev/sdb5 uses Grub. 
[*]You have 4 partitions on /dev/sdb (/dev/sdb1, 2, 5, 6) 
[*]/dev/sdb5, 6 are the / and swap for Linux 
[*]You have an unknown boot loader on /dev/sdb2 
[*]Also said that a broken WUBI install was detected... 
[/LIST]

I would try the recommended repair and see if that helps, but my thought is to install Grub on /dev/sda1 and add menu entries of Ubuntu on /dev/sdb5 since that is where the /boot/ directory is located and the other necessary files to boot Ubuntu.
(Look at the reinstalling part)
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

I would also go to the .iso you downloaded and re burn it to your disk and try and live boot again. You had something strange going on with the DVD...

You may need to reinstall, but it doesn't look like it right now, but if we do then we will need to double check where we are installing and where grub is going because right now, it's not looking at Grub.

I would personally get everything I could off the drive, wipe the entire thing, then install Ubuntu to that drive. Then maybe partition so we can still map that 34GB partition to XP that you are using on the /dev/sdb drive. But we will take baby steps until we get this worked out.

Good luck, 
Chris

---

### Post by oldfred on 2014-02-09
Which Windows install is your main working one?
sda or the 320GB drive or sdb the 80GB drive that also has Ubuntu now.

If  a user has more than one drive, I usually suggest Windows on one drive that works without the other. And Linux on the other drive that works without Windows drive.

---

### Post by philromford-q on 2014-02-09
Just a thought. The unknown bootloader could possibly be an old one from a previous release of Ubuntu from around two years ago.

---

### Post by philromford-q on 2014-02-09
Windows is on the 320GB drive

---

### Post by philromford-q on 2014-02-09
Chris,

I ran the boot repair which has done the trick, it is now booting properly. I am actually using it right now. I will look at your suggestion regarding putting Grub on sda1 and adding entries on sdb5 though - belt and braces is good.

Thank you for your help, is it greatly appreciated.

Phil

---

### Post by philromford-q on 2014-02-09
Windows is on the 320GB drive

---

### Post by philromford-q on 2014-02-09
Hmm, Ubuntu has now locked up solid, nothing is working. Now back to Windows to send this message.

---

### Post by oldfred on 2014-02-09
I would keep the Windows boot loader on the Windows drive.
And have grub2's boot loader only on the Ubuntu drive, and then set BIOS to boot from UBuntu drive. Then grub lets you still chose which to boot, but if grub does not work you can in BIOS or one time boot key (f12 on my system) boot the other drive directly.

Boot-Repair auto installs grub to all drives. Often better just to not use auto install, but in advanced options choose the Linux install and install grub to that drive. Then choose Windows install and it will install a Windows type boot loader.

---

