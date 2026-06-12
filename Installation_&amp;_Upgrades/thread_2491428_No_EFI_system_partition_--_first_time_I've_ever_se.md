---
title: "No EFI system partition -- first time I've ever seen this"
date: 2023-10-08
forum: Installation &amp; Upgrades
---

### Post by davepool on 2023-10-08
Hello all! It's been a few years since I've had the need to call on you here...and that was back when I first decided to stick my toes into the Linux waters, become at least functionally familiar with the OS and maybe learn a little something along the way. There's a good bit of back story with this but I'll spare you most of it. 

To facilitate my early Linux adventures, I bought a used Lenovo ThinkPad x131e from eBay. It had left the factory as a Windows machine but the previous owner had already converted it to Linux Mint and that was part of the appeal for me.  Once I got it...and in the months that followed...I turned it into a multi-distro device. I made two partitions on the HD. There was even an mSATA card which was previously used for storage which I wound up using as the location for a series of experiments with super lightweight distros. Over time I installed any number of distros on the two partitions of the HD, ultimately settling on newer installs of Linux Mint (which I did) on one and then using the other for a series of installs of Ubuntu flavors, ultimately settling on Kubuntu 22.04.2 LTS.  All of these have been running without a hitch for quite some time. And the reason I tell you this is to establish that a) the process of installing a new distro over an existing install is familiar to me and b) all of those many installs on this laptop ever produced the following.

Via a series of musings (I told you I'd spare you), a few days ago I thought maybe I'd install whatever is the newest Kubuntu LTS on top of what I already have (silly me, I did not think to check to see if this was significantly updated from what I already have or if there is a simple upgrade path from 22.04.2 to 22.04.3...I just had it in my head to do a fresh install. Work with me here.). All went as it usually does:

  Identify the proper partition, leave the size the same, use Ext4 journaling file system, format the partition, mount point /

   

  So I ran through all that and when I tapped Okay and Install Now, I immediately got this warning: 

   
  [B][FONT=Calibri]"No EFI System partition was found. This system will likely not be able to boot successfully and the installation process may fail"

[/FONT][/B]I've done some preliminary searching here in the forum but all of the results seem to revolve around some conflict with Windows which, again, has never been on this computer while it's been in my hands though, yes, it was originally built that way and might still have stuff "baked in".  An online friend of mine far more familiar with Linux than I told me he immediately suspected that it was "most likely a UEFI/Secure Boot issue and that I should disable Secure Boot.  But when I checked the BIOS, at the bottom of the list on the Main tab it shows UEFI Secure Boot Off

BTW (since he mentioned it)...all my my grub menus on this device including the grub menu of the Live USB session to get as far as I did with the attempted install are/were all center screen

So what's happening here with this first-time-ever problem? I'm not necessarily determined to follow through on this install...after all, I've got something like 3.5 years of support left on this LTS and plus I now see that what was 22.04.2 has now upgraded to 22.04.3 and it's working fine. OTOH, if this is a problem with something that won't cure itself, I'd rather address it now than have it pop up again down the line.

---

### Post by jeremy31 on 2023-10-08
What result from terminal for ```
sudo parted -l; mokutil --sb
```

---

### Post by davepool on 2023-10-08
```
Model: ATA HGST HTS725032A7 (scsi) 
Disk /dev/sda: 320GB 
Sector size (logical/physical): 512B/4096B 
Partition Table: msdos 
Disk Flags:  
 
Number  Start   End    Size   Type      File system  Flags 
 1      1049kB  538MB  537MB  primary   fat32        boot 
 2      539MB   320GB  320GB  extended 
 5      539MB   160GB  160GB  logical   ext4 
 6      160GB   320GB  160GB  logical   ext4 
 
 
Model: ATA SATA SSD (scsi) 
Disk /dev/sdb: 20.0GB 
Sector size (logical/physical): 512B/512B 
Partition Table: msdos 
Disk Flags:  
 
Number  Start   End     Size    Type      File system     Flags 
 1      1049kB  15.0GB  15.0GB  primary   ext4 
 2      15.0GB  20.0GB  5012MB  extended 
 5      15.0GB  20.0GB  5012MB  logical   linux-swap(v1) 
 
 
Command 'mokutil' not found, but can be installed with: 
sudo apt install mokutil
```

---

### Post by oldfred on 2023-10-08
How you boot install media UEFI or BIOS is how it installs. That starts from UEFI boot menu with two options to boot live installer. 
Or may be how you create live installer. ISO is configured for both. But some tools may make live installer from ISO as UEFI only or BIOS only installer. 

Microsoft required vendors to install in UEFI boot mode to gpt partitioned drives with Windows 8 in 2012, so most hardware is UEFI.
But users could install in UEFI or BIOS mode. And Ubuntu will let you install in either boot mode to either MBR (msdos) or gpt partitioning. But best to use gpt, but conversion totally erases a drive. I started conversion of drives to gpt in 2010.

If you want to see details of all of your installs, run the Boot-Repair report. I run it periodically and include in my backups, just to know what is where.
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by davepool on 2023-10-08
@oldfred The tool I have used for every iso burn to live installer has been Balena Etcher. No change with this one.

Beyond that, your suggestions are starting to cause my eyes to glaze (not a zing...I appreciate the reply...but even today I still haven't completely shed my newbie status!)

The question that still puzzles me is "Why now?"  This attempted install was done (starting with the iso file and Balena Etcher) exactly as I've done every previous USB Live session installation. And it's the first and only time this warning has appeared.

---

### Post by MAFoElffen on 2023-10-08
Preample- Forum policy to post raw output and commands within CODE Tags. On editing your previous post to correct that: Use edit > advanced edit > Select the text of the output. From the extended tool bar, select the "#" Icon. Code tags will be inserted around that selected text. On new posts, use Advanced Reply to get that extended toolbar. Just trying to keep you out of troubles, and good net-iquet.
  
2 things... 

1) If you get into the Settings on your Lenovo, for Boot mode, you will see that it has UEFU (only), and Hybrid (which will bot both EFI and Legacy/CSM). Change it to UEFI only.

2) Both of your drives have MS-DOS partition tables. It cannot boot from UEFI unless 
a) on a drive with an MS_DOS partition table, you add a boot_bios primary partion with a boot_bios flag, or
c) has a GPT partition table...

Since you are starting over without Windows... I would just repartition the disks with fresh GPT partition tables.  

On that machine, before you start an install, first go to a Terminal session in "Try" and do
```

ls /sys/firmware/efi/efivars

```
If it comes back as populated, it booted as UEFI. If it comes back as empty (no files in that directory, then it still booted as Legacy/CSM. If the later happens, thell us, and there are ways to burn the Installer LiveUSB media that will force booting from UEFI.

---

### Post by jeremy31 on 2023-10-08
davepool, have you completed the install and tried to boot? Do you know what this partition is?  1      1049kB  538MB  537MB  primary   fat32        boot 
I think it should boot fine and there is some bug in the installer that wants an EFI System Partition even on the BIOS/CSM/Legacy boot

---

### Post by oldfred on 2023-10-08
I have seen some posts where installer added a FAT32 partition which usually is for UEFI boot, but even with BIOS boot.
Not sure if bug or feature, so drive has space allocated for future UEFI install?
But UEFI recommends gpt partitioning, so no real need for FAT32 with MBR partitioning.
I think some said just to proceed after "error" on missing ESP and it just works.

---

### Post by davepool on 2023-10-08
@jeremy31 No, I did not complete the install. I might've been unclear but that's because I didn't want to drag everyone into the weeds of what I was thinking and at what point I was thinking that, etc. True, at one point I thought doing a fresh install would be best...but then when faced with this EFI warning, I thought better of that...and retreated to simply updating the already installed Kubuntu (which had experienced its own set of obstacles, which I didn't share because they magically went away). So, where I sit at this point is my existing install of Kubuntu 22.04.02 has upgraded to 22.04.03 and works fine. As a result, I'm no longer determined to do the fresh install. But that doesn't mean I'm not curious to know what's going on.

BTW, I like your idea of there maybe being a bug in the installer because, to me, that's the only explanation for why this has only happened with this one attempt at an install when so many other installs on the same device with the same partitions and USBs burned with the same tool never had this problem.

---

