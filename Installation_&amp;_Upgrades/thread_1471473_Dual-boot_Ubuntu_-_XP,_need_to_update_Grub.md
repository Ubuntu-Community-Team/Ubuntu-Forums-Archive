---
title: "Dual-boot Ubuntu - XP, need to update Grub"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by G-Sun on 2010-05-03
Hi!

I've installed Ubuntu and XP (in that order) and need to fix my boot. How?

I've installed Ubuntu 10.04 on hd0 part0
Installed XP on hd0 part1

Part1 is currently the active one,
and XP is the only OS loading now.

Tried to add an ubuntu line in boot.ini,
but didn't manage and don't wanna mess things up there.
Tried Super Grub, but no success.

So, I believe what I have to fix is:
- Setting Part0 as active
- Update Grub (and add entry for XP)

How to achieve this?

Thanks!

---

### Post by wilee-nilee on 2010-05-03
This is probably a easy fix, but not in the manner you suggest, post this boot script so we can see exactly what going on.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
We will need a little better description as to when you boot the computer what happens what happens, are you just going straight to XP.

for those of you who just want to throw fixes at the op, remember we don't really have any definitive information here, so lets find out whats really going on.

---

### Post by G-Sun on 2010-05-04
> **wilee-nilee said:**
> This is probably a easy fix, but not in the manner you suggest, post this boot script so we can see exactly what going on.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
I don't have access to Ubuntu at this point, and the script is for linux only. Right?
> We will need a little better description as to when you boot the computer what happens what happens, are you just going straight to XP.
Ok
- Boot.ini loads from part1/XP and executes XP
I've not been able to add working lines for Ubuntu/part0 in boot.ini
- I've tried to set part0 as active in XP > Computer Management > Storage, but the option is greyed out (I guess because part0 is ext3)

Thanks!

---

### Post by G-Sun on 2010-05-04
I\m now in my Ubuntu 10.04 Live CD
and having trouble with using the terminal:

```
grub> sudo nautilus
Error 27: Unrecognized command

``````
sudo grub
Error 27: Unrecognized command

```So I can not run 
root (hd0,0)
and
setup (hd0)
or edit 40_custom (add the windows entry)

grub
gives me:
```
 [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> 

```and
help
gives me:
```
grub> help
blocklist FILE                         boot
cat FILE                               chainloader [--force] FILE
clear                                  color NORMAL [HIGHLIGHT]
configfile FILE                        device DRIVE DEVICE
displayapm                             displaymem
find FILENAME                          geometry DRIVE [CYLINDER HEAD SECTOR [
halt [--no-apm]                        help [--all] [PATTERN ...]
hide PARTITION                         initrd FILE [ARG ...]
kernel [--no-mem-option] [--type=TYPE] makeactive
map TO_DRIVE FROM_DRIVE                md5crypt
module FILE [ARG ...]                  modulenounzip FILE [ARG ...]
pager [FLAG]                           partnew PART TYPE START LEN
parttype PART TYPE                     quit
quietboot                              reboot
root [DEVICE [HDBIAS]]                 rootnoverify [DEVICE [HDBIAS]]
serial [--unit=UNIT] [--port=PORT] [-- setkey [TO_KEY FROM_KEY]
setup [--prefix=DIR] [--stage2=STAGE2_ terminal [--dumb] [--no-echo] [--no-ed
terminfo [--name=NAME --cursor-address testvbe MODE
unhide PARTITION                       uppermem KBYTES
vbeprobe [MODE]

grub> 

```

---

### Post by G-Sun on 2010-05-04
Tried:
```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sd1
Probing devices to guess BIOS drives. This may take a long time.
/dev/sd1: Not found or not a block device.

```
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by G-Sun on 2010-05-04
Ran:
```
ubuntu@ubuntu:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/memtest86+.bin
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

---

### Post by Animal X on 2010-05-04
> **G-Sun said:**
> Ran:
```
ubuntu@ubuntu:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/memtest86+.bin
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```
how about a copy of that menu.lst ?

---

### Post by Animal X on 2010-05-04
> **G-Sun said:**
> Hi!

I've installed Ubuntu and XP (in that order) and need to fix my boot. How?

I've installed Ubuntu 10.04 on hd0 part0
Installed XP on hd0 part1

Part1 is currently the active one,
and XP is the only OS loading now.

Tried to add an ubuntu line in boot.ini,
but didn't manage and don't wanna mess things up there.
Tried Super Grub, but no success.

So, I believe what I have to fix is:
- Setting Part0 as active
- Update Grub (and add entry for XP)

How to achieve this?

Thanks!
wait a second, you did Ubuntu first then XP?
my thinking is that its better to have XP first then Ubuntu, both partitionally speaking and order of installation....XP overwrote your boot so i see these options right off:
try easybsd for windows
try grub for windows
reinstall grub with live CD

...maybe? Good Luck.

---

### Post by G-Sun on 2010-05-04
I\m a little pissed about the 10.04 Live CD -terminal
I just can\t use the codes I find on all the help/pages. Why!?

---

### Post by G-Sun on 2010-05-04
I reinstalled Ubuntu.
That seem to solve my problem..

---

