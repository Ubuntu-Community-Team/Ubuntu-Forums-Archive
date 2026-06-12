---
title: "Ubuntu Can't See Harddrive to Install"
date: 2021-04-26
forum: Installation &amp; Upgrades
---

### Post by happydog500 on 2021-04-26
I used Linux off and on for decades. Completely off for the last few years. I see coming back I forgot a lot of things.

 I tried to install voyager (Ubuntu with a dock and desktop using xfce). It couldn't see the hd.
 
 After giving up, I tried xubuntu with the same problem. I tried ubuntu and have the same problem. 

  I have an SSD with Windows 10 in a lenovo z570 laptop. I took out the hd and put in one i had laying around (formatted). After it didn't see the drive, I put back in the Windows HD and tried it to see if it could see that one, but still doesn't see it.

 I changed the bios to AHCI when I installed Windows. There's another setting mentioned on the internet I don't have. I've followed all the instructions found on the internet, none will work. 

  I was surprised to see so many other people have the same problem, some with no fix ("2021 and we still can't boot Linux?").

  Is there anything I can try? This is sad for me because i really want to run Linux. I bragged to my friends years a go and want to get back but can't even see the drive. 

  Thank you,
 Chris.

---

### Post by tea for one on 2021-04-26
> **happydog500 said:**
>  I've followed all the instructions found on the internet, none will work.
That must have taken an extraordinary amount of time.;)
> 2021 and we still can't boot Linux?
No need to bait the hook, there are many forum members who will try to help.

Nevertheless, let's press on.

Here are some things to consider:-

_UEFI settings_

Disable Secure Boot
Disable Fast boot 
Disable Legacy mode 
Check that Legacy USB Support is enabled
Change SATA mode to AHCI where the default is RAID or Intel RST (Windows may need AHCI driver)
Disable TPM

_Windows 10_

Backup your data
Turn off Bitlocker
Disable Fast Start Up i.e. Windows is [COLOR="#0000FF"]not hibernating[/COLOR]
Disable applications which manage Intel Optane memory & storage
Disk must be GPT
Install Windows 10 in UEFI mode
Check via System Information > System Summary > BIOS mode > UEFI
Windows will have  an EFI partition (needed by Ubuntu later)
Use Windows tools to reduce Windows partition size and create free space
Reboot Windows to allow chkdsk to run
Windows may need AHCI driver
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)

Can you confirm that you are able to boot into a live Ubuntu session (in UEFI mode)?

---

### Post by happydog500 on 2021-04-28
Thank you for getting me back into this.

  I found when I turned off fast boot, Windows turned it back on. 

  I turned it off, then put the disc in and restarted the live disk. It now sees the HD.

  Thank you. 

Voyger is set up just the way I set up my machine. When I download from their site, it tells me two files are corrupted. I downloaded from 3 different sources and all say the same thing. I emailed voyager and months later the same thing.

 I may install xubuntu, install the dock and desktop info and avoid voyager. 

  The, "2021 and we still can't boot Linux?" was a quote from another thread. Didn't mean to flame. 

  Thank you again,
 Chris.

---

### Post by yancek on 2021-04-28
>  I found when I turned off fast boot, Windows turned it back on. 

I rarely boot into windows but I have found that when I do it will sometimes do an update before shutting down.  I think this can be set to only manual but since I rarely use windows I have not investigated.  Some of these updates will turn hibernation on also and the user will not be asked if s/he wants this or that it is being done so you need to be aware that this happens.  The results of this will be that if you access your windows drive from Ubuntu (or any Linux) you will not be able to do this as a Linux OS will not mount (give access to) a hibernated partition.  This is one reason you will not see windows drives from Linux.  Some of the windows updates will also turn Secure Boot back on which can also be a problem with some Linux systems.

---

