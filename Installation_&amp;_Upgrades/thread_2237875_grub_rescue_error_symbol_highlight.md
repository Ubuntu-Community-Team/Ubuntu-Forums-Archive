---
title: "grub rescue error: symbol highlight"
date: 2014-08-04
forum: Installation &amp; Upgrades
---

### Post by aldo3 on 2014-08-04
Hi everybody,
today I installed from scratch ubuntu 14.04 (overwriting an existing 13.04) on my hp with UEFI. After the process, at the first startup I got this grub error. I tried to recover with boot-repait, many times as you can see here: [http://paste.ubuntu.com/7951398](http://paste.ubuntu.com/7951398) and here: [http://paste.ubuntu.com/7952036](http://paste.ubuntu.com/7952036) but I can't get the error. Every time I noticed that Restore options were unchecked.
I just tried some workarounds found in the forum, but none worked. 
Someone can help me, please?
thanks

Aldo

---

### Post by oldfred on 2014-08-04
Install looks normal.
The error is usually from upgrades?
 Ubuntu 14.04 Update breaks grub, resulting in "error: symbol 'grub_term_highlight_color' not found" 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977)
You need to chroot &   use dpkg-reconfigure grub-pc instead of grub-install directly, so that the system knows that it needs to run grub-install on that drive the next time grub is upgraded.

Rather than just a reinstall of grub to efi partition, try the full uninstall and reinstall in advanced options.  That is a chroot and should do the same as a dpkg reconfigure. And with UEFI it is not grub-pc but grub-efi-xxx depending on whether you have secure boot version or not.

Have you tried booting with secure boot off? You do not show the secure boot versions of grub & kernels installed.

And HPs have issues booting anything other than Windows. 
Many have to copy grub to /efi/Boot and rename bootx64.efi.

      
 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
Envy M6 Change boot order sudo efibootmgr-o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)

    
Other workarounds for UEFI that only boots Windows:

 [http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

---

### Post by aldo3 on 2014-08-04
Hi oldfred, thanks for your reply.
This error comes with fresh installs, I used to run ub 13.04 alongside win8 with secure boot disabled directly from bios, but on the live disc I have chosen to format the old system files. I just tried few commands from the lunchpad post you reported aka grub-install & chroot, but nothing at all. Are you suggesting I have to try the same procedure but with grub-efi-amd64 package? I have also to specify where the efi partition is? because I have tried it, but I got an error about proper partition labelling udev (I put --efi-directory=/dev/sda2).
Now the first step I have is just to have a grub startup screen, then I will think about it, thanks

---

### Post by oldfred on 2014-08-04
You do not have grub-pc as that is the BIOS version.
There are two grub-efi packages, one signed and the other grub-efi-amd64. 
I think they updated name over grub-efi, so currently they have a difference for 64 bit & Mac, but evenually they expect to have a 32 bit UEFI version also.

---

### Post by aldo3 on 2014-08-06
During boot-repair process I type the commands to install grub-efi-amd64, so I'm quite sure it gets the right package. But I notice in boot-info report (that I linked in my fisrt post) that I alway get en error, even if can't understand which one. If I'm right, it's about not having an MBR, but I was thinking I did not need it; perhaps I have to manually check the restore MBR option in boot-repair?

---

### Post by oldfred on 2014-08-06
If you have UEFI, you do not have a boot loader in the MBR.

Error code 0 is no error, so grub reinstalled correctly.
Reinstall the GRUB of sda6 into the MBR of sda
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

Boot-Repair has not been updated for 14.04 and is looking for grub-efi not the correct grub-efi-amd64 so that may be the error.

---

### Post by aldo3 on 2014-08-06
trying to force the commands by hand I type the following sequence:

```
sudo mount  /dev/sda6 /mnt
sudo mount  /dev/sda2 /mnt/boot/efi
sudo mount  /dev --bind   /mnt/dev
sudo mount  /dev pts --bind   /mnt/dev/pts
sudo mount  /proc --bind /mnt/proc
sudo mount  /sys --bind   /mnt/sys
sudo chroot /mnt

dpkg --configure -a
apt-get install -fy 
apt-get purge -y --force-yes grub*-common shim-signed linux-signed* 
apt-get install -y --force-yes grub-efi linux
grub-install  --target=x86_64-efi --boot-directory=/mnt/boot  --efi-directory=/mnt/boot/efi --bootloader-id=grub --no-uefi-secure-boot  --recheck --debug
```

but I return the error:
grub-install: ebug/modinfo.sh deosn't exist. Please specify --target or --directory

EDIT:
I slightly changed the commands into these, I got no error, but still not working:
```
sudo mount  /dev/sda6 /mnt
sudo mount  /dev/sda2 /mnt/boot/efi
sudo mount  /dev --bind   /mnt/dev
sudo mount  /dev pts --bind   /mnt/dev/pts
sudo mount  /proc --bind /mnt/proc
sudo mount  /sys --bind   /mnt/sys
sudo chroot /mnt

dpkg --configure -a
apt-get install -fy 
apt-get purge -y --force-yes grub*-common shim-signed linux-signed* 
apt-get install -y --force-yes grub-efi-amd64 linux
grub-install  --target=x86_64-efi --boot-directory=/boot/efi   --efi-directory=/boot/efi --bootloader-id=grub  --no-uefi-secure-boot  --recheck --debug
```

---

### Post by oldfred on 2014-08-06
This has slightly different directions for UEFI chroot.
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)

