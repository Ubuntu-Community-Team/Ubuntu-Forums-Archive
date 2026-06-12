---
title: "Cannot boot into installed Ubuntu"
date: 2014-10-25
forum: Installation &amp; Upgrades
---

### Post by paul_b4 on 2014-10-25
I have installed Ubuntu 14.04.01 on my Asus laptop with windows 8.1 installed, and the installation was successful, but the computer just boots straight into windows and I cannot boot into Ubuntu.  I followed the instructions [here]("https://help.ubuntu.com/community/UEFI"), ran Boot Repair as per instructions; Boot Repair indicated there was an error and did not provide a **paste.ubuntu.com/XXXXXX/**, but provided a text file instead, which I have attached to this post (I had to attach it as an .odt file because as a .txt file it said that it was too big for that type of file).  Any help would be greatly appreciated! 

Thank you

---

### Post by yancek on 2014-10-25
Your windows install is UEFI and you can see that the first partition (sda1) is an EFI partition and contains the windows efi files.  If you look at the top of the page, you can see that Grub boot code is installed in the master boot record and looking at the EFI partition there are no Ubuntu efi files.  If you have windows booting with EFI, then you need to install Ubuntu as EFI, mixing them results in exactly what you have.  Someone more familiar with EFI will probably be along to give you a suggestion.

---

### Post by paul_b4 on 2014-10-28
Ok, but like I said, I have followed instructions to the letter, and furthermore I have tried a reinstall, and to troubleshoot in other, very time-consuming methods as well.  How do I solve this problem?  

When I was installing, there was no option for whether to install Ubuntu as EFI or not.  Is there a specific install .iso for installing Ubuntu as EFI?  If there is I have not been able to find it in web searches.

---

### Post by oldfred on 2014-10-28
UEFI and CSM/BIOS/Legacy are not really compatible. Once you start booting in one mode you cannot switch. But you can dual boot from UEFI menu or maybe one time boot key. But grub will not boot another install that is not in the same UEFI or BIOS boot mode.

You choose how you install by how you boot installer. Your UEFI should show flash drive twice. Once as UEFI like UEFI-Kingston and just Kingston which then is BIOS/CSM install.

Boot-Repair can convert a BIOS install to UEFI by uninstalling grub-pc(BIOS) and installing grub-efi-amd64(UEFI). 

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

Even more info in link in my signature.

---

### Post by paul_b4 on 2014-10-31
Yay!! I finally was able to install it!  I went ahead and updated the UEFI as you suggested (I have an Asus D550M notebook).  Apparently it was too gargantuan a task to provide a UEFI that was able to boot from CD for these developers to get it right the first time.  The way I had booted from CD before, to install Ubuntu, was to select the "Use Windows recovery CD/USB" option, after holding down the Shift key and pressing "restart" in Windows 8.  I suppose that it rebooted in "Legacy" mode to accomplish for some incomprehensible reason, and therefore ruined my installation.  After updating the UEFI, I was able select the option in the UEFI menu to boot from DVD, and that worked.

It is unbelievable that in 2014, programmers have not mastered the task of a BIOS that is able to boot from something besides the hard drive.

Sadly however, upon installing Ubuntu, I am not able to adjust the screen brightness, which is a bigger problem than it seems, because after a while it makes my eyes hurt, and I can't compromise my eyes to use Ubuntu.  

Having searched online for some solutions, I added this file /usr/share/X11/xorg.conf.d/20-intel.conf and these lines

Section "Device"
        Identifier "card0"
        Driver "intel"
        Option "Backlight" "intel_backlight"
        BusID "PCI:0:2:0"
EndSection

[FONT=arial]That[/FONT] [FONT=arial]did not solve the problem, and I tried this

[/FONT]Update your Grub file, line no 11 in /etc/default/grub to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"

update grub using the command
update-grub
Reboot and you are done.

[FONT=arial]This did not solve the problem, but instead now when I put headphones into the computer, they do not work.  They do not work even after I changed the [/FONT]GRUB_CMDLINE_LINUX_DEFAULT [FONT=arial]back to what it was before.  Please help!

Thank you
[/FONT]

[FONT=arial]
[/FONT]

---

### Post by oldfred on 2014-10-31
Best to start a new thread with that issue in title. Someone may know about backlight, but not look at a boot issue thread.

Some other Asus, they have many models, not sure how similar they are or if backlight issues discussed.
 ASUS Zenbook Prime UX32VD
[http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1)
[http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1)
[https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)

 ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

---

