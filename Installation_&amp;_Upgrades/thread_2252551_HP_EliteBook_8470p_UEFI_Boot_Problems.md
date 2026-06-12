---
title: "HP EliteBook 8470p UEFI Boot Problems"
date: 2014-11-12
forum: Installation &amp; Upgrades
---

### Post by Thom_Dalladay on 2014-11-12
Hello,

Recently I've installed Ubuntu 14.10 on my HP EliteBook 8470p. The install itself has been "successful", however I'm having boot problems.  Upon rebooting, I get "No bootable image found".  In order to boot the machine, I have to go into Boot Options, select Boot from EFI file and navigate to find grubx64.efi.

I have manually added a UEFI entry via efibootmgr, pointed to "\\EFI\\ubuntu\\grubx64.efi".  This has made no difference, however.efi,

Has anyone else had this problem? If so, how was it resolved?  I don't want to use Legacy boot - I prefer keeping to UEFI Native (Without CSM).

---

### Post by ajgreeny on 2014-11-12
Thanks to a previous post by the UEFI expert on this forum, oldfred, the following info from his post at [http://ubuntuforums.org/showthread.php?t=2251757&p=13161466#post13161466](http://ubuntuforums.org/showthread.php?t=2251757&p=13161466#post13161466) may help you.

> HP  has modified UEFI to only boot a system in UEFI mode with Windows in  the description. But we have several work arounds for HP.

Several options that others have posted that work:
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Other HP's, most manually renamed files like bootx64.efi.

 It seems hp firmware do not allow you to boot anything other than  windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
Envy M6 Change boot order sudo efibootmgr-o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
HP Envy M6
[http://askubuntu.com/questions/34625...is-not-working]("http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working")
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)                                                                                                                                                                                                                     [COLOR=Navy]For info on UEFI boot install & repair:
[/COLOR] [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)
       Please use Thread Tools above first post to close thread when/if answered completely.

---

