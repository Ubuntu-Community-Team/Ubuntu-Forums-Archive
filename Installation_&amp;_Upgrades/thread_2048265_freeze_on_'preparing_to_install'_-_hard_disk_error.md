---
title: "freeze on 'preparing to install' - hard disk error but disk is healthy"
date: 2012-08-26
forum: Installation &amp; Upgrades
---

### Post by timurw on 2012-08-26
Hello, I thought I'd begin my escape from the impending tyranny of Windows 8 by     installing Ubuntu 12.04.1 LTS x64 on my Windows 7 PC. I have flashed a USB flash     drive and also tried the Wubi installer but I get the same issue in     both. They both start fine, connect to the internet and display the     GUI, as well as letting me mount the hard drive in question and accessing files.

However, they freeze on the 'preparing to install' step. Some analysis  of     the log files suggests Ubuntu thinks there is something wrong with     both my hard disks, despite the fact that I run Windows on them on a     daily basis and never have any issues. I've even run chkdsk /b but  that     didn't identify anything beyond a bit of free space being marked as     used. SMART information on Disk Utility suggests I have 8 bad  sectors but those have been present for months and I've been using  Windows on a daily basis since.
     
     The error messages I get are as follows:
     ```

     Aug 26 08:53:19 ubuntu kernel: [  187.119378] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Aug 26 08:53:19 ubuntu kernel: [  187.119383] ata5.00: BMDMA stat 0x24
Aug 26 08:53:19 ubuntu kernel: [  187.119386] ata5.00: failed command: READ DMA
Aug 26 08:53:19 ubuntu kernel: [  187.119392] ata5.00: cmd c8/00:80:60:00:00/00:00:00:00:00/e0 tag 0 dma 65536 in
Aug 26 08:53:19 ubuntu kernel: [  187.119394]          res 51/40:00:cf:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
Aug 26 08:53:19 ubuntu kernel: [  187.119397] ata5.00: status: { DRDY ERR }
Aug 26 08:53:19 ubuntu kernel: [  187.119399] ata5.00: error: { UNC }
Aug 26 08:53:20 ubuntu kernel: [  188.108272] ata5.00: configured for UDMA/133
Aug 26 08:53:20 ubuntu kernel: [  188.108282] ata5: EH complete
Aug 26 08:53:54 ubuntu kernel: [  221.988291] sd 4:0:0:0: [sdb] Unhandled sense code
Aug 26 08:53:54 ubuntu kernel: [  221.988294] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug 26 08:53:54 ubuntu kernel: [  221.988298] sd 4:0:0:0: [sdb]  Sense Key : Medium Error [current] [descriptor]
Aug 26 08:53:54 ubuntu kernel: [  221.988303] Descriptor sense data with sense descriptors (in hex):
Aug 26 08:53:54 ubuntu kernel: [  221.988305]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Aug 26 08:53:54 ubuntu kernel: [  221.988314]         00 00 00 cf 
Aug 26 08:53:54 ubuntu kernel: [  221.988318] sd 4:0:0:0: [sdb]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug 26 08:53:54 ubuntu kernel: [  221.988323] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 9f 00 00 80 00
Aug 26 08:53:54 ubuntu kernel: [  221.988333] end_request: I/O error, dev sdb, sector 207
Aug 26 08:53:54 ubuntu kernel: [  221.988336] quiet_error: 46 callbacks suppressed
Aug 26 08:53:54 ubuntu kernel: [  221.988339] Buffer I/O error on device sdb1, logical block 72
Aug 26 08:53:54 ubuntu kernel: [  221.988341] Buffer I/O error on device sdb1, logical block 73
Aug 26 08:53:54 ubuntu kernel: [  221.988344] Buffer I/O error on device sdb1, logical block 74
Aug 26 08:53:54 ubuntu kernel: [  221.988347] Buffer I/O error on device sdb1, logical block 75
Aug 26 08:53:54 ubuntu kernel: [  221.988349] Buffer I/O error on device sdb1, logical block 76
Aug 26 08:53:54 ubuntu kernel: [  221.988352] Buffer I/O error on device sdb1, logical block 77
Aug 26 08:53:54 ubuntu kernel: [  221.988354] Buffer I/O error on device sdb1, logical block 78
Aug 26 08:53:54 ubuntu kernel: [  221.988357] Buffer I/O error on device sdb1, logical block 79
Aug 26 08:53:54 ubuntu kernel: [  221.988359] Buffer I/O error on device sdb1, logical block 80
Aug 26 08:53:54 ubuntu kernel: [  221.988362] Buffer I/O error on device sdb1, logical block 81
Aug 26 08:53:54 ubuntu kernel: [  221.988389] ata5: EH complete
Aug 26 08:53:55 ubuntu kernel: [  223.021422] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Aug 26 08:53:55 ubuntu kernel: [  223.021427] ata5.00: BMDMA stat 0x24
Aug 26 08:53:55 ubuntu kernel: [  223.021431] ata5.00: failed command: READ DMA
     
```I was wondering if this could have anything to do with my BIOS and/or  SATA Controller. The drive is a Samsung HD502IJ SATA and the motherboard  is a Gigabyte P35C-DS3R. I've tried with AHCI on and off (it's off in the logs above), doesn't seem  to make a difference.

