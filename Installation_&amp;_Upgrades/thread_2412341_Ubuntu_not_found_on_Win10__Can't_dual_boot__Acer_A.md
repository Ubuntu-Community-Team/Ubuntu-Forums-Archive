---
title: "Ubuntu not found on Win10 / Can't dual boot / Acer Aspire TC-780"
date: 2019-02-11
forum: Installation &amp; Upgrades
---

### Post by zentraveler on 2019-02-11
*Hi, everyone! This is my first time here and first time with Linux. Thanks for any help you can provide! I tried to be as detailed as I could...*
[B]
My computer does not recognize Ubuntu and I can't boot from it[/B][B].
[/B]I installed Ubuntu 18.04 from USB-stick via [installation tutorial]("https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#0") and this video: [How to Dual Boot Ubuntu 18.04 and Windows 10 [2019]]("https://www.youtube.com/watch?v=u5QyjHIYwTQ"). Evidently, with an Acer computer, Windows 10, and my Bios, I can't dual boot ([https://neosmart.net/wiki/easybcd/uefi/](https://neosmart.net/wiki/easybcd/uefi/)).

*Please. Help.*

Here are my specs and everything I've tried to no avail...
[LIST]
[*]Computer: Acer Aspire TC-780 desktop, Intel Core i3-7200 CPU @ 3.90Ghz, 8GB RAM, 1TB hard drive
[*]Windows 10 Home 64-bit, 1809 version
[*]Bios: R02A3 and I upgraded it via the Acer website to R02-B2
[/LIST]


My Installation:

[LIST=1]
[*]Created ~80GB 'free space' partition on hard drive.
[*]Used Rufus to mount Ubuntu 18.04 .iso onto removable 32GB USB-stick
[*]Installed as 'Something else' and 'alongside windows boot manager'
[*]20GB Logical /, 4GB Logical swap area, 64GB Logical /home
[*]Finished installation process
[*]Remove USB-stick and restart, go into Bios to change boot order, no Ubuntu option
[/LIST]

Note: I can not login or access the installed Ubuntu. I can only access the 'Try Ubuntu' from my USB-stick

Things I've tried:
[LIST]
[*]Win: disable 'Fast Startup' in Power Settings
[*]Win: disable 'Hibernate' in Power Settings
[*]Win: Update & Security > Recovery > Advanced Setup > Restart > Troubleshoot > Advanced Options > UEFI Firmware Settings > Restart (THIS JUST TAKES ME INTO THE BIOS WITH NO UEFI SETTING OPTIONS! See image below)
[*]Bios: updated Bios via Acer website to the newest version, R02-B2
[*]Bios: Secure Boot disabled
[*]Bios: Set Supervisory Password
[*]Bios: THERE ARE NO "Select a UEFI file as trusted for executing" option or any "HDD0 > EFI" options as other threads suggest. See image below.
[*]Created a Boot-Repair USB-stick and loaded it - I couldn't install it from within Linux, it said "yannubuntu" not found. Boot-Repair Log: [http://paste.ubuntu.com/p/YWDhmbJdV4/](http://paste.ubuntu.com/p/YWDhmbJdV4/)
[*]cmd: admin command prompt: bcdedit set {bootmgr} path \EFI\ubuntu\grubx64.efi - the operation completed successfully (recommended from threads)
[*]cmd: admin command prompt: bcdedit set {bootmgr} path \EFI\ubuntu\shimx64.efi - the operation completed successfully (recommended from threads)
[*]cmd: admin command prompt: bcdedit set {bootmgr} path \EFI\BOOT\BOOTx64.EFI - the operation completed successfully (this is the exact file pathway on my USB-stick from the 18.04.1 .iso file)
[*]cmd: admin command prompt: bcdedit set {bootmgr} path \EFI\BOOT\grubx64.efi - the operation completed successfully (this is the exact file pathway on my USB-stick from the 18.04.1 .iso file)
[*]cmd: admin command prompt: powercfg.exe /h off
[*][EasyBCD]("https://neosmart.net/EasyBCD/") bootloader-modification tool - I can't work with the Linux options, because of UEFI mode, as listed [here]("https://neosmart.net/wiki/easybcd/uefi/").
[*]Installed Ubuntu on an external 160GB formatted hard drive and tried to boot from there - couldn't
[*]I can't find my Windows Installation Disk to try to restore Win10 to MBR, as suggested [here]("https://askubuntu.com/questions/62440/is-it-possible-to-boot-ubuntu-using-the-windows-bootloader").
[/LIST]

[IMG]https://photos.app.goo.gl/ZLBnnUb6Q9LqQ8FSA[/IMG]

[ATTACH=CONFIG]282476[/ATTACH][ATTACH=CONFIG]282477[/ATTACH][ATTACH=CONFIG]282478[/ATTACH][ATTACH=CONFIG]282479[/ATTACH]
[IMG]https://photos.app.goo.gl/ZLBnnUb6Q9LqQ8FSA[/IMG]

---

### Post by oldfred on 2019-02-11
Line 634 has this:
>  Windows is hibernated, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.) 



