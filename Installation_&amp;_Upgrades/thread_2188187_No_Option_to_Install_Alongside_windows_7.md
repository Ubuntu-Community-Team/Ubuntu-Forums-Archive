---
title: "No Option to Install Alongside windows 7"
date: 2013-11-15
forum: Installation &amp; Upgrades
---

### Post by Nate4846 on 2013-11-15
I'm trying to install ubuntu alongside windows 7 on my new machine. I boot it from a usb installer that I made by following the instructions on the ubuntu site. It live boots perfectly fine but then when I go to install it gives me the option to  Erase, encrypt, LVM, or something else. It says the current disk has no operating system currently on it. Under something else it shows my 256 gb ssd and it just says free space and doesn't recognize my partitions. I have one system reserved partition (100 MB) that windows created, the regular partition where my games and things are, and then a 10 GB unallocated partition that I was instructed to create in order for the alonside windows option to appear but that didn't work. I'm not exactly familiar with all of this, I tried something else before and I messed up the drives and had to reformat and reinstall windows. Luckily I keep all my files on my HDD and just unplug it when I'm trying to do this. So I just had to redownload my games and things. Please help... what am I doing wrong?

Also I'd like to note that when I boot up, I get the options of Trying Ubuntu, Installing Ubuntu, OEM (Manufacturers Only), and Check Disks. They are in GRUB GNU, which if I am correct is ubuntu's boot loader. It doesn't come up with the Graphic pictures and only the two options of try ubuntu and install ubuntu. Hope this helps.

Comopnenets:
Intel i5-4670
EVGA GTX 760
Gigabyte Z87X-D3H
G. Skill 8 gb of RAM
Samsung 256 gb ssd

---

### Post by fantab on 2013-11-15
Boot from Ubuntu DVD/USb and post the output of the following from Terminal [ctrl+alt+T]:

```
sudo parted -l
sudo fdisk -l
```

Is this a Laptop (Model and brand?) or a Desktop (Model and brand or custom built)?

---

### Post by Nate4846 on 2013-11-15
It's a custom built Desktop

---

### Post by oldfred on 2013-11-16
Yes, but it is a UEFI motherboard, so we need to know if you installed Windows in UEFI mode or BIOS boot mode. Partition layout will tell us. Also give us clues on what else may be wrong.

If the fdisk does not really work it will comment that it is gpt and then we know Windows is UEFI.

Ubuntu installer has both UEFI & BIOS boot and from your UEFI menu you should have both as a choice. How you boot installer is how it installs.

This shows both the UEFI grub menu and the purple accessibility (BIOS boot) menus.
       Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Do you have dual video or just nVidia? With nVidia you will need nomodeset also.

---

### Post by fantab on 2013-11-16
Post the output of the commands I requested.

---

### Post by Nate4846 on 2013-11-17
Sorry guys busy day yesterday, thanks so much for the feedback I appreciate it a lot. I'm much more familiar with bios than I am UEFI this is my first time dealing with it. I did not change anything about UEFI before I installed. My partitions are NTFS and the 10 GB is unallocated. I'm not sure if that is what you're looking for but I'll check for more info once I reboot into windows.
[http://imgur.com/zSEIeYx](http://imgur.com/zSEIeYx)
There are the commands you requested, for sudo parted -l I answered both yes and no to give as much info as possible

Thanks!

Edit: I have an HDD that I unplugged for the live boot, but it only has files on it. Windows, my programs, and my partition meant for ubuntu  are all on the ssd

Edit 2: [http://imgur.com/dzUT0YK](http://imgur.com/dzUT0YK)

---

### Post by oldfred on 2013-11-17
Better if you just copy & paste output to here. If long use code tags or #icon  in advanced editor.

Windows only boots from gpt with UEFI, but you only have the two standard BIOS partitions that Winows installs in BIOS mode.

Windows will auto convert an old gpt drive to MBR, but leaves the backup partition table. Then Linux sees MBR and backup gpt and does not really know what you have.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Or you have to convert back to gpt, convert standard Windows 7 installer to UEFI installer and reinstall. 
      
 Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

---

### Post by Nate4846 on 2013-11-17
Sorry about that, thought you might like the screen shot, I'll paste the output code next time.

Thanks for the help. I would like to avoid reinstalling windows. I could reinstall windows but it takes so much time to re-setup all my programs and settings. Could you explain what FixParts would be doing? So if I obtain FixParts and run it following the specified directions on the website would the option then show up because ubuntu can then recognize the partitions?

---

### Post by oldfred on 2013-11-17
As long as you have both MBR and gpt backup partition you will have issues. And that seems to be the issue.

Always good of have a full image backup of Windows. With Ubuntu I can easily reinstall system and have backups of my data and settings in /home.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by Nate4846 on 2013-11-18
Alright I'll give it all a try asap! Thanks so much for the help! I really appreciate it!

---

