---
title: "boot-repair created a lot of EFI entries into GRUB-how to eliminate them?"
date: 2015-04-25
forum: Installation &amp; Upgrades
---

### Post by ashu2 on 2015-04-25
[FONT=arial]1) I had added a new hard drive-3 TB Seagate internal SATA 3 drive that i want to add apart from my old 1TB hard drive.[/FONT][FONT=arial]2) The new 3 TB drive had some issues. Because of that - my GRUB got some problems....[/FONT]
[FONT=arial]3) then i ran the boot-repair and here is the report:
---------------------------------------------------------------------------------------------------------[/FONT]
[FONT=arial]Boot successfully repaired.


Please write on a paper the following URL:
[http://paste.ubuntu.com/10873304/](http://paste.ubuntu.com/10873304/)




In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.


You can now reboot your computer.




The boot files of [The OS now in use - Ubuntu 14.04.2 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))


If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi
---------------------------------------------------------------------------------------------------------





4) I got a replacement and correct drive(3TB)...after testing it...i can get into both Windows and Ubuntu Linux.GRUB is working fine....b**ut my last boot-repair introduced good # of entries into my GRUB entries.**...please refer to the screen shot:


5) As GRUB is working fine..i don't want to mess it with....**how i can fix these entries which got into my GRUB screen after the last boot-repair?**




So need help in terms of Cleaning up the GRUB entries....

Went thru a lot of forums...but the solutions provided is not working for me.
I looked into this solved thread also at:
[http://ubuntuforums.org/showthread.php?t=2202535](http://ubuntuforums.org/showthread.php?t=2202535)
[http://askubuntu.com/questions/265320/windows-7-ubuntu-12-04-invalid-efi-file-path-boot-repair-grub-many-entri/613876#613876](http://askubuntu.com/questions/265320/windows-7-ubuntu-12-04-invalid-efi-file-path-boot-repair-grub-many-entri/613876#613876)
[http://askubuntu.com/questions/281321/grub-efi-entries-and-boot-repair](http://askubuntu.com/questions/281321/grub-efi-entries-and-boot-repair)

but not very helpful...as it's somewhat related to GRUB - i want to proceed with caution...it took some good amount of efforts to make it working at the first place.




thanks in advance.
[/FONT]

---

### Post by oldfred on 2015-04-25
Part Boot-Repair and part HP.
Boot-Repair creates entries for every efi file in the ESP - Efi System Partition.
And HP has many extra repair or setup files and puts them all in the ESP. Other vendors may have them in another partition or other ways to configure sytem.

Since added by Boot-Repair into a new part of grub you can just edit file at will. I would back it up also.
Report shows this for all new entries, and it is not one of standard grub script files.
 BEGIN /etc/grub.d/25_custom 

sudo cp -a /etc/grub.d/25_custom /etc/grub.d/backup25_custom
gksudo gedit /etc/grub.d/25_custom

Do not name backup with two digits & underscore at beginning or else it will also be run. Changing start of name or turning off execute bit would also work.

You also left Windows hibernated or fast startup on, which is an issue. Grub cannot boot nor view hibernated Windows. You have to boot Windows directly from UEFI menu and turn off fast startup.
      
 Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

You may want to houseclean older kernels also. I like to keep one older and current one.
      
 Determine your current kernel:
uname -a
-s is similate so you can review first:
sudo apt-get -s autoremove

sudo apt-get install synaptic
In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by ashu2 on 2015-07-04
Thanks oldfred. But it's not working. In fact doing this has increased number of EFI entries even further. any help, thanks in advance.

---

### Post by oldfred on 2015-07-04
The grub-update runs any file with execute able bit set in /etc/grub.d and two numbers & and underscore. Did you rename backup with 25_ at beginning or change it to backup at beginning of name?

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by ashu2 on 2015-07-04
I did both of these commands:
[COLOR=#000000]sudo cp -a /etc/grub.d/25_custom /etc/grub.d/backup25_custom[/COLOR]
[COLOR=#000000]gksudo gedit /etc/grub.d/25_custom

and then [/COLOR][COLOR=#111111][FONT=Consolas]sudo update-grub

But the problem still persists. 
[/FONT][/COLOR]

---

### Post by oldfred on 2015-07-04
Did you edit out a lot of the HP entries in 25_custom?
Best to see details from Boot Repair's Summary report.

---

### Post by ashu2 on 2015-07-04
Now it looks like this:
ashu@ashu-700-430qe:/etc/grub.d$ ls -lrt
total 116
-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root  6058 May  8  2014 05_debian_theme
-rw-r--r-- 1 root root   483 May 15  2014 README
-rwxr-xr-x 1 root root   216 May 15  2014 41_custom
-rwxr-xr-x 1 root root  1416 May 15  2014 30_uefi-firmware
-rwxr-xr-x 1 root root 11692 May 15  2014 30_os-prober
-rwxr-xr-x 1 root root 10412 May 15  2014 20_linux_xen
-rwxr-xr-x 1 root root 11608 May 15  2014 10_linux
-rwxr-xr-x 1 root root  9424 May 15  2014 00_header
-rwxr-xr-x 1 root root  2506 Apr 23 11:49 25_custom~
-rwxr-xr-x 1 root root 14452 Jul  3 22:38 40_custom~
-rwxr-xr-x 1 root root 14452 Jul  3 22:38 40_custom
-rwxr-xr-x 1 root root   473 Jul  4 01:25 backup25_custom
-rwxr-xr-x 1 root root   473 Jul  4 01:25 25_custom
ashu@ashu-700-430qe:/etc/grub.d$

---

### Post by ashu2 on 2015-07-04
no matter how many times i edit this file:
[COLOR=#000000]gksudo gedit /etc/grub.d/[/COLOR]25_custom~~~
[COLOR=#000000]it keeps on creating another entry for it with more number of trailing '~' symbols...these EFI entries are just not going away.


[/COLOR]

---

### Post by ashu2 on 2015-07-04
Forget about fixing the unwanted EFI entries...i just can't even make Windows as a default OS to load. 
this is my /etc/defualt/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=5
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


Windows Boot Manager(on /dev/sda2) is the 5th one...editiing /etc/default/grub and then running grub-update is also not working....every time i need to get into Windows...i need to be very quick to choose it when GRUB comes up.

These EFI entries and GRUB 2 is nightmare with Windows 8.1...when GRUB works...it works as charm...otherwise lot of struggle...hit and trial.

---

### Post by ashu2 on 2015-07-04
Everytime if i update-grub there are more entries getting added.

---

### Post by oldfred on 2015-07-04
The backup files that are created are also being included. Delete those and/or turn off the execute bit.

        turn off executeable bit
sudo chmod a-x /etc/grub.d/25_custom~
sudo chmod a-x /etc/grub.d/40_custom~
sudo update-grub

---

### Post by oldfred on 2015-07-06
Did you try turning off execute bit or just delete the backup files, including those with the ~ at the end as those usually are hidden backups.

---

