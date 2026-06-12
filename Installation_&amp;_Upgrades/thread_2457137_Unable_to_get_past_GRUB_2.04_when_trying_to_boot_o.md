---
title: "Unable to get past GRUB 2.04 when trying to boot or get permissions"
date: 2021-01-26
forum: Installation &amp; Upgrades
---

### Post by 216ann on 2021-01-26
This is a continuation of an issue that initially involved Bios & now has migrated to a grub issue.
See the entire discussion at: ubuntuforums.org/showthread.php?t=2456255&page=2&p=14015707#post14015707
I tried posting in General but noone responded and now think that I posted in the wrong area but don't know how to change it or delete.

Initially, I was given a newer Toshiba laptop to replace my old HP one.  
I got what I thought was a bright idea to get my old 7200 HD with Ubuntu 20 to replace the 5400 HD in the Toshiba.
It could not boot just sitting there with the Toshiba & Ubuntu logos without ever ending.  
I tried to use a USB to boot off but I had issues with the bios supervisor password which I eventually solved.
Grub recovery did not solve my issues, nor trying to switch it to legacy/CSM & AHCI.
Previously it would say that the initramfs file was missing and give me a grub rescue prompt
Now it says: 
```
error: file '/boot/grub/i386-pc/normal.mod' not found
Entering rescue mode...
grub rescue>
```
I followed the directions at:  gutsytechster.wordpress.com/2018/07/24/how-to-resolve-grub-error-file-grub-i386-pc-normal-mod-not-found/
I was able to find the normal.mod in boot/grub.bak/
That allowed me to enter GNU GRUB version 2.04 with a grub prompt
When I tried to boot, it says to load the kernel first.
So I followed the link's instructions and searched for vmlinuz-5.8.0-58-generic & initrd.img-5.4.0-58-generic
I did what the link told me to do regarding insmod linux and then linux  with the paths to vmlinuz & initrd.img in the line above and booted.
It seemed to work but then it just ends with a black screen with the cursor in the most upper left corner.
It does not blink or do anything and I did not try to type anything but it sits there for hours.
As a noob, I am not sure what I am doing wrong and I also not sure if  maybe I should have picked different files (there are earlier versions  of initrd and vmlinuz).
I also tried using the version of vmlinuz without the numbers (so simply   "vmlinuz") at the end as well as various initrd.img files I found.
The error I get in grub is "error: invalid magic number."

I am thinking that the files such as initrd are broken so was thinking of following the instructions here:
linoxide.com/linux-how-to/fixing-broken-initrd-image-linux/
But I want to make sure that it is not going to break my computer.  

I would totally reformat/reinstall the ubuntu 7200HD with the USB but I  have some impt files I can't seem to completely copy off the 7200HD.
When I use the usb I can see the files but I can't copy them because I don't have permissions.
I can't seem to figure out how to get permissions on my own drive!!!   (the usb doesn't have any but the 7200HD does which I know but can't  seem to find where I can input it).  
It is very frustrating.  Please advise.  Thanks in advance.

---

### Post by yancek on 2021-01-26
>  When I use the usb I can see the files but I can't copy them because I don't have permissions.

I don't know why you would have that problem as it is not necessary to have any kind of permissions to copy FROM a device/partition but it is to copy TO.  What type of filesystem is on the drive?

The commands at the 'gutsytechster' link should work.  Do you know which partition your boot files are on?  I use the below to boot Ubuntu from the grub prompt.  You would obviously need to change the (hd0,gpt5) on the set root line with the correct partition number and change to msdos if it is not a gpt drive.  Also the exact kernel (vmlinuz) name and the correct /dev name and partition.  If you have those all correct it should boot unless as you mention, the files are corrupted.  Moving the drive from one computer to another is not likely to cause that kind of problem.  

>  grub>set root=(hd0,gpt5)
grub>linux /boot/vmlinuz-5.8.0-40-generic root=/dev/nvme0n1p5
grub>initrd /boot/initrd.img-5.8.0-40-generic
grub>boot

---

### Post by 216ann on 2021-01-26
First thanks so much for taking the time to help me.  I appreciate it.  

> **yancek said:**
> I don't know why you would have that problem as it is not necessary to have any kind of permissions to copy FROM a device/partition but it is to copy TO.  What type of filesystem is on the drive?

I am a noob so I am not sure what type of filesystem is the drive but I believe it is legacy & AHCI.  Not sure if NFTS or FAT32 orf what.  How do I check?
When booted through the live USB, I tried with the GUI to just cut and paste the files from the "other locations" of the 7200HD drive to my external HD but it said I didn't have the proper permissions.
If I have to usually use a password to get into the root of the 7200HD (when it was working) does that mean it is encrypted?
Perhaps I can't do it because I don't have "permissions" to the external HD?  Perhaps I have been thinking I don't have the permissions for the 7200HD but it is actually the permissions on the external HD that may be the problem.
How would I work around that???

