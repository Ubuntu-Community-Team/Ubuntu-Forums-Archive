---
title: "Dual Boot with Windows 8 and Ubuntu"
date: 2014-08-09
forum: Installation &amp; Upgrades
---

### Post by brythebeerbaron on 2014-08-09
I have read through several threads and I have tried many different configs but I still can not get Dual Boot for Windows 8 (Pre installed) and Ubuntu using GRUB.  Each are installed on separate HDs. I can boot Ubuntu no problem but Windows 8 just goes to "Preparing Automatic Repair" and never goes anywhere.  I suspect that the Windows HD (sda) has a corrupt MBR but in truth I don't think I understand GRUB and MBR well enough to diagnose the issue the correctly.  Output from boot-repair below.  I'd appreciate if anyone could point out where the problem might be and then I could focus my troubleshooting there.  Is the failure to mount the partitions on sda a real issue or just noise from boot repair?  I can mount all partitions read only from Ubuntu.  Thanks for any help or suggestions. 

[http://paste.ubuntu.com/8002916/](http://paste.ubuntu.com/8002916/)

---

### Post by dave131 on 2014-08-10
I noticed that boot-repair has a notice in it that it can't mount sda1, stating some options there that would indicate that Windows might not have been shutdown correctly prior to the boot of Ubuntu (says it might be hibernating).  I don't know if that has some affect on what you are doing or not.

---

### Post by brythebeerbaron on 2014-08-10
Yes, I noticed that too.  I can mount it read only in Ubuntu.  I can't get back into Windows so I can't try and shut it down again from windows.

---

### Post by oldfred on 2014-08-10
You do have to have fast boot or the always on hibernation off if dual booting. Usually best to have secure boot off also.
What model HP?
Are you booting to grub menu?
Can you go into UEFI and choose Windows? Or use one time boot key, with HP may be f9. Many systems are f12 or f10.

You have installed Ubuntu in BIOS Mode on sdb, but have Windows in UEFI mode on sda.
It looks like a Boot-Repair fix reinstall grub in UEFI mode into Windows efi partition, but you still have sdb in MBR partitioning. Generally UEFI requires gpt partitioning and only BIOS uses MBR(msdos) partitioning. I thought your configuration would not even work, but have seen one or two others. Much better to reinstall Ubuntu to sdb and have its own efi partition on sdb. Some even suggest disconnecting Windows drive during install to make sure they do not get mixed up. But you can install with Something Else and create partitions as required. But must choose to install grub2's boot loader to the drive the is sdb.

       It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[URL="http://ubuntuforums.org/showthread.php?t=2218154"]http://ubuntuforums.org/showthread.php?t=2218154
[/URL]
 Envy M6 Change boot order sudo efibootmgr-o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
HP Envy M6
[URL="http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working"]http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working
      [/URL]
 HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts. Key board issues try differnet USB ports maybe  front.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

    [URL="http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working"]
[/URL]

[URL="http://ubuntuforums.org/showthread.php?t=2218154"]
[/URL]

---

