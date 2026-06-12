---
title: "Acer ES1-533 hangs during Grub installation"
date: 2022-08-29
forum: Installation &amp; Upgrades
---

### Post by mark-wilkinson on 2022-08-29
I have an old (slow) Acer ES1-533 that came with Windows 10.  I thought I would install some version of Linux in a dual boot arrangement.  I went into the BIOS and disabled Fastboot and Secureboot (based on my reading).

I then used Rufus to create bootable ISO images for the latest Ubuntu, Mint, Pop, Zorin, Antix, Peppermint and several others in an attempt to find an OS that would successfully boot into a Live environment and let me do an installation.

I couldn't get most images to even boot properly with the exception of Antix.  However when I ran the install, the computer froze during the Grub installation phase.

I eventually found I could get the Live version of 18.04 of Ubuntu to start but when I tried to install it into the partition I created for Antix, it too froze during the Grub installation phase.

I re-ran the Live image and found I was able to mount the partition I created during the Ubuntu installation and it looks like all the directories are there.  I think I just need to create a Grub menu for Windows and Ubuntu.

I made a Boot-Repair image and was able to boot it up.  I ran Boot Info [IMG]https://ubuntuforums.org/attachment.php?attachmentid=290952&stc=1[/IMG]and saved the attached text file.

I ran Boot-Repair but as in the case of the Grub install, the computer froze.  As a result, I couldn't try out the Final Advice ideas in the text file because I never got to see the value of *****.

So would like to see if I can get this PC running in a dual boot environment and if I can get that working, I would like to update the version of Ubuntu to something a little newer than 18.04.  

Any tests I can run or ideas I can try out?

Thanks
Mark

---

### Post by grahammechanical on 2022-08-29
Warning everyone. Click on that link to open the bootinfo file and it downloads a file to your machine. I do not like files downloading to my system without my permission.

---

