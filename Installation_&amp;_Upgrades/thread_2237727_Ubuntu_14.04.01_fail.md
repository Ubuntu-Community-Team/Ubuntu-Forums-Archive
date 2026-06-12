---
title: "Ubuntu 14.04.01 fail"
date: 2014-08-03
forum: Installation &amp; Upgrades
---

### Post by leif-halvorsen on 2014-08-03
I’m attempting to install 14.04.01 on a new system:

Motherboard:                    Gigabyte 970A-DS3P
Memory:                          8192 MB DDR3
Processor:                       AMD FX 6350 6 Core Processor x6
BIOS Ver.                        F1
Crucial Solid State Drive:   120 Gig

Every time I try to install it gets to the screen that says “Any questions” and just sits there with the never ending circle going round and round. All the buttons on the screen are responsive but no means to move forward. No indication whether or not installation is still under way (no activity lights on HHD OR DVD. Also I believe failed attempts at installation have left partitions and otherwise non-optimized data fragments on the solid state drive (I also tried to install xp with no success (gets to 37% and goes to blue screen) with error message (sorry, didn’t write it down). I would re-format the drive and start over but Ubuntu say it will erase everything on disk during full installanyway, but I’m not so sure.  Can anyone tell me how to reformat the drive and how to get the installation to finish. Oh, also, during installation it asks to go online. The wireless network is shown as available but won’t hookup. The Ethernet cable is plugged in but it won’t connect there either. I have a driver cd for the Mobo but I believe I need to get an OS installed first.

I'm not very Ubunto Savvy. Have stuck with windows for cad program purposes but REALLY want to get away from it if possible.

Any help would be appreciated.

---

### Post by sudodus on 2014-08-03
Welcome to the Ubuntu Forums :-)

I suggest that before installing you should

1. Backup everything important (if anything is there)

2. [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

If you have problems trying the system live without installing

a. Check with ***md5sum*** that the download was good

b. Try some [boot options]("https://help.ubuntu.com/community/BootOptions") depending on graphics chip or card and wifi chip or card.

b. If you cannot connect to internet while trying live, we can discuss methods to cope with that during the installation.

---

### Post by leif-halvorsen on 2014-08-04
Thank you for your reply. I did try running Ubuntu off the DVD and it worked fine, except still not network connection. Also while running in this mode, I tried to run the mobo cd in order to install drivers (hoping that would provide a driver for the Ethernet card) but no go (not surprisingly since there is not os on the drive yet).
Ran Memtest86 with one error line (right from the start). Currently running Memtest86 v4.20 on each of the two 8 GB chips to try and isolate the bad module. First module has error, again right from the start. Read that bad areas can be mapped out but unless that can also be said for Windows, I'll pass as I need to keep Windows in order to run AutoCad. If I have at least one good chip, I'll try installing Both OS systems again. Perhaps that can help indicate whether or not bad memory is my only problem.
Thanks again for the good information.

---

### Post by yancek on 2014-08-04
The network connection is needed to install some proprietary software during the installation.  You can de-select installing this additional software and complete the installation and then install this software later.  If you can get the network connection, it is simpler and saves you from having to do it after the install.

You indicate that you were not able to install xp and also that you don't want to format the drive.  That would seem to indicate you either have some other operating system or a data partition on the drive, is that the case?

The motherboard CD with drivers is probably not going to help as they are usually limited to windows and maybe apple systems.

---

### Post by leif-halvorsen on 2014-08-04
Did that. Declined to install additional software and now getting (as before but forgot to mention) "attempt to mount a file system with ext type4 in SCSI1 (0,1,0), partition #1 (sda) at / failed". I continues after seeing that error message on the first attempt. Also to make clear, nothing on drive but whatever left from failed xp install attempt. Option chosen has always been to erase all on drive as I'd rather clean up the failed xp attempt rather than leave it there to have to be corrected. Second memory chip showed no errors on memtest86. That now, is the only memory installed. Also, subsequent attempt to install xp (with the good 8 gb of ram as mentioned above) failed in same manner. Tried to install the xp first and it failed, then tried to install Ubuntu which, as I said, failed.

---

### Post by oldfred on 2014-08-04
XP will not work with AHCI on which all newer systems have. AHCI is also required for trim to work with SSD, so I turned AHCI on in my system and stopped using XP when I got my SSD a couple of years ago.

XP also requires MBR(msdos) partitioning and will not work with the new gpt partitioning which is required with UEFI or drives over 2TiB.

XP should then install if you have a primary NTFS partition with the boot flag. But I would not install XP anymore. I was able to go back into BIOS and turn off ACHI and still boot my old XP install and then turn AHCI back on and boot Ubuntu but that was way too much hassle as my XP also took 3 to 4 minutes to boot and updates requried several reboots. Of course now you should not have any updates.

---

### Post by leif-halvorsen on 2014-08-04
Thanks OldFred,
based on that, I'll be running Ubuntu alone, maybe adding Windows7 or 8 later.

---