> **yancek said:**
> The commands at the 'gutsytechster' link should work.  Do you know which partition your boot files are on?  I use the below to boot Ubuntu from the grub prompt.  You would obviously need to change the (hd0,gpt5) on the set root line with the correct partition number and change to msdos if it is not a gpt drive.  Also the exact kernel (vmlinuz) name and the correct /dev name and partition.  If you have those all correct it should boot unless as you mention, the files are corrupted.  Moving the drive from one computer to another is not likely to cause that kind of problem.
 
Yes I used the (hd0,msdos5) which is /dev/sda5 that corresponds to the Ubuntu 7200HD but can't boot except to grub rescue.
But I suppose the boot files are corrupted because I can't seem to load the kernel properly.  
Is there a way to use the live USB to "repair" or otherwise transfer uncorrupted files to the corrupted 7200HD?
Would we still have the problem of not being able to write or overwrite on the drive because we don't have permissions?
Thanks again for your help.

---

### Post by CelticWarrior on 2021-01-26
> [COLOR=#000000]I am a noob so I am not sure what type of filesystem is the drive but I believe it is legacy & AHCI. Not sure if NFTS or FAT32 orf what. How do I check?[/COLOR]
"Legacy" (whatever you mean by that) -> NOT a filesystem
[AHCI]("https://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface") -> NOT a file system. It's a hardware feature. 

NTFS and FAT32 are filesystems but neither is typical of Linux. FAT32 is the typical filesystem of the ESP (EFI System Partition) so it can be seen in Linux only systems in UEFI mode. Both NTFS and FAT32 are supported by all major Linux distros but NEITHER can be used to install Linux. EXT4 is since many years the standard filesystem for / , /home and all the other system partitions in Linux. Other filesystems can be used - BTFRS, ZFS, etc. - but most are still experimental.

> [COLOR=#000000]If I have to usually use a password to get into the root of the 7200HD (when it was working) does that mean it is encrypted?[/COLOR]
It depends.
Did you have to enter a password to unlock the drive and then it would load Ubuntu and ask you for the username and (a different) password to login? If so then it's definitely encrypted and your problem isn't about permission (yet). You need to decrypt and mount the decrypted partitions *before* you can do anything with it. I'm not the person to help you with that as I don't usually use encryption and I have backups so never had to decrypt anything in a live session. Maybe yancek knows how to help you.

---

### Post by guiverc on 2021-01-26
> **216ann said:**
> 
I got what I thought was a bright idea to get my old 7200 HD with Ubuntu 20 to replace the 5400 HD in the Toshiba.

Note:  Most of use standard Ubuntu releases, and not the specialist releases like Ubuntu Core 20.

The majority of us will use Ubuntu 20.04 LTS on servers or desktops, being the main product product uses the  *year.month* format.

Only specialist *snap* only releases use the *year* format, such as Ubuntu Core 20, which is a different product, with different intended use (devices, appliances, cloud etc).

---

### Post by grahammechanical on 2021-01-26
When you run the Ubuntu live session have you tried using the file manager with administrator privileges?

```
sudo nautilus
```

If that allows you to copy and paste files from the drive remember that the ownership of them will now be root and you have to change the permissions using the file manager as administrator otherwise you will not be able to do anything with these files when you are working as a standard user.

Regards

---

### Post by 216ann on 2021-01-26
Thanks for all the help.  
Yes, Celtic...I discovered that sda5 (the 7200HD) is ext4
And yes, if memory serves me, I had to enter a password to get into ubuntu then another to get sudo privileges.
So probably encrypted.

I am sorry quiverc, I guess I am so silly I did not realize the difference.   
I did install the Ubuntu LTS 20.04 I believe.  
I did NOT install "core" only the LTS

Graham, I was only able to see the files after booting into the live USB.
I can see the 7200HD files in the GUI no problem but I can only copy some of them because of my lack of privileges.
Remember I am trying to copy the files off the internal boot 7200HD to my external HD (which is not encrypted) using the booted live Ubuntu USB (Try Ubuntu).
I have never been able to figure out how to change permissions or unencrypt either the internal or external (& the USB doesn't require root sudo password).

Honestly, all I want to do right now is to reliably copy everything off that 7200HD and freshly reformat the drive.
A second option would be to figure out how to boot into the 7200HD & then copy everything.
Thanks to everyone for their help.

---

### Post by oldfred on 2021-01-26
Mixing boot modes UEFI and BIOS causes more issues.
If hardware is UEFI, best to only use UEFI.
If hardware is old, before about 2012, then it will be BIOS and UEFI will not work.

You also have to have installer in correct mode, if created by Rufus as it makes UEFI only or BIOS only installer.
Other tools create the installer that will work in UEFI or BIOS/CSM/Legacy mode and you must then only boot in UEFI mode from UEFI boot menu when booting live installer.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Have seen multiple systems where some sort of special keys may be required to open additional settings.
Some need UEFI Secure Boot on to change settings, but often better to install with secure boot off.
Some like Acer use control-S to open added settings even when Secure Boot is on.
HP only allows some changes from within UEFI, common tools do not work to change boot order or UEFI settings.

Almost all systems need to be updated to latest UEFI as vendors also have various fixes that may be needed.

---

### Post by 216ann on 2021-01-26
> **oldfred said:**
> Mixing boot modes UEFI and BIOS causes more issues.
If hardware is UEFI, best to only use UEFI.
If hardware is old, before about 2012, then it will be BIOS and UEFI will not work.
You also have to have installer in correct mode, if created by Rufus as it makes UEFI only or BIOS only installer.
Other tools create the installer that will work in UEFI or BIOS/CSM/Legacy mode and you must then only boot in UEFI mode from UEFI boot menu when booting live installer.
Thanks for the advice oldfred.
the "newer" Toshiba laptop is still 7 or more years old but I put it on legacy/CRM mode and AHCI so I don't think that is the problem anymore.
I did use Rufus on the original live USB but that seemed to have corrupted so I was told to use balena etcher.
Currently, the laptop boots fine off the USB but not the boot 7200HD.
I was told that balena etcher would work even if it were not on legacy but I don't know of a reason to try it out.  

> **oldfred said:**
> Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I am embarrassed that I didn't really understand half of what you just said.
I am not sure how to "use ppa version" from the usb...does that mean I should "Try Ubuntu" or "Install Ubuntu" or something else like with grub?
Is that the shift key pressing thing?


I was thinking that if the USB boots then that must mean the kernel, vmlinuz, initrd.img, etc must be working properly, is there any way to boot the 7200HD then "borrow" or copy the correct files from the USB when I am confronted by the grub prompt?
When I create an Ubuntu USB should I use rufus or belena etcher, should I use MBR or GPT, etc?
Please let me know.  Thanks.

---

### Post by CelticWarrior on 2021-01-27
> [COLOR=#000000]I am embarrassed that I didn't really understand half of what you just said.[/COLOR]
[COLOR=#000000]I am not sure how to "use ppa version" from the usb...does that mean I should "Try Ubuntu" or "Install Ubuntu" or something else like with grub?[/COLOR]

It means to run a live session (Try...) as you've been doing.
Then follow the instructions of the 2nd option in Boot Repair's page. It's just a matter of copying and pasting commands in the terminal.

---

### Post by 216ann on 2021-01-27
It appears that things are getting worse.
Now it looks like even trying to boot off the USB, I enter the "/boot/grub/i386-pc/normal.mod" error & am stuck in grub rescue.
I created a brand new USB Ubuntu using Rufus (MBR) & I get the same error
Finding the normal.mod in the grub.bak file allows me to get to the grub 2.04 prompt but I can't seem to get past that despite using various versions of vmlinuz & initrd.img.
I am not sure what I am doing wrong.

Also, if I eventually get the live USB working, the commands proposed in terminal appear to fix the live USB & not the boot 7200HD.  
Am I missing something...how will running sudo boot repair on the live "Try Ubuntu" USB repair the boot 7200HD drive?
Thanks for all the help...as you can tell, I really don't have any clue what I am doing.

---

### Post by yancek on 2021-01-27
>  how will running sudo boot repair on the live "Try Ubuntu" USB repair the boot 7200HD drive? 

The purpose of running boot repair suggested in post 8 is to get information on your computer and boot files.  There is a 2nd option on the page on the link posted in post 8, download it and run it from the live usb and make certain you select the option to Create BootInfo Summary.  THis won't change anything but you will get a link when it finishes and you need to post that link here so members have an opportunity to view it and make suggestions.

---

### Post by 216ann on 2021-01-27
> **yancek said:**
> Create BootInfo Summary.  THis won't change anything but you will get a link when it finishes and you need to post that link here so members have an opportunity to view it and make suggestions.
I can't cut & paste but this is what I got
[HTML]https://paste.ubuntu.com/p/scKX3sfW2D/[/HTML]

Thanks for all the help folks.

---

### Post by oldfred on 2021-01-28
You booted live installer in BIOS/CSM/Legacy mode.

You have two versions of grub installed. One BIOS in MBR and one UEFI in ESP - efi system partition.
But fstab shows mount of ESP, so last install was UEFI boot.

So set system to boot in UEFI mode and boot.
See line 291

---

### Post by 216ann on 2021-01-28
> **oldfred said:**
> You booted live installer in BIOS/CSM/Legacy mode.

You have two versions of grub installed. One BIOS in MBR and one UEFI in ESP - efi system partition.
But fstab shows mount of ESP, so last install was UEFI boot.

So set system to boot in UEFI mode and boot.
See line 291

I don't understand most of what you said but aside from the booting into USB Ubuntu, the last successful boot was into Win10 with a different 5400HD.
I am pretty sure I made the live USB MBR and I am pretty sure that 7200HD when it was removed from my old computer was in AHCI mode.
are you saying that there are two versions of grub on the same 7200HD?
Or just that the USB and 7200HD has two different versions of grub?

I first encountered this boot problem when trying to boot off the 7200HD on the laptop's default of UEFI (which I didn't realize at the time)
It simply sits there with the Toshiba and Ubuntu logos without ever going anywhere.
I was told to change to legacy/CSM mode & AHCI.  
This seemed to make progress to a grub rescue/grub prompt
**I again tried it now and the UEFI boot does the same thing. ** 
It seems to be working fine going to the Toshiba then Ubuntu logos but then goes nowhere.
This appears to be the case whether the laptop is connected to the internet or not
Last time randomly pressing keys on the keyboard was able to show that there were some processes working behind the scenes but those processes never ended
It said something about while the boot is loading they update some things in the background.
But the boot never ends.

I am very confused now.   But I do appreciate your help.

---

### Post by yancek on 2021-01-28
Your boot repair output shows, beginning at line 5:

> Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location 

Further down beginning at line 14 it shows the EFI partition with the correct EFI files needed to boot Ubuntu in EFI mode.  When you boot the computer, you should 
see a message on the screen for a few seconds telling you which key to use to access the BIOS firmware.  When you do that, look for Boot Options or an Entry to 
Boot from EFI file.  If you have an entry to boot from EFI file, look for an option to select:    /efi/ubuntu/shimx64.efi  That shows on line 301 of boot repair.

---

### Post by 216ann on 2021-01-28
> **yancek said:**
> Your boot repair output shows, beginning at line 5:

Further down beginning at line 14 it shows the EFI partition with the correct EFI files needed to boot Ubuntu in EFI mode.  When you boot the computer, you should 
see a message on the screen for a few seconds telling you which key to use to access the BIOS firmware.  When you do that, look for Boot Options or an Entry to 
Boot from EFI file.  If you have an entry to boot from EFI file, look for an option to select:    /efi/ubuntu/shimx64.efi  That shows on line 301 of boot repair.

Yes, as far as I know, the sda is the live Ubuntu USB and sda5 is the 7200HD with Ubuntu on it.
The live USB boots when computer is placed on CSM/AHCI.
The 7200HD doesn't boot either way.  
When on CSM/AHCI then it goes to grub rescue with the normal.mod not found error, which I can, after pointing to the normal.mod in grub.bak, get to the grub 2.04 prompt but no further.
When on UEFI (ie, after changing the Bios settings), the 7200HD goes to the Toshiba plus Ubuntu screen but never progresses after that.  
This is confusing because I am pretty sure that the USB is legacy/AHCI and the 7200HD was AHCI (before I took it out of the old HP laptop).
So perhaps when I first tried the boot repair it automatically installed/replaced things with an EFI version.
Whatever the case, the 7200HD boots under neither UEFI nor Legacy/CSM mode.
The USB only boots under Legacy/CSM but I could reformat under UEFI and then set bios to UEFI & USB boot.
Should I do that?  
Thanks again for all of your patience.  I appreciate it.

---

### Post by oldfred on 2021-01-28
From Report:
```
[COLOR=#ff0000]Disk sda: 298.9 GiB[/COLOR], 320072933376 bytes, 625142448 sectors
Disk identifier: 0x0448ac69
      Boot   Start       End   Sectors   Size Id Type
sda1  *       2048   1050623   1048576   512M  b W95 FAT32
sda2       1052670 625141759 624089090 297.6G  5 Extended
sda5       1052672 625141759 624089088 297.6G 83 Linux
[COLOR=#ff0000]Disk sdb: 7.51 GiB[/COLOR], 8053063680 bytes, 15728640 sectors
Disk identifier: 0x56f48570
      Boot   Start      End  Sectors  Size Id Type
sdb1  *          0  5439487  5439488  2.6G  0 Empty
sdb2       5017392  5025327     7936  3.9M ef EFI (FAT-12/16/32)
sdb3       5439488 15728639 10289152  4.9G 83 Linux

```

So sda is your HDD & sdb is a much smaller drive, probably your flash drive.
You often need to know & be sure which drive is which. 
Sometime when I reboot with a flash drive plugged in as sdb, the drives change, or sda becomes sdb and then flash drive is sda.

If you are getting Ubuntu logo, then booted thru grub. Grub has loaded & started the boot process with the kernel.
Issues then are often related to video driver or other configuration issues.

Boot in UEFI mode, & press escape key immediately after the vendor logo appears, but before grub menu would normally appear. You should then get grub menu. Grub does not by default show menu, if one system. You may have to try several times as timing can be tight.

Then see if you can boot recovery mode, or second line in grub menu.

---

### Post by 216ann on 2021-01-28
> **oldfred said:**
> From Report:
```
[COLOR=#ff0000]Disk sda: 298.9 GiB[/COLOR], 
      Boot   Start       End   Sectors   Size Id Type
sda1  *       2048   1050623   1048576   512M  b W95 FAT32
sda2       1052670 625141759 624089090 297.6G  5 Extended
sda5       1052672 625141759 624089088 297.6G 83 Linux
[COLOR=#ff0000]Disk sdb: 7.51 GiB[/COLOR], 
```

So sda is your HDD & sdb is a much smaller drive, probably your flash drive.
You often need to know & be sure which drive is which. 
Sometime when I reboot with a flash drive plugged in as sdb, the drives change, or sda becomes sdb and then flash drive is sda.

Yes, as a noob, I have been calling my 7200HD sda5 because it says "Linux" next to it so I assumed that it was just sda but perhaps the reason why all the things I have been doing is wrong because I have been using sda5 instead of simply sda by itself.
For example, I have been thinking that the 7200HD is at (hd0,msdos5) in the grub menu.  
That's where I had found the initrd.img and vmlinuz files in before (which still didn't seem to work).  

But running ls (hd0,msdos1)/  does show an efi folder...
The (hd0,msdos1)/efi/boot/ file has grubx64.efi, bootx64.efi, & other efi files in it.  
The (hd0,msdos1)/efi/ubuntu/ file has grub.cfg, grubx64.efi, bootx64.csv files in it.

> **oldfred said:**
> If you are getting Ubuntu logo, then booted thru grub. Grub has loaded & started the boot process with the kernel.
Issues then are often related to video driver or other configuration issues.

Boot in UEFI mode, & press escape key immediately after the vendor logo appears, but before grub menu would normally appear. You should then get grub menu. Grub does not by default show menu, if one system. You may have to try several times as timing can be tight.

Then see if you can boot recovery mode, or second line in grub menu.

Yes, I can get to the "GNU GRUB version 2.04" screen & prompt, claiming that it is minimal bash-like line editing
I heard you can also press shift (or is that something different?)
I am not sure how to get to boot recovery mode from there.
I looked at the link at: askubuntu.com/questions/150367/how-do-i-boot-into-recovery-mode
Previously when using Linux, it would give me a selection of three or so things some which were recovery mode some which weren't but I don't see anything but a terminal like prompt.  
And I don't get any "advanced options" or GUI type set up.  
Should I use the instructions at: **youtube.com/watch?v=r7meKJsjqfY**
Remember it appears that I am missing or have a corrupted kernel.

---

### Post by oldfred on 2021-01-28
Then you are not booting thru grub.

You use shift if booting in BIOS mode & Escape when in UEFI mode, to get grub menu to show on a system with only one install. 
If getting grub> or grub rescue> you have grub configuration issues.
With two versions of grub, one in MBR and one in UEFI, booting the wrong one will also give the grub error. Make sure you are booting in UEFI mode.

If at grub> then you can use the ls commands to see which partition is which. 
Better to unplug flash drive to avoid confusion as it also has an ESP with boot files.

ls # Do you see (hd0), (hd0,5) ? If so, run the next command. Change if not hd0,5.
configfile (hd0,5)/boot/grub/grub.cfg

---

### Post by 216ann on 2021-01-28
> **oldfred said:**
> If at grub> then you can use the ls commands to see which partition is which. 
Better to unplug flash drive to avoid confusion as it also has an ESP with boot files.
ls # Do you see (hd0), (hd0,5) ? If so, run the next command. Change if not hd0,5.
configfile (hd0,5)/boot/grub/grub.cfg

Thanks for the explanation, although I don't understand all of it.
I am currently not using the USB and only trying to use UEFI to boot off  the 7200HD (which I believe is AHCI) based on your recommendation.
After pressing ESC, I get to the grub screen.
Running "ls", I get (proc), (hd0), (hd0,msdos5), & (hd0,msdos1).
Which should I run under?

---

### Post by oldfred on 2021-01-28
ls # Do you see (hd0), (hd0,5) ? If so, run the next command. Change if not hd0,5.
configfile (hd0,5)/boot/grub/grub.cfg

The (hd0,5) is the same as (hd0,msdos5) or (hd0,gpt5). The type of partitioning is not required in the command.

I do highly recommend gpt over MBR(msdos).
Microsoft has required gpt for all UEFI systems.
UEFI recommendends gpt.
Ubuntu will let you install in UEFI boot mode to MBR(msdos) partitioned drives.
The only time you must use the now 40 year old MBR is if you want to install Windows in the BIOS boot mode.
You can also use gpt with BIOS boot of Ubuntu (but not Windows). 

ls

---

### Post by 216ann on 2021-01-28
> **oldfred said:**
> ls # Do you see (hd0), (hd0,5) ? If so, run the next command. Change if not hd0,5.
configfile (hd0,5)/boot/grub/grub.cfg
The (hd0,5) is the same as (hd0,msdos5) or (hd0,gpt5). The type of partitioning is not required in the command.

Hi, I ran that configfile command but it goes back to the toshiba plus ubuntu screen without progressing further.
Some process is working in the background which looks like that updating stuff while waiting for boot that I experienced before.
Unless something switched it back, the bios is set to boot the 7200HD using UEFI even though as I stated, I believe I had the 7200HD on ACHI when it was in my old laptop.
Should I be toggling the settings?

> **oldfred said:**
> 
I do highly recommend gpt over MBR(msdos).
Microsoft has required gpt for all UEFI systems.
UEFI recommendends gpt.
Ubuntu will let you install in UEFI boot mode to MBR(msdos) partitioned drives.
The only time you must use the now 40 year old MBR is if you want to install Windows in the BIOS boot mode.
You can also use gpt with BIOS boot of Ubuntu (but not Windows). 
ls
I want to get the files off this Ubuntu 7200HD first.
Afterwards, I plan to do a fresh install of Ubuntu & if given the choice will choose to go UEFI/GPT (though isn't that based on the HD and not the laptop?).
I don't remember getting the choice when installing Ubuntu on the 7200HD of picking UEFI/GPT, only when I was creating the USB.
Thanks for your help.
This seems like it should be a lot easier than it has been.
?What did you think of the video at: youtube.com/watch?v=r7meKJsjqfY

---

### Post by oldfred on 2021-01-28
A drive is not AHCI.
The settings in UEFI used to access drive are required for drivers in the operating system to use it.
You do need to change to AHCI on your system.

I rarely watch videos. 
Details go by too quickly and are not explained well in most.

If drive is already partitioned, gpt or MBR then installer will not change it.
If drive is blank or over 2TB and install is UEFI, then installer will make it gpt.
Gparted still defaults to MBR for smaller drives and only defaults to gpt on drives over 2TB.
Changing from MBR to gpt will erase drive, so not recommended. 
There are tools to convert without data loss, normally but good backups required. And it complicates boot, at minimum full reinstall of grub is required.

With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting.
or in terminal, which also erases drive.
sudo parted /dev/sdX mklabel gpt  # where sdX is your drive

If reinstalling, use gparted to change to gpt. Under device in top menu, you then get this:

---

### Post by 216ann on 2021-01-28
> **oldfred said:**
> A drive is not AHCI.
The settings in UEFI used to access drive are required for drivers in the operating system to use it.
You do need to change to AHCI on your system.
If drive is already partitioned, gpt or MBR then installer will not change it.
If drive is blank or over 2TB and install is UEFI, then installer will make it gpt.
Gparted still defaults to MBR for smaller drives and only defaults to gpt on drives over 2TB.
Changing from MBR to gpt will erase drive, so not recommended. 
There are tools to convert without data loss, normally but good backups required. And it complicates boot, at minimum full reinstall of grub is required.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting.
or in terminal, which also erases drive.
sudo parted /dev/sdX mklabel gpt  # where sdX is your drive
If reinstalling, use gparted to change to gpt. Under device in top menu, you then get this:

??? This appears to be a discussion primarily to be made after I have successfully booted the drive or otherwise gotten a hold of the old files.
I had to change the bios to UEFI boot to comply with your recommendations...should I change it back to AHCI???
Remember that I had bios on AHCI which is what resulted in entrance straight into the grub rescue prompt.
As I stated the 7200HD was structured to boot in my old HP which was on legacy/CSM/AHCI by default.
That is what I meant by the 7200HD is AHCI.

I wasn't sure if I should continue trying to boot the 7200HD or try to use the live USB to some how access the files on the 7200HD so I can just copy and then completely reformat the 7200HD.
Am I able to do a full reinstall of grub so that I can get into the 7200HD?  
It seems like I should just be able to get some files off the USB or the internet and reboot the 7200HD...
Please advise.

---

### Post by oldfred on 2021-01-29
Do not confuse drive setting which is AHCI, RAID, or Intel RST with boot mode setting which is UEFI or BIOS/CSM/Legacy. But also if in UEFI mode, Secure Boot on or off. If UEFI Secure boot is on, then there is no option for BIOS boot as that is not secure.

Your UEFI/BIOS should have separate settings for how drive is seen AHCI, and how drive is booted UEFI.

---

### Post by 216ann on 2021-01-29
> **oldfred said:**
> Do not confuse drive setting which is AHCI, RAID, or Intel RST with boot mode setting which is UEFI or BIOS/CSM/Legacy. But also if in UEFI mode, Secure Boot on or off. If UEFI Secure boot is on, then there is no option for BIOS boot as that is not secure.
Your UEFI/BIOS should have separate settings for how drive is seen AHCI, and how drive is booted UEFI.
Appreciate the clarification.
I thought that drives done in AHCI can't be booted with UEFI?
Anyway, I am really frustrated.
Booting with CSM/legacy brings me to the grub screens & with UEFI brings me to the Toshiba/Ubuntu logos but no further.
**I am trying to either (a) access the files on the old 7200HD through the USB so that I can do a fresh install afterwards OR (b) I am trying to boot into the 7200HD (which I think are encrypted but I know the password) so I can grab the files the old fashioned way.**
_Which of these two choices would be the easiest and how would I go about doing it?_
It kind of seems like I should be able to get whatever missing/corrupted files off the live USB to "help" the 7200HD boot up correctly OR at least use the live USB to super sudo into the 7200HD and grab the files.
**The files are personal and I couldn't reproduce/replace and ones which took me years to compile.  **
Any ideas?  Thanks again for your patience.

---

### Post by oldfred on 2021-01-29
Drives fail, so backups are always required and need to be kept up to date.
And because even minor drive issues on encrypted drive can prevent recovery, you need even better, regular backups.
Encryption purpose is to prevent access from anyone else.

Can you boot live installer?
Did you use Rufus to make live installer, so it is either UEFI or BIOS but not both. Other tools to make live installer typically can be booted in either mode, but you have to choose from UEFI boot menu. One clearly UEFI:xxx and other just xxx which is BIOS boot.

If LVM & encrypted a lot more difficult to mount & decrypt volumes inside the partition.

---

### Post by 216ann on 2021-01-29
> **oldfred said:**
> Drives fail, so backups are always required and need to be kept up to date.
And because even minor drive issues on encrypted drive can prevent recovery, you need even better, regular backups.
Encryption purpose is to prevent access from anyone else.

Yes, you are right.  On Win it was always easier to backup.  As I am just learning Ubuntu, I don't really know how to back up onto another drive.  

> **oldfred said:**
> Can you boot live installer?
Did you use Rufus to make live installer, so it is either UEFI or BIOS but not both. Other tools to make live installer typically can be booted in either mode, but you have to choose from UEFI boot menu. One clearly UEFI:xxx and other just xxx which is BIOS boot.
If LVM & encrypted a lot more difficult to mount & decrypt volumes inside the partition.

I used Rufus and also Balena Etcher to make the USB, both which worked.  (With Rufus should I use the DD option?  Or the Recommended?ISO? option?)
I have been trying anything so I believe I may have tried using a version that was UEFI with Rufus.

So if you could teach me how to get through to the encrypted 7200HD drive (which I know the password for) using the live USB, that would be appreciated.
I would copy all the files (thus far, I can copy some but not all the files because I don't have "permission" and can't find where I am supposedly to change the permissions), then I would reformat the drive and fresh install Ubuntu and use the backup method you suggest.
I don't know anything about LVM (Logical Volume Management).  

I think my best bet is to either (a) use the Live USB to "Try Ubuntu", using terminal to copy the files from the encrypted 7200HD, OR (b) use grub (and maybe the internet) to try to repair the 7200HD so that it can boot by itself.  
Based on your experience, which, if either, would you suggest?
And how would I do it?
Thanks again for all your help.

---

### Post by CelticWarrior on 2021-01-29
> [COLOR=#000000]I would copy all the files (thus far, I can copy some but not all the files because I don't have "permission" and can't find where I am supposedly to change the permissions), then I would reformat the drive and fresh install Ubuntu and use the backup method you suggest.[/COLOR]

If you can see the files then it isn't encrypted.
From a live session you may need to change ownership of the folders/files to copy them. First thing you need to know is the mount point of the source. In the live session you can open Disks and click on the drive to select it (left column list) then in the partition itself on the right. Below the graphical representation of the drive you should see mounted as... Right-click and copy. Open a terminal and either right-click and paste or CTRL+SHIFT+V to paste the mount point after the following command:
```
sudo chown -R ubuntu:ubuntu <mount_point>
```
The argument "-R" means recursively and "ubuntu" is the username of the live session.
With this done you should be able to copy everything from your old user's user folder. Then you cam install a proper Ubuntu and from then on DO YOUR BACKUPS!

---

### Post by 216ann on 2021-01-29
> **CelticWarrior said:**
> If you can see the files then it isn't encrypted.
From a live session you may need to change ownership of the folders/files to copy them. First thing you need to know is the mount point of the source. In the live session you can open Disks and click on the drive to select it (left column list) then in the partition itself on the right. Below the graphical representation of the drive you should see mounted as... Right-click and copy. Open a terminal and either right-click and paste or CTRL+SHIFT+V to paste the mount point after the following command:
```
sudo chown -R ubuntu:ubuntu <mount_point>
```
The argument "-R" means recursively and "ubuntu" is the username of the live session.
With this done you should be able to copy everything from your old user's user folder. Then you cam install a proper Ubuntu and from then on DO YOUR BACKUPS!
Thanks Celtic...at least I know my files aren't encrypted 
(which is odd because when I used the 7200HD on my old HP laptop I had to put in password to get into ubuntu then another to use sudo/root.  Being a noob, I presumed that the need to use a password to access the drive meant I had encrypted it.).
When I entered the live session, it said initramfs initialization failed and some other stuff but got into the "Try Ubuntu" desktop.
Using terminal I followed advice here: askubuntu.com/questions/583909/how-do-i-check-where-devices-are-mounted
So the 7200HD is called sda & the linux partition which is the bulk of the 7200HD drive is called sda5 that is ext4
The USB is called sdb.

I went into Drives, saw the sda/7200HD drive and clicked on the sda5 partition.
But I can't seem to right click anything.  Right click works every where else and I tried several mice.
I noticed that it said "Not Mounted" so I used the instructions to mount here: cyberciti.biz/faq/mount-drive-from-command-line-ubuntu-linux/
So it is now mounted as /media/newhd/
I tried your command and eventually gave me a prompt back without errors.

Now I need to copy all the files into my external hd which is sdc.
I couldn't find the newhd through files using the GUI, so I assume I have to copy via terminal.
[B]I am presuming I would attach the usb external HD, then mount it, then transfer all the files from the sda5 to the ?sdc?(the drive)? or sdc1 (the partition)?
should I use cp or rsync or what?  [/B]
I would be appreciative if you said exactly which terminal commands I should use so I can get this right.
The last time I tried to wing it, I spent over a month trying to correct it...
_And yes, I promise I will back up...however, what is the recommended way to do that?  (such as the best app). _ 
help.ubuntu.com/stable/ubuntu-help/backup-how.html.en   tells me to use an app but doesn't say which one
Thanks for everyone who has helped me to this point.

---

### Post by CelticWarrior on 2021-01-29
You may need to copy *your*&#8203; personal files, certainly not all files from that drive.

---

### Post by 216ann on 2021-01-29
> **CelticWarrior said:**
> You may need to copy *your*&#8203; personal files, certainly not all files from that drive.
Understood but I would think that it would be safer and easier to just copy the entire drive than to pick and choose and make a mistake.
how would I do that reliably though?  
Do I use cp or rsync or what  and how do I verify?  
Is there a way to see if the contents of one file are exactly the same (including hidden and protected files) as another? Like "Merge" or compare.  
There's less than 100Gigs of files anyway.

---

### Post by CelticWarrior on 2021-01-29
You're creating problems for yourself for absolutely no reason.
You don't need any hidden files as those are settings of installed programs that you don't want to carry over from an old installation.
Copying your personal files after "chown'ing" them can be done with the file manager (Files) as you would do when copying/moving any other file in an installed system. The same for backups, all that matters is copying somewhere else your own files, the ones you would like not to loose in case of problems or drive failure. Simply use an external drive and, preferably and additionally, a cloud service of which there are many to choose from. No need, at this point, to use commands you don't understand.

---

### Post by 216ann on 2021-01-29
> **CelticWarrior said:**
> You're creating problems for yourself for absolutely no reason.
You don't need any hidden files as those are settings of installed programs that you don't want to carry over from an old installation.
Copying your personal files after "chown'ing" them can be done with the file manager (Files) as you would do when copying/moving any other file in an installed system. The same for backups, all that matters is copying somewhere else your own files, the ones you would like not to loose in case of problems or drive failure. Simply use an external drive and, preferably and additionally, a cloud service of which there are many to choose from. No need, at this point, to use commands you don't understand.
Oh, I must have misspoke.
[U]I wasn't trying to be smart, I have some website that was created in virtual box and I need to make sure EVERYTHING is copied so that it will work when I copy and then recopy it onto the fresh install.  
I am afraid that if I just copy the regular files some protected or system files that are part of the website will be lost or unusable[/U]

I first tried to go to Files to copy but got confused because there are, for example, TWO different external HDs one which says that gives an option to unmount with parent folder /media/ubuntu and another which gives the option to safely remove and says its parent folder is /media.
I am assuming that I copy from the /media/ubuntu that is mounted?  
However, there was some sudo error "Segmentation fault (core dumped) regarding the attempt to mount the sdc1 External HD.
Did I do that right?  I was assuming I am supposed to mount the partition sda5 and sdc1 and NOT the drives sda and sdc.
Please let me know.  

I tried remounting the External HD but the command is still processing...
If successful, My plan is to open the windows for the drives I see in the left menu column on the desktop and then cut & paste what is in the 7200HD to the External.
Am I doing something wrong with the External HD mounting?  
Did I not need to mount the external or did I mount it wrong?
Is there a way to ensure that the files are completely copied to the external?  Or compare the two files/directories?

---

### Post by CelticWarrior on 2021-01-29
A virtual machine is a file, ONE file... It has no special permissions, it isn't hidden, and there are no system files involved. All you need to do after saving that file somewhere else, reinstall the host OS and Virtualbox is to import it back to Virtualbox. Everything in that virtual machine will be as before.

Again, what makes sense is to retrieve your personal files of which that VM is one of them. Where to copy from and where to save them is up to you. We can't help you that, we can't see what your seeing.

> [COLOR=#000000]Is there a way to ensure that the files are completely copied to the external? Or compare the two files/directories?[/COLOR]
Yes, rsync does that. However, I'm afraid that will be another layer of confusion. You're already confused with the most trivial things and very likely worrying about things that doesn't matter and we're at it for days. Honestly, I'm tired.

---

### Post by 216ann on 2021-02-06
> **CelticWarrior said:**
> You're already confused with the most trivial things and very likely worrying about things that doesn't matter and we're at it for days. Honestly, I'm tired.

Your comments were a bit harsh especially considering that I am trying my best.
Perhaps it has been a while since you have been a noob and you may have forgotten how overwhelming everything is.

I think I have been able to successfully rsync the drive onto another drive which I had to do because the live usb method didn't work.
I had tried dragging and dropping from the GUI but it claimed a lot of  the files were special files that I could not copy so I ended up using  rsync.
I also tried the cp cmd but got some "error reading" and "Invalid argument" errors.
However, despite rsync what appears to be all the files (no error returned after the rsync cmd and eyeballing the files looks like nothing is missing), I am unable to pull up the VM using vagrant up.

When I tried to install vagrant and virtualbox and use them with vagrant up it claimed a "Gem::LoadError can't activate (some newer version vagrant file) because (another older version vagrant file) was already activated"
I have not been able to work around this.

I am assuming this is a vagrant issue and beyond the scope of ubuntu (so I need to ask elsewhere) but please let me know if that type of error can occur if I did something wrong on the rsync or perhaps if I am putting the vagrant or virtualbox or entering the "vagrant up" cmd in the wrong directory.
Celtic previously stated that the VM should be a single file but I guess I am unclear on, after I have successfully moved the file, how to access it once again using a different hard drive (eg, do I have to reinstall vagrant and virtualbox or use existing files or perhaps update existing files or replace).
Thanks for your time.

---

