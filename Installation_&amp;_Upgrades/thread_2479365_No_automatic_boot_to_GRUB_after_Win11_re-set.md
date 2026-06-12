---
title: "No automatic boot to GRUB after Win11 re-set"
date: 2022-09-22
forum: Installation &amp; Upgrades
---

### Post by von Stalhein on 2022-09-22
I had a glitch yesterday & had to re-set Win11.

There was some reordering of disks as I had to boot from a USB to get to the repair area.

I've changed the disk boot order back to the original and I can get into  Ubuntu by holding F11 (MSI board & BIOS) and selecting the Ubuntu  menu option which then boots to the GRUB menu.

The 2 options at that juncture are Win11 & Ubuntu, and they both  reference the same disk, which didn't worry me as ostensibly it is the  Win disk and I thought that's where the bootloader resided anyway  (UEFI).

So, I thought running the old ```
sudo update-grub
``` would restore things but it doesn't. 

After advice from oldfred I'm going down the Boot-Repair path & would appreciate any help.

The Pastebin link to the Boot-Info summary is [here]("https://paste.ubuntu.com/p/ZDxgdSpcKq/")

TIA!

---

### Post by oldfred on 2022-09-22
Looks like both Windows 7 (?, usually says 8,10 or 11) and Ubuntu are in UEFI boot mode & UEFI boot is from ESP on NVMe drive.
Windows 7 is obsolete.

For whatever reason, Boot-Repair report is not showing grub.cfg in your install. It seems to stop showing all the details (sometime very long) but did not even show summary entries. Was LVM mounted when you ran report.
Do not really know LVM installs.

You can add a standard Windows UEFI boot entry to 40_custom, and then you do not need os-prober.
But grub will only find Windows if not hibernated nor needs chkdsk. Windows 7 does not have the fast start up setting that Windows 8 or later has that is a partial hibernation & sets hibernation flag preventing os-prober from seeing the Windows install.
Grub 2.06 now turns off os-prober for security reasons. Some issue with opening all partitions to look for installs to boot.

You can check if os-prober is true or false:
cat /etc/default/grub

GRUB_DISABLE_OS_PROBER=true



sudoedit /etc/grub.d/40_custom
after editing
sudo update-grub

I believe your NVMe's drive will be hd0. Grub will only boot working Windows. If Windows 11, make sure fast start up is off. Not sure with 11 if any other settings are required. Windows on many systems will update UEFI which reverts UEFI to defaults. You then have to redo all the ones you need for Ubuntu. My old Asus motherboard had 7 settings to redo everytime I updated UEFI. My Gigabyte motherboard only has one or two.

```
#UEFI ESP on first drive hd0 & first partition gpt1
menuentry "Windows UEFI" {
    insmod part_gpt
    insmod chain
    set root='(hd0,gpt1)'
    chainloader /EFI/microsoft/BOOT/bootmgfw.efi
}

```

Maybe other examples in the very long custom grub thread.

---

### Post by von Stalhein on 2022-09-22
Thanks oldfred - Yes, LVM is mounted. I have already turned off fast start.

I [re-ran the report]("https://paste.ubuntu.com/p/ZDxgdSpcKq/") after making sure in Disks that everything was mounted - extra lines are included (100-108) but I don't know if that's any help.

I have no idea why there's a reference to Win 7, it's never been on this system. I've always been on the beta channel for Win 10 & 11.

```
cat /etc/default/grub gives:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
GRUB_TIMEOUT_STYLE="hidden"
GRUB_TIMEOUT="20"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE="1920x1080"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

export GRUB_MENU_PICTURE="/home/xxxx/Pictures/grubscreen1.JPG"
export GRUB_COLOR_NORMAL="dark-gray/black"
export GRUB_COLOR_HIGHLIGHT="dark-gray/black"

```
I haven't tried your suggested edits yet - thanks again!

This is the current entry in GRUB that starts Win - 

```
insmod part_gpt
insmod fat
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root  047E-E394
else
  search --no-floppy --fs-uuid --set=root 047E-E394
fi
chainloader /EFI/Microsoft/Boot/bootmgfw.efi
```

---

### Post by oldfred on 2022-09-22
Your Windows boot entry looks correct. Using UUID of ESP is better than hard coding hd0 which if you plug in a flash drive may change drive to hd1. That happens on my system.

If Windows does not boot, then that is a Windows issue.
Settings like fast start up, bitlocker, or needing chkdsk are most common issues.

---

### Post by von Stalhein on 2022-10-04
Partially "solved".

Research led me to using the following command in Windows:

```
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
```

Now the system boots to some error messages: 
```
"Failed to open \EFI\ubuntu\?S - Invalid Parameter     Failed to load image \EFI\ubuntu\?S - Invalid Parameter    
start_image() return Invalid parameter, falling back to default loader
```[FONT=verdana][SIZE=2]So now I just need to sort the path properly in the first command. At least it currently goes to GRUB without me having to manually select it.[/SIZE][/FONT]

---

### Post by von Stalhein on 2022-10-07
Windows updated & the system has reverted to the previous state. The partial fix achieved by the win cmd doesn't work this time.

Pastebin URL - [https://paste.ubuntu.com/p/58H5PGKPHr/](https://paste.ubuntu.com/p/58H5PGKPHr/)

Thanks for any pointers!

---

### Post by yancek on 2022-10-08
t/Your boot repair output shows you are booting from the installed Ubuntu system.  Is the problem now that you cannot boot windows?  Check the /boot/grub/grub.cfg entry for windows to ensure that the menuentry for windows is correct, particularly the last line of the menuentry beginning with chainloader is as shown in post 2 above by oldfred.

Your initial problem seemed to be that a windows update set windows to first boot priority in the BIOS firmware.  Line 94 in your boot repair shows the current boot is Ubuntu and the boot order on line 96 shows windows as first boot.  I'd first check the menuentry in grub.cfg for windows and change that to see the result.

---

### Post by oldfred on 2022-10-08
Windows updates often turn fast start up back on. Then grub cannot add Windows to menu nor boot Windows.
Both Windows & Ubuntu/grub major update reset boot order to have them first in boot order. You just may have to go into UEFI settings to change order or use efibootmgr in Ubuntu to change order (if not HP).

Updates may also include a UEFI firmware update that resets all UEFI settings back to defaults. If you changed any settings to make Ubuntu work like Secure Boot or AHCI, you probably have to redo them. My older Asus motherboard needed multiple settings redone. I had to keep a list to remember them all.

---

