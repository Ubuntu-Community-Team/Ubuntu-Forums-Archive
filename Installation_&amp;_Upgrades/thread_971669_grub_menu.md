---
title: "grub menu"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by Garabombo on 2008-11-05
Is there someone who can help me to understand why grub does not displays the selection menu?
I have Xp on first HD and ubuntu on the slave HD of the primary IDE.
The system ever boot with ubuntu without allowing me to choose from which OS to start

---

### Post by caljohnsmith on 2008-11-05
When you get into Ubuntu, open a terminal (applications > accessories > terminal) and do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "hiddenmenu" to:
```
# hiddenmenu
```
That should give you Grub's menu on start up.

---

### Post by Garabombo on 2008-11-05
Thanks for your help Caljohnsmith, but as you can see in the following  listing of menu.lst, the line with #hiddenmenu is already here.



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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
 color cyan/blue white/blue

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
# kopt=root=UUID=c848409e-8742-4dc1-b452-fd854cf1d1ec ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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



title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=c848409e-8742-4dc1-b452-fd854cf1d1ec ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet
Nuova cartella
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=c848409e-8742-4dc1-b452-fd854cf1d1ec ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c848409e-8742-4dc1-b452-fd854cf1d1ec ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c848409e-8742-4dc1-b452-fd854cf1d1ec ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
# title		Other operating systems:
# root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by caljohnsmith on 2008-11-05
So what exactly happens on start up? You don't see a Grub menu at all, but instead you boot directly into Ubuntu? Also, you have what looks like a small error in your menu.lst:
```
title Ubuntu 8.04.1, kernel 2.6.24-21-generic
root (hd1,4)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=c848409e-8742-4dc1-b452-fd854cf1d1ec ro quiet splash
initrd /boot/initrd.img-2.6.24-21-generic
quiet
[COLOR="Red"]Nuova cartella[/COLOR]
title Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root (hd1,4)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=c848409e-8742-4dc1-b452-fd854cf1d1ec ro single
initrd /boot/initrd.img-2.6.24-21-generic
```
I would remove that line above and keep an empty line between the two entries. See if that makes any difference on start up, and if not, please post:
```
sudo fdisk -lu
```

---

### Post by Garabombo on 2008-11-05
It makes no difference and I think  of a typing mistake I did when copying the listing.Homewhere, replying your question,the system boot directly into ubuntu and I can't see a grub menu at all.

Here it is the fdisk output

Disco /dev/sda: 61.4 GB, 61492838400 byte
255 heads, 63 sectors/track, 7476 cylinders, totale 120103200 settori
Units = settori of 1 * 512 = 512 bytes
Disk identifier: 0x03af03af

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81915434    40957686    7  HPFS/NTFS

Disco /dev/sdb: 122.9 GB, 122942324736 byte
255 heads, 63 sectors/track, 14946 cylinders, totale 240121728 settori
Units = settori of 1 * 512 = 512 bytes
Disk identifier: 0xaeabaeab

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   120101939    60050938+   7  HPFS/NTFS
/dev/sdb2       120101940   240107489    60002775    5  Esteso
/dev/sdb5       120102003   237087269    58492633+  83  Linux
/dev/sdb6       237087333   240107489     1510078+  82  Linux swap / Sola

---

### Post by caljohnsmith on 2008-11-05
OK, how about trying:
```
sudo apt-get purge grub
sudo apt-get install grub
sudo grub-install /dev/sda
```
Then reboot, and rapidly tap the down arrow key on start up. Do you see the Grub menu? And if not, do you boot into Windows instead of Ubuntu?

---

### Post by Garabombo on 2008-11-05
No news!  No one menu appears and again the systems boots into ubuntu

---

### Post by caljohnsmith on 2008-11-05
So did you rapidly tap the down arrow on your keyboard as soon as the computer restarted, and keep pressing it? If so, that would probably indicate your keyboard is not being recognized by BIOS, because you should have booted into Windows since it is the last entry in Grub's menu.lst. When you boot Ubuntu, do you get the Ubuntu splash screen? And on start up, does your monitor show anything, any text, like maybe a BIOS splash screen? Or at least some message about "Press F12 to enter BIOS" or something like that?

---

### Post by Garabombo on 2008-11-05
Sorry caljohnsmith, I wasn't accurate before.
When the computer restarted I quickly tapped the down arrow key but the system stopped here with a dark screen and so I had to restart again and, without tapping, I booted into ubuntu again.
When the system start up I can see the Asus logo and everithing after ( i.e. the grub messages indicating loading stage1.5), included the ubuntu screen.

