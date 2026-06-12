---
title: "No display when booting into linux installer"
date: 2015-09-28
forum: Installation &amp; Upgrades
---

### Post by sean104 on 2015-09-28
[FONT=verdana]I have windows 10 uefi installed on one ssd (which should not be a problem) and I just bought a separate ssd for a Linux install.
[/FONT]
[FONT=verdana]My hardware is a 3770k @4.4, 8gb 1600 ballistix ram, 980, and a Samsung 850 evo.
[/FONT]
[FONT=verdana]I created a bootable usb using Yumi, which I have never had a problem with before. I boot into the usb, non-uefi mode, where I am given the option to choose a linux distro to boot into (so far I have tried Xubuntu 15.04 and Ubuntu 15.04). When I select a distro I am brought to the menu where I can boot from live usb, install distro, etc.
[/FONT]
[FONT=verdana]This is where the problem comes in. When I select install or boot without install I am given the error "ACPI PCC probe failed." Followed by "Failed to initialize sync subsystem, -38." After this the display cuts out. Although I can hear the Ubuntu jingles in the background so I know that it is running, there is just no display.[/FONT]

---

### Post by oldfred on 2015-09-28
I thought there were some posts where some installer did not work well with UEFI.
If Windows is UEFI, you should install Ubuntu in UEFI boot mode. If not you cannot dual boot from grub, but only by going into UEFI. You may have to turn on/off UEFI or CSM to match system install.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
    
Is 980 a nVidia Maxwell card?
You probably need nomodeset to boot live installer & first boot or until you install proprietary nVidia driver. Best to use ppa to get newest driver.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

    Ubuntu Launches Its "Fresh" Proprietary Driver PPA
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
sudo apt-add-repository ppa:graphics-drivers/ppa.

      [URL="http://unetbootin.sourceforge.net/"]http://unetbootin.sourceforge.net/
[/URL]Rufus Create bootable USB drives the easy way  From Windows create Linux installer
[http://rufus.akeo.ie/](http://rufus.akeo.ie/)

Only use the Something Else install option with two drives.
       [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://linuxbsdos.com/2014/05/31/dual-boot-ubuntu-14-04-windows-7-on-a-pc-with-2-hdds-and-uefi-firmware/](http://linuxbsdos.com/2014/05/31/dual-boot-ubuntu-14-04-windows-7-on-a-pc-with-2-hdds-and-uefi-firmware/)
            Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

            Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

    

[URL="http://unetbootin.sourceforge.net/"]
[/URL]

---

