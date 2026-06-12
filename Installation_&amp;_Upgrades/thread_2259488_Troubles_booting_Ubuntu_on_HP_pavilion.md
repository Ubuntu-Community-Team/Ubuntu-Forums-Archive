---
title: "Troubles booting Ubuntu on HP pavilion"
date: 2015-01-04
forum: Installation &amp; Upgrades
---

### Post by Cath_Hester on 2015-01-04
Hi, 
I'm hoping for some sage advice with getting Ubuntu to boot - I'm new to this, and not so great with computers, so please excuse my lack of knowledge! 

I have a new desktop and wanted to remove windows 8 and use only ubunto as my OS (have previously installed and used this on my laptop without any probs). I have turned off secure boot and fastboot in the bios options, and installed from a USB and although the option of ubunto now appears on the boot menu, it won't actually boot. I have booted successfully as a trial from the USB and then run the boot-repair, and still no luck. Do I need to run the boot-repair with backup and rename EFI files? I didn't want to do this without checking that this is correct first! Anything else I should be doing?

my boot repair URL is:

[http://paste.ubuntu.com/9669290/](http://paste.ubuntu.com/9669290/)

Please let me know if you have any advice or suggestions, thank you!

---

### Post by oldfred on 2015-01-05
HP among many vendors now only boots Windows. The actually violate UEFI spec and make UEFI look for Windows in description only only allow that to boot.

We have several work arounds, but since you only have Linux we just add a new entry for "Windows" that really boots grub or shim. Shim is for secure boot but you really do not need that.

       
 **d1**:  If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

Other work arounds:
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

More info on efibootmgr
      
 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

Other HP and other single boot with similar UEFI issues
      
 Boot Ubuntu 14.04 LTS 64-bits on external hdd - HP Envy 17 w/Windows 8.1 
[http://ubuntuforums.org/showthread.php?t=2256244](http://ubuntuforums.org/showthread.php?t=2256244)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)


 Sony Vaio Pro  hard coded to only boot "Windows Boot Manager"
[http://ubuntuforums.org/showthread.php?t=2196415](http://ubuntuforums.org/showthread.php?t=2196415)
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"
[http://ubuntuforums.org/showthread.php?t=2200818](http://ubuntuforums.org/showthread.php?t=2200818)
Sony Vaio Pro SVP-1x21 - Arch but similar settings needed for any Linux Haswell
[https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21](https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21)

---

### Post by Cath_Hester on 2015-01-08
Hi oldfred, thank you for your time and reply. I am sorry to report that I am really struggling. I have tried the d1 solution but got sudo: efibootmgr: command not found. I then tried the bootrepair with the EFI rename option but no luck. Ubuntu still appears on my boot options, but it is not booting even when manually selected. I have no idea what to even try next. Any thoughts?

---

### Post by Gordonbp531 on 2015-01-08
This is what I had to do on my Acer:
Go into the BIOS and on the Security Tab, set a Supervisor password.
This allowed me to edit the UEFI boot settings, and add Ubuntu as a trusted boot option.

Maybe you need to do something similar on your HP?

---

### Post by oldfred on 2015-01-08
If you boot in BIOS/CSM mode you do not have efibootmgr.
Make sure you boot in UEFI mode with live installer.
From UEFI boot menu you should have two choices, UEFI - name and just name where the name if the name or label of your flash drive. The one with just the name is BIOS.

This also shows boot screens so you know which way you are booting.
       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Cath_Hester on 2015-01-09
Thanks both gordon and oldfred. I am booting in UEFI if I'm not horribly mistaken. esc and f9 and a list of options - UEFI boot sources USB and ubuntu. Able to boot from USB, but when a try ubuntu I get "boot device not found". When I'm in the terminal I get efibootmgr: comand not found. Why is this? I have even tried a clean install again, and no help - in fact I think it is worse as now I can't even access the boot repair anymore. Any thoughts other that it being time to convert my shiny new computer into an expensive anchor?

---

### Post by oldfred on 2015-01-10
Not sure after reinstall what settings would be in UEFI. Grub adds a new entry when it installs and UEFI remembers all entries, so you need to manually houseclean older entries with efibootmgr if your UEFI does not let you edit from inside it.

If you boot in BIOS mode efibootmgr is not available.
And you may have issues with secure boot on, need to make sure it is off.
Live installer loses all changes when you reboot, so any software you add to live installer must be reinstalled each time you boot. You can have persistence if you flash drive is larger, but that just saves downloading, not the installing. Or you probably have to reinstall Boot-Repair to flash drive.

---

### Post by ubfan1 on 2015-01-10
I think efibootmgr needs to be separately installed. Try
sudo apt-get install efibootmgr
in a terminal (Crtl-Alt-t) when are are on the internet (either wired or wireless).
Then try the efibootmgr command.

---

### Post by Cath_Hester on 2015-01-10
Thanks oldfred and ubfan1, I'll give those suggestions a try later on today.

---

### Post by Cath_Hester on 2015-01-11
Thanks for your patience, oldfred - I can now access efibootmgr and I have the boot option "windows boot manager" appearing on the UEFI boot menu so at least there has been some progress. I am still having the issue with 'Boot device not found" when I select ubuntu and the same with windos boot manager. I can still only boot from live USB. Do I need to delete all other boot managers/entries in efibootmgr? Which ones to keep? I was a bit reluctant to go deleting stuff in case I would permanently damage something. Also when I look in GParted I see the boot flag against the sda1 (FAT32) but I think ubuntu is in sda2. Please excuse my ignorance, but is this important?

---

### Post by ubfan1 on 2015-01-12
The boot flag should be on the EFI partition, so that's OK.  One other trick is to copy on the EFI partition the shimx64.efi and grubx64.efi from /EFI/ubuntu into /EFI/Boot, then rename /EFI/Boot/shimx64.efi to /EFI/Boot/bootx64.efi (like on the install media).  A failed boot attempt may try to run that and work.

---

### Post by oldfred on 2015-01-12
The Windows boot entry should have worked. The UEFI has been modified to only boot an UEFI entry with Windows in the description.

ubfan1's suggestion is our choice when users still have Windows. Even though they only allow the Windows description, they also allow the hard drive entry. So we edit the normal hard drive entry to be ubuntu and then boot the hard drive entry in UEFI.

I do not think with HP any ubuntu entry will work. But either work around, the Windows name (that is grub) or the hard drive entry (that is grub) should work.

Post this after you have also followed ubfan1's suggestions.

sudo efibootmgr -v

---

### Post by Cath_Hester on 2015-01-16
Thankyou both ubfan1 and oldfred - I am very grateful for your patience!
could I please have explicit instructions - eg what to type in the terminal - for ubfa1's suggestion?

In the meantime this is the current output from sudo efibootmgr -v

ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 000F
Timeout: 2 seconds
BootOrder: 0001,0002,000F,000D,000E,0005,0006,0003,0000
Boot0000* ubuntu    Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0001* USB Floppy/CD    Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0500000001)..BO
Boot0002* USB Hard Drive    Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0200000001)..BO
Boot0003* Windows Boot Manager    Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0005  USB Floppy/CD    Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0500000000)..BO
Boot0006  Hard Drive    Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0200000000)..BO
Boot000D* UEFI: IPv4 Realtek PCIe GBE Family Controller    ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(c454442fdf8b,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0..BO
Boot000E* UEFI: IPv6 Realtek PCIe GBE Family Controller    ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(c454442fdf8b,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000..BO
Boot000F* UEFI: VerbatimSTORE N GO 5.00    ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(2,0)HD(1,1f80,746080,c3072e18)..BO
ubuntu@ubuntu:~$

---

### Post by oldfred on 2015-01-17
Do you have a USB Floppy/CD? If not I would remove those entries.

Your entries are not what I have seen as standard UEFI entries.
See problem 2 here, that has your similar vendor entries:
[https://wiki.debian.org/GrubEFIReinstall](https://wiki.debian.org/GrubEFIReinstall)

Have you updated your UEFI/BIOS to the latest version?

This is a more typical entry, but I do not know the details on why there are different styles?
```
 Boot0004* ubuntu	HD(2,200800,32000,da9378d7-ebb6-11e3-867e-60029205e206)File(EFIubuntushimx64.efi)


```

If not USB - CD use this to delete those entries:
       sudo efibootmgr -v
ls /sys/firmware/efi/vars
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

Lets make a new folder and hard drive boot entry. You do not yet have a /EFI/Boot folder.

 From live installer mount the efi partition on hard drive, lines with # are comments only:
#Mount efi partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies.
mount /dev/sda1 /mnt
#only if not already existing
mkdir /mnt/EFI/Boot
cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
# If new folder created, the bootx64.efi will not exist, skip this command
mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
# make grub be hard drive boot entry in UEFI. If not existing, may have to update UEFI also with efibootmgr.
mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi

---

### Post by Cath_Hester on 2015-01-19
Thankyou oldfred. I agree the output looks a bit odd. I assume the 'floppy' is the DVD, so I haven't delected this. It is a brand new computer running grub2. 
I'm afraid I did not get far this time:

ubuntu@ubuntu:~$ mount /dev/sda1 /mnt
mount: only root can do that
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ mkdir /mnt/EFI/Boot
mkdir: cannot create directory &#8216;/mnt/EFI/Boot&#8217;: Permission denied
ubuntu@ubuntu:~$ 

any suggestions?

---

### Post by oldfred on 2015-01-19
It used to be you did not have to have sudo with liveCD as everything was default.
Try adding sudo before every command, but live installer does not have a password.

---

### Post by Cath_Hester on 2015-01-23
Thanks oldfred. I'm still not having any success and I'm about to leave for about 4 weeks, so I'll wait and take my pc to someone who is more able than me to fix it when I get home either by getting it to boot properly or just going back to windows - groan. Thank you for both your time and patience, I'm sure if I was more experienced this would have worked out. Will leave the thread open, so when it is fixed I can post the solution.

---

