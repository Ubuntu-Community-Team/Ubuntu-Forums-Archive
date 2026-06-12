---
title: "Trying to install Windows 7 and Ubuntu on a windows 8 laptop (retain windows 8)"
date: 2013-12-14
forum: Installation &amp; Upgrades
---

### Post by RedG8Beast on 2013-12-14
I have a Refurb ASUS K75DE that came with Windows 8 on it, and I want to run Windows 8, Windows 7 and Ubuntu on the main HDD. I disabled the fastboot option in BIOS, and set my user password as well. Tried to boot to the windows USB stick I have for Windows 7, but I did something wrong and it loaded windows 8. Now when I go back into the BIOS, I'm locked out of changing anything except the time, all options are greyed out. You guys are the best help I know of, and it's kind of Ubuntu related since I need to A] Install Windows 7 before ubuntu, and B] and I would also need to get to the boot order to install ubuntu. Please help me guys!  What info do you need?

---

### Post by mohitsharma3172 on 2013-12-15
I'm a newbie too..
I had the same problem...
windows 8 does not allow boot from flash drives easily...
what i did was i made a bootable cd for windows 7 and removed windows 8 completely...
then i made a bootable flash drive for installing ubuntu using Yumi...
It worked well for me
P.S.
Change boot device priority to your dvd-rom

---

### Post by RedG8Beast on 2013-12-15
I can't change boot device priority in BIOS, I cannot change any options except for the system time.

---

### Post by oldfred on 2013-12-15
You have to get back into UEFI/BIOS. 
       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

Is Windows 8 in UEFI mode? I do not know if you can dual boot Windows 7 in UEFI mode, but you do have to copy Windows 7 DVD to flash drive and convert it to UEFI mode.
      
 Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

If in BIOS mode, Windows only boots from one primary partition. Additional installs have no boot files. Shows Vista, but all Windows in BIOS mode are the same. Has link to Windows 7 minor changes.
      
 Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
Best to keep all Windows in primary partitions and install Linux in logical partitions in one extended partition.

Windows only boots from gpt partitioned drives with UEFI.
Ubuntu & Windows only boot from MBR(msdos) partitioned drives with BIOS.
You will need all systems in the same boot mode.

Microsoft wanted vendors to not provide new drivers for new systems back to Windows 7. So not sure if your system will fully work with Windows 7. Early Windows 8 systems were essentially the same hardware, so they seem to have worked.

 [http://www.eightforums.com/](http://www.eightforums.com/)

---

### Post by electrohandyman501 on 2013-12-15
> [COLOR=#000000]Microsoft wanted vendors to not provide new drivers for new systems back to Windows 7. So not sure if your system will fully work with Windows 7. Early Windows 8 systems were essentially the same hardware, so they seem to have worked.

Why does this not surprise me.......[/COLOR]

---