---

### Post by caljohnsmith on 2008-11-05
OK, so if you don't press any keys on start up, you see your Asus logo, the Grub loading stage1.5, and then is there about a 10 second delay before Ubuntu boots? You have your Grub menu delay set to 10 seconds right now; how about arbitrarily setting it to 30 seconds to see if that delays the time before Ubuntu boots. To set the timeout line in your menu.lst to 30 seconds:
```
timeout 30

```
Also, see if it makes any difference to comment out the "pretty colors" line:
```
# color cyan/blue white/blue
```
Also, you are sure you are modifying the /boot/grub/menu.lst and not maybe /boot/grub/menu.lst~ with the tilde at the end? Please also post:
```
ls -l /boot/grub/
```

---

### Post by Garabombo on 2008-11-05
I already tried to modify the timeout to a greater value to understand if  menu.lst executed and really the delay increased so i'm sure the code execute.
In a similar way, the # before color cyan/blue white/blue was already here and I removed this only to see if something changed.

Here it is the output of  ls -l /boot/grub
totale 212
-rw-r--r-- 1 root root    197 2008-11-05 16:38 default
-rw-r--r-- 1 root root     30 2008-10-30 15:08 device.map
-rw-r--r-- 1 root root   8056 2008-11-05 16:38 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-11-05 16:38 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-11-05 16:38 installed-version
-rw-r--r-- 1 root root   8608 2008-11-05 16:38 jfs_stage1_5
-rw-r--r-- 1 root root   5021 2008-11-04 13:53 menu.lst
-rw-r--r-- 1 root root   5021 2008-11-04 13:48 menu.lst~
-rw-r--r-- 1 root root   5103 2008-11-02 18:12 menu.lst_bkup
-rw-r--r-- 1 root root   7324 2008-11-05 16:38 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-11-05 16:38 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-11-05 16:38 stage1
-rw-r--r-- 1 root root 108356 2008-11-05 16:38 stage2
-rw-r--r-- 1 root root   9276 2008-11-05 16:38 xfs_stage1_5

---

### Post by Garabombo on 2008-11-05
I already tried to modify the timeout to a greater value to understand if  menu.lst executed and really the delay increased so i'm sure the code execute.
In a similar way, the # before color cyan/blue white/blue was already here and I removed this only to see if something changed.

Here it is the output of  ls -l /boot/grub
totale 212
-rw-r--r-- 1 root root    197 2008-11-05 16:38 default
-rw-r--r-- 1 root root     30 2008-10-30 15:08 device.map
-rw-r--r-- 1 root root   8056 2008-11-05 16:38 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-11-05 16:38 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-11-05 16:38 installed-version
-rw-r--r-- 1 root root   8608 2008-11-05 16:38 jfs_stage1_5
-rw-r--r-- 1 root root   5021 2008-11-04 13:53 menu.lst
-rw-r--r-- 1 root root   5021 2008-11-04 13:48 menu.lst~
-rw-r--r-- 1 root root   5103 2008-11-02 18:12 menu.lst_bkup
-rw-r--r-- 1 root root   7324 2008-11-05 16:38 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-11-05 16:38 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-11-05 16:38 stage1
-rw-r--r-- 1 root root 108356 2008-11-05 16:38 stage2
-rw-r--r-- 1 root root   9276 2008-11-05 16:38 xfs_stage1_5

---

### Post by sandy8925 on 2008-11-05
> **Garabombo said:**
> Is there someone who can help me to understand why grub does not displays the selection menu?
I have Xp on first HD and ubuntu on the slave HD of the primary IDE.
The system ever boot with ubuntu without allowing me to choose from which OS to start

most probably your slave hard disk containing ubuntu is set as the 1st boot device before ur windows xp hard disk. I think each hard disk has it's own bootloader and since you have  only ubuntu on your slave hard disk that's probably why no choice is getting displayed.

---

### Post by Garabombo on 2008-11-05
I verified this but the first boot device is the one where windows is installed.

---

### Post by caljohnsmith on 2008-11-05
Right now your Grub is installed to the MBR (Master Boot Record) of your Windows drive, so how about if you install Grub to the MBR of the Ubuntu drive, and then set your BIOS to boot the Ubuntu drive on start up; we can then see if the behavior is the same, to see whether or not you get the Grub menu. 

To install Grub to the MBR of sdb:
```
sudo grub
grub> root (hd1,4)
grub> setup (hd1)
grub> quit
```
Reboot, set your BIOS to boot the Ubuntu sdb drive, and see if you get the Grub menu. If you do get the Grub menu, choosing Ubuntu to boot will result in a Grub error 17 or some other Grub error, but just see if you can at least get a Grub menu.