Any help would be much appreciated!

Thanks in advance

edit: I've also used Steam Mover and other programmes to create NTFS junction points on the drive, could this be causing some issues in compatibility?

---

### Post by dino99 on 2012-08-26
freeze often means graphic driver not activated, or acpi issue. You might need to use / try some boot option, like nomodeset or noacpi.

Google around "ubuntu boot option" to find a wiki

---

### Post by timurw on 2012-08-26
Sorry, I should've said - the system doesn't freeze completely, it's just the install that freezes. I get the hourglass type cursor and the window becomes unresponsive. However, I can shut down the machine normally and do everything else in the background. This, coupled with the error logs, makes me think that graphics card issues are quite unlikely.

---

### Post by oldfred on 2012-08-26
I have nVidia and always have needed the nomodeset. But it now could also be a slide show issue, if not any corruption on hard drive partition sdb1.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

Just saw this from arpanaut's post in another thread.
There is a bug in ubiquity on the 12.04 iso that causes the installer to crash part way through on some hardware.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568)
From liveCD before install. 
sudo apt-get remove ubiquity-slideshow-ubuntu
or (ubiquity-slideshow-lubuntu) (and ubiquity-slideshow-xubuntu)
The Alternate iso is another option as it is text based and also does not use the slideshow.
[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

---

### Post by timurw on 2012-08-26
Thanks for the reply. Just tried both nomodeset and  sudo apt-get remove ubiquity-slideshow-ubuntu but I keep getting the same error message I posted in the original post.

---

### Post by timurw on 2012-08-27
Would anyone have any other ideas? I've got ACPI switched off in the BIOS so it's not that.

---

### Post by oldfred on 2012-08-27
These are BIOS  issues usually related to booting as posted by others. See if any apply.

> BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA 6 Gbit/s  from 6 Gbs to a SATA II - 3Gbs 
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Old BIOS, new drive 137GB max boot size
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)
Old gpt data on drive
Disable Quickboot in BIOS
turning off UDMA in the BIOS my problem has gone away.(old system & may make system slower)
BIOS setting, Keyboard response in grub really slow
Fast Boot setting prevents keyboard from working & other issues
Bios not loading no key works - disconnected power for about 10-15 minutes and the bios reset itself.
After update, It had reset to the BIOS defaults, setting the video to ONBOARD and switching off the dynamic video memory allocation (manually allocating 32Mb instead of leaving it as AUTO).
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Sometimes specific issues by motherboard like this:
[Natty] Marvell 88SE9120 IDE-Part not working 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777325](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777325)
External drive needed separate power supply
Asus m4a87td  core unlocker feature on usb3 was causing the problem
Asus - Security> I / O interface Security> "New interface card" or so. SET IT TO LOCKED!!! 
In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.
Changed IDE Mode to AHCI Mode
Then,when the SATA3G_1 selection appears in the drive list below,select the Enabled option.
set pci=nomsi or other boot paramter
So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!

It was in the BIOS. Under Onboard Devices Settings, the SATA Mode was set to SATA. I changed it to AHCI. Then another  showed up in the BIOS that stated "Change the AHCI DID for Linux to Enabled. I booted to win7 and it loaded some new drivers. I booted to Gpart and glory be there were my hard drives.


---

