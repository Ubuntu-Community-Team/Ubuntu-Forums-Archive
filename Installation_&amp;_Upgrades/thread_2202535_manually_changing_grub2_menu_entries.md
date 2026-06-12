---
title: "manually changing grub2 menu entries"
date: 2014-01-29
forum: Installation &amp; Upgrades
---

### Post by parminides on 2014-01-29
I dual boot to Windows 8 and Ubuntu 12.10. After upgrading to Windows 8.1, I lost my grub2 menu. I could only boot to Windows.

Running boot-repair restored my dual boot capability, but the grub menu still has a couple of minor issues.

Here's the new menu:

Ubuntu
Advanced options for Ubuntu
Windows UEFI bootmgfw.efi
Windows Boot UEFI loader
EFI/Asclepiou/bootx64.efi
Windows 8 (loader (on /dev/sda2)
Windows Recovery Environment (loader) (on /dev/sda9)
System setup

Options 1 and 2 work fine. Options 3 and 4 both boot to Windows 8.1, so I'd like to get rid of one of them, preferably the one with the weird filename bootmgfw.efi.

I think the double-entry for Windows may have arisen the first time I ran boot-repair and chose the option to backup EFI files. I later tried to rerun with the "Restore EFI backups," but the extra entry is still in the grub2 menu.

The 5th option, EFI/Asclepiou/bootx64.efi, boots to Windows recovery, so I'd like to rename it to something more appropriate.

The next 2 options don't work, both generating the messages,

```

error: can't find command 'drivemap'.
error: invalid Efi file path.
Press any key to continue...

```

I'd like to manually edit my grub2 menu to remove the redundancy, rename the Windows recovery entry that works, and remove the entries that don't work.

The write-protected file /etc/grub.d/25_custom seems pertinent:

```

#!/bin/sh
exec tail -n +3 $0

menuentry "Windows UEFI bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root A2CD-D8D5
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

menuentry "Windows Boot UEFI loader" {
search --fs-uuid --no-floppy --set=root A2CD-D8D5
chainloader (${root})/EFI/Boot/bootx64.efi
}

menuentry "EFI/Asclepius/bootx64.efi" {
search --fs-uuid --no-floppy --set=root DED3-7756
chainloader (${root})/EFI/Asclepius/bootx64.efi
}

```

It has the two Windows 8 entries that work, as well as the badly named option.

The write-protected file /boot/grub/grub.cfg has those same lines, after the comment,

```

### BEGIN /etc/grub.d/25_custom ###

```

I know I could edit one or both of these files and see what happens. But I just spent hours restoring my dual boot after the Windows upgrade, so I want to proceed with caution.

Is there a way for me to safely rename some of my grub2 menu entries and remove some other entries that are redundant or don't work? If so, how? The key word is safely.

---

### Post by oldfred on 2014-01-29
All the entries in 25_custom were created by Boot-Repair. You can edit and rename menuentry text at will. Instructions in the link in my signature. UEFI also remembers entries in NVRAM, so you may also have to edit those.

Only Ubuntu 13.10 has the fix to grub2's os-prober that finds the BIOS boot entries in UEFI systems.
       grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
grub2's os-prober creates wrong style (BIOS) chain boot entry Fixed with 13.10
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
menuentry "Windows UEFI bootmgfw.efi" {
menuentry "Windows Boot UEFI loader" {
Type of entry from os-prober that does not work:
'Windows ...) (on /dev/sdXY)'

I might turn off os-prober to elimiate the incorrect BIOS entries. You can turn it on later if desired.
      
 In /etc/default/grub I added this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

---

### Post by parminides on 2014-01-29
Thank you for your very quick reply. I did the following:

```

sudo cp /boot/grub/grub.cfg /boot/grub/grub_cfg.sav
sudo cp /etc/default/grub /etc/default/grub_sav
sudo gedit /etc/default/grub

```

I added the following line to /etc/default/grub (and saved):

```

GRUB_DISABLE_OS_PROBER=true

```

Then,

```

sudo cp /etc/grub.d/25_custom /etc/grub.d/25_custom.sav
sudo gedit /etc/grub.d/25_custom

```

and changed it to...

```

#!/bin/sh
exec tail -n +3 $0

menuentry "Windows 8" {
search --fs-uuid --no-floppy --set=root A2CD-D8D5
chainloader (${root})/EFI/Boot/bootx64.efi
}

menuentry "Windows Recovery" {
search --fs-uuid --no-floppy --set=root DED3-7756
chainloader (${root})/EFI/Asclepius/bootx64.efi
}

```

Last,

```

sudo grub-update

```

When I rebooted, the grub2 menu had more entries than before:

Ubuntu
Advanced options for Ubuntu
Windows 8
Windows Recovery
Windows UEFI bootmgfw.efi
Windows Boot UEFI loader
EFI/Asclepiou/bootx64.efi
System setup

To summarize, of the three options that were previously in 25_custom (Windows UEFI bootmgfw.efi, Windows Boot UEFI loader, EFI/Asclepiou/bootx64.efi), I deleted one and renamed the other two. Nonetheless, all three reappeared in the grub menu (but they are not in 25_custom).

The good news is that all 8 options now work. The bad news is that the menu is more redundant and cluttered than ever. Do you see anything that I did wrong? Maybe I shouldn't have updated grub at the end?

---

### Post by parminides on 2014-01-29
I just re-read oldfred's reply and saw: "UEFI also remembers entries in NVRAM, so you may also have to edit those."

I'll look into that and post the result.

---

### Post by parminides on 2014-01-29
I did a little Google research and saw a Linux Mint post that seemed relevant: [http://forums.linuxmint.com/viewtopic.php?f=46&t=129451](http://forums.linuxmint.com/viewtopic.php?f=46&t=129451).

With a live DVD of Ubuntu 12.10 I thought I booted to EFI mode. I tried the steps outlined in the above link. It didn't work. 

I found out later that the live boot wasn't really in EFI mode (cf. [https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode](https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode)).

When I adjusted the BIOS to try to force an EFI boot, the computer seemed to ignore the CD/DVD drive in the boot order. (I have a Series 5 Ultra laptop.)

I think the moral is that it's not worth it to spend so much time for what amounts to tidying up a boot menu.

Thanks for your help, oldfred. At least I was able to rename a couple of menu entries that I use.

---

### Post by oldfred on 2014-01-30
This name for backup file is part of the issue.

       sudo cp /etc/grub.d/25_custom /etc/grub.d/25_custom.sav

A grub update runs all executable files that start with two numbers and an underscore. So adding .sav at end will still leave its entries being added. 
You can add text at beginning, change executable bit, copy to another folder, or just delete.

If Windows is in UEFI mode, you cannot easily dual boot from grub if Ubuntu is in BIOS mode as you have to boot from UEFI/BIOS or one time boot key each time. Some systems also require turning on/off legacy or UEFI boot settings.

      
 Query to see if UEFI or BIOS
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"

---

### Post by parminides on 2014-01-30
I tried what you said because it was quick and easy. I renamed 25_custom.sav to sav_25_custom and updated grub. I also verified "EFI boot on HDD."

The only change was that the System setup entry in grub2 was above the three I want to get rid of, i.e.,

Ubuntu
Advanced options for Ubuntu
Windows 8
Windows Recovery
System setup
Windows UEFI bootmgfw.efi
Windows Boot UEFI loader
EFI/Asclepiou/bootx64.efi

I suspect that I need to do something like in the Linux Mint post to get rid of those extraneous entries. But I can't figure out how to EFI boot to live DVD. If BIOS is in secure boot mode, it ignores the CD/DVD drive. If I disable secure boot and select EFI, it still ignores CD/DVD drive.

Right now the only way to boot live to DVD is to disable secure boot and select CFM OS. Then it's not EFI.

I believe my BIOS has been flaky and inconsistent. It probably didn't help that I ran the Linux Mint post steps (involving modprobe efivars and efibootmgr) while not in EFI mode yesterday.

I consider myself lucky that everything still works. It's really quite tolerable. The three entries I dislike are now at the very bottom.

Thanks for all your help, oldfred.

---

### Post by oldfred on 2014-01-30
Those three still look like 25_custom entries from Boot-Repair. And if you renamed it, it should not be running unless they changed the rules & it runs anything executable.

Another quick change.
 sudo chmod a-x /etc/grub.d/sav_20_custom
sudo update-grub

---

### Post by parminides on 2014-01-30
That did the trick! I tried to run you off at least twice because I'd already spent too much time on a non-critical "problem," but you kept giving me advice. Thanks so much. I'm marking it solved.

---

### Post by oldfred on 2014-01-30
We like to fix things even if it takes weeks. :)
Glad you got it resolved.

---

