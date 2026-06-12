---
title: "Cannot dual boot into Linux after fresh install, WIndows 10 loads up without GRUB"
date: 2017-08-19
forum: MINT
---

### Post by faraz_k86 on 2017-08-19
Hi,

I have windows 10 installed in UEFI mode, so I installed Linux mint in UEFI as well. 

The problem is that at boot up, GRUB does not even show up, and Windows 10 loads up automatically. I tried boot-repair as well but that did not help. Below is the output of boot-repair:

[http://paste.ubuntu.com/25349593/](http://paste.ubuntu.com/25349593/)

Can someone please help me get grub running which would allow me to boot up windows and linux.

Thanks

---

### Post by oldfred on 2017-08-19
Moved to Mint sub-forum.
Do not know Mint specific issues.
What brand/model system.

But you at some time installed grub to gpt's protective MBR for BIOS boot and added the bios_grub partition. 
But you also have grub installed in ESP - efi system partition for UEFI boot. And since fstab shows mount of /EFI/ubuntu you currently are configured for UEFI boot. Do not attempt to boot in BIOS mode.
Grub only boots Windows installed in same boot mode, so both Windows & Ubuntu must be UEFI.
And grub only boots working Windows. So best to always have a separate flash drive with Windows repair/recovery tools.

Boot-Repair also says NTFS is inconsistent. Almost always from leaving fast start up on in Windows. You need to turn that off. 
You may want to turn off UEFI Secure boot and UEFI fast boot also. You may possibly turn UEFI fast boot back on once fully reconfigured. UEFI fast boot restart systems assuming no hardware or system configuration changes.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html

[/URL]
 How to: perform a repair upgrade using the Windows 10 ISO file
[http://answers.microsoft.com/en-us/insider/wiki/insider_wintp-insider_install/how-to-perform-a-repair-upgrade-using-the-windows/35160fbe-9352-4e70-9887-f40096ec3085](http://answers.microsoft.com/en-us/insider/wiki/insider_wintp-insider_install/how-to-perform-a-repair-upgrade-using-the-windows/35160fbe-9352-4e70-9887-f40096ec3085) 
   Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 

[URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]
[/URL]

---

### Post by faraz_k86 on 2017-08-20
Thanks but I solved my own problem.

I opened command line in windows as admin and typed this command. ```
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
```. Then shut down not reboot (I don't know if this matters though) then I was welcomed by the very familiar grub menu :)

---

