---
title: "[Howto] Make Win8/Ubuntu dualboot work on a Lenovo U410"
date: 2013-11-30
forum: Installation &amp; Upgrades
---

### Post by mar.derungs on 2013-11-30
First of all: For this, I used "Boot-Repair", which is an excellent tool. I run it three times with different settings. Although none of these three attempts of solving my booting issues with Boot-Repair did work straightaway. But ***without*** Boot-Repair, I had never been able to make dual boot work in a stable way at all. 
My English is not the best, sorry for that.
[U][SIZE=4]
The starting situation 
[/SIZE][/U]My notebook is a Lenovo U410, but maybe other Lenovo models and models from different manufacturers are set up in a way similar to the U410, so this How-To may help in those cases.
[LIST]
[*]The notebook comes with a pre-installed Windows 8 and equipped with two harddisks. The first one (called "sda") is a 24 GB SSD drive, and the second ("sdb") is a 1 TB HDD drive.
[*]For the SD card reader slot, I have a 128 GB "USB HDD" drive ("sdc") to plug in, where I installed Elementary OS (which is based on Ubuntu), in default (standard) way, i. e. MBR-bootable with GRUB, without any use of UEFI.
[/LIST]
BIOS booting settings were:
[LIST]
[*]"USB HDD" on top position of the booting device list, right before "Windows 8 bootloader"
[*]Booting mode set to "Legacy support" (instead of UEFI) with the option "Legacy first" (instead of "UEFI first")
[/LIST]

With this setup, booting Linux was possible whith the SD card plugged in, and booting Windows was possible when the SD card was not in the slot. 

I could have been satisfied with this setup - if not both Windows and Linux sometimes did *not* start up - in this cases, it took one or two restarts for startup. Then I googled and found Boot-Repair an run it with its default (recommended) settings. Result: I couldn'd startup neither Windows nor Linux anymore. I was stuck. I had to start "googling" again, reading lots of different forum threads, learning about UEFI & co. ... 

I try to make the long story as short as possible :-)
[U][SIZE=4]
What I had to learn / to deal with - Part one: The preconditions of running Boot-Repair[/SIZE][/U]
[LIST]
[*]The 24 GB SSD (with 4 partitions on it) is used for chaching purposes only (things like "Intel fast boot"). You don't need this drive, do not touch it.
[*]In Windows, you have to ***disable*** fast boot (according to advices in different threads).
[*]The HDD has 10 (!) different partitions on it. These four are interesting:
[/LIST]
[TABLE="width: 500"]
[TR]
[TD][INDENT]_Device_[/INDENT]
[/TD]
[TD][INDENT]_Type_[/INDENT]
[/TD]
[TD][INDENT]_Label_[/INDENT]
[/TD]
[TD][INDENT]_Flags_[/INDENT]
[/TD]
[/TR]
[TR]
[TD][INDENT]/dev/sdb1[/INDENT]
[/TD]
[TD][INDENT]ntfs[/INDENT]
[/TD]
[TD][INDENT]WINRE_DRV[/INDENT]
[/TD]
[TD][INDENT]hidden, diag[/INDENT]
[/TD]
[/TR]
[TR]
[TD][INDENT]/dev/sdb2[/INDENT]
[/TD]
[TD][INDENT]vfat[/INDENT]
[/TD]
[TD][INDENT]SYSTEM_DRV[/INDENT]
[/TD]
[TD][INDENT]hidden, boot[/INDENT]
[/TD]
[/TR]
[TR]
[TD][INDENT]/dev/sdb3[/INDENT]
[/TD]
[TD][INDENT]vfat[/INDENT]
[/TD]
[TD][INDENT]LRS_ESP[/INDENT]
[/TD]
[TD][INDENT]hidden[/INDENT]
[/TD]
[/TR]
[TR]
[TD][INDENT]/dev/sdb5[/INDENT]
[/TD]
[TD][INDENT]ntfs[/INDENT]
[/TD]
[TD][INDENT]Windows8_OS[/INDENT]
[/TD]
[TD][INDENT]-[/INDENT]
[/TD]
[/TR]
[/TABLE]

[LIST]
[*]In UEFI tutorials, you may read that an "ESP" partition is needed for UEFI booting. As you see, sdb3 has an ESP label here - but it is ***not*** the right partition in this case. Instead, ***sdb2 is the right one, as it has the boot flag***.
[*]Boot-Repair chose to use sdb2 in default setting, so id did the right thing. But since booting did not work, I tried using sdb3, which wasn't working neither. So in Boot-Repair, go to "advanced settings" and check the setting for the target UEFI partition according to the particular conditions of your partitions.
[*]In the BIOS, ***activate UEFI*** as the booting method before running Boot-Repair.
[*]I ***disabled Secure Boot*** in BIOS settings. But this option was hard to find:
[*]When UEFI booting is unsuccessful, you are repeatedly prompted with a UEFI booting menu, containing a device list to choose from. This is your chance to enter the BIOS menu by pressing "TAB" and choose an entry called "setup".
[*]You may ***not*** see any Secure Boot option unless you ***set an administrator password in the BIOS***.
[*]Even then, when entering the BIOS menu, you may see the Secure Boot options on time, but next time you don't. So retry several times.
[*]Having finally disabled Secure Boot in the BIOS, be aware of the behaviour of Windows: The attempt to boot Windows - even when unsuccessful - or maybe *because* of that - may *re-enable *Secure Boot in BIOS. So double check this setting when in doubt.
[/LIST]