---

### Post by Garabombo on 2008-11-05
All in vain, again no one menu, again ubuntu start in the same way before

---

### Post by caljohnsmith on 2008-11-05
> **Garabombo said:**
> All in vain, again no one menu, again ubuntu start in the same way before
I don't think there is any way you could be booting the sdb Ubuntu drive if Ubuntu still boots, because your entries for Ubuntu use (hd1,4), which means Ubuntu will boot only if it is the second drive in the boot order; that's the case when you boot the sda Windows drive, but booting the Ubuntu drive should give you a Grub error when Ubuntu tries to boot. Are you sure you set your BIOS to boot the sdb drive?

---

### Post by Garabombo on 2008-11-05
Oops! I had forgotten to select the boot drive as  required. Now, after having done it, the system stop with a dark screen.
The last things that I can see are the  messages:
1) loading stage 1.5
2) loading grub, please wait.
No error messages.

---

### Post by caljohnsmith on 2008-11-05
OK, well at least that Grub behavior you got on start up makes more sense, but unfortunately you're still not getting the Grub menu. Do you have a Live CD you can use? You might need your Live CD though at some point, so I just want to make sure you have one that works OK. 

How about trying the following (from your Ubuntu install though, not the Live CD) to see if there is maybe something in your menu.lst that is causing problems: 
```
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.11-05-08
sudo update-grub 
```
And please post the output of the update-grub command. Next reboot, and you can boot either sda or sdb, we just want to see if you get the Grub menu.

---

### Post by Garabombo on 2008-11-05
here it is the output from update grub:

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-genericSearching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


I do have a live CD .
Now I try to reboot and then I'll post what it happens

Thank you again for your kindness and your patience

---

### Post by Garabombo on 2008-11-05
I tried to boot from sdb and again, as before, the system stops.
Next from sda and again ubuntu starts without displaying a menu.
Nothing seems to change

---

### Post by caljohnsmith on 2008-11-05
> **Garabombo said:**
> 
```
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
[COLOR="Blue"]Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst[/COLOR]
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-genericSearching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
[COLOR="Blue"]Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst[/COLOR]
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```

The highlighted text above shows that update-grub found your menu.lst, when your menu.lst should have been moved to that backup menu.lst.11-05-08 file. Did you do that "mv" command I gave in post #19? How about trying one more time just to make sure your problem is not with your menu.lst:
```
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.11-05-08
ls -l /boot/grub
```
Check the directory listing and make sure you don't have a menu.lst, but you do have the new menu.lst.11-05-08 file. If that is true, then do:
```
sudo update-grub
```
And again, please post the output of the update-grub command. Reboot, and let me know if anything changes. If nothing changes, then maybe not getting the Grub menu is related to one of your BIOS settings for your HDD, but I'm skeptical about that idea because you see everything else OK on start up.

---

### Post by Garabombo on 2008-11-05
after entering sudo update-grub it appears :
[COLOR="Red"]Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) [/COLOR]
have I type y ?

---

### Post by caljohnsmith on 2008-11-05
> **Garabombo said:**
> after entering sudo update-grub it appears :
[COLOR="Red"]Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) [/COLOR]
have I type y ?
Yes. :)

---

### Post by Idefix82 on 2008-11-05
Type y, post the whole output from the command and reboot after the update process has finished.

---

### Post by Garabombo on 2008-11-05
this is the output of update-grub

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

---

### Post by Garabombo on 2008-11-05
I rebooted again but, again, I can't obtain the menu and all goes in the same way

---

### Post by caljohnsmith on 2008-11-05
About the only thing I can think of is maybe changing your BIOS settings related to your HDD might correct the problem. One last thing I would try would be to intentionally set the "hiddenmenu" line in menu.lst (remove the pound sign):
```
hiddenmenu
```
You can modify your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
Then on start up, see if it gives you a message about "Press ESC to see menu", and press ESC to see if you can get the Grub menu to show up. If that doesn't do anything, I'm running out of ideas, except for the problem maybe being BIOS related.

---

### Post by caljohnsmith on 2008-11-05
I just thought I would mention that if you don't figure out your Grub menu problem, in the meantime a workaround would be to restore the Windows MBR to your sda drive so you can boot Windows, and then modify your menu.lst so you can boot Ubuntu from your sdb drive. Then to boot either OS, you would just change which drive boots on start up. If you want help with that, let me know.

---

