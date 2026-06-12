---
title: "Can't boot after installing theme from adept"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by BryanFRitt on 2007-12-10
I was trying to install themes for my computer (KUbuntu) using **adept**.  I don't remember what I was trying to install, other than it probably had the word **theme** in it.  At the end of the install it prompted me to pick either **kdm** or **gdm**, not wanting to mess with anything technical at the time I clicked **cancel**.  This message came up twice, and I picked cancel both times. (When it installed I think my window title bar icons disappeared, but the title bar was still there?)  When I rebooted it went into the boot menu fine, but after that I get error messages and it doesn't even boot into a command prompt.  

Here's pictures of what it looks like during boot, note this text was copied by hand from the pictures.

Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
> ...
Linux agpgart interface v0.102 (c) Dave Jones
Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing
enabled
serial8250: ttys0 at I/O 0x368 (irq = 4) is 16550A
RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bloc
ksize
input: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq
1,12
serio: i8042 KBD port 0x60,0x64 irq 1
serio: i8042 AUX port 0x60,0x64 irq 12
mice: PS/2 mouse device common for all mice
TCP cubic reqistered
NET: Registered protocol family 1
/build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: u
nable to open rtc device (rtc0)
input: AT Translated Set 2 keyboard as /class/input/input1
VFS: Cannot open root device ""UUID=a686d711-2986-44dc-8bab-ca7661
b00981"  or unknown-block(0,0)
Please append a correct "root=" boot option; here are the availab
le partitions:
Kernel panic - not syncing: VFS: Unable to mount root fs on unkno
wn-block(0,0)

Default mode:
Ubuntu 7.10, kernel 2.6.22-14-generic
> Kernel panic - not syncing: VFS: Unable to mount root fs on unkno
wn-block(0,0)

kernel alive
kernel direct mapping table up to 120000000 @ 8000-e000

the Alpha and Scroll lock blink

My /boot/grub/menu.lst
[http://www4.ncsu.edu/~bfritter/menu.lst](http://www4.ncsu.edu/~bfritter/menu.lst)

System info:
Dell Latitude D830
2.2GGHz Intel Dual Core 2
4GiB RAM
Bluetooth
ABGN
WUXGA (1920x1200)
DVD Drive

Dual Boot (at least was)
Vista Business, and KUbuntu 7.10
from
kubuntu-7.10-dvd-amd64.iso

In Windows, I have Read/Write access to the Linux partitions using IFS Drives installed using compatibility mode. (causes delayed shutdowns)

How can I get booted back in KDE, etc...? (or at least a command prompt)
What happened? (to prevent it from happening again)

If you need more info to help, ask, 

 Thanks,
  - Bryan

---

### Post by BryanFRitt on 2007-12-13
I found some files in /boot that where backup files, and so I make a backup of the whole directory, and replaced the originals with the backups.  Booted in to recovery mode, it worked (it scanned some partitions).  Then I rebooted into normal mode.  Messed with kwin --replace and compiz --replace commands.  (The messed up windowings might have been because I had an extra monitor attached that I don't normally have., so I unplugged it and rebooted)  Everything seams to work fine now, Except for it looks like Emerald is doing my window decorations now, instead of KDE.

I tried to run adept again, it told me it was already running, I did something, it crashed.  Tried running adept again looks like it worked, but it isn't showing anything for the last package run.

Here's a list of what adept said when I looked for "theme":

[http://www4.ncsu.edu/~bfritter/Screenshot-Adept%20Manager%20-%201.png](http://www4.ncsu.edu/~bfritter/Screenshot-Adept%20Manager%20-%201.png)
[http://www4.ncsu.edu/~bfritter/Screenshot-Adept%20Manager%20-%202.png](http://www4.ncsu.edu/~bfritter/Screenshot-Adept%20Manager%20-%202.png)
[http://www4.ncsu.edu/~bfritter/Screenshot-Adept%20Manager%20-%203.png](http://www4.ncsu.edu/~bfritter/Screenshot-Adept%20Manager%20-%203.png)
[http://www4.ncsu.edu/~bfritter/Screenshot-Adept%20Manager%20-%204.png](http://www4.ncsu.edu/~bfritter/Screenshot-Adept%20Manager%20-%204.png)
[http://www4.ncsu.edu/~bfritter/Screenshot-Adept%20Manager%20-%205.png](http://www4.ncsu.edu/~bfritter/Screenshot-Adept%20Manager%20-%205.png)
[http://www4.ncsu.edu/~bfritter/Screenshot-Adept%20Manager%20-%206.png](http://www4.ncsu.edu/~bfritter/Screenshot-Adept%20Manager%20-%206.png)

I hope this helps someone in the future.

-Bryan

---

### Post by BryanFRitt on 2008-01-15
I think this was because I hit CANCEL instead of picking KDM (for KDE in KUbuntu). 
(Would have worked if I picked the wrong one?)

---

### Post by BryanFRitt on 2008-03-07
This has happened two more times since I've wrote this.  These times with Adept Manager crashing or something not installing or updating right.  The solution has been the same, replace the boot files with their backups.  I'm glad there are backups, just wish I didn't have to go through all the trouble of booting into an alternate OS and the restoring the backups.

---

