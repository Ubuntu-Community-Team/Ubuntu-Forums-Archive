---
title: "UEFI Ubuntu Boot Problem - HP P001TX"
date: 2014-07-24
forum: Installation &amp; Upgrades
---

### Post by palerdot on 2014-07-24
Hi,

I recently purchased a HP P001TX laptop with windows 8.1 preinstalled. I installed linux, but the grub disappeared and the machine automatically goes into windows. I tried Boot repair, and the url is

[B][http://paste.ubuntu.com/7848548/](http://paste.ubuntu.com/7848548/)

Please let me know on how to proceed. Thanks.
[/B]

---

### Post by oldfred on 2014-07-24
This says grub installed correctly, error code 0 is no error.

And this says Ubuntu is in UEFI NVRAM memory so it should be a boot choice. Can you choose it from UEFI menu or one time boot key. (probably not)
 Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

   BootOrder: 0002,0001,3001,2001,2002,2003
Boot0000* USB Hard Drive (UEFI) - SanDisk U3 Cruzer Micro
Boot0001* Windows Boot Manager
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot3000* Internal Hard Disk or Solid State Disk
Boot3001* Internal Hard Disk or Solid State Disk
Boot3002* Internal Hard Disk or Solid State Disk
Boot3003* Internal Hard Disk or Solid State Disk
Boot0002* [COLOR=#ff0000]ubuntu[/COLOR].

HP's have been consistent so far. Everyone has been modified to only boot Windows and work arounds required.
      
 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

Most find this works.
      
 Rename /efi/boot/bootx64.efi, copy shim or grub from /efi/ubuntu into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.

More info in link in my signature including major caution if reinstalling Ubuntu.

---

