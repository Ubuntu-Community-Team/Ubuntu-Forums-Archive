---
title: "Error Installing Ubuntu 10.04 on New Build"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by Hypernon on 2010-08-23
Hello, I've recently built a new computer and I'm unable to install Ubuntu 10.04 64-bit. I have verified that the install CD is working properly as I successfully installed Ubuntu 10.04 on my other machine with the same CD. When I run the CD on my new machine, I get the purple screen with the keyboard icon at the bottom, and I get to the Ubuntu logo with the options, but whenever I try to install Ubuntu I get a black screen with error text covering the whole screen. Testing Ubuntu without installing it also gives the same error. Installing with **nomodeset** selected gives the same error.

Here's the text at the bottom of the screen which seems to be the most important: 

[     1.483273] ---[end trace a7919e7f17c0a726  ]---
[     1.483322] Kernel panic - not syncing: Attempted to kill init!
[     1.483356] Pid : 1 , comm: swapper Tainted:  G    D W 2.6.32-21-generic#32-
Ubuntu
[     1.483392]  Call Trace:

There's more text above this so let me know if I should post it.

**acpi=off**
Running with acpi=off I get a new error screen with much smaller text. After a few seconds it then scrolls down with some more text including "BUG: soft lockup -CPU#0 stuck for 61s! [blkid:313]"
Once when I ran with this setting I simply got a black screen with a white underscore at the top.

_Hardware Configuration_
CPU: AMD Athlon II X2 255 Regor 3.1GHz
Motherboard: GIGABYTE GA-870A-UD3 AM3 DDR3
Video Card: ATI Radeon HD 4650 (SAPPHIRE 100253HDMI)
RAM: 2GB G.Skill DDR3 1600 (Tested with Memtest 86, no errors)
HDD: Hitachi HDT725050VLA 500GB SATA (This has had Windows XP previously installed on it, but has been wiped)
PSU: COOLER MASTER Silent Pro M600 RS-600-AMBA-D3 600W

I am sure the disc drive is not the issue as I have successfully used the same disc drive to install the same Ubuntu CD onto another system.

NOTE: This is probably unrelated but I have tried to install Windows XP onto this system and I do get a blue screen telling me to check my hard drive, however it is well known that Windows XP does not install properly on machines using SATA Hard Drives without the proper drivers installed. Is it possible that there really is a problem with my hard drive that Linux is detecting also?

---

### Post by oldfred on 2010-08-23
I would first check BIOS settings.

Look at AHCI and Native Mode or legacy IDE mode. Also while in BIOS make sure if you have USB keyboard & mouse you enable that. Possibly some other settings.

---

### Post by Hypernon on 2010-08-23
> **oldfred said:**
> I would first check BIOS settings.

Look at AHCI and Native Mode or legacy IDE mode. Also while in BIOS make sure if you have USB keyboard & mouse you enable that. Possibly some other settings.

I looked for options with those keywords. I found OnChip SATA Type which I have set to Native IDE, other options are RAID and AHCI. I found Onboard GSATA/IDE Mode which I have set to IDE, other options are AHCI and RAID/IDE. Anything related to USB Controllers and whatnot is enabled, nothing talking about USB keyboard/mouse though, which I am using.

---

### Post by oldfred on 2010-08-23
Was the drive ever set to RAID mode? Drives retain meta data from RAID that can interfere.

---

### Post by Hypernon on 2010-08-23
> **oldfred said:**
> Was the drive ever set to RAID mode? Drives retain meta data from RAID that can interfere.

No, I have never intentionally done anything with RAID and I'm fairly sure I haven't done it by accident either.

---

### Post by oldfred on 2010-08-24
I have saved a list of issues, see if anything looks like it might apply:

