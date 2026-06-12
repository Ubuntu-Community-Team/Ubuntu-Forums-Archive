---
title: "GNU GRUB instead of Ubuntu in live mode when installing on Windows 8."
date: 2014-06-22
forum: Installation &amp; Upgrades
---

### Post by leslie3 on 2014-06-22
I own a Toshiba P50-A and when I try to boot Ubuntu 14.04 LTS in live mode I just get a black command prompt screen called GNU GRUB.

---

### Post by oldfred on 2014-06-22
When booting in UEFI mode from live installer you do get grub menu.

       Backup efi partition and Windows partition before Install of Ubuntu.

Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

Some other Toshiba threads.

  [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)
Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)
How to install Ubuntu 13 dual boot with Windows 8 Ubuntu Studio
[http://ubuntuforums.org/showthread.php?t=2186838](http://ubuntuforums.org/showthread.php?t=2186838)

---

### Post by leslie3 on 2014-06-22
I can't relate to any of those links. I used unetbootin to make the bootable USB if it helps.

---

### Post by oldfred on 2014-06-22
Did you see the posts by the user with a P50 and some of the UEFI/BIOS changes he had to do?

And if booting from grub menu just gives black screen you may need boot options on grub menu kernel line.
If Intel video see other options in post by ufban1 to nomodeset, but follow instructions on adding nomodeset on how to edit grub boot.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by leslie3 on 2014-06-26
This is what my grub menu looks like. Typing e or edit doesn't open anything.

---

### Post by oldfred on 2014-06-26
That is not a grub menu, but a grub error screen. It means it cannot find any grub to use to boot with.

Did you see some of the others with your system or similar systems that had to turn on or off specific UEFI settings to get it to work in post #2.

Is that from Live installer? Then your installer is not correctly configured. Some flash drives, or difference with USB3 or USB2 ports, or just a different installer sometimes works.
       Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it 
[http://ubuntuforums.org/showthread.php?t=2230389](http://ubuntuforums.org/showthread.php?t=2230389)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

    
Or is that after you have installed? Then you may not have fully installed grub and Boot-Repair may reinstall it or fix it or if not create a report that we can review to see what the issue is. Just post pastebin link it gives.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by leslie3 on 2014-06-26
How do I create a report? Sorry I'm new at this sort of stuff.

---

### Post by oldfred on 2014-06-26
Click on the BootInfo Summary. It will give you a link. Copy & paste the full link so we can see your configuration.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by leslie3 on 2014-06-27
But I don't have boot repair. I only have windows 8, not Ubuntu. I'm trying to install Ubuntu.

---

### Post by oldfred on 2014-06-27
If you only get the grub error on booting flash drive that is the install, it would seem that the installer is not correct. 
Verify that download is correct with md5sum. 
Some find just using a different installer works.
You can also try a different flash drive and different USB port.

       Also instructions for DVD or USB flash drive for both Ubuntu & Windows
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Also frugal install to hard drive without flash drive./
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

       Usb installer from Windows
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
SOLVED!!! Used rufus to create bootable USB and it worked! I've tried UUI and unetbootin before. 
[http://rufus.akeo.ie/](http://rufus.akeo.ie/)

Some flash drives just seem to have issues.
      
 Howto make USB boot drives 
[http://ubuntuforums.org/showthread.php?t=1958073](http://ubuntuforums.org/showthread.php?t=1958073)
pendrive speed tests USB2 & USB3 various brands - user sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)
Includes links to speed tests and lists some that do not work well.
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

---

