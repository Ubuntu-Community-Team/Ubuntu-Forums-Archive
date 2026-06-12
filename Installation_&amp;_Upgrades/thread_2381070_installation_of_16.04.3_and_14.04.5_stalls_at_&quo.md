---
title: "installation of 16.04.3 and 14.04.5 stalls at &quot;installing grub2 ...&quot;"
date: 2017-12-26
forum: Installation &amp; Upgrades
---

### Post by che-ffe-muc on 2017-12-26
I am not new to ubuntu and/or edubuntu. I installed a few edubuntu and ubuntu on older laptops (11.10./12.04./14.04.).
This time the installation did not succeed (I am trying hard for almost ten days now).
 I bought this notebook with FreeDos only: Lenovo ideapad 320-15IAP, Intel N3350 1.1G, 4GB RAM, 1TB HDD. Sounded like a good starting point for my 13-year-old first notebook.

Ok, here is the issue:
Boot-Info: [https://paste.ubuntu.com/26256049/](https://paste.ubuntu.com/26256049/)

1. I installed from LiveCD ("Try Ubuntu") and/or installed directly ("Install Ubuntu"). 16.04.3 Ubuntu and/or 14.04.5 Edubuntu.
2. In case of direct install I changed the command line: removed "quiet splash", set "nosplash --verbose text nomodeset" (otherwise I got a black screen during installation process)
3. All went fine (language, local, user, pwd, copying files, install system, install hardware, ...) until it gets to "installing grub2"

This is what I can see:
 /usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID xxxx was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID zzzz was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)
 
First few times I killed it with ~ Source ID 50.000, later I gave it Source ID ~ 200.000, the last time I let it go for a day and killed it with Source ID somewhat >1.500.000

I have also tried this:
4. I tried boot-repair according to [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) -> 2nd option (i killed it after 30+ minutes)
Before I started it I had:
(appstreamcli. xxx): CRITICAL **: Error while moving old database out of the way.
AppStream cache update failed.

5. I have disabled secure boot

I searched quite some time in the past days, having read some articles in this forum and on askubuntu i.e. black screen issues (nomodeset, etc.), boot-repair, etc. with little progress.
BTW: I even tried to install Win7 (to start ubuntu install from that point) but even this did not complete.

Thank you in advance for your support!

---

### Post by oldfred on 2017-12-26
Default Windows 7 is BIOS, and you have UEFI system. It might still install, but would convert entire hard drive from BIOS/MBR to UEFI/gpt.

But if you tried to install Windows it may have tried the conversion to MBR from gpt and it does not do it correctly.

What does this show?
 sudo gdisk /dev/sda
Command (? for help): 
      
 p (print/show)
w (write)
q (quit) 

Skip write if print does not look correct, and copy output back here.

Also some FAT32 partitions need repairs.
      
 dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

### Post by che-ffe-muc on 2017-12-26
Answer to 1)
ubuntu@ubuntu:~$ sudo gdisk /dev/sda -p
GPT fdisk (gdisk) version 1.0.1

Usage: gdisk [-l] device_file

Question to 2)
ubuntu@ubuntu:~$ sudo dosfsck -t -a -w /dev/sda1
fsck.fat 3.0.28 (2015-05-16)
0x41: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
 Automatically removing dirty bit.
Performing changes.
/dev/sda1: 6 files, 298/130812 clusters
ubuntu@ubuntu:~$ sudo umount /dev/sda1
umount: /dev/sda1: not mounted
ubuntu@ubuntu:~$ sudo dosfsck -t -a -w /dev/sda1
fsck.fat 3.0.28 (2015-05-16)
/dev/sda1: 6 files, 298/130812 clusters

---

### Post by oldfred on 2017-12-26
Type ? to see commands, but you do not put command on same line as device.

```
fred@Asusz97:~$ sudo gdisk /dev/sda
[sudo] password for fred: 
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): p

```

Yes, run from live installer. It should not be mounted normally, but if you click on it to see what it there it will be mounted, and you have to then unmount it.

---

### Post by che-ffe-muc on 2017-12-26
*Now I think I did it right - ad 1)*

ubuntu@ubuntu:~$ sudo gdisk /dev/sda
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): p
Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 90BB7C4B-A198-4E78-ABFA-E845443A4CC4
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 3437 sectors (1.7 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1050623   512.0 MiB   EF00  EFI System Partition
   2         1050624      1945495551   927.2 GiB   8300  
   3      1945495552      1953523711   3.8 GiB     8200  

Command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT) to /dev/sda.
Warning: The kernel is still using the old partition table.
The new table will be used at the next reboot or after you
run partprobe(8) or kpartx(8)
The operation has completed successfully.