After having run Boot-Repair (from a live system) in this state and having restarted your computer, you can expect that you get a proper GRUB menu and Linux is starting up successfully in UEFI mode. Windows still didn't start in my case.
[U][SIZE=4]
What I had to learn / to deal with - part two: The corrections in GRUB settings, grub.cfg and UEFI files[/SIZE][/U]
[LIST]
[*]When GRUB generates its boot menu, it does an OS-probing, resulting in Windows start menu entries (in /boot/grub/grub.cfg) like this:
[/LIST]
```

menuentry [COLOR=#BB4444]"Windows 8 (loader) (on /dev/sdb5)"[/COLOR] --class windows --class os [COLOR=#666666]{
[/COLOR]    insmod part_gpt
    insmod ntfs
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd1,gpt5)'
[/COLOR]    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root B496806696802B46
    drivemap -s [COLOR=#666666]([/COLOR]hd0[COLOR=#666666])[/COLOR] [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#AA22FF][B]}
[/B][/COLOR]    chainloader +1
   }

```
[LIST]
[*]This is for MBR booting and doesn't work in UEFI mode. Edit [FONT=fixedsys]/etc/default/grub[/FONT] and insert (or uncomment) "***GRUB_DISABLE_OS_PROBER=true***".
[*]There are other menu entries, basically UEFI compliant, but they also ***do not work*** (resulting in errors like "no such device"). They look like this:
[/LIST]
```
[INDENT][COLOR=#000000]menuentry [/COLOR][COLOR=#BB4444]"Windows Boot UEFI recovery"[/COLOR][COLOR=#666666]{
[/COLOR][COLOR=#000000]search --fs-uuid --no-floppy --set[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#000000]root 227C-C21B
[/COLOR][COLOR=#000000]chainloader [/COLOR][COLOR=#666666]([/COLOR][COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#AA22FF]**}**[/COLOR][COLOR=#666666])[/COLOR][COLOR=#000000]/EFI/Boot/bkpbootx64.efi
}[/COLOR][/INDENT]

```
[LIST]
[*]This doesn't work because some modules are missing. Edit [FONT=fixedsys]/etc/grub.d/25_custom[/FONT]. There you find the corresponding menu entry templates. Add four ***insmod*** lines like this:
[/LIST]
```
[INDENT] menuentry "Windows Boot UEFI recovery" {[/INDENT]
[INDENT=2]  insmod part_gpt[/INDENT]
[INDENT=2]  insmod fat[/INDENT]
[INDENT=2]  insmod search_fs_uuid[/INDENT]
[INDENT=2]  insmod chain[/INDENT]
[INDENT]search --fs-uuid --no-floppy --set=root 227C-C21B[/INDENT]
[INDENT]chainloader (${root})/EFI/Boot/bkpbootx64.efi[/INDENT]
[INDENT]}[/INDENT]

```
[LIST]
[*]Now edit the file [FONT=fixedsys]/etc/grub.d/40_custom[/FONT]. There you find the menu entry template for starting up Windows in UEFI mode. It does not work either. Add the insmod lines. The entry  must look like this:
[/LIST]
```
[INDENT] menuentry "Windows 8 UEFI" {[/INDENT]
[INDENT=2]  insmod part_gpt[/INDENT]
[INDENT=2]  insmod fat[/INDENT]
[INDENT=2]  insmod search_fs_uuid[/INDENT]
[INDENT=2]  insmod chain[/INDENT]
[INDENT]  search --fs-uuid --no-floppy --set=root 227C-C21B[/INDENT]
[INDENT]  chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi[/INDENT]
[INDENT]}[/INDENT]

```
[LIST]
[*]In the line starting with "search" there is the ***ID number of the sdb2 partition***. It should be correct, but to be sure, double-check it by taking a look into /etc/fstab.  There you find a (new) entry for mounting the "sdb2" partition to[FONT=fixedsys] /boot/efi[/FONT]. That line starts like " UUID=227C-C21B", and this number must be used in the grub menu entry line.
[*]If the line starting with "search" does not look like shown above, but has something like "search --file" instead, you have to change it according to the given example.
[*]Having corrected all this, do a "sudo update-grub" in a terminal. Reboot.
[*]Now eventually Windows still doesn't start up - just the GRUB menu re-appears immediately after choosing the Windows start entry. If this is the case, you have to look into the directory "[FONT=fixedsys]/boot/efi/EFI/Microsoft/Boot[/FONT]".
[*]Look for a file like "bkpbootmgfw.efi" This should be a backup of the original Windows UEFI startup file. Make an additional backup of this file and then rename it to "bootmgfw.efi" (like in the menu entry) - this will overwrite the file that was there before and that didn't work.
[/LIST]

Having done all that - in my case - Windows [FONT=Verdana]finally!!! [/FONT]startet up without a glitch. I have now a fully working UEFI dual boot installation. The SDcard must stay in the reader slot, but that is what I wanted.I hope I have written down everything correctly. If not, let me know, an I will edit this post. Since I am far from being an expert in this matter, please note that I cannot give any support. The guys from the Boot-Repair team are perfect for this - just do not forget to donate.

**EDIT**: 
Above, I wrote that one have to insert the following four "insmod" lines:

[LEFT][COLOR=#000000][INDENT=2]insmod part_gpt
insmod fat[/INDENT]
[/COLOR][COLOR=#000000][INDENT=2]  insmod search_fs_uuid[/INDENT]
[/COLOR][COLOR=#000000][INDENT=2]  insmod chain[/INDENT]
[/COLOR][/LEFT]

I now have tested if Windows still starts up when I remove one of these lines; I tested them to remove one by one. Result: It seems that only the first line, "insmod part_gpt" is really needed. If it is missing, I got an error saying "no such device" and "file not found". 
However, when I remove one of the other three lines, Windows starts up. I also tested by removing the other three lines all together (so that only [FONT=Verdana]"insmod part_gpt" remains), and, in my case, Windows did start up. Thus, you may try first to  insert the first insmod line only, and when Windows starts up, you're done.
 [/FONT]

---

