---
title: "Ubuntu 14.04 is installed but does not start automatically"
date: 2015-04-04
forum: Installation &amp; Upgrades
---

### Post by mirjam2 on 2015-04-04
Hi, I have problems with booting the ubuntu  14.04. The programm is installed on my computer, but does not boot  automatically when turning on the computer. I use a HP EliteBook 1020 M-5Y51

pleas see: [http://paste.ubuntu.com/10737200/](http://paste.ubuntu.com/10737200/)

Do you have any suggestions?

---

### Post by oldfred on 2015-04-04
It looks like originally or at some time you installed in BIOS/CSM/Legacy mode as you have a grub in the gpt protective MBR.
But since fstab has been updated to see /boot/efi it looks like you reinstalled or Boot-Repair converted you to UEFI install.

But HP is one of many vendors that modify UEFI to only the the "Windows" entry. That is not per UEFI standard.

You should be able to just boot this entry:

```
 BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0000,0000
Boot0000* ubuntu	HD(2,1000,f3800,087c7d2c-2031-4836-a6ec-007f6fcc6280)File(EFIubuntushimx64.efi)


```

Since you only have Ubuntu, the preferred solution is to just rename it to be Windows. Then UEFI is happy. And when grub does updates you do not have to copy grub again into other locations like the Windows efi folder or the hard drive boot folder (which you do not have, but can create). Most of the other HP users copied grub to /efi/boot and renamed bootx64.efi as they wanted a Windows entry that still booted Windows.

       Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"
**d2**:  Disable Windows in UEFI and only boot from rEFInd or grub. If Windows is #1
sudo efibootmgr -A -b 0001

 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

Other work arounds, many for dual boot with Windows:
       [URL="http://ubuntuforums.org/showthread.php?t=2234019"]http://ubuntuforums.org/showthread.php?t=2234019

      [/URL]
 HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 

 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

 
    [URL="http://ubuntuforums.org/showthread.php?t=2234019"]
[/URL]

---

### Post by mirjam2 on 2015-04-09
Thanks **oldfred** for your detailed answer, it was a great help. I have used your first suggestion, i.e., d1, and it worked perfectly. (I have not tried the second suggestion, so I cannot tell you about that.)
Mirjam

---