### Post by jeremy31 on 2023-10-08
The warning about EFI System Partition could be a failsafe in case someone intended on booting EFI, the partition is usually only 500MB

---

### Post by MAFoElffen on 2023-10-08
> **oldfred said:**
> I have seen some posts where installer added a FAT32 partition which usually is for UEFI boot, but even with BIOS boot.
Not sure if bug or feature, so drive has space allocated for future UEFI install?
But UEFI recommends gpt partitioning, so no real need for FAT32 with MBR partitioning.
I think some said just to proceed after "error" on missing ESP and it just works.
True. I have noticed that also. 

Which is a problem if the installer tried to install grub-efi-amd64 if booted as BIOS Legacy/CSM and had MS-DOS partition tables, because EFIVARS would not exist.

NOT finding EFIVARS in /sys/firmware/eif/efivars, because it is not populated, then it is booted as BIOS Legacy/CSM... But if it still created ESP and tried to install grub-efi-amd64. Yes, that seems to be a BUG. 

Hmmmm. I have to think on that, and test a few more. Maybe he should submit a Bug Report, filed against Subiquity. Or I could file one and link it to this thread, BUT it isn't going to get any weight behind it unless I can recreate the problem, so it submits the underlying system reports to the Bug Report, and this user joins the Bug Report as also affected, so they see that there are more than one person affected. 

That is the problem with trying to submit Bug Reports to LaunchPad "by proxy". If he now, while this is still like this after the install, from the LiveUSB while doing continue to explore, do
```

ubuntu-bug subiquity

```
Then it will generate the Bug Report with the correct system reports uploaded, and we can jump into the report to link it to this thread, and explain it. That will add weight to it.

I still think this user needs to install as UEFI, but it did uncover another problem with the installer. With booted as Legacy and MS-DOS partitions, it should have just installed as MBR.

---

### Post by davepool on 2023-10-08
@MAFoElffen it actually came back as neither. It said it cannot access, no such file or directory (which I don't read as being "empty" since the directory for any files doesn't exist). 

BTW, I'm not "starting over without Windows." Since this laptop has been in my hands, it has never had Windows on it. It was the previous owner who made the conversion (full system, not dual-boot) to Linux with Linux Mint (which was, IIRC, LM18 and I have since done newer installs).

---

### Post by davepool on 2023-10-08
> **MAFoElffen said:**
> 
That is the problem with trying to submit Bug Reports to LaunchPad "by proxy". If he now, while this is still like this after the install, from the LiveUSB while doing continue to explore, do
```

ubuntu-bug subiquity

```
Then it will generate the Bug Report with the correct system reports uploaded, and we can jump into the report to link it to this thread, and explain it. That will add weight to it.

I still think this user needs to install as UEFI, but it did uncover another problem with the installer. With booted as Legacy and MS-DOS partitions, it should have just installed as MBR.

I'm not sure from the above what, if anything, you folks want me to do but...I'm not enthusiastic about forcing any kind of install on my device when I've got a working LTS installed AND the consensus seems to be there's a problem with the installer.  Not saying "no," mind you...just don't count on me to have a lot of skill "under the hood" without some hand-holding.

---

### Post by MAFoElffen on 2023-10-08
Okay. Understood. Dang.

If you could please tell me one thing before you destroy the remnants of that install. Look in the /var/log/installer/media-info file... and please post what that first line says. That should be which ISO image it was installed from. That way I can try to recreate the problem.

---

### Post by davepool on 2023-10-09
> **MAFoElffen said:**
> Okay. Understood. Dang.

If you could please tell me one thing before you destroy the remnants of that install. Look in the /var/log/installer/media-info file... and please post what that first line says. That should be which ISO image it was installed from. That way I can try to recreate the problem.

Let me just be clear here...the install never went through. I attempted it...and got all the way through identifying the desired partition, choosing the file system, ticking the box for format, selecting the mount point (all described in the initial post) ...and then when i tapped on Okay and Install Now, I got that EFI warning. I did not "agree" to proceeding past that, so the install process never went any farther than that. I backed out from there, booted up the existing 22.04.2 installation and have since run an update of that (making it now 22.04.3).

The first (and only) line of the media-info file reads: Kubuntu 20.04.1 LTS "Focal Fossa" - Release amd 64 (20200731)

---

### Post by yancek on 2023-10-09
I see in your output of the parted -l command above that your first  partition on the 320GB drive shows as boot but it does not show 'esp'  which it should if you are using an EFI system.  You might just need to set the esp flag on the EFI partition but that is just a guess.

You have an msdos drive which usually means a Legacy (not uefi) install but you can install Ubuntu UEFI on an msdos drive.  It just isn't the common or recommended way  If you look at the /boot/efi partition from a terminal or a file manager, do you see an ubunt/kubuntu directory.  If not, you have a Legacy install and don't need that partition and trying to install a newer system would require that you boot the install media in Legacy mode.

I don't know why you would get that error as you have an EFI partition but you could try the above suggestions, check the /boot/efi directory and set the esp flag on that partition.  Good luck.

An EFi partition should show both boot and esp flags from parted as shown below from my drive example.

>  [1      1049kB  274MB   273MB   fat32        EFI system partition          boot, esp

---

### Post by davepool on 2023-10-09
@yancek, thanks very much for your reply but...it's more than a bit over my head. 

I'll just ask again...why, with all of the easily dozen distros I've installed on this device in the time I've had it (and some of them Ubuntu), have all previous installs gone without a hitch, never once producing that EFI warning...and only now on this one attempted install it pops up?  From what little I think I grasp of your thoughts...why would this have not happened before (and many times)?

---

### Post by oldfred on 2023-10-09
Microsoft has required vendors to install in UEFI boot mode with gpt partitioning since 2012.
So almost all hardware is UEFI, and even Ubuntu needs a system that is newer than 10 years old. 
Older systems need a lighter weight flavor like Lubuntu or other lighterweight flavor.
My newer laptop is UEFI only, so no BIOS/Legacy/CSM mode at all, only UEFI.

It looks like you used 22.04.1, but there is a slightly updated ISO. Did you try that?

---

### Post by davepool on 2023-10-09
> **oldfred said:**
> 
It looks like you used 22.04.1, but there is a slightly updated ISO. Did you try that?


I wonder if the 22.04.01 isn't the previous install of Kubuntu (the one that's been on there for, oh, a year or so?).  The iso file I was using for the attempted re-install was downloaded from the Kubuntu site the very day I tried to use it...and the file is kubuntu-22.04.3-desktop-amd64.iso

---

### Post by pbear42 on 2023-10-18
> **MAFoElffen said:**
> That way I can try to recreate the problem.
This problem is well known and easily duplicated.  Boot any version of Ubuntu 22.04 in BIOS mode.  Easily done in VirtualBox, as that's its default boot mode. With GParted, create an MBR partition table, then set up one or more partitions.  Run Ubiquity; install by manual method.  When you click install, the dire warning mentioned by the OP will appear.  Click to continue anyway.  The install will go through and the system boot without a hitch. On a BIOS system, the warning is a red herring.

I've not tested whether the problem persists with the new installer.  Edit: Have now run the test.  The installer for 23.10 does **not** give the spurious EFI warning when booted in BIOS mode.

---

### Post by ubfan1 on 2023-10-18
...or maybe it was just that the esp flag was missing on the EFI partition (?) which had only the boot flag.

---

### Post by digisus on 2023-10-28
Just came here after 2h searching for a solution... In short, I just had the same problem as the OP:

