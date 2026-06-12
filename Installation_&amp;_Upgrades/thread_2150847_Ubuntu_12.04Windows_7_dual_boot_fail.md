---
title: "Ubuntu 12.04/Windows 7 dual boot fail"
date: 2013-06-02
forum: Installation &amp; Upgrades
---

### Post by dariusd on 2013-06-02
I've been trying to install Ubuntu 12.04 to dual boot alongside Windows 7 on my Lenovo Ideapad U410 for a while now.

  
THE SHORT VERSION:

  At first I couldn't boot anything.  This was my non-working boot config:

  [http://paste.ubuntu.com/5719520/](http://paste.ubuntu.com/5719520/)

  I ran boot-repair, and afterwards I started getting the boot menu to  choose between Ubuntu and Win7.  Ubuntu now works, but Win7 still  doesn't work.  Here is my current, repaired boot config:

  [http://paste.ubuntu.com/5719533/](http://paste.ubuntu.com/5719533/)

  
THE LONG VERSION:

  The Ideapad has an SSD in addition to the HDD and that got in the way  initially.  My /dev/sda/ (a.k.a. Disk 0) is some Windows hibernate  partition.  /dev/sdb/ (a.k.a. Disk 1) is where all the real stuff is.   The installer only ever saw /dev/sda until I did a few things: turned  off Intel Rapid Start Technology, switched the mode from RAID to  Compatible in the BIOS, and also removed dmraid before running the  Ubuntu installer.  Then it detected the existing operating system and  let me install Ubuntu alongside.  I chose the option to have it ask me  which OS to boot into on startup every time.
  
After the initial install, it kept trying to boot straight to Windows  instead of giving me a choice.  It would hit a blue screen of death and  then restart and try to run Windows Startup Repair, which didn't fix  anything (see first link for my boot config at this point).

  
Then I ran boot-repair with the automatic settings, and now it pops  open the menu on startup and lets me choose.  If I choose Ubuntu, it  boots correctly.  If I choose Windows 7, I still have the same problem:  BSoD and automatic restart. (see second link for my current boot config)

  
Any ideas how I can go about repairing the Windows boot record?  The  Windows config with the various partitions is really obnoxiously  complicated, so I'm not sure how to proceed or what the root of the  problem is.  I've also tried turning off UEFI Boot in the BIOS to no effect.

---

### Post by fantab on 2013-06-02
Your Windows does not boot in UEFI. So you cannot boot Ubuntu in UEFI. Either both OS should boot in UEFI or both in legacy BIOS.
When you installed Ubuntu you installed Ubuntu in 'EFI' Mode. I have no idea how you managed this, though I suspect that UEFI is 'enabled' in the BIOS/UEFI. Disbale it. Boot-repair removed grub-efi and installed grub-pc for you hence you can boot Ubuntu.

> 
The following packages will be REMOVED: grub-efi grub-efi-amd64 The following NEW packages will be installed: grub-gfxpayload-lists grub-pc grub-pc-bin

[QUOTE=paste.ubuntu.com/5719533/]

Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *        2048      411647      204800    7  HPFS/NTFS/exFAT 
/dev/sdb2          411648   [COLOR=#b22222]**833247231**[/COLOR]   416417792    7  HPFS/NTFS/exFAT 
/dev/sdb3       935811072 [COLOR=#008000]**  976361471**[/COLOR]    20275200   12  Compaq diagnostics 
/dev/sdb4       [COLOR=#b22222]**833249278**[/COLOR]   935811071    51280897    5  Extended 
**Partition 4 does not start on physical sector boundary**. 
/dev/sdb5       833249280   919318527    43034624   83  Linux 
/dev/sdb6       919320576   935811071     8245248   82  Linux swap / Solaris  
**Partition table entries are not in disk order**[/QUOTE]

Ideally your partition 4, /dev/sdb4 should start after [COLOR=#008000]**  976361471 **[/COLOR]but it starts at[COLOR=#b22222]** 833249278**[/COLOR]. I am not sure if Boot-Repair can fix this.

To recheck post the output of:
```
sudo fdisk -l
```

_[**FIXPARTS**]("http://www.rodsbooks.com/fixparts/")_ can fix this for you.

I am not sure if this can cause BSOD in Windows, but it is possible.
I also suspect that when you installed ubuntu in efi mode it may have corrupted Windows. I may be wrong.
Use 'fixparts' if the above partition error still shows up with 'fdisk -l'. And try to boot Windows.

What you can do is '_[**fix Windows MBR**]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html")_'... this will corrupt GRUB but if Windows boots then we can re-install Grub or use Boot-Repair to do so.

EDIT: or try this if you don't have a Windows install disc: [http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)

---

### Post by dariusd on 2013-06-03
I've already tried booting with UEFI mode enabled or disabled and it hasn't made a difference.  You say that I installed Ubuntu in EFI mode, but the strange thing is that using the diagnostic instructions here, it says it's installed in Legacy mode:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I think Windows must have been installed in EFI mode as well, because UEFI boot was enabled by default until I turned it off.  Anyway, I'll try fixing the partitions and maybe repairing the Windows MBR and see how far I can get.  Thanks for the detailed response!

---

