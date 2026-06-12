---
title: "Precise Update 11.10 not notifying of 12.04.2; How to upgrade?"
date: 2013-08-23
forum: Installation &amp; Upgrades
---

### Post by raleightom on 2013-08-23
I installed from an older DVD Ubunto Desktop 11.10 Aug.23, 2013.

I tried to utilize the PRECISE UPGRADE procedure to upgrade to 12.04.2 LTS. 

I ran the update-manager with the NOTIFY FOR LONG SUPPORT VERSIONS option checked. It made over 200 updates and then I rebooted.
I ran the update-manager again and it showed that there were no updates to install.

As 11.10 is unsupported and I need to upgrade; when does the notification come ?  else How to I upgrade without notification ?

Any advice appreciated ;)

---

### Post by warrencanada on 2013-08-23
[http://askubuntu.com/questions/84501/how-can-i-change-convert-a-ubuntu-mbr-drive-to-a-gpt-and-make-ubuntu-boot-from](http://askubuntu.com/questions/84501/how-can-i-change-convert-a-ubuntu-mbr-drive-to-a-gpt-and-make-ubuntu-boot-from)

---

### Post by oldfred on 2013-08-24
Is Windows installed in BIOS mode or UEFI mode? Both Ubuntu & Windows need to be installed in the same boot mode to work.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

I think 11.10 was the first Ubuntu with secure boot for Windows 8, but had UEFI bugs. Much better if you have Windows in UEFI mode to use a newer version of Ubuntu. If Windows is BIOS, Ubuntu needs to be BIOS and Boot-Repair can convert and install back to BIOS if UEFI.

---

### Post by raleightom on 2013-08-25
Thank You WarrenCanada & OldFred for responding.  
 

 All this information is a bit much and not anything I recall ever dealing with on windows, although I needed to cleanup up that windows boot procedure you are about to see. Just didn't know how.

Currently booting straight into Ubuntu since I loaded 11.10 to disk. My Windows files look to be intact. Prior to Ubuntu, I was setup in a dual boot between Windows Vista and Windows 7. After upgrading Vista to 7, I was unable to delete Vista (it isn't usable). That is much of what the boot analysis shows. I did attempt a custom install of Linux (Ubuntu) thinking I could chose my own partition to install into. When I saw I could not, I backed out of the install (don't recall how). The final Ubuntu install, I believe, I chose the option to install beside Windows and preserve those files. I thought Ubuntu was going to utilize some of my Windows data; but, I don't think that happened. Hopefully, this provides a little background of what you will see.

In the future, I plan to have a Windows 7 or 8 (I don't really care for 8 as a user) to support what needs I have, that Ubuntu is having a problem with like my Brother MFC-J835DW all-in-one printer and possibly Magicjack Plus if it never decides to use my router. The more I learn, the more I am liking Ubuntu and not due to the price. I appreciate all the help from anyone and everyone. All said and done, I hope to have one boot managing one Windows 7 or 8 and one Ubunto 12.04.2. I am guessing Win 8.1 (Oct. 18 unless I can preview soon) will be better equipped than Win 7 to handle UEFI and other advances I am unfamiliar with. I still have no Windows in hand to use to re-install.

In one sense, this experience has overwhelmed me. In others, it is quite an adventure and at 67, I can use the brain teasing to help keep my brain alert and exercise this faulty memory of mine. 


 The Boot Info/Repair link for this system is [http://paste.ubuntu.com/6026564](http://paste.ubuntu.com/6026564) .
 

 Thanks,
 Tom

---

### Post by oldfred on 2013-08-25
Do not delete Vista as the boot files for 7 are in the sda1 partition. You may be able to move boot flag to sda2 and copy boot files to your Windows 7 install. Best to have a current version Windows repairCD in case of issues.

       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

I prefer clean installs but you should be able to upgrade to 12.04.

---

