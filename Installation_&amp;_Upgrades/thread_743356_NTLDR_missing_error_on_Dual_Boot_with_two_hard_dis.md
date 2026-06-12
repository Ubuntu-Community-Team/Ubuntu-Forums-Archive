---
title: "NTLDR missing error on Dual Boot with two hard disks"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by ali999 on 2008-04-02
Hi
I have two hard disks in my computer one with Ubuntu 8.04 Hardy Heron and one with Windows Vista on it. I installed Vista first and then installed Ubuntu, Ubuntu loads up just fine but whenever I start my computer, Vista would not show up as an option on GRUB. I edited my menu.lst file to detect my second hard disk. The contents of the file are now as follows:

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=c711984a-549d-49b7-ba87-70a0da9d2e09 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=c711984a-549d-49b7-ba87-70a0da9d2e09 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=c711984a-549d-49b7-ba87-70a0da9d2e09 ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows Vista Ultimate
root		(hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader	+1


Vista shows up now as an option on GRUB but when I choose it, I get an error saying "NTLDR is missing, press Ctrl + Alt + Delete to restart." I am not sure if this is because I have edited my menu.lst file incorrectly ( how can i check to be sure that all the hard disk numbers and everything else is correct?), or if the drive Vista is installed on is not master, I didn't think that would be an issue as I was running Vista off this hard disk before installing Ubuntu. Can I just set this disk to master and then restart or will I have reformat the disks or something to make the switch from slave to master? Please help, I need to get my Vista running again to run some programs for my school.

---

### Post by dabang on 2008-04-02
> title Windows Vista Ultimate
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
This seems to be the trouble.... 
First: Hardy is still beta, so be careful. Besides that, at least with other Ubuntu versions, Vista is added to grub automatically and I wonder why this wasn't the case?
OK, but now to the Vista grub entry: I don't know the two "map" options, I'd remove them. Then look at the "root (hd1,0)" part. This would assume, that Vista is on your second HD's first partition. Is this correct? Start counting at zero, first number is HD, second number partition.

Second thought:
You said, you first installed Vista? You installed it to the second HD? Was your first  HD formatted with NTFS then? If so, Vista would see the first partition on your first HD and copy some system files to it, like "ntldr". If you install Ubuntu to that partition later on, it would overwrite those files which would also explain, why Ubuntu didn't recognize Vista.
Also, you shouldn't change your disk order AFTER installing an OS. Just a third thought...

---

### Post by ali999 on 2008-04-02
I removed the two map lines. However, now when I choose Vista in GRUB it just says "starting up..." and freezes. I'm thinking this might be because in windows, Vista is now installed on my F:/ drive and what used to be my C:/ drive has been formatted to put Ubuntu on. Perhaps Vista is looking for some boot file in C;/ or something? Also, the second hard drive containing Vista has not been partitioned into separate drives, that entire disk is devoted to Windows. The original C:/ drive was formated as FAT32. Any suggestions on how I can get Vista to boot? I really don't want to have to reinstall it.

---

### Post by dabang on 2008-04-03
> Vista is now installed on my F:/ drive and what used to be my C:/ drive has been formatted to put Ubuntu on. Perhaps Vista is looking for some boot file in C;/ or something?
Indeed, Vista is looking for "ntldr" on the first partition of you primary disk - which has changed... (bad idea).

I don't know if it's possible to make it work without re-installig Vista and I guess re-installing is the cleanest and quickest way to repair it. After installing Vista, your MBR will be overwritten, so you need to reinstall grub after that. (There are some HOWTOs here in the forum).
So, best way to dual boot:
1. Boot Ubuntu to create partitions
2. install Windows
3. install Ubuntu
4. DO NOT change disk order ;-)

---

### Post by Herman on 2008-04-03
> I removed the two map lines. However, now when I choose Vista in GRUB it just says "starting up..." and freezes. **I'm thinking this might be because in windows, Vista is now installed on my F:/ drive and what used to be my C:/ drive has been formatted to put Ubuntu on. Perhaps Vista is looking for some boot file in C;/ or something? **Also, the second hard drive containing Vista has not been partitioned into separate drives, that entire disk is devoted to Windows. The original C:/ drive was formated as FAT32. Any suggestions on how I can get Vista to boot? I really don't want to have to reinstall it.Can you explain more about what your C: drive was used for?
Did it ever have a different version of WIndows running in it?
If so, Windows probably copied your boot files from Vista to your old operating system and yes, now you have deleted them when you wiped your C: drive to install Ubuntu.

What partition number is your Windows Vista in? (Drive letters like 'C:' and 'F:' I find rather meaningless). Does it have a partition number between 1 and 4, (meaning a primary partition?), or number 5 or greater?, (indicating a logical partition?).

Can you mount your Vista drive from Ubuntu and take a look and see if the boot loader files are there or gone?
I don't have a Vista computer, but here's the equivalent of what you would be looking for in XP, [A Birds's eye view of Windows XP]("http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP")...showing the important files needed for booting
            
If Windows is in a primary partition you might be able to get it to boot by copying the important booting files from your Vista installation CD or from another Vista in someone else's computer and pasting them into yours.
I have not yet heard of anyone succeeding in getting Windows to boot in a logical partition. The reason why, I think, is that for Windows to be bootable it needs the boot flag in the partition table.

I don't know if it's possible or not, but it might be worth a try to make a small primary partition in that hard disk and copy the boot loader files to that and see if it will do anything.

Another possiblity is to copy the entire partition after shrinking it first, and then paste it to some free space in your hard disk to make it into a primary partition and add the vital boot loader files to it.

I am not sure if it's okay to copy and paste a Windows operating system because of possible anti-piracy booby traps, I don't think Windows likes being copied and pasted. That's one of the problems with proprietary software. It's also a lot harder to fix.
Although you signed an agreement about not copying parts of the software, in this case it seems as if Microsoft is willing to make an exception as they themselves recommend doing that very same (illegal?) thing here, [How to make your own Windows Xp boot floppy]("http://support.microsoft.com/kb/305595/EN-US/").

There is also a CD available here, [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm") ,. It has a special boot.ini file edited to boot Windows in hard disk 0, partitions 1,2,3 or 4, or hard disk 1 partitions 1,2,3 or 4
It doesn't help you if you have Windows in a logical partition.
> Indeed, Vista is looking for "ntldr" on the first partition of you primary disk - which has changed... (bad idea).
Yes, if you ever set up a Windows-Windows dual boot again, be sure to use GRUB to hide your first Windows install to prevent Windows from setting up a default Microsoft style dual boot.
If you have time to this you'll understand what went wrong and why,  [http://www.goodells.net/multiboot/principles.htm](http://www.goodells.net/multiboot/principles.htm), that link is from: [Understanding MultiBooting and Booting Windows from an Extended Partition]("http://www.goodells.net/multiboot/index.htm") , by Dan Goodell.[COLOR=#CC0000][FONT=Arial][/FONT][/COLOR]

---