[I]I understand: we have repaired /dev/sda1 and now repaired partition /dev/sda
Next step: reboot and start to install ubuntu again?[/I]

---

### Post by oldfred on 2017-12-26
It looks like gdisk is not showning any issues, so not the problem.

Not sure what your specific issue is.

Some other ideapad's, often issues can be similar even if not same model.
       Lenovo Ideapad z585 Precise Installed wifi OK Dual Boot Win 7 no Sound SOLVED - other issues
[http://ubuntuforums.org/showthread.php?t=2170099](http://ubuntuforums.org/showthread.php?t=2170099)
[URL="https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS"]https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS
[/URL]
 Lenovo Ideapad Y500 LiveUSB Problem, also brightness
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://ubuntuforums.org/showthread.php?t=2230117](http://ubuntuforums.org/showthread.php?t=2230117)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358) 
      
 Lenovo Y700 Ideapad Windows 10 & Ubuntu SSD & HDD
[http://www.everydaylinuxuser.com/2016/05/how-to-dual-boot-ubuntu-and-windows-10.html](http://www.everydaylinuxuser.com/2016/05/how-to-dual-boot-ubuntu-and-windows-10.html) 
    [URL="https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS"]
[/URL]

---

### Post by che-ffe-muc on 2017-12-26
Thank you, oldfred. I will check your proposed readings.

Unfortunately I still face the same situation:
1. Boot from DVD
2. "Install Ubuntu" (16.04.3 amd64) - change command line: removed "quiet  splash", set "nosplash --verbose text nomodeset"
3. run install & all went fine (language, locale, user, pwd, copying files, install  system, install hardware, ...) until it gets to "installing grub2"

/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18:  Warning: Source ID xxxx was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131:  Warning: Source ID zzzz was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)

---

### Post by oldfred on 2017-12-26
found a bug with similar errors reported from a variety of programs, but considered a nuisance not a real problem.
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1264368](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1264368)

Have you tried booting after install?

Or running Boot-Repair after install?
And having it run its suggested fixes (which seemed to be a reinstall of grub).

---

### Post by che-ffe-muc on 2017-12-26
The installation process seems to wait for something in the "install package grub2 ..." sequence. The installation has not been finished yet.
The current status is:
.../nmwidgets.py:18:  Warning: Source ID 130600 was not found ...
.../nmwidgets.py:131:  Warning: Source ID 130804 was not found ...
(cont.)

Boot or boot-repair _after_ install is not yet a question.

---

### Post by oldfred on 2017-12-26
Some users were able to install but had other issues.
[https://ubuntuforums.org/showthread.php?t=2369571](https://ubuntuforums.org/showthread.php?t=2369571)

What video card/chip?

Have you verified ISO you downloaded was correct?
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Some just find using different installer to USB flash drive works.

Are you installing full Ubuntu or one of the lighter weight flavors? If 2GB or RAM or less, lighter weight flavor recommended.

       
 Light weight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors) 
    
