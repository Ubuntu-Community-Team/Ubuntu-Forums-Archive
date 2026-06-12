---
title: "dual install XP + Xubuntu on 2 HDs"
date: 2012-08-08
forum: Installation &amp; Upgrades
---

### Post by sweetlinux on 2012-08-08
Hello, I currently have XP installed on a SATA HD. I'm planning on getting a 2nd SATA HD and I'd like to install Xubuntu on that 2nd drive.

So there's no confusion, I plan to install the 2nd hard drive, unplug the XP drive, install Xubuntu on the 2nd HD, plug back in the XP drive....Then, reboot the PC, press F-12 to access the boot menu and choose my Xubuntu HD any time I want to boot into Linux....Does this sound like a good plan?

thanks

---

### Post by mikewhatever on 2012-08-08
It should work, but whether you'll find it good or bad, or neither, I don't know.

---

### Post by drmrgd on 2012-08-08
Your solution would work.  However, it's a bit tedious to have to change the boot drive through BIOS each time.  There is a very simple solution, which is to use Grub 2 as the bootloader.  This will bring up a menu each time you reboot that will quickly allow you to change the OS without having to enter any extra menus.  It will also just start whatever OS you choose as default after a few seconds (all of this is customizable, by the way). 

Probably the easiest way to start is to have a look at the Boot-Repair software, which will analyze the system and set up Grub correctly.  I've not used the tool myself, but others seem very happy with the results.  You can find out more here:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

The basic goal is to install the Grub bootloader to your /boot partition on you Xubuntu drive.  Then update Grub to detect your Windows XP drive, and you're all set.  Boot-Repair should automate that for you.

---

### Post by oldfred on 2012-08-08
Many suggest disconnecting the drives as then you do not have to worry about where grub2's boot loader will be installed. And it is best to have grub2's boot loader on the Ubuntu drive and Windows boot loader on the Windows drive, so you can choose from BIOS if issues with default.

But you set Ubuntu as the default boot drive and run this after connecting both drives and you can boot Ubuntu or Windows from the grub2 menu as drmrgd suggest. You only need Boot-Repair if you have boot issues. I do like to have several repair CD/USBs as backup ways to boot. LIve CD/USB is one, and you should also have the XP install disk for Windows. With Windows 7 you have to make a repairCD/USB.

Ubuntu's default install is just / (root) and swap and it defaults to installing the grub2 boot loader to sda. But if you use the more advance manual install (something else) you can add a /home partition and also get a choice on which drive to install grub2's boot loader.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it.
Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)

---

