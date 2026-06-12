---
title: "Problem installing Lubuntu on a ThinkPad with Windows 8 preinstalled (boot repair)"
date: 2014-07-27
forum: Installation &amp; Upgrades
---

### Post by Peppe_L-G on 2014-07-27
My desire is to run Lubuntu and Windows 8 on the same computer.

I installed Lubuntu on a ThinkPad shipping with Windows 8 (so that it contains both OS:es). Got Lubuntu to work, and didn't use Windows 8 for a long time. I then used Windows 8, it downloaded and installed a big update, and then only Windows 8 started. I used Windows 8 for a long time, and then tried to fix the problem by using boot repair. But after that, Windows 8 starts and shows the following error (I can't do anything, I got no alternative to start Lubuntu at all):

> 
The boot configuration data for your PC is missing or contains errors.

File: \EFI\Microsoft\Boot\BCD
Error code: 0xc000000f


I've tried to fix it by starting Windows in failsafe mode (the things in [this image]("http://cdn.redmondpie.com/wp-content/uploads/2012/12/Safe-Mode-2.png")) and try out the different things, but when I run the three tools to the left in the image, they always complains about something and can't finish.

Summary from boot repair: [http://paste.ubuntu.com/7872683/](http://paste.ubuntu.com/7872683/)

My settings in BIOS (or what it's called) I think are relevant ([selected]):
```
Config -> SATA
    Compatibility
    [AHCI]


Security -> Security Chip -> Security Chip
    [Active]
    Inactive
    Disabled


Security -> Secure Boot -> Secure Boot
    [Disabled]
    Enabled


Startup -> UEFI/Legacy Boot
    Both
    [UEFI Only]
    Legacy Only


Startup ->  - CSM Support
    [No]
    Yes


Startup -> Boot Mode
    [Quick]
    Diagnostics

```

Any suggestions on what I can do to make it work?

Thanks in advance!

---

### Post by ajgreeny on 2014-07-27
According to your boot-repair output there is no Linux partition on your machine so that is why you can not boot Lubuntu.

Did you install Lubuntu using separate partitions for the OS and swap, as there is a swap partition at sdb8, or did you use the installation within windows (wubi)?  I do not think that uses a separate swap partition so I presume you did a proper partitioned install.
However, you also have two EFI partitions, one small one at sdb2 as expected but another huge one at sdb4, which may be confusing the system.

I gave up on windows many years ago and have never used Win8 with all its idiosyncrasies, and therefore do not have any experience of dealing with your sort of problem, but it looks as if either the big update to win8 or your own attempts to recover it with those three tools on the left of your pic. have somehow removed your Lubuntu installtion.

---

### Post by Peppe_L-G on 2014-07-27
When I installed Lubuntu, I downloaded the iso image, burn it to an USB stick with startup disk creator, inserted the USB stick into the computer, started the computer and then chose the alternative "install Lubuntu". I don't remember exactly what I did after that, but I think I chosed to use a new partition for Lubuntu.

I'm trying to figure out my options here. It would be nice to have Windows on the computer. I have an older computer with Windows XP I can use, but I only need Windows to do some bank errands (and similar things that requires Windows), and since Microsoft no longer provides any updates for Windows XP, it would feel safer to use Windows 8.

I have no important things in the installed OS:es, so there is no important data to take into consideration. Can I somehow easily reinstall Windows 8 and Lubuntu? I've been looking into how to reinstall Windows 8, but that seems like a hell. The product key is somehow in the hardware in the computer (I can't seem to find it), and I have no installation DVD:s; those are instead in a partition on the harddrive, and I guess that one is messed up now, since I can't use "System Restore" or "System Image Recovery" in Windows failsafe mode (when I use this mode, I'm running the partition with the label [COLOR=#000000]*Lenovo_Recovery*, right?)[/COLOR].

What do you think is easiest for me? I must have Lubuntu on the computer, should i settle with only having it? Many seems to have problem with installing Windows 8 and Ubuntu on the same computer.

---

### Post by ajgreeny on 2014-07-27
Sorry, I can't help with installing Windows 8; as I said, I have never even used it, nevermind installed it on anything, but if you did not get the restore DVDs made when you first got the computer I suspect you may have big problems unless you can get a DVD from the machine manufacturer at a sensible cost.  Only you will know whether that is a price worth paying, but as you can run Win8 in failsafe mode I presume you should be able to recover a proper bootup of that OS, though I can't tell you how.

Installing Lubuntu should be a half-hour job to get it running, then a bit more to add all the other applications and codecs etc etc that you will probably need.

---

### Post by ubfan1 on 2014-07-27
Try getting to Windows directly through the efi menu -- invoked at power on via a function key, or DEL, or ESC (varies by machine).  Choose Windows and see if it boots.  You probably should also ensure the boot-repair you ran did not rename all the bootloaders, (uncheck the box should undo the renames).  If the Windows selection still tries to run grub, you still have a rename problem.

---

### Post by Peppe_L-G on 2014-07-27
Yea, I finally got Windows 8 to work! Just as in [this case]("http://www.eightforums.com/installation-setup/24039-uefi-boot-error-2.html#post224374"), multiple of my partitions had the *boot* flag. I removed so only the partition with the file system *fat32* had the boot flag, started Windows in fail safe mode and entered the following 4 commands in the command prompt: 

```
bootrec /fixmbr
bootrec /fixboot
bootrec /scanos
bootrec /rebuildbcd
```

After that, I could start Windows 8 :D

But now I'm unsure how to get Lubuntu to work. Here's my [new boot-repair summary]("http://paste.ubuntu.com/7877073/") (guess it's quite similar to the previous one). Should i burn the Lubuntu iso-image to a USB stick and install it that way (again)? Should I clean up (remove?) some partition first? Will I probably end up with the problem I've already encountered? Or do you have no idea? :P

[SIZE=1]Curse Microsoft for creating this hell![/SIZE]

---

### Post by ubfan1 on 2014-07-27
We see no partition on your disk which could run lubuntu, so we can only guess which one you might have used in the past -- maybe sda7, which is 34G, but with an ntfs filesystem, cannot currently run lubuntu without reformatting.  The other big partition would then be for Windows, but that looks really full to me, with only 3 or 4 G free.  Which lubuntu release did you install?  If old enough, maybe you actually installed lubuntu into a file on the Windows system (wubi, but that is not supported anymore).  
  Reread these:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

Consider a fresh download of an iso (Ubuntu 14.04.1 just came out, but I'm not sure if Lubuntu did a similar release).
Figure out if sda7 is where you want to put Lubuntu, and reinstall.

---

### Post by Peppe_L-G on 2014-07-28
I don't know which Lubuntu version I installed, but I installed it about a year ago, and I'm quite sure I used the latest version available by then (I don't know if I used a stable version or not). I've never heard about WUBI before (I've read about it now, though), so I don't think I've used that.

But when I start Windows 8 and look at "Devices and drives", I see "Windows8_OS" being 55.9 GB big (with 3.88 GB free) and "My Windows 2" being 33.7 GB big (with 33.6 GB free). All "My Windows 2" contains is an empty file called "Recovery.txt".

The theory that Lubuntu was installed in this partition, which Windows 8 then transformed into a storage partition (or what it's called), seems very likely, right? So when I re-install Lubuntu, I should install it in this partition (sda7, as you said)?

---

### Post by Peppe_L-G on 2014-07-30
I freed the space in sda7 and used it to install Lubuntu according to [these instructions]("http://askubuntu.com/a/343352/255935") (after I disabled fast boot in Windows 8), and now it seems like everything works as I wish. The GRUB menu appears on startup, and I can start/exit Lubuntu 14.04/Windows 8.1 without problems.

Thank you guys for your help! If it wouldn't be for friendly guys like you, I wouldn't dare to play with this alone, so thank you!

---

