---
title: "single boot 32gb SSD"
date: 2014-11-18
forum: Installation &amp; Upgrades
---

### Post by jarkema on 2014-11-18
I have noticed a number of manufacturers have recently introduced aggressively priced netbooks with a 32GB SSD, 2GB RAM, a decent processor, and Windows 8 or 8.1 (???) preinstalled.  I'm not sure why anyone would install Windows 8 (which occupies 26GB on the drive and really needs minimum 4GB RAM) on hardware such as this. In fact the salesman at Best Buy advised me to pass it over (funny enough, as we were talking, an "insufficient memory" error flashed on the unit's screen - the only program running was McAfee automatic update!).

On the other hand, these should run Ubuntu no problem ! **But not as dual boot**.

I bought one and tried to boot off the LiveCD to see if it was Ubuntu-compatible.  It appears that the BIOS only allows the user to boot into Windows OS, even with SafeBoot in BIOS turned off - the only way to boot onto the LiveCD is clicking Shift-Restart in Windows 8 and then choosing to boot off the CD in the advanced restart options which appear.

I am very nervous about having LiveCD wipe the entire SSD and install Ubuntu as the only OS.  Is anyone familiar with how the Ubuntu installation process deals with a BIOS which seems to check to see if Windows is available, and otherwise does not boot?  Does UEFI require an EFI partition for all operating systems, and if so does the default Ubuntu installation handle it properly? 

My guess is that in clearing the SSD, Ubuntu will have to leave the EFI partition alone but change some of the files on it to trick the BIOS into thinking it is booting Windows while it is actually booting Ubuntu.  It will have to delete the recovery and Windows partitions, then create root, swap, and home partitions, then go through its normal installation procedures, ending with the EFI partition tweaks I mentioned in the previous sentence, so the unit can safely reboot in Ubuntu on the next restart.  Can anybody confirm that is what happens?

I suspect that in a couple months these 32GB SSD, 2GB RAM computers will be clearance-priced everywhere, as the manufacturers realize they need minimum 64GB SSD and 4GB RAM.

---

### Post by oldfred on 2014-11-18
Some of these systems also install 32 bit UEFI even though rest of system is 64 bit. 
Linux did not have a 32 bit UEFI so it was just to prevent Linux from installing, but that is changing. 
But I would not consider wasting money on that kind of system.

And even Ubuntu runs better with 64GB drive and 4GB of RAM. 

