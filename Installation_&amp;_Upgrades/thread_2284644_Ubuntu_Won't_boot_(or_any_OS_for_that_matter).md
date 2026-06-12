---
title: "Ubuntu Won't boot (or any OS for that matter)"
date: 2015-06-30
forum: Installation &amp; Upgrades
---

### Post by Rajendra_Adhikari on 2015-06-30
I started from installing Fedora linux on top of windows 8 (wishing for dual boot), and had issues with booting.I have been messing around with the hard-disk and boot-loader, and formating drives and all. (I have my data backed-up).
Right now, I did a clean install of Ubuntu 15 on a clean drive, but it won't boot. All I want is a functional os ](*,).
Live Ubuntu works though, and I am using live ubuntu right now.

The output from boot-repair attempted: [http://paste.ubuntu.com/11802310/](http://paste.ubuntu.com/11802310/)
Can somebody please help me out.

Thanks.

---

### Post by Rajendra_Adhikari on 2015-07-01
Hi,
I tried messing around more, formated the whole hard-drive, and here is the new result of running boot-repair: [http://paste.ubuntu.com/11802864/](http://paste.ubuntu.com/11802864/)
Any idea whats going on?
Thanks.

---

### Post by Bucky Ball on 2015-07-01
Welcome. You need to switch off secure boot in the BIOS and take Windows out of hibernation too is a good idea. Install Ubuntu in EFI mode, not legacy which it looks like the mistake here (you have an EFI partition but no Ubuntu entry in it). Boot repair can fix some EFI problems. Have you tried fixing it with that or only used Boot Repair to create the bootinfo? 

When you get to the partitioning section of the install, what are you doing? Are you using the 'Something Else' option and partition manually?

---

### Post by Rajendra_Adhikari on 2015-07-01
Hi,
Thank you for the reply.
I have turned off secured boot.
I have enabled 'UEFI only' boot mode. 
I booted my USB flash-drive containing live Ubuntu 15 in UEFI mode, selected Install, then 'Something else', then created a new Partition Table on my Harddrive (Effectively deleting everything), then created 3 partitions:
1. EFI system partition (size 500 MB).
2. Linux Swap partition (size 10 GB).
3. ext4 partition size (100 GB).

I tried installing Ubuntu 15 on the 100 GB partition. The installation went fine (apparantly).
When the computer reboots, the Ubuntu fails to boot.

tI boot into live Ubuntu in my flash drive. I tried running boot-repair. It complained that I didn't have any BIOS-partition, which I created as instructed. It then complained that I didn't have EFI partition, (even though I think I have 500 MB one). I proceeded anyway. And hence the [http://paste.ubuntu.com/11802864/](http://paste.ubuntu.com/11802864/) I posted.

Since, I created a completely new partition table (which I believe is same as formatting the harddrive ?), I don't think windows is relevant any more?

Thank you.

---

### Post by oldfred on 2015-07-01
UEFI has its own NVRAM and saves entries. You may still have a Windows entry there. You can use efibootmgr to remove that entry.

       # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

efibootmgr -b XXXX -B

What model Lenovo?

Some other model Lenovo's had these issues:

 Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

---

### Post by Rajendra_Adhikari on 2015-07-01
Mine is Lenovo Thinkpad Yoga.

So, I followed your instruction and removed the entry for Windows Boot Manager (even though it was second in the priority order, first being ubuntu). The output from efibootmgr now is:

ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 000A
Timeout: 2 seconds
BootOrder: 000D,0000,0001,0002,0003,0006,0007,0008,0009,000A,000B
Boot0000  Setup    FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
Boot0001  Boot Menu    FvFile(126a762d-5758-4fca-8531-201a7f57f850)
Boot0002  Diagnostic Splash Screen    FvFile(a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380)
Boot0003  Lenovo Diagnostics    FvFile(3f7e615b-0d45-4f80-88dc-26b234958560)
Boot0004  Startup Interrupt Menu    FvFile(f46ee6f4-4785-43a3-923d-7f786c3c8479)
Boot0005  Rescue and Recovery    FvFile(665d3f60-ad3e-4cad-8e26-db46eee9f1b5)
Boot0006* USB CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)
Boot0007* USB FDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
Boot0008* ATA HDD0    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f600)
Boot0009* ATA HDD1    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f601)
Boot000A* USB HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803)
Boot000B* PCI LAN    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)
Boot000D* ubuntu    HD(2,145f6800,119800,3f001bad-398a-462f-8fd1-dfb9237a9783)File(\EFI\ubuntu\shimx64.efi)

I can't seem to locate the \EFI folder though. I mounted the EFI system partition, but the partition was empty. I also looked at the ext4 partition where Ubuntu was installed but the EFI folder is not there too. 
Should I be able to find the \EFI\ubuntu\shimx64.efi from the Ubuntu running from live CD? If yes, where should it be?
Also, can someone enlighten me what HD, VenMsg and FvFile means and how they work? 
Thanks.

---

### Post by oldfred on 2015-07-01
HD is just the drive. Not sure what VenMsg & FvFile are, but they must be from Lenovo.

You have an ESP - efi system partition. It is FAT32 formatted. With parted it is set as the ESP with the boot flag, but other tools use different ways to set it as ESP. It internally is a long GUID code.

It is this:
 /EFI/Boot
/EFI/Microsoft/Boot
/EFI/ubuntu
/EFI/refind/refind_x64.efi

   And fstab mounts at:
/boot/efi
So if booted it is 
/boot/efi/EFI/ubuntu

If you mount from live installer adn ESP is sda2:

 sudo mount /dev/sda2 /mnt
then
/mnt/EFI/ubuntu


 Lenovo Yoga 11s (Intel i5/Intel HD 4000)
Needed this: acpi_backlight=vendor 
[http://ubuntuforums.org/showthread.php?t=2188199](http://ubuntuforums.org/showthread.php?t=2188199)
[http://ubuntuforums.org/showthread.php?t=1911972](http://ubuntuforums.org/showthread.php?t=1911972)
Yoga2
[http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/](http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/)

---

### Post by Rajendra_Adhikari on 2015-07-02
Ok, so after manually deleting the entry for windows boot manager, and then restarting the boot-repair tool (which asked me to run a bunch of commands on terminal), I finally got my Ubuntu to boot;\\:D/

Here is the output from the efibootmgr (from the successfully booted Ubuntu)

BootCurrent: 000C
Timeout: 2 seconds
BootOrder: 000C,0000,0001,0002,0003,0006,0007,0008,0009,000A,000B
Boot0000  Setup    FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
Boot0001  Boot Menu    FvFile(126a762d-5758-4fca-8531-201a7f57f850)
Boot0002  Diagnostic Splash Screen    FvFile(a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380)
Boot0003  Lenovo Diagnostics    FvFile(3f7e615b-0d45-4f80-88dc-26b234958560)
Boot0004  Startup Interrupt Menu    FvFile(f46ee6f4-4785-43a3-923d-7f786c3c8479)
Boot0005  Rescue and Recovery    FvFile(665d3f60-ad3e-4cad-8e26-db46eee9f1b5)
Boot0006* USB CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)
Boot0007* USB FDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
Boot0008* ATA HDD0    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f600)
Boot0009* ATA HDD1    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f601)
Boot000A* USB HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803)
Boot000B* PCI LAN    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)
Boot000C* ubuntu    HD(1,800,64000,e1f5267b-4bbf-4440-a347-40fd8b624757)File(\EFI\ubuntu\shimx64.efi)

the xhimx64 is located as \boot\efi\EFI\ubuntu\shimx64.efi

I will now try to install back windows 8 and will see what happens.
Thanks for the help.

---

