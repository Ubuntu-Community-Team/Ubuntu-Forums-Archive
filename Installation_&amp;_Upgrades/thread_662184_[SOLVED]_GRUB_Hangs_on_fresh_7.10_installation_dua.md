---
title: "[SOLVED] GRUB Hangs on fresh 7.10 installation dual boot"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by Edge74 on 2008-01-08
Hello all,

I had Fedora 8 dual booting with Windows XP Pro x64 with GRUB on the MBR giving me the choice of OS. This was no problem. I had read good things about Ubuntu and wanted to have a look. 

I installed Ubuntu 7.10 (server, 64 bit) on the HD that was previously home to Fedora, selecting "guided - use entire disk" and choosing sda as the disk to partition (sdc = windows xp installation, sdb = ntfs for storage). Ubuntu detected Windows XP and I opted to install GRUB on the MBR. I completed the installation process. 

My problem is that on rebooting the system hangs at the word GRUB with a flashing cursor. No menu. Nothing. 

I used the XP CD to get a command prompt through the recovery console and tried the following:

D:\WINDOWS 
C:
FIXBOOT C: 
FIXMBR 

This didn't work as on rebooting my system still hangs at a blank screen with the word GRUB and a flashing cursor. 

I apologise for being a bit of a noob and that I have probably missed something obvious but would somebody be kind enough to point me in the direction of a suitable solution to my problem?

Best wishes,

M.E.

---

### Post by Partyboi2 on 2008-01-08
What are your system specs?

---

### Post by Edge74 on 2008-01-08
AMD64 X2 4400+
2 Gb DDR400 RAM
3 x 160 Gb SATAII HD
2 x GeForce 6600GT

---

### Post by logos34 on 2008-01-08
try the easiest thing first--reinstall (ubuntu) grub to mbr of sda:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
(since you also have fedora there will be two roots to choose from)

post back if it doesn't work

---

### Post by Edge74 on 2008-01-08
Install CD (Ubuntu 7.10 server, 64 bit) gives option to boot from first hard disk only. When I attempt this I get the error "ntldr is missing". I tried to copy ntldr from Windows CD but got access denied. 

I tried installing GRUB to hd0 from the Ubuntu CD but still encountering same problem. Do I need to get a copy of the Ubuntu 7.10 desktop CD in order to install GRUB according to instructions in the link you provided?

---

### Post by logos34 on 2008-01-08
If the server install cd is anything like the alternate cd, there's a menu option 'Rescue a broken system'--go into rescue mode and select 'Reinstall grub bootloader'

---

### Post by Edge74 on 2008-01-09
OK- i chose the "rescue a broken system" option from the install CD's main menu and  selected /dev/sda1 as device to use for root system. I then selected "Reinstall GRUB bootloader" and entered (hd0) to install grub to the MBR. The installing GRUB bootloader progress bar stalled at 50% and dropped back to the rescue operations menu so I rebooted and was met by GRUB plus flashing cursor again.

I ran the rescue again but instead of choosing to reinstall grub I chose to execute a shell in /dev/sda1 and followed the guide posted at [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) which seemed to work. GRUB detected stage 1 at (hd0,0) so I continued, entering the following commands:

root (hd0,0)
setup (hd0)

I got an output telling me that embedding of e2fs_stage1_5 (hd0) succeeded as did installation of stages 1 & 2. I quit the shell and rebooted only to be met with GRUB plus flashing cursor again. 

I dunno what has gone wrong...

---

### Post by logos34 on 2008-01-09
check out [this page]("http://users.bigpond.net.au/hermanzone/p15.htm") (->'grub errors')

You could try it one more time.  Select 'reinstall grub bootloader', then enter **/dev/sda**.

Go into the Bios and make sure it's booting first from sda hard disk.

---

### Post by Edge74 on 2008-01-09
Many thanks for your help Logos34 and apologies for wasting your time - all sorted out now. Had to change boot order in BIOS. Didn't need to do so with Fedora so I guess that's why I overlooked it. Feeling a bit stupid nonetheless. 

Best wishes,

M.E.

---

### Post by logos34 on 2008-01-09
> **Edge74 said:**
> Many thanks for your help Logos34 and apologies for wasting your time - all sorted out now. Had to change boot order in BIOS. Didn't need to do so with Fedora so I guess that's why I overlooked it. Feeling a bit stupid nonetheless. 

no problem.  my pleasure.  Glad it's working.  click 'thread tools' and mark as 'solved'

enjoy

---

### Post by contents on 2008-03-13
thanks, Edge74, I had the exact same problem, and changing the boot order in the bios fixed it.

---

