---
title: "no dual boot"
date: 2015-06-26
forum: Installation &amp; Upgrades
---

### Post by onur6 on 2015-06-26
I installed ubuntu 2 days ago. After I install it, I expected a dual-boot screen but it doesn't even ask and start with windows 8.

Here is my boot repair report:[http://paste.ubuntu.com/11776419/](http://paste.ubuntu.com/11776419/) 

I tried what it says me to try, "write [COLOR=#000000]bcdedit /set [/COLOR][COLOR=#666666]{[/COLOR][COLOR=#000000]bootmgr[/COLOR][COLOR=#666666]}[/COLOR][COLOR=#000000] path [/COLOR][COLOR=#BB6622]**\E**[/COLOR][COLOR=#000000]FI[/COLOR][COLOR=#BB6622]**\u**[/COLOR][COLOR=#000000]buntu[/COLOR][COLOR=#BB6622]**\s**[/COLOR][COLOR=#000000]himx64.efi" in cmd. It didn't give any error, however still did not work.
[/COLOR]
**Please help me guys**

---

### Post by oldfred on 2015-06-26
Your main issue is that you have an HP.
HP modifies UEFI to boot only allowing a description that has "Windows" in UEFI mode. That is not per UEFI standard. There is one thread where newer HP now does have a convoluted way to add other systems. Is your UEFI updated to latest version from HP, it may include a way?

But most with HP do a work around. System will also boot with a hard drive entry which is /EFI/Boot/bootx64.efi. So we copy grub into /EFI/Boot and rename grubx64.efi to be bootx64.efi and from UEFI menu boot a hard drive entry.
Details in link in my signature and several attached threads with HP.

You also have grub legacy installed to the gpt drive's protective MBR for a BIOS boot. That should never be used and you should never boot in CSM/BIOS/Legacy mode. You also tried to install wubi, which does not really work on gpt partitioned drives. Wubi is not supported anymore as it does not work with gpt. It was intended for a trial of Ubuntu using hard drive and worked well with Windows 7 or old versions. But now it is not an easy to install version, since not supported. 
Just uninstall wubi from inside Windows.

       HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)

            HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

You already show many duplicate UEFI entries for the hard drive. Best to delete the duplicates.
       # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

---

