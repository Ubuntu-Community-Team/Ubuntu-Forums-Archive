---
title: "GRUB loading error"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by Llamano on 2010-01-02
Hello,

I am totally new to both Linux and Ubuntu and this is my first attempt to install it. Unfortunately I received an error message after what seemed to be a successful installation on restart: 
"GRUB loading
error: no such disk
grub rescue>"
Just a quick note to the community, because I cannot boot into either XP or Ubuntu to access the net (livecd boot doesn't recognize my wireless drivers) ths entire post is done from my iPhone. 
Here is the posting from the 'sudo fdisk' command (booted from livecd and accessed terminal). Due to extreme typing limitations on my iPhone, it probably won't be formatted the way it appears onscreen. 

(note: I have my internal 120gb drive, where windows is installed, and an external 1tb drive, where ubuntu and a whole bunch of my windows data resides)

disk /dev/sda: 120.0 gb, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
units=cylinders of 16065 *512 = 8225280 bytes
disk identifier: 0xe686f016

Device Boot. Start. End. Blocks. Id. System
/dev/sda1 1. 6. 48163+. de. Dell Utility
/dev/sda2. *. 7. 13725. 110197867+ 7. HPFS/NTFS
/dev/sda3. 13727. 13987. 2096482+. f. W95 Ext'd (lba)
/dev/sda4. 13988. 14593. 4867695. db. CP/M / CTOS / ...
/dev/sda5. 13727. 13987. 2096451. dd. Unknown

Disk /dev/sdb: 1000.2 gb, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes
disk identifier: 0x81611240

Device Boot. Start. End. Blocks. I'd. System
/dev/sdb1. 1. 108777. 873751221. 7. HPFS/NTFS
/dev/sdb2. 108778. 121601. 103008780. 5. Extended
/dev/sdb5. 108778. 121074. 98775621. 83. Linux
/dev/sdb6. 121075. 121601. 4233096. 82. Linux swap/Solaris

there is the entire record of what is going on. I tried all the 'stub grub' or '$ grub' commands to type into the terminal followed by the find command that I have seen in other forums. The stub grub or $ grub commands don't work from booting from livecd or from the initial prompt that I get when my computer starts up, and the finds command universally fails from both these platforms as well. I'm really afraid that I will have to pop my ancienne XP Installation disk back in to restore my computer to a workable state. I'd really just rather fix this, without destroying the existing data on my external HD (the one where Linux was installed). 

I have come across several other posts with the same problem, but there does not seem to be a coherent solution (half the commands do not even work for me). 
Any help is seriously appreciated, but remember I cannot copy and paste from my computer and I am a serious noob to Linux. 

edit: changing the boot sequence does not work, as my external HD operates off an eSata cable through my expressport. My bootsequence does not allow for that. 

Thank You

---

