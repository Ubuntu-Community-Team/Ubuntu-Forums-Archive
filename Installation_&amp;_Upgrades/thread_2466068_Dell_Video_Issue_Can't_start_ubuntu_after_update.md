---
title: "Dell Video Issue Can't start ubuntu after update"
date: 2021-08-18
forum: Installation &amp; Upgrades
---

### Post by RobertoRecordo on 2021-08-18
I have a similar problem, and while I looked at other threads including 
**[SIZE=3][Graphics Resolution- Upgrade /Blank Screen after reboot]("https://ubuntuforums.org/showthread.php?t=1743535")[/SIZE]**

and this discussion seems to be most similar to my situation.

System:
Dell Optiplex 7010 Intel Core i5-3550 3.30Ghz 4GB RAM 500GB
Service Tag 3CRJHT1  - Dell recognizes it , BUT the BIOS reports DPCC002   ????
BIOS: American Megatrends 2.4.0 1/13/2011

[FONT=sans-serif]Video[/FONT][FONT=sans-serif] Feature[/FONT][FONT=sans-serif] Specification[/FONT]
[FONT=sans-serif]Integrated[/FONT]

[LIST]
[*][FONT=sans-serif]Intel HD Graphics (Celero/Pentium CPU-GPU)[/FONT] 
[*][FONT=sans-serif]Intel HD Graphics 2000 (iCore DC/QC Intel 7 Series Express [/FONT][FONT=sans-serif]Chipset CPU-GPU combo)[/FONT] 
[*][FONT=sans-serif]Intel HD Graphics 2500/4000 (i3/i5/i7 DC/QC Intel 7 Series [/FONT][FONT=sans-serif]Express Chipset CPU-GPU Combo)[/FONT] 
[/LIST]


I am doing a fresh install of Xubuntu 20.04.2.0  [https://torrent.ubuntu.com/xubuntu/releases/focal/release/desktop/xubuntu-20.04.2.0-desktop-amd64.iso.torrent](https://torrent.ubuntu.com/xubuntu/releases/focal/release/desktop/xubuntu-20.04.2.0-desktop-amd64.iso.torrent)

[LIST=1]
[*] The new hard drive, in this system, had the latest LTS of Kubuntu installed. No problems at all.  I decided that XFCE was my preference. 
[*] Both the ISO and install disk were verified with sha256 scan, and passed 
[*]The Live CD works as expected 
[*]The installation fails with blank screen and blinking cursor. This is after I see the keyboard = man at the bottom of the screen. I think I see the keyboard at the top left of the screen for a brief period. 
[*]I tried to hold the shift key and ctl-alt F1 to get a terminal several times with no success 
[/LIST]

I will provide more information if it is helpful, or try a non LTS version if it is of diagnostic value.

I need that system back up!

---

### Post by oldfred on 2021-08-18
Moved to your own thread to avoid issues of different instructions probably are needed.

Dell has rolled out UEFI updates to many older systems due to an issue.
Did your system get an UEFI update?
You may need to review and redo your UEFI settings that you changed when you first installed.
Particularly check if UEFI drive setting was changed back to RAID or Intel RST. It needs to be AHCI.

Also:
Often better to have UEFI Secure boot off. And UEFI fast boot off, as that assumes no system changes & you are changing system.

---

### Post by MAFoElffen on 2021-08-19
if the first panel was the purple with the man and keyboard options at the bottom, then the BIOS is booting in Legacy BIOS mode... if when you first get to that panel, it you press the <Enrer> or <Spacebar> key... Doe sit go to a panel where it has F-x keys maps in the bottom, where <F6> would bring up the Options Menu?

---

### Post by RobertoRecordo on 2021-08-19
Old Fred - 

I have an AMI Bios 2.4.0 1/13/2011  - I think it is too old for EFI 
I am at the moment trying to install Xubuntu 21.04, out of lack of any other idea. Kubuntu was able to install, as I mentioned.

Did my system get an UEFI update?  I have not updated the bios, I bought it it 2017.


MAFoElffe

                                     I only tried shift and F1 - there was only seconds between the appearance of keyboard=man and the blinking cursor of death.

~~~~ This Just In ~~~~
1) I rebooted after installing Xubuntu 21.04  
2) I looked at the BIOS settings, there is no mention of EFI or UEFI
3) Xbuntu booted successfully

Recalling that I had two attempts at installing the LTS version, the first with my usual partitioning scheme for two users, and the second with the vanilla install, I think that the problem may be in Xubuntu 20.04 LTS , some users reported that using an earlier Kernel solved the problem - here, I think
[https://ubuntuforums.org/showthread.php?t=2456498]("https://ubuntuforums.org/showthread.php?t=2456498")

I appreciate you comments about this, I am curios to know if this is effecting other users.

---

### Post by RobertoRecordo on 2021-08-19
I declared victory too soon.

What worked was booting from the install disk - is that the same as a hard reset?

This morning, I did a cold start - and get the  blank screen and blinking cursor. 
I do not see the keyboard = man
*** The Wrong Hard Drive was first in the boot order: and it has the boot flag set, even though there is nothing bootable on it. ***
I did check the boot order when I was trying to boot 20.04 LTS.  

Just for fun, I cleared the boot flag on the second drive, and changed the boot order so it was first. The system tried to boot it did nothing more. I had thought the bios would attempt to boot the next drive (21.04) but it did not. 

I thank you, and will close this thread.

---