---

### Post by aldo3 on 2014-08-06
That link imho is not "complete" because the uefi partition destination for grub-install is missing, and i think that is part of the problem. i still have some questions:
1) my EFI partition is /dev/sda2  mounted in /boot/efi, i have to add --efi-directory=/boot/efi or /boot/efi/EFI ? from [https://wiki.archlinux.org/index.php/GRUB#UEFI_systems_2](https://wiki.archlinux.org/index.php/GRUB#UEFI_systems_2) seems the first one. 
2) then i don't know if i have to install grub on ubuntu partition or uefi partition, in the second case i have to choose in which directory, /boot/efi or /boot/efi/EFI. the same link suggest the second, but it didn't work.
3)the echo part
echo "configfile (hd0,gpt#)/boot/grub.cfg" > /boot/efi/ubuntu/grub.cfg
                                     #Tell grub to load grub.cfg from /boot
is not needed, because that line is just written in the file

---

### Post by oldfred on 2014-08-06
If you do not have a grub.cfg in /efi/ubuntu then the echo may be needed.

I think it depends on how you mount or if internally already mounted which set of instructions on where to install.

Without any mount:
 /EFI/Boot
/EFI/Microsoft/Boot
/EFI/ubuntu

And fstab mounts at 
       /boot/efi

So from within your working install it is 
/boot/efi/EFI/Boot
/boot/efi/EFI/ubuntu

But if you manually mount from live installer or chroot then it depends.

And you install grub to a drive, and generally with UEFI just specifying sda will install grub in the efi partition. With BIOS install you have to install to the MBR, but if you install to a partition it is in the first sector or boot sector of the partition. I have seen one or two users with grub's BIOS boot installed to the partition boot sector of the efi partition which is not correct.

---

### Post by aldo3 on 2014-08-07
In last test, after mount and chroot, I typed simply grub-install --target=x86_64-efi --no-uefi-secure-boot /dev/sda2. Not only it did not work, but also it let not the system startup by livecd, so i had to first open bios setup. Maybe this can be an evidence of which directory i have to use?

EDIT - Some light at the end of the tunnel?

I found in another post [http://ubuntuforums.org/showthread.php?t=2237263](http://ubuntuforums.org/showthread.php?t=2237263) you suggested to use efibootmgr. So i tried my boot options are:

Boot0000 Ubuntu
Boot0001 Windows Boot Manager
Boot0003 grub
Boot2001 usb drive uefi
Boot2002 internal cd dvd drive uefi
Boot3000 int hdd
Boot3001 int hdd
Boot3003 int hdd

I tried to type sudo efibootmgr -n 0003 and at startup i see e black/purple screen, then the ubunt login screen. Definitively I have a grub problem...

Next on ubuntu i tried to make that boot option definitive with -o option, but at the reboot i see always the same error message

---

### Post by oldfred on 2014-08-07
I am just about out to suggestions.

I know a few give up on UEFI boot and just use BIOS boot, which still works for just about every system.

Some have had success with rEFInd, but one or two still had issues.

 Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

---

### Post by aldo3 on 2014-08-11
thanks for showing some alternatives, i'll read your links. but i think the problem is getting the system to load any bootloader. i noticed that when i load the livedvd, first on screen appears the message "/EFI/BOOT/fallback.efi not found". maybe my EFI needs the boot directory name case sensitive? i'm also asking myself why the boot order sometimes is rewritten and sometimes isn't. i'd try to delete 3000 and 3001 boot entries, but i'm not sure of that and i'm afraid of losing what i've got until now...
any suggestions? thanks

---

### Post by oldfred on 2014-08-11
That is a known issue.
Could not open "\EFI\BOOT\fallback.efi"
[https://bugs.launchpad.net/ubuntu/+bug/1241824](https://bugs.launchpad.net/ubuntu/+bug/1241824)

Post #11 in bug report has one work around I have seen suggested.

Secure boot:
 copy /EFI/ubuntu/shimx64.efi to /EFI/BOOT/fallback.efi
copy /EFI/ubuntu/grubx64.efi to /EFI/BOOT/grubx64.efi
 Nonsecure boot:
copy /EFI/ubuntu/grubx64.efi to /EFI/BOOT/fallback.efi

UEFI updates from efi partition and saves entries.
You can and should back up entire efi partition before any changes.

You can delete & add UEFI entries yourself. But some systems either UEFI or Windows seem to reset order to make Windows first and then may only boot hard drive entry. A few with Ubuntu only where they erased Windows have had to add a /efi/Microsoft/Boot folder with the Windows efi file name that really is grub to boot.
       [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by aldo3 on 2014-08-11
Justo to talk about MBR agaiin, here [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977) post #110 and #115 it's said that grub is (part of it) installed in the efi partition MBR and the error is caused because an that part is not changed during installation, searching for a file that in newer version has been not ported. Can be the same case even here? can i manually install that?

---

### Post by oldfred on 2014-08-11
The fix was to manually boot and run dpkg to totally update, or chroot into install and run the dpkg. I think Boot-Repair's total un-install and reinstall of grub does the same sort of update.

But it is that type of issue.

The efi partition and MBR are two totally different ways to boot. You use efi partition for UEFI booting and MBR for BIOS booting. The two boot methods are not really compatible, so you can only choose when you boot from UEFI/BIOS.

---

