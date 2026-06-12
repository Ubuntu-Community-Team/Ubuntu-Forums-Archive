---
title: "I appear to have broken my machine's bootloader in some fashion"
date: 2024-03-11
forum: Installation &amp; Upgrades
---

### Post by endlessinstant on 2024-03-11
Device is a ThinkPad T470 w/ Core i5-6400U, 8 GB RAM, and a Samsung 256 GB NvME drive

I decided to install Xubuntu on it.   I was previously using Legacy BIOS on it.   Xubuntu install with default options using the wizard.   OS refuses to boot.  Quick search suggests I switch to UEFI mode.  I do, Xubuntu boots.   "Great!" Problem solved.   System works.   

Decide I'm going to restore the computer to what I had before which was legacy boot with Slackware.      I switch modes, install slackware, reboot, annnnd nothing.   

The system now no longer boots but goes to a firmware menu asking me to select a boot device because it can't find anything to boot.   So I presume that I've broken the bootloader partition in some fashion.   I've attempted a reinstall both with defining an EFI partition and without, booting into legacy mode and without, and I cannot get the OS to load.    I am having some trouble getting elilo to install (haven't had a chance to diagnose that yet) but that seems more of a slackware issue than anything else.  

I guess my real question is - the heck did the Xubuntu installer do to my system and can I reverse it? Since I don't exactly know what I broke, I've struggled to google the problem.    

I have been able to boot from USB with no issue so I think I scrambled something on my NvME drive.

---

### Post by oldfred on 2024-03-11
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Have you updated to the latest firmware for both UEFI and SSD?
Do you have the Boot order lock setting like many other Lenovos?


Older install, but should be similar. Shows UEFI screens:
[https://tothepoles.co.uk/2017/11/16/lenovo-t470p-ubuntu-16-04-install-notes/](https://tothepoles.co.uk/2017/11/16/lenovo-t470p-ubuntu-16-04-install-notes/)

Lenovo T450 Problem with boot repair GRUB - Boot Lock issue
[https://ubuntuforums.org/showthread.php?t=2494747](https://ubuntuforums.org/showthread.php?t=2494747)
Lenovo Locked UEFI/BIOS setting:
[https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg](https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg)

---

### Post by yancek on 2024-03-11
How many physical hard drives do you have?  Did you try to install Slackware on the same hard drive?  If Xubuntu was an EFI install and you have 1 hard drive, you will have had several options when installing Slackware.  One option is to NOT install a bootloader, the other 2 would be to install Lilo (which would  not work using EFI) or to install using elilo.  Simplest option would be to not install any bootloader with Slackware and simply reboot into Xubuntu and update grub.  This should detect the Slackware and put an option in the grub.cfg file to boot it.  If you did this, you would not have the option to boot Slackware from your EFI menu but only from the Xubuntu Grub.  If you used the option to install elilo, you should see an option in the BIOS boot options for it.  Boot into Xubuntu and look in the /boot/efi/EFI directory to see if you have a Slackware directory with the proper EFI files.

If you want both Slackware and Xubuntu installed on the same physical drive, they both must be either Legacy or both must be EFI.  Post the output of the boot repair script suggested above which should give more detailed information.

---

