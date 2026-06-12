---
title: "Install hangs after hardware detect"
date: 2004-11-11
forum: Installation &amp; Upgrades
---

### Post by Arnb on 2004-11-11
Using Warty install the system hangs after hardware detect with a blank screen, cd spins for a while then stops. 

The Warty Live CD works in Safemode only, otherwise it hangs.

System: Dell Inspiron 7000 Notebook, 256meg ram, 333 PII, 8G HD. No Internet connection during install. Connection will be via  PCMCIA Network Card currently in use on this laptop. 

Any help appreciated

Thank you
Arn

---

### Post by johnny5 on 2004-11-11
I have the exact same problem. I downloaded the file warty-release-install-i386.iso today 11/11/04 and tried installing it on the following hardware: Gateway 2000 GP6-233 (Pentium2 233 mhz) with 128MB RAM and a 6 GB Quantum Fireball which already had Windows 2000 Pro on it. Then I tried again using the same PC with a Western Digital 10GB HDD which is blank. Both times, the same: After the hardware detection completed, the CD spun for a minute and then nothing. It has sat there for over an hour with the blue screen, a gray bar at the bottom, and one black rectangle in the far low left corner. Machine is unresponsive, to eject the CD it requires a paperclip, and to shut down requires holding the power button in for 10 seconds. 

I have tried unplugging my USB mouse and Keyboard which were connected via a KVM, and using an old PS2 Keyboard and mouse. I also noticed that the last thing I see is "starting PC Card Services" before it hangs up.

ANyone had this problem and resolved it?

This is my first time trying to install Linux. 

Thanks,
johnny5

---

### Post by Arnb on 2004-11-11
Decided to try "expert" mode. This is the result of "Detect and Mount CD Rom"
Unable to load some modules
Linux kernal modules needed to drive some of your hardware arer not available yet. Simply proceeding with the install make these modules available later.

The unavailable modules, and the devices that need them are: 
agpgart (Intel Corporatioon 440BX/ZX/DX - 82443BX/ZX/DX Host Bridge),
ide-mod (Linux IDE Driver),
ide-detect (Linux IDE detection
ide-floppy (Linux IDE floppy)

When I press enter to continue, it hangs as stated in my initial post.
Pressing Alt-F3 brings up a list of modules that were installed- no errors
Pressing Alt-F4 when system hangs shows 
cdrom-detect: searching for Ubuntu installation media
ide-cd 0x28 timed out
hdc: DMA interrupt recovery
hdc: lost interupt
hdc: status error 0x58 drive ready seekrequest datarequest
hdc: status error 0x00
hdc: drive not ready for command

Then after a minute or so it loops, constantly displaying the following message on console
grep /cdrom/dists/Stable/release/ not a directory 
 
I am a Linux nubie, can someone out there decipher this information.
Thank you

Update: Edited the error messages to include the drive id. So my question is now  is: what's wrong with my HD setup?

Thank you
Arn

---

### Post by avallon on 2004-11-12
I have described a similar problem in the following threads:
How do I install Ubuntu from Live CD
Ubuntu Warty Hangs up during the installation.

The difference is that my install went as fas as network configuration,
which was done successfully. It hanged up immediately after that and before partition set up of the install procedure.

To this day I could not find the correct answer.

Instead, I have installed Mandrake 10.0 in the mean time, while I am waiting for the officialy pressed CDs. This one works on both of my notebooks (one even with ATI Mobility Radeon 9200, but I did not try 3D) and my DIY desktop.

---

### Post by Arnb on 2004-11-12
I was able to get around this problem and Ubuntu is now installing.

I have the luxury of many spare parts for this machine, a Dell Inspiron 7000 and plugged in another cd/floppy module, registered it in BIOS (go into bios then exit saving without making changes) and it worked. The faililng CD drive was a Toshiba  XM-1902B likely with the original ROM level 1A15 version A02, although this drive works for everthing else but Ubuntu Install.  

As a suggestion to those who are still having difficulty and don't have another CD drive: 
First check the consoles Press Alt-f4 and if the error messages match mine go to the CD drive manufacturer site to see if there is an update to the ROM, it may help.   


Good luck on your path to Ubuntu
Arn

---

### Post by d0gbert on 2004-11-14
I had a similar problem with system hanging during install.  The CD-ROM would spin up for a while and then it would stop.  So the system would hang at whatever point in the installatin I was at.  I was able to do a successful install by typing the following variables into the boot prompt:  'linux noapic nolapic'

After that, everything has been going fabulous!

Good luck!
d0gbert

---

### Post by mr.frenzy on 2006-08-07
i typed in just was above and it installed. linux noapic nolapic  
works now and is installing :)

---

