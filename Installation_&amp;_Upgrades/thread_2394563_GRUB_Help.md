---
title: "GRUB Help"
date: 2018-06-18
forum: Installation &amp; Upgrades
---

### Post by mxp9mm on 2018-06-18
Im not sure if im posting this in the right place but I thought this could be appropriate

So i had ubuntu (14.something) i think. I went to replace the os with a new linux version and after i deleted the OS and went to install a new iso from a disk i get the "unknown filesystem, grub rescue" message. Ive tried finding the ubuntu partition using "ls" and get (hd0) and (hd0,msdos1) options. After trying to boot to those partions, it still cant.  Thank you for reading

---

### Post by A Traveller on 2018-06-18
Hi mxp9mm.

I usually can't reply to any posts as I do not have ANY knowledge on these matters, however, I had a similar question just recently and found some very clear, easy to follow instructions. Maybe you could try following the steps at the following link.

[https://www.easytechguides.com/error-unknown-filesystem-grub-rescue.html](https://www.easytechguides.com/error-unknown-filesystem-grub-rescue.html)

Before you do, I would still wait for someone with more knowledge to reply to your thread as I wouldn't want your problem to get worse!

Thanks.

---

### Post by yancek on 2018-06-18
Before you deleted the OS (Ubuntu 14?) did you create a bootable DVD or flash drive of the new OS you want to use?  YOu need to change the BIOS boot option settings to boot from the DVD or falash drive you are using?

---

### Post by oldfred on 2018-06-18
If you deleted Ubuntu, then the version in MBR will not be bootable.
You need to boot flash drive or DVD. If they do not boot, then it reverts to next choice which is you now unbootable hard drive.

Make sure you are selecting USB flash drive to boot from BIOS/UEFI boot menu often f10 or f12, check your manual. If not shown, then flash drive may not be correctly configured.

       Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

---

### Post by mxp9mm on 2018-06-19
Yes, i have made an iso and i do get this error when booting from a cd as well as when i boot from hd

---

### Post by mxp9mm on 2018-06-19
I have tried booting to many differant linux iso's (ubuntu included (multiple times))

---

### Post by mxp9mm on 2018-06-19
I have tried this many times being that this is the most common solution i have found and i do not see anything like "[COLOR=#000000]grub rescue> ls (hd0,gpt5)/./ ../ lost+found/ etc/ media/ bin/ boot/ dev/ home/ lib/ mnt/ opt/ proc/ root/ run/ sbin/ selinux/ srv/ sys/ tmp/ usr/ var/ initrd.img initrd.img.old vmlinuz cdrom/ grub rescue>  
[/COLOR]when i put in ls and my found partions

---

### Post by mxp9mm on 2018-06-19
I dont know if this helps bt, the only partions "ls" finds are (hd0) and (hd0,msdos1)

---

### Post by oldfred on 2018-06-19
Did you verify ISO download?
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

UEFI or BIOS hardware?
What brand/model system? Many UEFI or BIOS need settings to allow USB boot and/or full USB access.
Are you making installer from Windows or Linux?
And then what tool to make installer are you using?

       
 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download) 
    
If one install tools does not work, try another. And if one flash drive does not work, another may. Same with USB ports. I do not use DVD as I have had so many bad burns, still using some as coasters.
 [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
      
 Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

### Post by mxp9mm on 2018-06-19
BIOS
Lenovo G770
Downloading as a .iso from windows and burning onto a DVD using integrated DVD burn from windows

I have probably made and put in 10 differant DVDs with differant iso's. I know i downloaded Ubuntu 16.4 (i think it was 16.4) about 3 times just incase it was a bad burn

---

### Post by oldfred on 2018-06-19
It sounds like integrated DVD burner may just copy ISO to DVD. That will not make a bootable disk.
You have to use one of the installers. They format drive, extract ISO, and add boot loader.

Much better to use flash drive. 

If it has core i5, then it also is UEFI, so you have to turn off UEFI and turn on BIOS/Legacy/CSM.
Also have you updated UEFI from Lenovo for your system. That is now required with some of the issues relating to Meltdown and Spectre CPU vulnerabilities. Both Windows & Ubuntu have updated kernel for those issues, but UEFI also requires updates.

---

### Post by mxp9mm on 2018-06-22
I looked through the BIOS menu and did not see anything about UEFI since it is indeed Core i5
Can you elaborate on "use one of the installers"?

---

### Post by oldfred on 2018-06-22
If an i5 then definitely UEFI, but some vendors still call it BIOS.
You should have Secure boot on/off setting, but it may be called "Windows" and "Other" where fine print in your manual says if installing Windows 7 use "Other". Windows 7 does not support Secure boot.

Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[URL="http://www.ubuntu.com/download"]http://www.ubuntu.com/download
      [/URL]
 [https://help.ubuntu.com/community/USB](https://help.ubuntu.com/community/USB) Installation Media
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows) 
            Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Ubuntu install guide - multiple ways to create live installer to flash drive
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) 
    [       ]("http://www.ubuntu.com/download")
 Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 
    [URL="http://www.ubuntu.com/download"]
[/URL]

---

### Post by Paddy Landau on 2018-06-26
> **oldfred said:**
> … you have to turn off UEFI and turn on BIOS/Legacy/CSM.
Slightly off topic: Why do you have to turn off UEFI? I thought that Ubuntu had the standard signing key as provided by Windows so that Ubuntu works on Windows-based UEFI machines.

---

### Post by oldfred on 2018-06-26
Generally best to have UEFI on.
On my one system, it only boots in UEFI mode, if set to UEFI only. The UEFI or CSM/BIOS setting only boots in BIOS mode.
If UEFI, lots of details in link in my signature below.

---

