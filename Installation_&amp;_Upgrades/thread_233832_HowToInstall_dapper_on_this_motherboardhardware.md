---
title: "HowTo:Install dapper on this motherboard/hardware"
date: 2006-08-10
forum: Installation &amp; Upgrades
---

### Post by codejunkie on 2006-08-10
[SIZE="2"]After jumping through hoops trying to get dapper installed on my new motherboard, and not being able to find any info about installing linux on it on the forums/google etc, I decided to start a motherboard/hardware specific installation thread. everyone please contribute to this thread, and please add all the systems you have running dapper, since it will be very helpful to the new users trying to get ubuntu installed on there hardware.[/SIZE]
[LIST=1]
[*]Please list the motherboard model, and additional hardware you have installed.
[*]Give a detaled explanation of any special tricks/boot commands you had to use to get dapper to install correctly on the hardware.
[*]list all hardware that works correctly out of the box so to speak.
[*]list all the hardware that doesn't working out of the box, and what you had to do to make it work.
[/LIST]
[B]
ECS K7S5A pro
Athlon 2100+
1gig pc133 ram
40gig seagate ide harddrive
liteon 16x dvd drive
Nvidia GeForce4 mx 4000 agp
[/B]
[I]no special boot options needed.
dapper install's and runs great on this machine out of the box.
all onboard devices and my nvidia video card are supported.[/I]

[B]Biostar NF325-A7
Athlon64 3400+
256mb DDR 400
80gig maxtor ide harddrive
40gig maxtor ide harddrive
pioneer 8X DVDRW
Nvidia 6200 agp graphics card
[/B]
[I]When using the live Desktop cd to install ubuntu, you need at least 512MB of ram in this board for some reason else the installer freezes at setting up the partitions.

When using the live/install DVD or the alternate install discs, if you have 512MB + it should install without a hitch. for systems with low memory like mine, the only way i could get it to install was by doing a server install then when i reached the terminal run ```
sudo apt-get install ubuntu-desktop
```the system runs fine and is fast with only 256MB of ram, but the installer hangs on selecting and installing software with a small amount of memory installed.

all onboard devices and my Nvidia 6200 card are working out of the box.[/I]

---

### Post by SebMKd on 2007-01-12
[B]ECS K7S5A
AMD Athlon XP 1900 Palomino @ 133MHz
256MB DDR266 @ 133MHz
40GB 5400rpm WD
Generic 32x CD-ROM
Apollo GeForce4 MX440-SE AGP 4x
[/B]
[I]CD ROM and HDD are old and maybe buggy. I couldn't get the LiveCD to install Dapper all the way through. I've had to use the Alternate Dapper version, and it finally worked fine.
I didn't install the ENVY script (for Nvidia) because the screen resolution and refresh rate were fine.[/I]

**AsRock K7S41**
See signature

*No problem what so ever! Dapper LiveCD worked like a charm* :)

---