Mint is not an official Ubuntu flavor but based on Ubuntu. This user had many boot parameters.
[https://www.reddit.com/r/linuxmint/comments/6vccn4/problem_touchpad_not_working_lenovo_ideapad_320e/](https://www.reddit.com/r/linuxmint/comments/6vccn4/problem_touchpad_not_working_lenovo_ideapad_320e/)

---

### Post by che-ffe-muc on 2017-12-26
Thank you for more options to validate:
- checksum is ok
- decided to go for Ubuntu 16.04.3 LTS (AMD64): i.e. 4GB RAM

Actually the installation seemed almost done after 30-40 mins but since then no real movement except these warnings

[INDENT]The current installation status (still "install  package grub2 ..."):
.../nmwidgets.py:18:  Warning: Source ID 390712 was not found ...
.../nmwidgets.py:131:  Warning: Source ID 390910 was not found ...
(cont.)[/INDENT]

---

### Post by oldfred on 2017-12-26
Not familiar with that error. Not common.

Do you have the latest UEFI/BIOS from Vendor?
Found these, but not sure they help much.
[https://askubuntu.com/questions/874895/installing-ubuntu-16-04-1-on-new-ssd-drive-from-live-usb-errno5-during-install](https://askubuntu.com/questions/874895/installing-ubuntu-16-04-1-on-new-ssd-drive-from-live-usb-errno5-during-install)

If you reinstall grub with Boot-Repair from live installer, do you get same or similar errors?

Edit:
My install just shows swap as swap, not as swsuspend. I have seen that, but I do not think it was with standard Ubuntu.
I might delete swap and re-create it with gparted and then try a reinstall.

---

### Post by che-ffe-muc on 2017-12-26
on swap as swsuspend:
swap might be swsuspend because I have suspended an earlier installation.
Might this be an issue? I think this partition will be deleted/overwritten when using the "erase disk and install ubuntu" or "erase 16.04 and install ubuntu" option.

---

### Post by che-ffe-muc on 2017-12-26
How do I know if UEFI is latest version from vendor? I am not familiar with how to find out. Sorry.

At least the last linked forum post knows the warning message. I am currently at:

/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 587823 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 588025 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 588194 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 588376 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)

---

### Post by che-ffe-muc on 2017-12-26
This post sounds familiar to my situation: [https://ubuntuforums.org/showthread.php?t=2311311](https://ubuntuforums.org/showthread.php?t=2311311)
and another one (in the French forum) describes it, too: [https://forum.ubuntu-fr.org/viewtopic.php?id=2018753](https://forum.ubuntu-fr.org/viewtopic.php?id=2018753)

---

### Post by oldfred on 2017-12-26
Did French thread have any suggestions.
I see it is also Acer which after install has a unique requirement for setting "trust" in UEFI.

Normally during install it uses an existing swap. So if existing swap is perhaps the issue then it may use it, but then have issues with it. (just a guess as I am running out of ideas).

Somewhere in UEFI, it will show version number.
Then you can go to vendors site and for your model search for updates, support or what ever it has to find new updates to UEFI/BIOS. If current good, if not you need to install the newer version. Usually instructions are for installing from Windows, but often alternative instructions for installing from flash drive or directly from within UEFI and file in FAT32 partition that UEFI can see.

---

### Post by che-ffe-muc on 2017-12-27
I had a similar idea about the swap partition:
New installation uses existing partitions, and does not erase swap partition (maybe because protected by swsuspend).
When installation has finished, ubiquity/frontend/gtk_components tries to remove temporary sources from swap partition.

The French post said that (apart from talking about Acer) according to the linked boot-info ubuntu was already installed when user Polopolopolopolo asked for help with similar warnings.

This is what I will try next (but first I give ubiquity some time for more warnings):
- check UEFI version, and update if necessary
- check boot-repair
- try to install ubuntu again - using the "something else" option and manually delete and create the 3 partitions.


But my computer still counts the source ids to remove. It is currently at:[INDENT][I]/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18:  Warning: Source ID 2150112 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131:  Warning: Source ID 2150339 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)
[/I][/INDENT]
I am now just curious how far this will go. I think I'll give it another day.

---

### Post by che-ffe-muc on 2017-12-30
Update:
I let it go with those warnings as mentioned above for two full days (source id > 3.000.000).

What I did next: I installed ubuntu 16.04.3 from scratch using the "something else" option. Here is a new [boot-info]("https://paste.ubuntu.com/26273263/") for this.
During installation process the same issue occured (unfinished installation, continuous warnings).
Because I could not do anything else I suspended the machine.
Next I started the computer again - but I removed the DVD, And it booted from disk successfully. Surprise, surprise.

Basic installation with WLAN, Office, Firefox is working, but now I cannot install new software (i.e. VLC) or upgrade existing software (Firefox) and I cannot install any ubuntu updates (i.e. security updates). I will create a new thread for this new situation.

I consider this thread as not solved because any installation of ubuntu ends in a (seems to be) endless loop of warnings.

[I]/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18:   Warning: Source ID 2150112 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131:   Warning: Source ID 2150339 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)[/I]

I regard this warnings as an installation bug - but I do not know how to provide those trace files or how to create a bug for this.

---

### Post by fred0r on 2018-06-30
Just bought a Lenovo 320-15IAP without any OS and tried to install the current 18.04.x64 and have also the same error.
I installed the latest BIOS (06/2018) and tried it in Legacy/UEFI/LegacyFirst, with/without IntelTrust 

Perhaps its important, so:
In the BIOS-Information beside Version/SN/CPU there are some entries i've never seen in any BIOS before:

UUID Number:                    8digits/chars-4digits-4digits/chars-4digits/chars-12digits/chars
Preinstalled OS licsense:      NO DPK
OA3 Key ID:                       0000000000000
OA2:                                 N

---

### Post by fred0r on 2018-07-01
I was able to install 16.04.4 on that Maschine.

---

