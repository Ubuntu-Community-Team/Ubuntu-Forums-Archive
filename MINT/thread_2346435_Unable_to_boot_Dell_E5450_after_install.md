---
title: "Unable to boot Dell E5450 after install"
date: 2016-12-14
forum: MINT
---

### Post by lostinuefiland on 2016-12-14
I tried to install a 2nd instance of Mint on my laptop, but grub wasn't seeing the 2nd install.. I had to enable legacy boot support to boot the live CD.
I have 2 partitions (/home, /apps) I wanted to save, so I attempted to manually configure partitions.  I couldn't get it to work, so I manually deleted some old windows partitions and old root (/) partition.
I now get errors that no partitions are found, I've tried twiddling bits, etc, running boot-repair, with no luck.   I may have destroyed the UEFI boot partition, but thought grub would recreate it.

I've tried several options in the BIOS setup to enable, disable UEFI with no luck.

Here is the log to the boot-repair..  also, I manually created the bios/grup partition on sda2, thought I read somewhere that may need to be on /sda1?  I'm also away from home, so I was only able to get a mint 18 install disk.  Hopefully that's a derivative for support here :)

[http://paste2.org/28C41P2x](http://paste2.org/28C41P2x)

Thanks for any assistance.

---

### Post by oldfred on 2016-12-14
Somehow you converted sda1 to ext4, but it says it is the ESP - efi system partition. That may be just the boot flag?
For UEFI boot you must have the ESP, FAT32 formatted 300 to 500MB with boot flag. No other partition with gpt should have boot flag, but a few systems will not boot anything unless at least one partition has boot flag.
And you show the bios_grub partition as sda2 for BIOS boot.

But nowhere is fstab or kernels, so either script did not find install or you do not have / (root) partition.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by lostinuefiland on 2016-12-14
Yeah, I think I just realized that... I just created an EFI partition and reset those flags.  boot flag did at the esp automatically previously.  I also get an error trying to run efibootmgr.
I think I need to adjust how I boot into the liveCD.  I may attempt to adjust that and reattempt an install once I get efibootmgr working at the prompt.  Hopefully, it will populate my EFI partition for me.
Trying that now...

---

### Post by oldfred on 2016-12-14
I do not think efibootmgr works in BIOS mode.
You have to boot installer in UEFI mode.
How you boot install media UEFI or BIOS, is then how it installs.
But then you have to have system set in that same boot mode.

I just installed 17.04 with UEFI. I just had to create a new 25GB  / (root) partition on my sda SSD. I had not fully partitioned it. And I have ISO on sdb which I boot directly with grub. It took about 10 minutes to install. But not sure if I will configure it or not, that is more to test if my configure scripts work with newer version or not.

---

### Post by lostinuefiland on 2016-12-14
so, I can't seem to boot my external dvd in uefi mode.  dell bios doesn't show it?  my original install was non-uefi mode, so why didn't it boot then?  do I still need a proper boot partition?  install seamed to finish fine, then, no bootable system after restart.

I figured a workaround.     When booted up in legacy mode on the LiveCD, there was a partition mounted to /cdrom.
Here, there was a boot/EFI/ folder that had the files I needed.    
BOOTx64.EFI  grubx64.efi

  I manually mounted my EFI partition, copied these files there, and then DELL recognized it was a valid EFI boot partition.  
Then, when I tried to boot, grub wasn't configured correctly and dropped into the grub prompt.
I just had to manually boot using the 
set root=....
linux /boot/vm.....
initrd /boot/init....
boot

  Once booted into my actual linux, I just ran update-grub, and grub-install /dev/sda

  I'm all working now.. Thanks for the help.

Ok.. jumped the gun a little...  It still drops to the "grub>" prompt when booting up.. however, I can still manually enter the parameters and boot up.
I thought the ESP partition needed to be first, so I moved that around a little.  From reading, it seems like I didn't need the grub_bios partition if I have the EFI partition, so I tried deleting that, but boot-repair was complaining.

My current setup.
[http://paste2.org/FLDz1OPa](http://paste2.org/FLDz1OPa)

Also, notice I don't have /boot/efi directory created anywhere... likely because I didn't actually install with UEFI mode.. 

Here is the other odd error
"[COLOR=#BA2121][FONT=InconsolataMedium]The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating a EFI partition (FAT32, 100MB~250MB, start of the disk, boot flag)."
[/FONT][/COLOR]but I think I do?

 Again, any help appreciated.

---

### Post by howefield on 2016-12-15
Thread moved to the "*MINT*" forum.

---

### Post by lostinuefiland on 2016-12-15
Found the issues, after scanning the plethora of other people that have had similar issues...  1st, boot-repair definitely has bugs on it's setup detection logic.
It also doesn't help that grub has gone through some radical changes over the last couple years and several recommendations over that times don't currently apply.

 My clue was somebody posted  [COLOR=#6A6A6A][FONT=Roboto]**grub**[/FONT][/COLOR][COLOR=#545454][FONT=Roboto]-[/FONT][/COLOR][COLOR=#6A6A6A][FONT=Roboto]**install**[/FONT][/COLOR][COLOR=#545454][FONT=Roboto] --[/FONT][/COLOR][COLOR=#6A6A6A][FONT=Roboto]**target**[/FONT][/COLOR][COLOR=#545454][FONT=Roboto]=x86_64-[/FONT][/COLOR][COLOR=#6A6A6A][FONT=Roboto]**efi**[/FONT][/COLOR][FONT=Roboto]**[COLOR=#545454] [/COLOR]**[/FONT] which gave me errors about missing  /boot/grub/x86_64-efi/ files... The wrong version of "grub" was actually installed when I booted in legacy mode for my original install. 
 I went into Software manager and install "grub-efi".   Once I did this, and reran update-grub, grub-install, I got the proper message about installing for EFI target.  
It also then created /boot/efi/EFI/ubuntu folder with grubx64.efi    file.
Then... I went into my DELL BIOS and pointed my UEFI boot config to that file in that directory... NOW... it boots correctly with a Grub menu!!!! yea!
[FONT=Roboto][B][COLOR=#545454]


[/COLOR][/B][/FONT]

---

### Post by oldfred on 2016-12-15
Glad you figured it out.

Boot-Repair does have an advanced option like a chroot that has you uninstall grub-pc(BIOS) and install grub-efi-amd64(UEFI). But you have to have the ESP partition in advance as Boot-Repair does not create partitions.

---

### Post by lostinuefiland on 2016-12-15
the problem I had was boot-repair kept saying it couldn't find my efi partition even though I had one.  perhaps related to the incorrect grub installed, not sure.  Ill run it again to see if it's happy now that it's actually working.

---

### Post by lostinuefiland on 2016-12-15
Looks like it's still a little confused... 

Above in the output, it says:
> =================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this installed-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [email]boot.repair@gmail.com[/email])


But then later..
> =================== Advice in case of suggested repair
BIOS-Boot detected. You may want to retry after deactivating the [Separate /boot/efi partition:] option.
Do you want to continue?


  It may be partially, because I still have a bios_grub flag on a partition?  Either way, it's confused.

---

### Post by oldfred on 2016-12-15
No, its how you boot.

You have UEFI system.
But UEFI systems have three ways to boot, each incompatible with the other.
UEFI with Secure boot, standard UEFI, and CSM/BIOS/Legacy.
And you separately boot flash drive in any of the three ways. 
So system must then be set to boot in same boot mode as you boot flash drive. How you boot flash drive installer is then how it installs.

So Boot-Repair is saying you have an UEFI system but booted in BIOS mode, or at some point you booted in different mode or install is BIOS and you booting in UEFI, so it is seeing the diffferenc. Best to always boot in one mode or the other.

Boot-Repair can only fix a BIOS boot on gpt if you have the bios_grub partition.
Or Boot-Repair can only fix an UEFI boot if you have an ESP - efi system partition.
And Boot-Repair does not create partitions, so you must have those. I normally add both partitions to all new drives using gpt before doing anything else.

---