[LIST=1]
[*] Installed ubuntu 22.04.1 single-boot on brand-new Lenovo X1 with UEFI, using "/boot/efi" (FAT32) on p1 partition, then "/" on p2, empty p3 (as a future "/" when upgrading), and rest "/home" on p4. (1TB SSD).
[*] All worked flawlessly and as expected: "esp, boot" flags correctly set on /boot/efi.
[*] While starting to use the machine, several updates of Lenovo firmware failed, complaining that EFI partition (60MB) is full, which happened never before. Anyway, I learned that EFI partition should be 100-500MB, so I decided to repeat the install with larger EFI (550MB).
[*] 2nd install (now 22.04.3) was planned to be identical to first except a larger EFI partition (now 550MB).
[*] USB stick with installer booted into UEFI as before and I was able to do the same paritioning with larger "/boot/efi" (FAT32).
[*] But then the parted tool in the installer did not set the "ESP, boot" flags and there was no obvious way for me to do it manually, there, on the spot.
[*] So, on clicking [Continue] I got the same EFI warning as OP, which I also saw for the first time. Actually there are 2 warnings, the 2nd warning that install may fail, etc. Can be frightening for less experienced folks (I am on ubuntu exclusively since 04.10).... but after reading this thread and a dozen other ones on BIOS/UEFI, I decided to ignore the warning and continue all through to see what happens.
[*] The 2nd install was successful in the sens that booting via UEFI worked, BUT the /boot/efi partition has an irritating flag. Instead of "esp, boot" is says "msftdata". I don't like to see anything MSFT on my machine ;-) and it is beyond me why it does not say "esp, boot" as everything around here is definitely on UEFI.
[/LIST]

Conclusion: I tend to agree with the opinion voiced in this thread that the installer makes a mistake at some point and/or shows wrong information to the user.

I hope this additional information helps. Happy to post output from the now installed machine if you tell me what you need.

My question is: Should I by worried about the (IMHO wrongly set) "msftdata" flag on /boot/efi and even consider doing a 3rd re-install? Or can I just safely continue configuring the new machine which should be my base for the next years as the install went through and booting (into UEFI) works? Thanks.

---

### Post by tea for one on 2023-10-28
> **digisus said:**
> My question is: Should I by worried about the (IMHO wrongly set) "msftdata" flag on /boot/efi and even consider doing a 3rd re-install? Or can I just safely continue configuring the new machine which should be my base for the next years as the install went through and booting (into UEFI) works? Thanks.
As your system boots OK and is working, I would not install for a third time.

You can change the msftdata flag with Gparted.
You can do this via a "Try Ubuntu" session or even in your installed system.
After you have booted the PC
Open Gparted (or install it if it has been removed)
Unmount the ESP
Right click the partition > Manage Flags
Change the flags to esp and boot.

---

### Post by digisus on 2023-10-30
Thanks a lot for the tip, @teaforone! 
I followed your suggestion and changed flags from within the system - it worked like a charm. :D

---

### Post by davepool on 2024-01-22
Hey there...OP here. It's been more than 3 months since I first posted to this thread. Yesterday, on a whim, I decided to download both the Kubuntu 22.04.03 LTS (on the hunch...based on nothing...that maybe a fix had been found and the file re-uploaded) and also the 23.10.  I tried to install both and got the same EFI partition error/warning.  

I decided to drop in and take a look at where this thread stood....and I see that one other person experienced essentially the same problem (though, to me, his sounds far more complex than mine) and concludes that the installer is making a mistake and showing the wrong info to the user.

Net-net...does this problem still exist (as yesterday's attempts to install would seem to confirm)?

---

### Post by yancek on 2024-01-23
Part of the problem may be that you appear to have an EFI install on an msdos drive which is very uncommon and not recommended but can be done.  Did you ever set the vfat partition on your drive (first partition) label to boot and esp by using gparted as previousoy suggested?  That's pretty simple to do.  Before doing it, you could take a look at the contents of that partition to see if there are actually any files there.  Do this from a terminal:  sudo ls /boot/efi/EFI should show an ubuntu directory and if so, going into that ubuntu directory should show efi boot files.

 You may have done all your previous install in Legacy mode so you would not have seen any warning message about an EFI partition as an EFI partition wouldn't have been used on your old msdos drives.  If you booted in UEFI mode from the BIOS to install on the msdos drive, it would have needed an EFI partition (vfat) and it would need the boot and esp flags set.

---

### Post by davepool on 2024-01-23
> **yancek said:**
> Part of the problem may be that you appear to have an EFI install on an msdos drive which is very uncommon and not recommended but can be done.  Did you ever set the vfat partition on your drive (first partition) label to boot and esp by using gparted as previousoy suggested?  That's pretty simple to do.  Before doing it, you could take a look at the contents of that partition to see if there are actually any files there.  Do this from a terminal:  sudo ls /boot/efi/EFI should show an ubuntu directory and if so, going into that ubuntu directory should show efi boot files.

 You may have done all your previous install in Legacy mode so you would not have seen any warning message about an EFI partition as an EFI partition wouldn't have been used on your old msdos drives.  If you booted in UEFI mode from the BIOS to install on the msdos drive, it would have needed an EFI partition (vfat) and it would need the boot and esp flags set.

Okay, now, see....everything you've said here (even the part before the quote) is Greek to me. What's important for all here to know is that _*I*_ didn't do anything but use the device. When I bought this laptop, it had already been converted from Windows to Linux Mint. In the time I've owned it, I made it dual-boot from the HDD, successfully installing new versions of Mint in that partition and multiple additional distros in the new partition _*including*_ the Kubuntu 20.04 LTS that's on there now and has always run fine.  The computer also came with a 20MB mSATA drive which the previous owner used for storage but I decided to use it for experiments with a number of installs of very lightweight distros. For quite some time that drive has held Zorin OS 15 Lite.

_*At no time during any of those installations of previous and current distros did anything like that EFI warning appear.*_ 

Most of those installs were done from a USB drive while the last two for Mint were upgrades. And I've changed nothing in terms of using something like gparted to reset a label or set flags or anything like that (as if I would know what I was doing). All I can say is that only with these attempts to install the newest Kubuntu (and maybe that's pointing a finger at Ubuntu 22.04 LTS) that this problem has existed...so I don't know what part of that is "Legacy Mode" or whatever else you're saying.

If this sounds frustrated or annoyed, let me assure you that's not the intended tone. I'm just puzzled.  And I just want to be clear to everyone that I'm only a notch or two above Newbie (I dabble in Linux, my daily driver is still a Windows PC) and after all of those many uneventful distro installs, this one is the first to sound this alarm (for whatever reason).

---

### Post by yancek on 2024-01-23
The 2 most likely scenarios are that you tried to do an EFI install but the EFI partition did not have the boot and esp flags set.  The other possibility is that all your previous installs were Legacy and the EFI partition was not needed or used.   There is no way for anyone at these forums to know if either of those scenarios is the problem but you can tell.  If you don't know the difference between a UEFI and Legacy install then you will continue to have problems.  Lots of information on UEFI/Legacy here at these forums and elsewhere online.

---

### Post by MAFoElffen on 2024-01-23
Please post the output of these posted within CODE Tags:
```

lsblk -e7 -o name,label,size,fstype,mountpoint,model
sudo fdisk -l 2>&1 | sed '/\/dev\/loop/,+3 d' 2> /dev/null | uniq
for n in $(sudo fdisk -l 2>&1 | sed '/\/dev\/loop/,+3 d' 2> /dev/null | uniq | grep -E '^Disk /dev/' | grep -v /mapper | awk '{print $2}' | sed 's/://g'); do sudo sgdisk -p $n; done

```

---

### Post by davepool on 2024-01-24
```
[COLOR=#000000][FONT=monospace]NAME   LABEL   SIZE FSTYPE MOUNTPOINT MODEL
sda          298.1G                   HGST HTS725032A7E630
&#9500;&#9472;sda1         512M vfat   /boot/efi   
&#9500;&#9472;sda2           1K                    
&#9500;&#9472;sda5       148.8G ext4   /           
&#9492;&#9472;sda6       148.8G ext4               
sdb           18.6G                   SATA SSD
&#9500;&#9472;sdb1          14G ext4               
&#9500;&#9472;sdb2           1K                    
[/FONT][/COLOR][COLOR=#000000][FONT=&quot][FONT=monospace]&#9492;&#9472;sdb5         4.7G swap  [/FONT][/FONT][/COLOR]

```