[https://help.ubuntu.com/10.04/installation-guide/i386/boot-troubleshooting.html](https://help.ubuntu.com/10.04/installation-guide/i386/boot-troubleshooting.html)
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page)
Some issues on booting install:
Bad write on CD - check md5sum, write at slowest speed, Use USB to install
CD or USB not written as bootable, just copied, DVD or RW (not just R only) sometimes an issue
BIOS settings need USB mouse & keyboard
BIOS should be set for IDE compatibility mode
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Raid meta data on drive - even if one drive (Vendor happened to set it on)
NTFS partition needs chkdsk, gparted will not see drive if flag set, flag is set on resize
Other Drive errors - Partitions errors, corruption etc
Mixed MBR (msdos) & gpt partitions (either does work)
Video issues - use f6 to set nomodeset or other options
Computer is older and does not meet minimum install standards
Install stops at partitions or only full disk install - (All four primary partitions used)
Various hardware issues - bad cables, loose cables, 
Search for Unique issue with your specific hardware.

---

### Post by Hypernon on 2010-08-24
> **oldfred said:**
> I have saved a list of issues, see if anything looks like it might apply:

[https://help.ubuntu.com/10.04/installation-guide/i386/boot-troubleshooting.html](https://help.ubuntu.com/10.04/installation-guide/i386/boot-troubleshooting.html)
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page)
Some issues on booting install:
Bad write on CD - check md5sum, write at slowest speed, Use USB to install
CD or USB not written as bootable, just copied, DVD or RW (not just R only) sometimes an issue
BIOS settings need USB mouse & keyboard
BIOS should be set for IDE compatibility mode
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Raid meta data on drive - even if one drive (Vendor happened to set it on)
NTFS partition needs chkdsk, gparted will not see drive if flag set, flag is set on resize
Other Drive errors - Partitions errors, corruption etc
Mixed MBR (msdos) & gpt partitions (either does work)
Video issues - use f6 to set nomodeset or other options
Computer is older and does not meet minimum install standards
Install stops at partitions or only full disk install - (All four primary partitions used)
Various hardware issues - bad cables, loose cables, 
Search for Unique issue with your specific hardware.

I've checked all of those things. I thought it might be the 6GB/s SATA, because my board does run SATA 3.0 6GB/s, but even when I disabled SATA 3.0 support in the BIOS I still got the same errors.

EDIT: I just went to boot from CD and I didn't get to the purple screen with the keyboard, all I got was a black screen with a white underscore at the top. I restarted and tried again and I got the purple screen like usual. It seems the black screen happens occasionally? This seems like a disc drive issue, but it can't be, as I've verified the disc drive is 100% functional, and I've tried using two different IDE cables, one of them brand new.

---

### Post by Hypernon on 2010-08-24
I just replaced the SATA cable for the Hard Drive, which didn't fix the problem. Is there anything I can do to determine what the problem is using Linux error codes, or am I stuck with fiddling around with my hardware?

---

### Post by oldfred on 2010-08-24
From the liveCD can you drill down to /var/log and look at the log files. I would look for error messages in messages and syslog, but I look in all the logs that show activity (current date).

Can you get a grub menu by holding down the shift key from BIOS until menu appears. If you use e for edit and remove quiet splash. That lets you see the messages as they are run. You can also try recovery mode.

---

### Post by olligobber on 2010-09-30
I had exactly the same problem and changed the video card, and it worked fine! 
I first tried with an on-board video card; no luck, produced thousands of [  2.65117] etc. The new card I tried is very old but worked straight away.

---

### Post by olligobber on 2010-09-30
Actually, try this instead
[http://ubuntuforums.org/showthread.php?p=9906902#post9906902]("http://ubuntuforums.org/showthread.php?p=9906902#post9906902")

---

### Post by asrao on 2010-10-05
I am new to Linux/Ubuntu. I had 9.04 installed. It worked reasonably well till I decided to install 10.04.1. Downloading and burning the CD were correct. Post burning and pre installing checks  confirmed 'no errors'. However, installation process hangs at the first out of seven steps, i.e., at the selection of language. Tried several times with the same result.
I am unable to download the 10.04.1 manual(PDF file). I am directed to sites which keep putting me in a loop. 
What is the correct procedure to install 10.04.1 or the latest 10.10
Will it be necessary to install 10.04 to progress to 10.10?
I just upgraded to 9.10. However, I am unable to access internet. I am also unable to play audio as well as video files. The system keeps asking me for additional plugins which are not available even on the internet.
Thank you.

---

