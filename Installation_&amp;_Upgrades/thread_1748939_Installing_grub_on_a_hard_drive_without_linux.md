---
title: "Installing grub on a hard drive without linux"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by Geek10 on 2011-05-04
PROBLEM: I have an old Pentium 3 1.2GHz laptop with no CD drive, a couple of USB ports in the back, 2 sticks of RAM (128 MB + 256 MB), and a 30 GB Hard Drive. I want to install Xubuntu on it for use on my long public transport trips. My plan is to use the xubuntu-11.04-alternate-i386.iso.

SOLUTIONS SO FAR: Many solutions seem to be quite clear about what to do without a CD Drive, but most of them assume I have a linux OS already running somewhere, which makes Grub easy to install on the Hard Drive. But I don't. I only have 3 Windows machines - XP, Vista, and 7.

What I have is a 2.5inch to 3.5 inch IDE adapter, so I have removed the laptop 30GB HDD from the laptop, and put it in my XP Tower Computer. The hard drive did not come up automatically, so at first I thought something was wrong, but it turned out I just needed to use Windows Device Manager to format the HDD. I formatted 2 partitions with FAT32 (NTFS is not recommended for Linux, and I could use GParted to format to "Ext3" which is journalised and thus better than FAT32). The first partition is 1GB, to store the 620 MB Xubuntu alternate i386 ISO file and other boot files. The second partition is the rest of the 30GB drive.

How do I install Grub on this 1GB partition though?

This forum thread gives some instructions, which I tried.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
I tried it with a CD burnt with "xubuntu-10.10-desktop-i386.iso" which had a correct md5sum as instructed. But typing "sudo grub" in the terminal brought a response which said the "grub command not found" or something similar.
I then tried to do it with a CD burnt with "xubuntu-11.04-alternate-i386.iso" which had a correct md5sum, but then of course I couldn't get to the "try xubuntu without installing it" option at boot up.

I then tried this link, [http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html](http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html), which seems good if I get the relevant xubuntu 11.04 files as it instructs. But it says:

"[COLOR=Blue] 6. Now you have to add grub to your c:\boot.ini file. You can open  boot.ini by clicking on Start>Run and typing c:\boot.ini. If Windows  does not allow the file to be modified, then go to Control  Panel>System and click on the Advanced tab. Now under Startup and  Recovery click Settings and then under System Startup click Edit. Open  boot.ini and add this line in the end.

**C:\grldr=”Start GRUB” **

7. You are now ready to install Linux. Restart your PC and from the boot screen select "**Start GRUB**". This will load GRUB. From the grub[/COLOR]   "

What does this mean for my situation? [COLOR=DarkRed]Do I copy the boot.ini file on my Windows XP HDD to the 1GB partition on my laptop HDD (as well as all of the other files instructed in earlier steps), and then modify boot.ini as shown, and then transfer the laptop HDD back to the laptop and try to boot it?
[/COLOR]
I will appreciate any help whatsoever. In my experience, the people who are active users on the Ubuntu forum have been extremely kind and have superb computing skills, so I do hope my post is easy for you to understand!

Thanks!

---

### Post by Geek10 on 2011-05-04
Bump...does anyone have any suggestions?

---

### Post by pkzj on 2011-05-14
Boot from an iso and install grub from there.  Puppy Linux is a good choice.

---

### Post by pkzj on 2011-05-14
Sorry, missed the part about no CD.  Forum didn't display correctly.  Can you boot from USB?  There is also a program called loadlin that uses LILO instead of grub.  If you're just trying to boot various windows versions why not use the windows boot loader and just add the partitions/drives to your boot.ini file?

---

### Post by Hedgehog1 on 2011-05-15
A number of folks with similar hardware situations have found this plan of attack to function:

1) Remove the Hard Drive from the target Laptop.

2) Connect the hard drive to another PC using a USB to SATA/IDE cable

3) Install Ubuntu onto the laptop hard drive.

4) Place the laptop hard drive back into the laptop.

5) Power up and complete your setup of Ubuntu from the laptop

Unlike Windows, Linux installs generally move easily from one pc to another.

***The Hedge***

:KS

---

