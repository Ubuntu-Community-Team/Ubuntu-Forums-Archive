---
title: "Ubuntu won't dual boot with windows 8"
date: 2014-10-17
forum: Installation &amp; Upgrades
---

### Post by Martin_Kellner on 2014-10-17
I can't get ubuntu 14.04 to dual boot with Windows 8. The word thing is,  I can boot ubuntu from within windows using system settings,  searching for bios and then choose ubuntu to boot from. How can I make my computer load grub from start?

---

### Post by yancek on 2014-10-17
Did you use the wubi installer to install Ubuntu inside windows?  Was your windows 8 preinstalled?  Does it use UEFI to boot?

---

### Post by oldfred on 2014-10-17
Did you install Ubuntu in BIOS boot mode not UEFI boot mode?

May be best to see details, post link to summary report.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Martin_Kellner on 2014-10-18
I used a usb stick to install, not WUBI. Windows 8 was preinstalled and I'm a bit uncertain i ubuntu tries to use UEFI. In boot repair, the separate boot/efi partition is ticked and set to sda2.
If I boot into windows, choose restart while pressing shift key I will be given the choice to boot into ubuntu. Choosing that, I will get somthing that looks like grub and ubuntu will boot fine but it's really annoying having to go through windows.

Summary report: [http://paste2.org/AgAjmngW](http://paste2.org/AgAjmngW)

---

### Post by yancek on 2014-10-18
I've read a number of posts indicating that with an HP computer uses EFI differently, apparently needs windows files.  Not really sure as I don't use UEFI but maybe someone else more familiar can give you details.

---

### Post by oldfred on 2014-10-18
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
      
 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

Most seem to do the rename of bootx64.efi and make that file really be grub. Then you can set UEFI to boot hard drive.


 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order](http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order)

---

