---
title: "Stuck at Grub after 16.10 install"
date: 2017-01-07
forum: Installation &amp; Upgrades
---

### Post by SpionSkummis on 2017-01-07
I have been using Ubuntu for a couple of years and for the most part it has "just worked", so I'm kind of stumped about what to do now that I've actually got some trouble which some quick googling won't find a simple solution for.

I tried doing a fresh install of Ubuntu 16.10 on my laptop (Sony Vaio Pro 13), previously running Ubuntu 16.04 (originally 14.04, I think, and then successively upgraded). Everything seemed to go well, but after rebooting I got stuck with the "GRUB minimal BASH-like" screen (as far as I can tell, it is not the GRUB rescue, the prompt simply says "grub>").

I ran Boot Info Script from a Live USB, giving the following results (sda is the laptop harddrive, sdb is simply the USB stick): [http://paste.ubuntu.com/23757947/](http://paste.ubuntu.com/23757947/)

The partition layout of the harddrive is:
sda1 - Partition called SONYSYS, fat32
sda2 - Windows restore partition, ntfs
sda3 - ESP, fat32
sda4 - "Microsoft reserved partition", Gparted says unknown filesystem
sda5 - Root partition (formatted during install of 16.10), ext4
sda6 - Home partition (not formatted during install of 16.10), ext4
sda7 - Swap partition

Partitions sda1, sda2 and sda4 exist mostly because some people reported problems running Linux on this computer model (Sony Vaio Pro 13) and I didn't dare remove them when I originally installed Ubuntu, should I have to reinstall Windows.

I also tried running some commands in the Grub prompt, but I honestly really don't know what I should be doing or looking for.

```
grub> boot
error: you need to load the kernel first.
grub> ls
(hd0) (hd0,gpt7) (hd0,gpt6) (hd0,gpt5) (hd0,gpt4) (hd0,gpt3) (hd0,gpt2) (hd0,gpt1)
grub> ls (hd0,gpt1)
efi/
grub> ls (hd0,gpt3)
Boot/ bootmgr bootnxt efi/ Temp/
grub> ls (hd0,gpt5)
error: unknown filesystem.
```

I guess not being able to load the kernel and reporting my root partition (which i assume should be hd0,gpt5) as "unknown filesystem" are at least part of the problem. But other than that, I have no idea what is going on.

Sorry about the wall of text. Any suggestions about what to do would be greatly appreciated!

---

### Post by yancek on 2017-01-07
You have two EFI partitions on the same drive (sda1 and sda3) which is never a good idea.  Not sure how that would happen.  You do seem to have the correct files for both windows and Ubuntu on sda1.  Ubuntu is on sda5, what's on or was on sda4?  Was that a windows partition?  The drive/partition info shows it as a windows filesystem.  If you have a windows DVD, you might use the repair option to run chkdsk on it.

Since 16.04 will be supported until April, 2021 and 16.10 until July, 2017, was there something not working on 16.04 that prompted you to install the newer version?

---

### Post by oldfred on 2017-01-07
Your sda1 may be a hidden FAT32 just for Sony's own utilities for repair or configuration.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

But Sony in UEFI mode has usually had issues booting anything other than "Windows Boot Manager".
If only running Ubuntu, the work around is to rename the ubuntu entry to read in UEFI as "Windows Boot Manager".

       
 **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description. Assumes default ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 
Yours is sda3 (?), so have to add parameters for drive & partition.
 New Windows entry - assumes default sda1  add -p 2 if sda2:
sudo efibootmgr -c -L "Windows Boot Manager" -p 3 -l "\EFI\Microsoft\Boot\bootmgfw.efi" 

You may still have old Windows UEFI entries. So have to keep track of which is which as all may have same description in UEFI boot menu.
      
 # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr) 
    
Other Work arounds (also in link below in my signature):
Copy to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114)
Rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

---

### Post by SpionSkummis on 2017-01-09
> **yancek said:**
> You have two EFI partitions on the same drive (sda1 and sda3) which is never a good idea.  Not sure how that would happen.  You do seem to have the correct files for both windows and Ubuntu on sda1.  Ubuntu is on sda5, what's on or was on sda4?  Was that a windows partition?  The drive/partition info shows it as a windows filesystem.  If you have a windows DVD, you might use the repair option to run chkdsk on it.

Since 16.04 will be supported until April, 2021 and 16.10 until July, 2017, was there something not working on 16.04 that prompted you to install the newer version?Thank you for the reply.

Both sda1 and sda3, as well as sda4, were on the drive when I bought the computer. sda1 is flagged as hidden, and since it's called SONYSYS I assume it is used by some repair tool or the like. sda4 is untouched and I have no idea what's on it. I kept it since I feared I might have to reinstall Windows at some point.

Regarding the choice of 16.10, I had upgraded to 16.04 via at least one or two of the intermediate versions and even though the upgrades went a lot smoother than I had expected, since upgrading to 16.04 I had an increase in appcrashes and generally lower stability. So I simply thought that, hey, if I'm to make a fresh install I might as well try the latest version.

