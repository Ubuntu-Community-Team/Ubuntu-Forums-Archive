---
title: "Install Glitch- 14.04.3 LTS &amp; Windows 10"
date: 2015-10-10
forum: Installation &amp; Upgrades
---

### Post by oxvectors on 2015-10-10
Greetings to the list:

Absolutely brand-spanking new Ubuntu user here.  Got very tired of MS and their shenanigans, and wanted to try Ubuntu in a dual-boot configuration.

(Spoiler alert:  Boot Repair Tool results:  [http://paste.ubuntu.com/12728649/](http://paste.ubuntu.com/12728649/))

Machine specs:

Lenovo IdeaPad N580
500 GB HD
Windows 7 OEM OS 'upgraded' to Windows 10 recently (and my catalyst for trying Ubuntu)

Our story so far:

Did my research and started the prep for install.  Shrank partition for windows, resulting in 224GB unallocated space. Unable to create new partition due to four already present (C:/windows, D;/Lenovo, Windows recovery and Reserved).  Deleted Lenovo and created new D:/Linux 160GB.

Installed Ubuntu. During install, no OS recognized.  Selected 'Other'.  Dialog box said the 160GB partition wasn't in file root (or something similar. Going from memory here.)  Researched and selected EXT4 type and '/' as mount point.

Got warning of no swap file present.  Designated remaining free space as swap file (approx 70GB).  Remainder of install smooth.  Machine booted directly into Ubuntu and it works flawlessly.  Queried a veteran Ubuntu user about the absence of boot dialog to offer Windows option (needed for some work requirements).  He suggested Boot Repair. Ran it and followed directions.

Results were the link [http://paste.ubuntu.com/12728649/](http://paste.ubuntu.com/12728649/) and the following message:  

[COLOR=#000000][FONT=arial]The boot files of [The OS now in use - Ubuntu 14.04.3 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([/FONT][/COLOR][https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)[COLOR=#000000][FONT=arial])

I now get the option dialog box on boot (Ubuntu, Win 7 & Win Recovery).  Even though I had upgraded to Win 10, I realize this just may be semantics.  My issue is that when selecting Win 7, I run into a loop of error dialogs (black & white screen) about unsigned drivers, etc.

Being new to Ubuntu and especially dual-booting, I don't want to make a bad problem worse, hence my posting here.  What can I do to properly configure this machine?  Am I relegated to starting completely over with a Win10 install, then installing Ubuntu? (I hope not.)  Or is there a way that you, the collective wizards of Ubuntu, can suggest for me to salvage this novice attempt so far.  I firmly believe in doing something correctly (which I've obviously failed at so far).

Thank you for your help & guidance.

oxvectors[/FONT][/COLOR]

---

### Post by ubfan1 on 2015-10-10
BIOS machine, with MBR disk, OK.  The only odd thing at first glance is the boot flag on sda1, the Windows recovery partition instead of sda2, the Windows partition.

---

### Post by oxvectors on 2015-10-10
ubfan1- thanks for looking at the results file.  "Can the patient be saved?" LOL

---

### Post by yancek on 2015-10-10
> 
[COLOR=#000000][FONT=arial]The boot files of [The OS now in use - Ubuntu 14.04.3 LTS] are far from the start of the disk[/FONT][/COLOR]

I would not worry about that if Ubuntu boots.

> [COLOR=#000000][FONT=arial]I now get the option dialog box on boot (Ubuntu, Win 7 & Win Recovery).  Even though I had upgraded to Win 10[/FONT][/COLOR]

I would not worry about that either.

> [COLOR=#000000][FONT=arial]My issue is that  when selecting Win 7, I run into a loop of error dialogs (black &  white screen) about unsigned drivers, etc.[/FONT][/COLOR]

Can you post more specifics on what the errors are?  On my Desktop with windows 7, the boot partitions (sda1) is marked active and I have no trouble booting it so I'm not sure that is the problem.  Simple enough to change using GParted on the Ubuntu install medium.  If it doesn't help, you can change it back.

How did you shrink the windows partition?  Usually best to use windows Disk Management tool then reboot and run chkdsk.
Your Grub menu shows three entries for windows.  The first points to sda1 which is too small to be other than a boot partition.  Have you tried the first two options and what are the results.  I also notice that the first and third windows entries are labelled Windows Recovery.  You should not have two Recovery partitions.

---

### Post by oldfred on 2015-10-10
I do not see any major issues. You show Windows boot files in both sda1 & sda2, so either may be bootable. Boot-Repair will copy boot files from the typical 100MB Windows boot partition to main install. Many users just delete Windows boot partition not knowing it is essential and then have no way to recover boot files. And then grub finds boot files in both partitions and adds two entries to grub menu.

Windows uses boot flag to know which partition has boot files. Grub searches for boot files.
Grub also has not been updated to add a 'Windows 10' description, so it uses default which may be just recovery?

Since new UEFI hardware but BIOS installs, it may want to give booting in Non-secure mode.
You do not need swap to be more than 2GB. Use rest of space as a NTFS shared data partition.
But with Windows 8 or later, the fast startup or hibernation leaves all NTFS partitions mounted & hibernated, so you must have the fast startup off.

       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

---

### Post by oxvectors on 2015-10-11
[ATTACH=CONFIG]264900[/ATTACH][ATTACH=CONFIG]264899[/ATTACH]

"I'd rather be lucky than good."

It appears it's all a matter of semantics.  Through the process of trial and elimination, I've discovered that the Windows Recovery on sda4 was (probably) for the Win7 original install.  All that loads when that option is selected is a wallpaper, then a reboot back to the Ubuntu boot menu.

If the Windows Recovery on sda1 is selected, Windows 10 loads (and operates) as normal.

I've included a screenshot of both the boot menu and disk management for reference.

To answer yancek, windows disk management was used to shrink win10.

So, given the above, how should I proceed from here?  As I said (and I'm sure my post confirms), I'm new to Ubuntu, but learning fast.  Please give specifics on what my next steps should be to have a healthy set-up.

oldfred-  fast startup & hibernation disabled.  What's the best way to redesignate the swap file size?

I thank you all for your help and guidance.

ox

---

### Post by yancek on 2015-10-11
I'm not sure what you want.  You said in the initial post you could boot Ubuntu and your last post indicates you can boot windows 10 selecting the first boot option.  Do you want to remove the other options?  I would think the sda4 partition was the original recovery partition for windows 7.  Not sure if that would be useful to you now with windows 10 or whether it would create problems.  

You can use GParted which is on the Ubuntu install medium to turn off swap and then shrink that as it is much too large.

---

### Post by oxvectors on 2015-10-11
Your last sentence is what I was definitely looking for, and I was wondering about deleting the recovery on sda4.  Thank you for bearing with me.

ox

---