Turn off Windows fast start up.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Your Ubuntu entry in UEFI is was not a correct entry. It looks like Boot-Repair added a correct entry. 
But normally with Acer it would show unknown, until you enabled trust. 

       
 Old entry, typical of removed hard drive:
Boot0001  ubuntu	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)

New entry that looks correct (line 1167):
Boot0001* ubuntu	HD(1,GPT,b5c33ef3-4698-4279-8c45-7344d62fb008,0x800,0x32000)/File(EFIubuntushimx64.efi) 

    
All Acer have need you to set "trust" on the ubuntu UEFI boot files from within UEFI.
Secure boot needs to be on to set trust.
       
 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[https://community.acer.com/en/categories/predator](https://community.acer.com/en/categories/predator)

---

### Post by zentraveler on 2019-02-11
Thanks for reading through the Boot-Repair log. I'm not familiar with Linux code.

> 
All Acer have need you to set "trust" on the ubuntu UEFI boot files from within UEFI.
Secure boot needs to be on to set trust.
       
Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:


Thanks, however, I can't find any place in my Bios to set/change Acer Trust Settings. As most forum posts I've checked, it says that in the Security Tab there is "[COLOR=#000000]*Select an UEFI file as trusted for executing*[/COLOR]" that's greyed out until you disable Secure Boot and/or Set-up Supervisor Password and then it becomes active in blue. I've done both and this "trusted" option isn't in my Bios. See the fourth attached image of my Bios Security Tab.

I've Googled and haven't found a way to 'set trust on Acer Aspire' yet other than posts about the aforementioned. I updated my Bios to the latest from Acer.

---

### Post by oldfred on 2019-02-11
Your screen shots show legacy enabled which means UEFI Secure Boot is off.
You need UEFI secure boot on, and supervisor password to get correct screens.

Do you have a UEFI hard drive boot entry? Some call it fallback.
That uses /EFI/Boot/bootx64.efi. 
Generally it is a copy of the Windows boot file as a backup way to boot.
We used to manually copy shimx64.efi to that, but now grub installs to bootx64.efi or Boot-Repair auto copies shimx64.efi so the new backup entry will boot Ubuntu.

---

### Post by zentraveler on 2019-02-11
Thanks again!

> **oldfred said:**
> Your screen shots show legacy enabled which means UEFI Secure Boot is off.
You need UEFI secure boot on, and supervisor password to get correct screens.

Okay, I changed the settings. Attached photos.
[ATTACH=CONFIG]282481[/ATTACH][ATTACH=CONFIG]282482[/ATTACH][ATTACH=CONFIG]282483[/ATTACH]

> Do you have a UEFI hard drive boot entry? Some call it fallback.
That uses /EFI/Boot/bootx64.efi. 
Generally it is a copy of the Windows boot file as a backup way to boot.
We used to manually copy shimx64.efi to that, but now grub installs to bootx64.efi or Boot-Repair auto copies shimx64.efi so the new backup entry will boot Ubuntu.

I don't know how to check this? In my Bios I only have "Windows Boot Manager" available as a 'Hard Disk Drive' boot option. Is this what you mean? See photos.

[ATTACH=CONFIG]282484[/ATTACH][ATTACH=CONFIG]282485[/ATTACH]

---

### Post by zentraveler on 2019-02-11
> **oldfred said:**
> Do you have a UEFI hard drive boot entry? Some call it fallback.
That uses /EFI/Boot/bootx64.efi. 
Generally it is a copy of the Windows boot file as a backup way to boot.
We used to manually copy shimx64.efi to that, but now grub installs to bootx64.efi or Boot-Repair auto copies shimx64.efi so the new backup entry will boot Ubuntu.


I did a search in Windows (C:) and found a number of .efi files. None of them called "bootx64.efi". Mostly "bootmgfw.efi", "bootmgr.efi", and "memtest.efi" files. See photo.
[ATTACH=CONFIG]282486[/ATTACH]

---

### Post by zentraveler on 2019-02-12
Not sure if this helps or not but the three partitions that I created when installing Ubuntu don't show up in cmd/diskpart...

[ATTACH=CONFIG]282487[/ATTACH]

---

### Post by yancek on 2019-02-12
Your windows EFI files are on the EFI partition which shows as disk 0 partition 1 and your Linux partitions show as disk 0 partition 4, 7 and 8.  This shows in the background image (white with blue fonts) in your last post.  You obviously have an EFI entry for Ubuntu as shown in the boot repair.  I'm not familiar with Acer UEFI so hopefully someone else will have suggestions.

---

### Post by oldfred on 2019-02-12
Not sure how you mount ESP in Windows to see it.
I am in my system, so ESP is mounted at /boot/efi and partition has folders /EFI and the /EFI/Boot & /EFI/ubuntu.

```
fred@Bionic-Z170N:~$ ll /boot/efi/EFI
drwxr-xr-x  2 root root 32768 Oct 23 11:23  Boot/
drwxr-xr-x  3 root root 32768 Feb  6 21:22  ubuntu/
```

---