---

### Post by SpionSkummis on 2017-01-09
> **oldfred said:**
> Your sda1 may be a hidden FAT32 just for Sony's own utilities for repair or configuration.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

But Sony in UEFI mode has usually had issues booting anything other than "Windows Boot Manager".
If only running Ubuntu, the work around is to rename the ubuntu entry to read in UEFI as "Windows Boot Manager".

       
 **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description. Assumes default ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 
Yours is sda3 (?), so have to add parameters for drive & partition.
 New Windows entry - assumes default sda1  add -p 2 if sda2:
sudo efibootmgr -c -L "Windows Boot Manager" -p 3 -l "\EFI\Microsoft\Boot\bootmgfw.efi" 

You may still have old Windows UEFI entries. So have to keep track of which is which as all may have same description in UEFI boot menu.
      
 # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr) 
    
Other Work arounds (also in link below in my signature):
Copy to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114)
Rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
Thank you for the reply!

sda1 is flagged as hidden in Gparted, so you're probably correct. 

The BootInfo summary from Boot-Repair can be found at [http://paste2.org/eK8cyZkp](http://paste2.org/eK8cyZkp).

I haven't tried renaming yet, as I'm still reading up on your links. If there's anything in the BootInfo summary that points towards another solution, please tell me. Otherwise I'll try renaming the Ubuntu entry.

---

### Post by oldfred on 2017-01-09
You are showing Secure Boot enabled.
Often better with it off.

You have a Sony. Everyone we have seen will not boot anything other than "Windows Boot Manager" as they use description as part of boot. UEFI standard says not to do that.

There have been several work arounds. An old one was to make/rename grub/shim as the Windows boot file. You are showing these which might indicate you did that rename before? Ubuntu's boot files would not normally be in Microsoft's /EFI boot folder. Some old versions of Boot-Repair would also do this:
/EFI/Microsoft/Boot/grubx64.efi
/EFI/Microsoft/Boot/shimx64.efi

Now several other work arounds are suggested. The rename of Windows files would stop working when Windows did updates & overwrote it. And from grub you can only boot working Windows. So if Windows turns on fast startup with updates, or gets corrupted and needs chkdsk, you have to use your Windows recover flash drive to fix & be able to boot Windows. If Windows UEFI entry is still a Windows entry then you can usually directly boot it from UEFI when grub entry stops working and get into its internal repair console.

Links above have the various alternatives. Usually booting a fallback or hard drive entry works. You system shows that as Sony Original HD to boot /EFI/Boot/bootx64.efi as Boot0005* in UEFI boot entries. That should be your fallback entry to boot Ubuntu.
To see entries:
sudo efibootmgr -v

You also show two Windows boot entries, one is Windows Boot0001 and Boot0007 is /EFI/Boot/bootx64.efi which also is a fallback.
Running Boot-Repair's advanced mode you should update those entries to boot Ubuntu.
 
 Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI. 
 	'Use the standard EFI file' in advanced options.

---

### Post by SpionSkummis on 2017-01-10
> **oldfred said:**
> You are showing Secure Boot enabled.
Often better with it off.

You have a Sony. Everyone we have seen will not boot anything other than "Windows Boot Manager" as they use description as part of boot. UEFI standard says not to do that.

There have been several work arounds. An old one was to make/rename grub/shim as the Windows boot file. You are showing these which might indicate you did that rename before? Ubuntu's boot files would not normally be in Microsoft's /EFI boot folder. Some old versions of Boot-Repair would also do this:
/EFI/Microsoft/Boot/grubx64.efi
/EFI/Microsoft/Boot/shimx64.efi

Now several other work arounds are suggested. The rename of Windows files would stop working when Windows did updates & overwrote it. And from grub you can only boot working Windows. So if Windows turns on fast startup with updates, or gets corrupted and needs chkdsk, you have to use your Windows recover flash drive to fix & be able to boot Windows. If Windows UEFI entry is still a Windows entry then you can usually directly boot it from UEFI when grub entry stops working and get into its internal repair console.

Links above have the various alternatives. Usually booting a fallback or hard drive entry works. You system shows that as Sony Original HD to boot /EFI/Boot/bootx64.efi as Boot0005* in UEFI boot entries. That should be your fallback entry to boot Ubuntu.
To see entries:
sudo efibootmgr -v

You also show two Windows boot entries, one is Windows Boot0001 and Boot0007 is /EFI/Boot/bootx64.efi which also is a fallback.
Running Boot-Repair's advanced mode you should update those entries to boot Ubuntu.
 
 Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI. 
     'Use the standard EFI file' in advanced options.

I may very well have renamed the files once upon a time when I first installed Ubuntu, but in that case I don't remember it.

Anyways, after reading up on your links I decided to try renaming the boot entries using efibootmgr and now Ubuntu boots perfectly. Thank you very much for your help!

---

