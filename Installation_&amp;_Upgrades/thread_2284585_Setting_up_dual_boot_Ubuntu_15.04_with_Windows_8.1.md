---
title: "Setting up dual boot Ubuntu 15.04 with Windows 8.1"
date: 2015-06-30
forum: Installation &amp; Upgrades
---

### Post by unaiza-ahsan on 2015-06-30
[COLOR=#333333][FONT=Ubuntu]I am trying to set up Ubuntu 15.04 dual boot into my Dell Alienware Area-51 R2 machine with Windows 8 preinstalled. I created three partitions (for /, home, and swap) manually in Windows 8. I booted from a Live USB of Ubuntu 15.04 and selected "Something Else" when choosing how to install. I set the partitions up as ext4 journaling file system ( for / and home) and swap for swap. Then, I installed into the main partition and it reboots.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]After rebooting, I get the exact same menu again (which appeared when I booted from Live USB) and I have to click on Esc - it goes into grub menu and I press Cntrl Alt Del to restart the PC.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Now.. it always reboots into Windows. Whatever settings I set.. always Windows. My secure boot is disabled and boot mode is UEFI.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]The reason I used 15.04 (and not 14.04) was that I wanted no such hassle and one of the ubuntu forums had a nice long article of an answer explaining that 15.04 is problem free.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Appears there is still something going wrong.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]For the record, I followed (exactly) the instructions given in this website: [http://www.pcsteps.com/961-install-ubuntu-linux-windows/](http://www.pcsteps.com/961-install-ubuntu-linux-windows/)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]
I would really appreciate suggestions. Thank you.[/FONT][/COLOR]

---

### Post by oldfred on 2015-06-30
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Can you go into UEFI and set ubuntu entry as first? Or use one time boot key often f10 or f12 to choose ubuntu entry?

This is now older and originally user used 32 bit, and 64 bit worked.

 [SOLVED] UEFI boot Issue with Alienware X51 
[http://ubuntuforums.org/showthread.php?t=2039451](http://ubuntuforums.org/showthread.php?t=2039451)

More up to date info in link below. but not specific to your system.

---

### Post by ajgreeny on 2015-06-30
You say you made new partitions using Windows.

I believe that partitions created with windows will often not work for an installation of linux as windows will creates dynamic partitions.  I do not use windows any more so I am not sure if this is always the case, or depends upon the circumstances.

You should simply make unallocated space with windows then create the partitions you want either with gparted from the live ubuntu system, or in the installer itself by choosing Something Else at partitioning stage.

Any thoughts, oldfred?

---

### Post by oldfred on 2015-06-30
Yes, you must be careful creating partitions with Windows that you use the more standard primary, extended & logical partitions if you have MBR(msdos). Windows likes to convert to dynamic, which is proprietary to Windows and some Windows tools do not even work on it. Linux sees dynamic as SFS in fstab listings.

With gpt there is only one type of partition, but Windows also has dynamic partitions called LDM in Linux.

Best rule of thumb is use Windows tools for Windows and Linux tools for Linux. Or use gparted or command line tools to create Linux partitions.

---

### Post by unaiza-ahsan on 2015-06-30
I made sure the disk was set to "basic" and not "dynamic" as the article (link I posted in my question) suggested. I still got that problem.

---

### Post by unaiza-ahsan on 2015-06-30
Hi. I ran Boot Repair and my Boot Info summary is here: [http://paste.ubuntu.com/11801996/](http://paste.ubuntu.com/11801996/)

Thanks.

---

### Post by oldfred on 2015-06-30
An ubuntu entry never was added to UEFI. Line 685
sudo efibootmgr -v

Installing grub should have added an entry.
Just run the fix that Boot-Repair is suggesting, be sure you have booting in UEFI mode. It says you are now per line 696.
It should show adding an ubuntu entry to UEFI.

You then can rerun this to see if ubuntu is added. Or post new report link.
sudo efibootmgr -v

---

### Post by unaiza-ahsan on 2015-06-30
All right. I did as the Boot Repair URL suggested and manually added the command "[COLOR=#000000]bcdedit /set [/COLOR][COLOR=#666666]{[/COLOR][COLOR=#000000]bootmgr[/COLOR][COLOR=#666666]}[/COLOR][COLOR=#000000] path [/COLOR][COLOR=#BB6622]**\E**[/COLOR][COLOR=#000000]FI[/COLOR][COLOR=#BB6622]**\.**[/COLOR][COLOR=#000000]..[/COLOR][COLOR=#BB6622]**\g**[/COLOR][COLOR=#000000]rub*.efi" in Windows Command Line and the problem is solved. Thanks![/COLOR]

---

### Post by ajgreeny on 2015-07-01
Great!

Please mark the thread as SOLVED from the Thread Tools menu at top.

---

