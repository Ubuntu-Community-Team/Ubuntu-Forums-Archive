---
title: "GRUB2: When I choose Windows 8, error invalid EFI file path"
date: 2013-05-20
forum: Installation &amp; Upgrades
---

### Post by microice on 2013-05-20
I had a problem with install Ubuntu 13.04 next to Windows 8. I have a Dell inspiron 15 notebook with UEFI.


In Boot-setup I changed to Legacy Boot on and switched UEFI boot off. Then I installed Ubuntu but the computer always starts Windows.


I have followed the instructions here : UEFI but it hasn't helped.


I used Boot-Repair and it helped; but It did not list Windows 8 in grub. Then I wrote with QGRUBEditor Windows 8.


Now when I turn on my notebook in grub I have Windows 8 listed but if I choose it I get the error:

> Invalid EFI file path.
this is my bootinfoscipt:

[Deleted due to formatting.] See link below

what can i do to fix it??

---

### Post by oldfred on 2013-05-20
I do not know how you posted it. Probably from a word processor with the wrong line endings. 
Better to use Boot-Repair and just post link to BootInfo report it creates.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

To be able to dual boot easily both systems need to be UEFI. If Ubuntu is BIOS, you cannot use its boot entries for Windows as BIOS writes data for system differently than UEFI does.

---

### Post by microice on 2013-05-20
Here it is : [http://paste.ubuntu.com/5684533/](http://paste.ubuntu.com/5684533/)
If i had UEFI secure : ON i couldn't run Ubuntu from CD. And now if i change UEFI secur:on i can't do anything, just reboot PC, so i must change UEFI secure : off

---

### Post by oldfred on 2013-05-20
Right now you have no way to boot in UEFI mode as all the files in the efi partition are missing. If you manually look in efi partition are files there? Script is not showing any and Windows has to have its and a lot of other files we do not see as script only shows boot files.

You have Ubuntu in BIOS/CSM mode as it has a bios_grub partition, but you installed grub2's boot loader to the partition, so it cannot boot. If just Ubuntu on a gpt partitioned drive you could install grub2's boot loader to the MBR and boot.

Better to use Boot-Repair to uninstall grub-pc(BIOS) and install grub-efi (UEFI) and that should get you booting Ubuntu.
But some Windows systems only boot with secure boot on. If you boot in secure boot mode, Boot-Repair will install signed versions of grub & kernel to let you boot Ubuntu with secure boot on.
Also some systems only boot the Windows efi file. Yours is now missing.

Do you have a Windows 8 repair flash drive? Or can you use a restore function to recover the missing Windows efi files?

It also looks like you did not turn off hibernation as Boot-Repair is saying it is hibernated and NTFS will not let us mount it.
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
[http://www.eightforums.com/](http://www.eightforums.com/)

---

### Post by microice on 2013-05-20
How to manually look in efi partition? How can i use restore functicon?

---

### Post by oldfred on 2013-05-20
You can use any file browser from a live install to mount and look at efi partition.

You would have to look at the manual for your system to see exactly how it recovers. All Windows systems have two recovery one is really just the Windows repair and the other is the vendor recovery. But both usually need the efi partition to load those files. Some systems have a one key recovery that just restores system.

---

### Post by microice on 2013-05-20
where is it recovery?

---

### Post by oldfred on 2013-05-20
You have to look in your manual on how to use this:

>  /dev/sda6   1,926,948,864 1,953,523,119    26,574,256 Windows Recovery Environment (Windows)



---

### Post by microice on 2013-05-21
How to do this?

---

### Post by oldfred on 2013-05-21
Again it varies by vendor but almost all of them require the files in the efi partition.

You may have to contact vendor and order a recovery DVD, if you have no backups of the original efi partition. You should be able to get Ubuntu working in the mean time.

How did you erase data in efi partition. You might be able to use testdisk and see if deeper search shows any files, but that is more if partition was deleted.
       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition")
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

    
 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by microice on 2013-05-21
Thanks

---