```
[COLOR=#000000][FONT=monospace]Disk /dev/sda: 298.09 GiB, 320072933376 bytes, 625142448 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Disk model: HGST HTS725032A7[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Disklabel type: dos[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Disk identifier: 0xbf8a8eba[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace][/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Device     Boot     Start       End   Sectors   Size Id Type[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sda1  *         2048   1050623   1048576   512M  b W95 FAT32[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sda2         1052670 625141759 624089090 297.6G  5 Extended[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sda5         1052672 313097216 312044545 148.8G 83 Linux[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sda6       313098240 625141759 312043520 148.8G 83 Linux[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace][/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Partition 2 does not start on physical sector boundary.[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace][/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Disk /dev/sdb: 18.64 GiB, 20014718976 bytes, 39091248 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Disk model: SATA SSD         [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Disklabel type: dos[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Disk identifier: 0x49d22543[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace][/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Device     Boot    Start      End  Sectors  Size Id Type[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdb1           2048 29298687 29296640   14G 83 Linux[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdb2       29300734 39090175  9789442  4.7G  5 Extended[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdb5       29300736 39090175  9789440  4.7G 82 Linux swap / Solaris [/FONT][/COLOR]
```


```
***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory.  
***************************************************************

Disk /dev/sda: 625142448 sectors, 298.1 GiB
Model: HGST HTS725032A7
Sector size (logical/physical): 512/4096 bytes
Disk identifier (GUID): 7302A100-EB06-4168-949A-0F249291AC40
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 625142414
Partitions will be aligned on 2048-sector boundaries
Total free space is 5740 sectors (2.8 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1050623   512.0 MiB   0700  Microsoft basic data
   5         1052672       313097216   148.8 GiB   8300  Linux filesystem
   6       313098240       625141759   148.8 GiB   8300  Linux filesystem

***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory.  
***************************************************************

Disk /dev/sdb: 39091248 sectors, 18.6 GiB
Model: SATA SSD         
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): A00C86C3-677F-4F7A-9BF1-2423BD39DFD0
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 39091214
Partitions will be aligned on 2048-sector boundaries
Total free space is 5101 sectors (2.5 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048        29298687   14.0 GiB    8300  Linux filesystem
   5        29300736        39090175   4.7 GiB     8200  Linux swap
```

---

### Post by #&amp;thj^% on 2024-01-24
@ davepool what happens if you try to install grub on that drive?
```
sudo grub-install /dev/sda
```
Also yancek asked to see this:
```
  sudo ls /boot/efi/EFI
```
I'm on debian unstable today so mine will look different.
```
sudo ls /boot/efi/EFI
boot  Parrot

```

I need to ask though did you manually partition before installing?
yancek brings up another good point via mdos in post #28

---