If 64 bit UEFI, you should be able to install. Some only boot Windows but we have work arounds.
You should be able to install Lubuntu which is lighter weight and uses less space so it should run well. 
My full working root uses about 11GB including /home. I have data all on another hard drive, so if not saving much data you could run the entire system in that 32GB SSD. I have a 32GB flash drive more for emergency boot installed in 16GB and the other 16GB for a data partitiona, but I do not use it regularly.

       Linux 3.15 Kernel Gains EFI Mixed Mode Support
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)
New  32 bit UEFI class 3 (no CSM) Only with recompile UEFI/grub/Ubuntu
[http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855)
Packard Bell ENME69BMP InsydeH2O  or Gateway LT41P04u
32-bit UEFI Support Proposed For Ubuntu Linux
[http://www.phoronix.com/scan.php?page=news_item&px=MTU1NjE](http://www.phoronix.com/scan.php?page=news_item&px=MTU1NjE)
Bay Trail -The ASUS "Bay Trail" T100 Is Not Linux Friendly
[http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE)
But someone has it partially working:
[http://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html](http://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html)

---

### Post by jarkema on 2014-11-19
Thank you, OldFred, those are very interesting observations, but I don't think that is the issue - these are all 64 bit systems running 64 bit Windows 8.1, and presumably 64 bit UEFI.

If I install Windows and then do Shift-Restart, I can boot up the LiveCD, no problem, from the "Use a Device" option, which I have done many times to make a computer dual boot.  The difference this time is that I would be wiping out the Windows OS in a Ubuntu single boot installation, and could possibly render the computer unbootable with any OS (if it insists on booting a Windows OS which isn't there any more, and any other device has to be booted using Shift-Restart in Windows).

I am hoping someone who is familiar with how the LiveCD does what it does can confirm that if you choose to erase the drive of one of these computers and install Ubuntu, that either it preserves the EFI partition or creates a new one, and after installing the Ubuntu, tweaks files in the EFI partition to fool the computer into thinking it is booting Windows OS when it is actually booting Ubuntu.

---

### Post by oldfred on 2014-11-19
Some were Windows 32 bit or at least UEFI was and could only be booted with a 32 bit UEFI.

If you totally erase drive, Ubuntu will create a new efi partition, if installing in UEFI mode. You have to boot installer in UEFI mode to install in UEFI mode.
 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


Does live installer, flash drive boot in UEFI mode and can you run this without major issues?

There are a variety of work arounds for those systems that 'only' boot Windows. If just Ubuntu, using efibootmgr to just rename the grub file to read Windows. 
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Ubuntu assumes vendors comply with UEFI spec and do not restrict UEFI boot to only Windows. So you have to manual do one of the work arounds.

I normally partition in advance with gparted. And I make sure drive is gpt partitioned, which you must select before doing anything else.
      
 I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

Then I use Something Else to choose partitions.

I would backup Windows just in case, or if later you decide to sell system.
      
 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Since drive is smaller, I would not have a separate /home, then unused space is shared, so whichever uses more data has space.

---

### Post by jarkema on 2014-11-22
Making a set of recovery CDs for Windows before experimenting is a good idea.  I had been hesitant to install Windows in the first place because of all the little partitions it seems to create, which I was afraid Ubuntu wouldn't delete, but since you say Ubuntu erases the driive and creates a new EFI partition, that shouldn't be a problem.

I returned the laptop I was originally working on to get a full refund, but this Friday is Black Friday, I'll see if I can pick up one of these 32gb SSD netbooks, install Windows, make recovery disks, then boot into the LiveCD from UEFI devices in Windows after doing Shift-Restart in Windows.  Then I'll choose the "erase drive and install Ubuntu" option, see how it goes, and report back to this thread how it went.

Let's keep this thread open until I can report back.  Thanks.

---

### Post by jarkema on 2014-12-04
By way of a progress report, the laptop I was originally working on (which wouldn't even boot oft the 64 bit Ubuntu 14.04 LiveCD was an Asus X205TA, and I learned on an Amazon post for that product that it used 32 bit UEFI, so it turns out, OldFred, you were dead on right about that.  From that, we learn the X205TA with UEFI is not a candidate for Ubuntu.

On Black Friday, I picked up an Acer E11 for $229 (pretty good price for Canada).  Ubuntu does install on that, but boots intermittently, and when it does, it takes over a minute to boot (not acceptable for an SSD).  When it does boot, there are all kinds of I/O error messages flashing down the screen, makes me wonder if the problem is a defective SSD.  I'm stll working on trying to get it to boot quickly.

---

### Post by oldfred on 2014-12-04
Someone did get at least partially a 32 bit UEFI to work.
 Instructions to install Ubuntu 14.10 on ASUS EeeBook X205TA - Atom Bay Trail 32 bit UEFI
[https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md)
Linux 3.15 Kernel Gains EFI Mixed Mode Support
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)

Not sure if this is a similar model or not:

 Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)
Acer E1-531 UEFI menus.
[http://www.tomshardware.com/forum/65627-63-body](http://www.tomshardware.com/forum/65627-63-body)
Herman's 2014_02_09 - My Adventure with Secure Boot in an Acer Aspire E1-531 Laptop
[http://members.iinet.net/~herman546/2014_02_09%20-%20My%20Adventure%20with%20Secure%20Boot%20in%20an%20Acer%20Aspire%20E1-531%20Laptop.html](http://members.iinet.net/~herman546/2014_02_09%20-%20My%20Adventure%20with%20Secure%20Boot%20in%20an%20Acer%20Aspire%20E1-531%20Laptop.html)

---

### Post by Gordonbp531 on 2014-12-04
FWIW, I have an Acer E3 that came with Windows 8.1 with Bing.
I discovered that I had to set a UEFI password in the BIOS before I could then add the Ubuntu EFI to the "secure boot database". It then booted straight into Grub with no problems - beforehand it hadn't even acknowledged the presence of a Linux install, even though all the files were in the partition!

---

### Post by jarkema on 2014-12-08
I would like to emphasize to all following this thread that the issue is not whether the Acer E11 with a 32 gb SSD can single boot Ubuntu; it does, but it is S-L-O-W. It takes about a minute and a half to boot, and during that time the screen dumps about sixty error messages about mmcblk0rpmb: error -110 transferring data... and mmcblk0rpmb: timed out sending r/w cmd command... and so on.

I did some more Internet research on this error, and found that it is apparently a Linux kernel problem associated with SSDs: this web page
[https://dev-nell.com/rpmb-emmc-errors-under-linux.html](https://dev-nell.com/rpmb-emmc-errors-under-linux.html)
shows the exact same error I was getting, and although it has a kludge solution, I think it is beyond the capability of most Ubuntu users (such as myself) to implement "kernel patches".

This web page
[http://linuxnorth.wordpress.com/2014/08/23/installing-linux-on-the-asus-transformer-book-t100/](http://linuxnorth.wordpress.com/2014/08/23/installing-linux-on-the-asus-transformer-book-t100/)
gives a step by step instruction for solving this problem in a dual boot situation, but looks like it is using 32 bit Ubuntu; it specifically deals with the Asus T100. I'm not sure how they installed 32 bit Ubuntu in UEFI mode, but the only version of Ubuntu my Acer E11 recognized was the 64 bit 14.04 (which happens to be fully UEFI compliant). It didn't recognize 32 or 64 bit Ubuntu 12.04.4 Live CDs.

Since this all suggested an updated Linux kernel would solve the problem, I made a copy of the latest 14.10 LiveCD 64 bit and installed that, using the “Erase drive and install Ubuntu” option.  This installed without incident, and I didn't even have to run Boot-Repair (in the Acer BIOS, I could just set shimx64.efi in the ubuntu folder of the EFI partition as a trusted efi file), however it still took 48 seconds to boot (I suspect this kernel is getting the same time out errors, just not displaying them).  This is the same speed as my HP Mininote 2140 running Ubuntu 12.04 from a hard disk, but waaaaay longer than the 8 seconds it takes to boot in Windows 8.1 with “Fast startup” turned off.  I also noticed that the touchpad could point, but couldn't drag (this was not a problem in 14.04). All pointing functions worked for a USB mouse though.

Once Ubuntu is loaded, LibreOffice Write loads from the SSD in 4 seconds (the same speed as it does in Windows), and Firefox loads in 6 seconds (vs. 4 seconds in Windows). It appears that the time out errors only occur on boot.

Readers can draw their own conclusions, but the long boot time and the lack of touchpad drag support tell me that for my purposes (i.e. getting a decent value laptop which single boots Ubuntu faster than a computer with a conventional HDD), Ubuntu has not been sufficiently developed to run as single boot on hardware such as this (although with larger SSDs it does not appear to be a problem to dual boot Windows and Ubuntu – perhaps because on dual boot, GRUB2 chains into the Windows bootloader to avoid the time outs?)

There have been a number of threads dealing with installing Ubuntu on Chromebooks, but these MUST be dual boot, since Chromebooks have a custom BIOS that needs Google Chrome OS to run.

I'll keep this Acer E11 – I think I messed it up too much to get away with returning it  :-) .  However I plan to install future upgrades of Ubuntu on it until I find one that works properly (fast boot, all functions enabled) as single boot.

Thank you, OldFred, for your patience.  If you don't mind, I'll keep this thread open another week or two for other comments from the community before closing it.

---

### Post by oldfred on 2014-12-08
Some progress.

You might want to review boot logs to see if something else is an issue.
It is long but errors, warnings, repeated tries and either success or failure. And long time to next time stamp.
 sudo nano /var/log/dmesg 

But if errors or delays are from UEFI to grub I do not think there is a log.

---