### Post by davepool on 2024-01-24
> [COLOR=#000000]@ davepool what happens if you try to install grub on that drive?[/COLOR]

I don't know. Do I **_want_** to do that? Let me know what you're after here.



> [COLOR=#000000]Also yancek asked to see this:[/COLOR]
[COLOR=#000000]Code:
  sudo ls /boot/efi/EFI[/COLOR]

The result was: No such file or directory


> [COLOR=#000000]I need to ask though did you manually partition before installing?[/COLOR]

If you mean _**immediately**_ before attempting to install 24.04 LTS....no.  As I think I've said elsewhere in this thread, I haven't changed anything in years. Let's ignore the mSATA drive and just talk about the HDD.  When I bought this device (maybe 3 years ago), the previous owner had already converted it from Windows to Linux Mint (full disk or "Normal" install). I left his LM install onboard (but have since done both clean installs and upgrades with no problems) and then added a partition when I wanted to make the HDD dual-boot.  I have since installed multiple distros in that partition, including many flavors of Ubuntu, ultimately landing on Kubuntu 20.04 LTS.  But I did NOT "manually" make those partitions.  During the install of the first distro to be added there, I simply chose the option that the installer presented to put the distro alongside the one already there.  Whatever decisions I had to make regarding the size and location of the new partition, etc. etc those was made THEN...with no adjustments or any other fiddling since then.

---

### Post by #&amp;thj^% on 2024-01-24
> **davepool said:**
> I don't know. Do I **_want_** to do that? Let me know what you're after here.





I can't guess if you want to or not, but MAFoElffen asked me to visit this thread this morning after your PM to him.

I'm trying to help ie:
This is mine for example only:
```
sudo grub-install /dev/sdb
[sudo] password for me: 
Installing for x86_64-efi platform.
Installation finished. No error reported.
```

If you want just for  MAFoElffen. I'm done here. :)
This sounds like a bug worthy report...
Good Luck

---

### Post by davepool on 2024-01-24
> [COLOR=#000000]MAFoElffen asked me to visit this thread this morning after your PM to him.[/COLOR]

Ah, good to know. And now I understand.


Well, then...here's what I get when I run sudo grub-install /dev/sda:

```
Installing for i386pc platform
Installation finished. No error reported.
```

If you want, you can go back to MAFoElffen's message #11 here, see my replies in #12 & #13 and then see his reply #14 to see where he once stood on bug reports and bug reports "by proxy".

Also, in message #20 pbear42 said:

> [COLOR=#000000]This problem is well known and easily duplicated. Boot any version of Ubuntu 22.04 in BIOS mode. Easily done in VirtualBox, as that's its default boot mode. With GParted, create an MBR partition table, then set up one or more partitions. Run Ubiquity; install by manual method. When you click install, the dire warning mentioned by the OP will appear. Click to continue anyway. The install will go through and the system boot without a hitch. On a BIOS system, the warning is a red herring.[/COLOR]

[COLOR=#000000]I've not tested whether the problem persists with the new installer. Edit: Have now run the test. The installer for 23.10 does [/COLOR]**not give the spurious EFI warning when booted in BIOS mode.**

The first part of that makes my eyes glaze over and would be a challenge.  But I like that part about plowing ahead anyway and how "on a BIOS system, the warning is a red herring."

---

### Post by #&amp;thj^% on 2024-01-24
Now run 
```
sudo update-grub
```
And paste that back here so we can see please..

---

### Post by davepool on 2024-01-24
The results of running sudo update-grub

```
[COLOR=#000000]Sourcing file `/etc/default/grub'[/COLOR]
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-91-generic
Found initrd image: /boot/initrd.img-5.15.0-91-generic
Found linux image: /boot/vmlinuz-5.15.0-88-generic
Found initrd image: /boot/initrd.img-5.15.0-88-generic
Found linux image: /boot/vmlinuz-5.15.0-86-generic
Found initrd image: /boot/initrd.img-5.15.0-86-generic
Found linux image: /boot/vmlinuz-5.4.0-139-generic
Found initrd image: /boot/initrd.img-5.4.0-139-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Linux Mint 21.3 Virginia (21.3) on /dev/sda6
Found Zorin OS 15.3 (15) on /dev/sdb1
done
```

---

### Post by #&amp;thj^% on 2024-01-24
Will it boot now?

---

### Post by davepool on 2024-01-24
> Will it boot now?

Wait....maybe I'm dense here. Maybe I'm missing something. But this hasn't been about an inability to boot. It's been about an inability (check that, an unwillingness) to complete an install of Kubuntu 22.04 LTS over a previous (and functioning) install of Kubuntu 20.04 LTS without producing the following alert:

[B][FONT=Calibri]"No EFI System partition was found. This system will likely not be able to boot successfully and the installation process may fail"


[/FONT][/B]This is an alert that 2) never appeared back when 20.04 LTS was installed on this computer and 2) has never appeared during installs in the other partition on the HDD (typically Linux Mint).
many 
I've never pressed on past that alert. Never been brave enough.

---

### Post by #&amp;thj^% on 2024-01-24
I see now, also the frustration of replying back to the same questions over and over. (Been there done that myself with developers)

My only advice now is to try another Fresh install and then submit the bug.
```
ubuntu-bug subiquity
```

I see a few reported on Kubuntu 22.04, but best to file a new one and let them decide if it is a duplicate.

---

### Post by davepool on 2024-01-24
Just to repeat what @pbear24 said in Message #20:

> [COLOR=#000000][COLOR=#000000]*I've not tested whether the problem persists with the new installer. Edit: Have now run the test. The installer for 23.10 does *[/COLOR][/COLOR]**not give the spurious EFI warning when booted in BIOS mode.**

If he's right...I'm willing to give it a shot. I've tended to prefer LTS but I'm not so in love with it that I wouldn't use the version with shorter support periods (do they upgrade easily when released?)

If the installer is the problem (and now a known problem for it to have been corrected in 23.10) is there any likelihood that the installer for 22.04 will be updated soon and maybe I should just sit tight and wait for it?

---

### Post by #&amp;thj^% on 2024-01-24
> **davepool said:**
> 
If the installer is the problem (and now a known problem for it to have been corrected in 23.10) is there any likelihood that the installer for 22.04 will be updated soon and maybe I should just sit tight and wait for it?

Who knows for sure if they will fix it for 22.04? But it would interesting to see if 23.10 will install for you

Choices should always be left up to the user, as I do things no one but me would do and try.
EDIT: 24.02 is just around the corner "April" so at least you could be enjoying your Plasma install faster. :)

---

### Post by davepool on 2024-01-24
@1fallen, I seem to have spun myself up needlessly. Somewhat contrary to what @pbear24 said, the installer for 23.10 _*did*_ produce the EFI warning.  HOWEVER, I note his qualifier that it did not produce the warning when he booted the installer _*in BIOS mode*_.

So now what's puzzling me is that in about 3 passes of the installer (to that EFI warning) I didn't see any specific way to select a BIOS mode (which doesn't mean it wasn't there).  Now, to be clear, I've been using a Ventoy drive (and, as of yesterday, the newest version of same) so I don't know if that matters. But all of my choices have come down to: 1) choice of USB Flash Disk, then 2) choosing the file from the Ventoy menu (and BTW, down in the lower left corner of that menu it shows "1.0.97 BIOS, if that matters) and 3) a choice to Boot in Normal Mode or Boot in Grub2 Mode (I've been choosing Normal)....then Try or Install Kubuntu.  So, nothing that obviously (to me) says "boot in BIOS mode."

---

### Post by oldfred on 2024-01-24
If you are in the installer, it is too late to choose UEFI or BIOS.
You choose by how you boot live installer from UEFI boot menu.
UEFI boot menu should have two options for live installer. One clearly UEFI and one that just shows name or label of flash drive (which is then BIOS mode).
Some tools that create live installer may make UEFI only or BIOS only installer. Then UEFI/BIOS will only have one choice.

Some systems just have multiple entries, some have separate sections in boot menu. One section is UEFI and one is BIOS/CSM/Legacy.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Newer systems after about 2020 may be UEFI only.
My Dell with 11th gen CPU is UEFI only. In UEFI menu it says BIOS can only boot in UEFI mode? Its not really BIOS if UEFI, but vendors still call it BIOS.

---

### Post by #&amp;thj^% on 2024-01-24
Thanks oldfred for jumping in that explains a lot I haven't seen that kind of activity so it's all new to me.

---

### Post by davepool on 2024-01-24
> **oldfred said:**
> If you are in the installer, it is too late to choose UEFI or BIOS.

I understand that. I've been talking about the menu that appears whenever one "breaks" the usual boot up process via Fn 2, Fn12 or the magic pin on the side or whatever.


> [COLOR=#000000]UEFI boot menu should have two options for live installer. One clearly UEFI and one that just shows name or label of flash drive (which is then BIOS mode).[/COLOR]
[COLOR=#000000]Some tools that create live installer may make UEFI only or BIOS only installer. Then UEFI/BIOS will only have one choice.[/COLOR]

I am not presented with such a choice.  Once I select F12 for an alternate boot procedure, I see:

ATA HDD0: HGST HTS725032A7E630
USB HDD: General USB Flash Disk
PCI LAN: Realtek PXE B03 D00

---

### Post by MAFoElffen on 2024-01-24
Here is what I saw from the queries I asked to be run.
```

# This is /dev/sda1...
 1            2048         1050623   512.0 MiB   0700  Microsoft basic data

```
There was more supporting data. But this shows the big problem and what needs to be corrected.

Note that this is an MS-DOS MBR partition table. Not GPT. Not that 0700 is not ESP (which is type code EF00). It is a "Microsoft Basic Data" partition type. Yes it is formatted as vfat and the boot flag is set, but this is why its is not recognized as an EFI partition.

Is there anything on that drive that you want to keep? If so, back it up, so it can be restored.

Give the disk a new GPT partition table. Create the first partition as EFI (type EF00). That will be the same as giving it a Boot and ESP flag.

Start the installer > Use Ohter in the install, to get into the manual partitioner. Create your other partitions. Set the didk to boot from that drive. The installer will find that EFI partition.

Finish the install. Restore the data you backed up, it you did... But ths was a new install of Kubuntu right?

---

### Post by davepool on 2024-01-25
Thanks, MAFoEllfyn, for your diligence and suggestions.  Of course, I have questions. ;)


> [COLOR=#000000]Note that this is an MS-DOS MBR partition table. Not GPT. Not that 0700 is not ESP (which is type code EF00). It is a "Microsoft Basic Data" partition type. Yes it is formatted as vfat and the boot flag is set, but this is why its is not recognized as an EFI partition.[/COLOR]

So, if I'm understanding you, this is a remnant of the Windows OS that used to be on the device before the previous owner converted it to Linux Mint (because Windows is not currently on it)?  My first question, then (and still) is....why only now? Why is this a problem now for the install of Kubuntu 22.04 LTS when it wasn't a problem for the install of Kubuntu 20.04 LTS years ago, nor for any of the many other flavors of Ubuntu that I installed in that same partition before I landed on Kubuntu?


> [COLOR=#000000]Is there anything on that drive that you want to keep? If so, back it up, so it can be restored.[/COLOR]

It's a dual-boot HDD so there's also an updated version of Linux Mint alongside. For what few changes I've made to Mint, it probably wouldn't be any additional work to just re-install it.


> [COLOR=#000000]Give the disk a new GPT partition table. Create the first partition as EFI (type EF00). That will be the same as giving it a Boot and ESP flag.[/COLOR]

[COLOR=#000000]Start the installer > Use Ohter in the install, to get into the manual partitioner. Create your other partitions. Set the didk to boot from that drive. The installer will find that EFI partition.[/COLOR]

[COLOR=#000000]Finish the install. Restore the data you backed up, it you did... [/COLOR]

Yikes. Okay, I'm already thinking of a weasel work-around because I really don't want to make hash of the whole thing.

If the entire HDD is going to be wiped anyway....why couldn't I install the new Kubuntu 22.04 LTS as a "Normal" or full disk installation (wouldn't that create all the new and proper partitions and flags?Or would the remnant of Windows that you spotted still remain?) .....and then install Mint using the installer option to put it alongside the existing distro?  Would that second distro's new partitioning et al be what it needs to see?  I think some installers are more flexible with this sort of thing...so, maybe the way to go would be to reverse the order, with Mint first, then Kubuntu...?  


> [COLOR=#000000]But ths was a new install of Kubuntu right?[/COLOR]

The install of Kubuntu 20.04 LTS that's already on the device was done years ago. The only thing "new" has been all these fruitless attempts to install Kubuntu 22.04 LTS on top of it, with the resulting EFI alerts.

---

### Post by #&amp;thj^% on 2024-01-25
> **davepool said:**
> 

The install of Kubuntu 20.04 LTS that's already on the device was done years ago. The only thing "new" has been all these fruitless attempts to install Kubuntu 22.04 LTS on top of it, with the resulting EFI alerts.

Is the Bios Current?
I'm a strictly Lenovo user I own several laptops, but they can and do have some edgy Bios on some models.
The point I'm trying to relay my ThinkPad X1 carbon was a bugger to install any Linux system to>>> as said by MAFoElffen because of this
 (which is type code EF00). It is a "Microsoft Basic Data" partition type.
I just wiped the Drive and proceeded to install my many Linux systems to. (But I'm not a Dual Booter)

---

### Post by davepool on 2024-01-25
> **1fallen said:**
> Is the Bios Current?

Simply put, if that's something that's done automatically, it might be. If not....I wouldn't know...or know what to do to update it.  



> [COLOR=#000000]I just wiped the Drive and proceeded to install my many Linux systems to. (But I'm not a Dual Booter)[/COLOR]

That's pretty much what I was alluding to in another message: if all of that manual re-partitioning and such will result in wiping everything from the HDD, why couldn't I just start over with a full-disk "Normal" install of one distro or the other?

---

### Post by #&amp;thj^% on 2024-01-25
It's not simply put, for Linux it takes a user to be responible for that;

I'll list a few ways:
Install fwupd (if not already installed):
```
sudo apt install fwupd
```
Start the daemon service:
```
sudo service fwupd start

```
Refresh the list of available firmware updates:
```
 sudo fwupdmgr refresh
```
List devices connected and supported:
```
fwupdmgr get-devices
```
List updates available (for previously listed devices):

```
fwupdmgr get-updates

```

Install the firmware update (if available):
```
sudo fwupdmgr update
```

There are some GUI's available for ease but I prefer the terminal.
EXAMPLE on mine:
```
sudo fwupdmgr update
[sudo] password for me:               
Devices with no available firmware updates: 
 &#8226; ELAN06FA:00 04F3:31DD
 &#8226; BCM20702A0
 &#8226; CS2311 1TB SSD
 &#8226; GL3224 SD reader [0x0749]
 &#8226; SSD 980 PRO 1TB
 &#8226; System Firmware
 &#8226; UEFI Device Firmware
 &#8226; UOEOS Laptop Dock
 &#8226; USB2.1 Hub
Devices with the latest available firmware version:
[COLOR="#FF0000"] &#8226; UEFI dbx[/COLOR]


```

---

### Post by oldfred on 2024-01-25
I have been using gpt starting in 2010.
The only place you must use MBR(msdos) is with Windows in BIOS boot mode.
Ubuntu and most Linux will  boot in UEFI or BIOS mode from gpt partitioned drives.
But you need an ESP - efi system partition for UEFI boot or a bios_grub partition for BIOS boot on gpt. Both are not required, but for several years when first converting from old BIOS system to new UEFI system I would put both partitions on all new drives and larger flash drives.

The only real difference with UEFI and BIOS boot is version of grub. Grub-pc is for BIOS boot and grub-efi-amd64 is for UEFI boot. And then supporting partition, ESP or bios_grub.
Of course system must be UEFI, but almost all systems since 2012 are UEFI as Microsoft required vendors to install in UEFI boot mode to gpt drives starting with Windows 8 in 2012.

If booting multiple installs, often better to have a shared data partition rather than have all data in both installs or other work arounds.
I even shared data with XP and Ubuntu back when I had XP in a NTFS data partition. Then when only Linux have an ext4 data partition. I like to keep system (including /home) separate from data as I have multiple installs. I also do not install snaps and use Kubuntu so / is not as large as typically now required for standard Ubuntu.

---

### Post by davepool on 2024-01-25
[COLOR=#000000]Refresh the list of available firmware updates:[/COLOR]
[COLOR=#000000]Code:
 sudo fwupdmgr refresh[/COLOR]
WARNING: UEFI firmware cannot be updated in legacy BIOS mode


[COLOR=#000000]Code:
fwupdmgr get-updates[/COLOR]
[COLOR=#FF5454]**WARNING:**[/COLOR][COLOR=#000000] UEFI firmware can not be updated in legacy BIOS mode[/COLOR]
  See [https://github.com/fwupd/fwupd/wiki/PluginFlag:legacy-bios](https://github.com/fwupd/fwupd/wiki/PluginFlag:legacy-bios) for more information.
Devices with no available firmware updates:  
 • HGST HTS725032A7E630
 • SATA SSD
 • BCM20702A0
No updatable devices

---

### Post by MAFoElffen on 2024-01-25
Remember me asking you in Post #6 to run something, right after boot to ensure you were always booted as UEFI and not as Legacy mode? In Legacy mode, it does not matter if an EFI partition is there or not, and you would not need to do anything to the partitions or partition table.

But, on a system that is UEFI capable, it is a lot of wasted resources, that you are not using, and hitting some limitations that you have to work around because of that.

Just saying...

Well, on the other hand, if you can live with all that, just set your BIOS back to CSM/Legacy (only)... Boot as that and install Ubuntu as that. Since you are dual-boot create a partition for it to live and install it. It will create an MBR/MS-DOS extended partition.. and you your other install will not have to have any other changes done to it. 

That is probably the option with the least work for you. But, then you can just delete that partition that is type 0700. You said the only other OS is Mint right? No Windows any more right?

---

### Post by #&amp;thj^% on 2024-01-25
> **MAFoElffen said:**
> 
But, on a system that is UEFI capable, it is a lot of wasted resources, that you are not using, and hitting some limitations that you have to work around because of that.

Just saying...



+1 That machine is UEFI capable.
Too many cooks now here, I'm setting out unless I'm needed.
It's just not this hard....:(

---

### Post by davepool on 2024-01-25
From your Message #6 and what you requested there.


> **MAFoElffen said:**
> 
2 things... 

1) If you get into the Settings on your Lenovo, for Boot mode, you will see that it has UEFU (only), and Hybrid (which will bot both EFI and Legacy/CSM). Change it to UEFI only.

2) Both of your drives have MS-DOS partition tables. It cannot boot from UEFI unless 
a) on a drive with an MS_DOS partition table, you add a boot_bios primary partion with a boot_bios flag, or
c) has a GPT partition table...

Since you are starting over without Windows... I would just repartition the disks with fresh GPT partition tables.  

On that machine, before you start an install, first go to a Terminal session in "Try" and do
```

ls /sys/firmware/efi/efivars

```
If it comes back as populated, it booted as UEFI. If it comes back as empty (no files in that directory, then it still booted as Legacy/CSM. If the later happens, thell us, and there are ways to burn the Installer LiveUSB media that will force booting from UEFI.

Item 1: Done.  Changed to UEFI.

Once that was done, here's the result of starting a "Try" session with 22.04 and running the command...

```

ls /sys/firmware/efi/efivars

``` 

```
[COLOR=#000000]AcpiGlobalVariable-af9ffd67-ec10-488a-9dfc-6cbf5ee22c2e        [/COLOR]
        AmdSetup-3a997502-647a-4c82-998e-52ef9486a247        
        Boot0000-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Boot0001-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Boot0002-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Boot0003-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Boot0004-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Boot0005-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Boot0006-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Boot0007-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Boot0008-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Boot0009-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Boot000A-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        BootCurrent-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        BootOptionSupport-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        BootOrder-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        BootOrderDefault-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        ConIn-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        ConInDev-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        ConOut-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        ConOutDev-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        db-d719b2cb-3d3a-4596-a3bc-dad00e67656f        
        dbx-d719b2cb-3d3a-4596-a3bc-dad00e67656f        
        DIAGSPLSHSCRN-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        ErrOutDev-8be4df61-93ca-11d2-aa0d-00e098032b8c        
FirmwarePerformanceDataTable-9dab39a4-3f8a-47ac-80c3-400729332c81        
        FlashDeviceVar-61b6dd0e-5aa1-437f-b29f-dd0890ef712e        
        HDDPWD-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        KEK-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Key0000-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Key0001-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Key0002-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Key0003-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Key0004-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Key0005-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        LastBootCurrent-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        LBC-2a4dc6b7-41f5-45dd-b46f-2dd334c1cf65        
        LBL-2a4dc6b7-41f5-45dd-b46f-2dd334c1cf65        
        LBOL-2a4dc6b7-41f5-45dd-b46f-2dd334c1cf65        
        LBOP0000-2a4dc6b7-41f5-45dd-b46f-2dd334c1cf65        
        LBOP0001-2a4dc6b7-41f5-45dd-b46f-2dd334c1cf65        
        LBOP0002-2a4dc6b7-41f5-45dd-b46f-2dd334c1cf65        
        LBOP0003-2a4dc6b7-41f5-45dd-b46f-2dd334c1cf65        
        LBOP0004-2a4dc6b7-41f5-45dd-b46f-2dd334c1cf65        
        LBOP0005-2a4dc6b7-41f5-45dd-b46f-2dd334c1cf65        
        LBOP0006-2a4dc6b7-41f5-45dd-b46f-2dd334c1cf65        
        LBOP0007-2a4dc6b7-41f5-45dd-b46f-2dd334c1cf65        
        LBOP0008-2a4dc6b7-41f5-45dd-b46f-2dd334c1cf65        
        LBOP0009-2a4dc6b7-41f5-45dd-b46f-2dd334c1cf65        
        LBOP000A-2a4dc6b7-41f5-45dd-b46f-2dd334c1cf65        
        LenovoConfig-2a4dc6b7-41f5-45dd-b46f-2dd334c1cf65        
        LenovoFlashScratch1-67c3208e-4fcb-498f-9729-0760bb4109a7        
        LenovoHiddenSetting-1827cfc7-4e61-4273-b796-d35f4b0c88fc        
        LenovoScratchData-67c3208e-4fcb-498f-9729-0760bb4109a7        
        LenovoSecurityConfig-a2c1808f-0d4f-4cc9-a619-d1e641d39d49        
        LenovoSystemConfig-2a4dc6b7-41f5-45dd-b46f-2dd334c1cf65        
        LenovoThermalShutdown-943d1460-da6e-499a-af6d-4593b12bc4d7        
        LenovoWolInfo-0af4027f-9b58-41c0-b62f-cd3a1cef54ee        
        LKOP0000-2a4dc6b7-41f5-45dd-b46f-2dd334c1cf65        
        LKOP0001-2a4dc6b7-41f5-45dd-b46f-2dd334c1cf65        
        LKOP0002-2a4dc6b7-41f5-45dd-b46f-2dd334c1cf65        
        LKOP0003-2a4dc6b7-41f5-45dd-b46f-2dd334c1cf65        
        LKOP0004-2a4dc6b7-41f5-45dd-b46f-2dd334c1cf65        
        LKOP0005-2a4dc6b7-41f5-45dd-b46f-2dd334c1cf65        
        LWO-2a4dc6b7-41f5-45dd-b46f-2dd334c1cf65        
        MailBoxQ-67c3208e-4fcb-498f-9729-0760bb4109a7        
        MokListRT-605dab50-e046-4300-abb6-3dd810dd8b23        
        MokListTrustedRT-605dab50-e046-4300-abb6-3dd810dd8b23        
        MokListXRT-605dab50-e046-4300-abb6-3dd810dd8b23        
        MTC-eb704011-1402-11d3-8e77-00a0c969723b        
        OpromDevicePath-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        OsIndicationsSupported-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        PbaStatusVar-0ec1a7f5-4904-40a0-8eab-4bcc4666da45        
        PK-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        PlatformLang-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        PlatformLangCodes-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        ProtectedBootOptions-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        PwdStatusVar-3e72b3ad-2b91-424a-ad73-c3270e91ed88        
        QCIConfiguration-8f7bf0fe-5f4d-4650-88cc-4c91a1517592        
        SbatLevelRT-605dab50-e046-4300-abb6-3dd810dd8b23        
        SctHotkey-4650c401-93f1-4aeb-b87d-c8204c047dec        
        SecureBoot-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Setup-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9        
        SetupHotKey-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        SetupMode-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        SimpleBootFlag-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        SMBIOSELOG000-c3eeae98-23bf-412b-ab60-efcbb48e1534        
        SMBIOSELOGNUMBER-c3eeae98-23bf-412b-ab60-efcbb48e1534        
        SMBIOSMEMSIZE-c3eeae98-23bf-412b-ab60-efcbb48e1534        
        SmmS3NvsData-8983fd2d-113c-4e2b-8f47-0abfeb20a41a        
        Time-470733de-df43-448b-8b45-4eeb0df8c812        
        Timeout-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        TpmAcpiData-6403753b-abde-4da2-aa11-6983ef2a7a69        
        TpmSaveState-5e724c0c-5c03-4543-bcb6-c1e23de24136        
        VentoyOsParam-77772020-2e77-6576-6e74-6f792e6e6574
```

So, based on your info, it booted as UEFI

---

### Post by #&amp;thj^% on 2024-01-25
You still have many old boots showing, and possibly a problem as shown below:
```
Boot0000-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Boot0001-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Boot0002-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Boot0003-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Boot0004-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Boot0005-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Boot0006-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Boot0007-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Boot0008-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Boot0009-8be4df61-93ca-11d2-aa0d-00e098032b8c        
        Boot000A-8be4df61-93ca-11d2-aa0d-00e098032b8c 
```
Please show us this now:
```
efibootmgr

### Mine
BootCurrent: 0006
Timeout: 0 seconds
BootOrder: 0006,0003,0000,2002,2001,2003
Boot0000* EFI Hard Drive (S5P2NU0W607176Z-Samsung SSD 980 PRO 1TB)	PciRoot(0x0)/Pci(0x1,0x2)/Pci(0x0,0x0)/NVMe(0x1,00-25-38-B6-31-A4-B7-1C)/HD(1,GPT,581e4afa-a9ea-1546-9171-fee82fa93029,0x1000,0x96000)RC
Boot0001* EFI PXE 0 for IPv4 (9C-2D-CD-15-0B-65) 	PciRoot(0x0)/Pci(0x2,0x1)/Pci(0x0,0x0)/MAC(9c2dcd150b65,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0002* EFI PXE 0 for IPv6 (9C-2D-CD-15-0B-65) 	PciRoot(0x0)/Pci(0x2,0x1)/Pci(0x0,0x0)/MAC(9c2dcd150b65,0)/IPv6([::]:<->[::]:,0,0)RC
Boot0003* Linpus lite	HD(1,GPT,0afd26be-c684-be46-99ff-ce1ea5130c7d,0x1000,0x96000)/File(\EFI\Boot\grubx64.efi)RC
Boot0005* EFI USB Device (SanDisk)	UsbWwid(781,5581,0,4C53000105042312307)/HD(1,GPT,eb0ef56a-4816-4dd1-9067-dfd783891989,0x800,0x301f)RC
Boot0006* parrot	HD(1,GPT,581e4afa-a9ea-1546-9171-fee82fa93029,0x1000,0x96000)/File(\EFI\parrot\grubx64.efi)
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot2003* EFI Network	RC

```

---

### Post by MAFoElffen on 2024-01-26
> **oldfred said:**
> 
Some tools that create live installer may make UEFI only or BIOS only installer. Then UEFI/BIOS will only have one choice.

Some systems just have multiple entries, some have separate sections in boot menu. One section is UEFI and one is BIOS/CSM/Legacy.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Newer systems after about 2020 may be UEFI only.
My Dell with 11th gen CPU is UEFI only. In UEFI menu it says BIOS can only boot in UEFI mode? Its not really BIOS if UEFI, but vendors still call it BIOS.
Because it's still referred to as "UEFI [COLOR=#ff0000]BIOS[/COLOR]", and follows the SMBIOS standard... Yes, some confusing mixed terminology.
My old ThinkPad has UEFI only, and CSM & UEFI... So with that one, if in that hybrid mode, I have to either watch how I create the bootable disks, and check which mode it boots into.

That is why I am quick to tell people to check that... And recommended to Yann to we add a 'User Prompt' telling people from the UI, this booted in <this> boot mode... To give people a better clue.

I think that would also benefit users with installer live images... But if they just checked the Grub2 Menu for if the  "Firmware Settings" Option is there or not... They would know right then. Grub is already aware of what boot mode it booted from to display the menus.

---

### Post by davepool on 2024-01-26
@1fallen, I'll get on with your latest request here shortly....

But I just wanted to report that this morning when I booted up this laptop, it did not go to the grub menu.  I had to go back into the BIOS settings and change back to BOTH from the UEFI Only setting that you asked me to make in the first step of Message #6 (which MAFoEllfen reminded me of yesterday).  Once I did that, all was well.

---

### Post by MAFoElffen on 2024-01-26
Is the BIOS somehow "changing the boot mode on it's own"? That would be odd...

---

### Post by MAFoElffen on 2024-01-26
I think what we need to do at this point, is to clarify what you want to do as your goal. We should have done that earlier.

You seem to be going in different dirrections, and I think this is causing some confusion with us. I pointed this out, when I said you have two options. Let me spell this out a little more.

1) Your thread title implies that you want and need to boot as UEFI. And the error said there was no ESP partition present to do that.

2) But your other installed OS is installed as Legacy/CSM... MBR.

That is two different things, which would mean two different approaches.

If you go with UEFI (#1), you have more options open to you, and have a future path forward to do many things. It is the best option available for your hardware, but would mean some more work on your part. 
 -- BIOS set UEFI only
 -- Convert storage boot disk from MS-DOS to GPT.
 ** The above would mean backing up the other existing OS, and restoring it back into a new GPT partition...
 -- Add a (correct) EFI partition
 -- Install Ubuntu as UEFI
 -- Convert the existing Mint install from MBR to UEFI boot, by mounting the install, chrooting into it, and reinstalling grub there as UEFi boot mode.
 
If you stayed as CSM Boot mode, there would be less work, but your disk is limitted by the MS-DOS partiton type scheme. You lose the advanced UEFI options in your BIOS Settings. You lose the UEFI boot menu (on most machines)... A few other things. But
 -- BIOS Set to CSM mode
 -- No changes to disk storage type
 -- No changes needed to Mint
 -- Ensure the installer disk booted as Legacy boot mode, and install Ubuntu...
 
When I brought this up previously, you seemed to balk, but never really gave us an answer to that... 
 
*** Now, before doing anything else, tell us which of these is your decision and path forward. I don't think we should proceed any further until you help clarify that.

Understood?

---

### Post by davepool on 2024-01-26
> Please show us this now

```
efibootmgr
```


It responded to say it wasn't installed.  So I installed it and ran it.

```
EFI variables are not supported on this system.
```

---

### Post by #&amp;thj^% on 2024-01-26
Please see post #60
We need a clear path forward.

EDIT: "efibootmgr" only works in a uefi boot...not legacy. :)

---

### Post by MAFoElffen on 2024-01-26
> **1fallen said:**
> Please see post #60
We need a clear path forward.

+1000 We will not help you until you answer the questions from Post #60.

No more jumping back-and-forth.

Answer that, then we will give you clear instructions on what to do to get there. Do not complicate this and make it harder than it it.

---

### Post by davepool on 2024-01-28
I’m coming around to the thought that being a Forum staffer, certainly staff emeritus, carries with it as an occupational hazard the difficulty of following so many different conversations and keeping track of who said what and when (and how many times).  For that, I have some sympathy.
 
 
> I think what we need to do at this point, is to clarify what you want to do as your goal. We should have done that earlier.
 
My goal from the outset has been to get Kubuntu 22.04 LTS installed and with the same lack of drama I experienced when I installed 20.04 years ago, especially since I had made NO CHANGES to the computer, certainly not the BIOS mode (and especially since until this “chat” I had no idea where that was or how to do it or why.
 
 
 
Here’s a point I made that I think was lost on most, if not everyone: 
 
> I just want to be clear to everyone that I'm only a notch or two above Newbie (I dabble in Linux, my daily driver is still a Windows PC) and after all of those many uneventful distro installs, this one is the first to sound this alarm (for whatever reason).
 
 
From MAFoEllfyn:

> You seem to be going in different dirrections, and I think this is causing some confusion with us. 


Then imagine the confusion on my end with many people explaining WHAT is happening but no one explaining WHY this is happening ONLY NOW, especially since I’d made NO CHANGES to anything.


 
 

 
> I pointed this out, when I said you have two options. Let me spell this out a little more.

1) Your thread title implies that you want and need to boot as UEFI. And the error said there was no ESP partition present to do that.

2) But your other installed OS is installed as Legacy/CSM... MBR.

That is two different things, which would mean two different approaches.

If you go with UEFI (#1), you have more options open to you, and have a future path forward to do many things. It is the best option available for your hardware, but would mean some more work on your part.
-- BIOS set UEFI only
-- Convert storage boot disk from MS-DOS to GPT.
** The above would mean backing up the other existing OS, and restoring it back into a new GPT partition...
-- Add a (correct) EFI partition
-- Install Ubuntu as UEFI
-- Convert the existing Mint install from MBR to UEFI boot, by mounting the install, chrooting into it, and reinstalling grub there as UEFi boot mode.

If you stayed as CSM Boot mode, there would be less work, but your disk is limitted by the MS-DOS partiton type scheme. You lose the advanced UEFI options in your BIOS Settings. You lose the UEFI boot menu (on most machines)... A few other things. But
-- BIOS Set to CSM mode
-- No changes to disk storage type
-- No changes needed to Mint
-- Ensure the installer disk booted as Legacy boot mode, and install Ubuntu...

When I brought this up previously, you seemed to balk, but never really gave us an answer to that...


Balk?  Yeah…

 
From Message #47, MAFoEllfyn
 
> [I]Give the disk a new GPT partition table. Create the first partition as EFI (type EF00). That will be the same as giving it a Boot and ESP flag.

Start the installer > Use Ohter in the install, to get into the manual partitioner. Create your other partitions. Set the didk to boot from that drive. The installer will find that EFI partition.

Finish the install. Restore the data you backed up, it you did...[/I]
 
 
Yikes. Okay, I'm already thinking of a weasel work-around because I really don't want to make hash of the whole thing.
 
 
Do I need to translate? Okay. “That’s not comfortable for me. Isn’t there any other way? I’m reading warnings of how a mistake here can make the system un-bootable.”
 
 
Still in Message #47

Now from me:

> If the entire HDD is going to be wiped anyway....why couldn't I install the new Kubuntu 22.04 LTS as a "Normal" or full disk installation (wouldn't that create all the new and proper partitions and flags?Or would the remnant of Windows that you spotted still remain?)
 
 
Then again in Message #49, still from me:
 
> …if all of that manual re-partitioning and such will result in wiping everything from the HDD, why couldn't I just start over with a full-disk "Normal" install of one distro or the other?
 
 
<crickets><crickets> 
 
 
From MAFoEllfyn:
 
> *** Now, before doing anything else, tell us which of these is your decision and path forward. 
 
 
I chose a third solution. I finally got the answer to my question (via the devicetests-dot-com website):


[B]Method 1: Re-install Ubuntu using UEFI Mode
 
The simplest and most straightforward method to switch from Legacy to UEFI is to re-install Ubuntu in UEFI mode. Here’s how to do it:
 
·        Access your system’s firmware settings: The process to access these settings varies depending on the system manufacturer. Generally, you can access them by pressing a specific key (like F2, F10, or Del) during the system startup.
 
·        Change the boot mode to UEFI: Once in the firmware settings, look for the boot mode option and change it from Legacy or CSM to UEFI.
 
·        Re-install Ubuntu: Boot your system using a USB drive containing the Ubuntu setup. During the installation process, select the option to erase the disk and install Ubuntu. [COLOR=#ff0000]This process will convert the disk from MBR (Master Boot Record) to GPT (GUID Partition Table) format and set up the necessary EFI partitions.[/COLOR][/B]
 
 
 
I’ve installed Kubuntu 22.04 LTS as a full-disk installation. It created the fat 32 EFI partition and set the proper flags. Wi-fi works, I've installed the packages I want and uninstalled those I don't.
 
 
 
> I don't think we should proceed any further until you help clarify that.

Understood?
 
 
How charming. 
 
Yeah, I understand much. Everyone’s default solution was to “get under the hood,” with one reply even saying that Linux _*requires*_ this of its users. No real consideration for my very limited skillset (other than some veiled suggestions that it’s up to me to search for the info I need and work it out). Come on, this is easy. Well, everything is easy when you know what you're doing.
 
Linux sits at about 3% of the desktop market (I’m not counting Chrome). I think I represent a lot of the potential market “out there” who are simply USERS. For us (and where lots of potential growth lies), the answer to someone who just wants to start his car and drive it is not “learn how to be an auto mechanic and learn our language.”

Thanks for everything.

---

### Post by MAFoElffen on 2024-01-28
I saw that you were getting frustrated and being pulled in different directions, by trying to answer and do what many people were asking of you. For that I apologize. I saw that and saw that it needed to be stopped. For all our sake.

I sympathize  and fully understand how that feels. I have been stuck in that situation from time to time. I get that from the upstream Intel Graphics Teams while trying to resolve upstream bugs for us. I try to do all that I am asked of me, even though it is in different directions.

Option #3 was a very wise solution, ending up with the result of option #1, with a faster much simpler journey. My compliments in your decision.

I am personally sorry this took so long to get here to your solution, and how it got to here. Yes, I do try to keep track of what was said, and do take some personal responsibility at how things progress. I take pride in helping others. I care about how you are treated and that you are being helped. As you said, I guess that does come from being a Moderator previously here. Keep order, and peace. 

I felt even more responsible when you PM'ed me personally to ask me to come aback and help you. That made it personal "to me" that you were taken care of.

My previous message was not just for you to help clarify, but to others who were pulling you in different directions at the same time. I know that can be frustrating. That way it could go forward in a more organized path. Things should not have to be so hard. And you should not have to be caught in the middle of conflicting paths.

I am very happy that you have reached a working solution.

---

