---
title: "How-to Install 9.10 on fakeraid"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by gilson585 on 2009-12-20
This is how I installed 9.10 karmic onto *a stripped fakeraid* Raid 0 array. These instructions may or may not work for a mirrored raid 1 array, I have gotten limited feedback on this. All you really need is the LiveCD and an internet connection. The steps outlined here are used after Ubuntu has been installed but fails to boot. Just load the LiveCD environment and follow these steps. Mind you this may be a daunting task to a person new to Ubuntu but if you have any command line experience you should be fine. I made this how-to cause I felt many others were lacking in some areas. I had searched around the net and found bits and pieces to make this work and thought how nice to have it all in one spot so here it is. ##Note this works on ext4 w/o any patch, 9.10 no longer requires install via Alternate CD as the LiveCD has *dmraid* included, also note *fdisk* does not work well with *dmraid* use *gparted* instead.

      1. Open a terminal: Applications, Accessories, Terminal.
  
      2. Create a mounting point
**sudo mkdir /mnt/root**

3. [B]ls /dev/mapper
[/B]In this example the output would have shown "nvidia_cffbdeda, nvidia_cffbdeda1, nvidia_cffbdeda2" where nvidia_cffbdeda is the hdd. All the others listing a # on the end are the partitions. If you don't know what partition is the root of your installation check out *gparted*. I will use nvidia_cffbdeda1 in the following steps as an example for mounting and chrooting into the installation.
  
  4. Mount the installation
**sudo mount /dev/mapper/nvidia_cffbdeda1 /mnt/root**
*If this fails use *nautilus* (*thunar* in xbuntu) to mount your Ubuntu root partition then use **mount** to find the mount location. This location will be used in place of **/mnt/root** in the following steps.
**sudo mount --bind /dev /mnt/root/dev**
**sudo mount -t proc proc /mnt/root/proc**
**sudo mount -t sysfs sys /mnt/root/sys**[B][COLOR=#000000]
[/COLOR][/B]**sudo mount -t devpts devpts /mnt/root/dev/pts**[B]
sudo cp /etc/resolv.conf /mnt/root/etc/resolv.conf[/B]

5. Login into the installation
**sudo chroot /mnt/root /bin/bash**

6.Fetch most recent package lists[B]
apt-get update[/B]

7. Remove GRUB2
**apt-get purge grub2 grub-pc**
**rm -r /boot/grub**
##The system will be unbootable until another bootloader is installed.

      8. Install GRUB 0.97
**apt-get install grub**
**grub-install /dev/mapper/xxx** ##note please substitute your hdd in this line (mine would have been *nvidia_cffbdeda*)

9. At this point it may be a good idea to check the *device.map*
      **chmod 777 ****/boot/grub/device.map**##For write access
**nano /boot/grub/device.map**
Mine was incorrect and I changed it to:
          (fd0)    /dev/fd0
          (hd0)    /dev/mapper/nvidia_cffbdeda ##was listed as /dev/sda which is incorrect
          (hd1)    /dev/sdc
  Afterwards use this to restore file permissions
**chmod 744 ****/boot/grub/device.map**
If changes were made then re-run *grub-install*

10. **grub --no-curses** ##you will now be at the grub prompt##
**grub> device (hdx) /dev/mapper/xxx** ##note please substitute your hdd in this line
**grub> find /boot/grub/stage1** ##make a note of the output it is used in the next step
**grub> root (hdx,y)** ##(hdx,y) where x is the drive (most likely 0) and y is the partition (first partition would be 0 NOT 1)
[B]setup (hdx)
quit
update-grub [/B]##When prompted to generate a menu.lst file say yes

13. Run these commands to keep it from upgrading automatically:
**echo "grub hold" | sudo dpkg --set-selections**
**echo "grub-common hold" | sudo dpkg --set-selections**

14. Reboot

As much as I have tried to make this guide complete it seems to not work for some people and anyhelp I can get in making this guide complete is much appreciated. Namely Raid 1 issues.
**Step 10** *problems* arise when you don't specify the correct device for (hd0)
BIOS boot order can also affect this step so make sure it's correct
In some extreme cases it's necessary to remove other hard drives from the sys as some cheap motherboards lack the understanding of fakeraid and tell grub IDE devices boot first. Thus effectively installing grub to the wrong disk in some cases.

---

### Post by ashakeandfrys on 2009-12-21
Thanks! Finally a guide that has all the steps listed in one location. The last time I did this I had to span a handful of websites to get all the information.

---

### Post by danwood76 on 2009-12-21
Hi Gilson,

Why dont you add the karmic entry to the wiki community docs?

---

### Post by gilson585 on 2009-12-21
Thanks for the suggestion danwood, I will as soon as I get a lil more feedback. Probably in the next few days.

---

### Post by [Neurotic] on 2009-12-23
I'm going to be testing this out tonight/tomorrow. If this works you'll be my next best friend.

I've been fighting this all day long, its been driving me crazy.

Thanks for putting in the effort.

---

### Post by jpichie on 2009-12-23
Thanks for the post Gilson, unfortunately I get the same error as the Howto for Jaunty. I am using an Intel ICH9 FakeRaid.

On step 10

> 10. grub --no-curses ##you will now be at the grub prompt##
grub> device (hdx) /dev/mapper/nvidia_cffbdeda ##note this is the hdd not a partition
grub> find /boot/grub/stage1 ##make a note of the output it is used in the next step
grub> root (hdx,y) ##(hdx,y) where x is the drive (most likely 0) and y is the partition (first partition would be 0)
setup (hdx)
quit

I get "unspecified something something" before getting the grub prompt. And I also cannot do a find on stage 1, as I get "error: 15 file not found" even when the file is under /boot/grub ...
I would really like to get this solved soon, but I fear I may have to wait for Lucid Lynx.

---

### Post by gilson585 on 2009-12-23
I'm sorry to hear that jpichie. Can you post the output of **ls /dev/mapper**, your *device.map*, and the entire terminal session of the steps above. I'll review it and see what I can find.

---

### Post by wkulecz on 2009-12-23
> grub> device (hdx) /dev/mapper/nvidia_cffbdeda ##note this is the hdd not a partition

I suspect the device/mapper/nvidia_ field in the commads is incorrect for Intel ICH9 fake raid.  Unfortunately, I don't know the correct device name but it could be a clue to guide your googling.

--wally.

---

### Post by gilson585 on 2009-12-23
Yes that would very much so cause his problem. Although I was just using that as an example, I may have to change it to make things a lil clearer.

---

### Post by [Neurotic] on 2009-12-23
I'm attempting to run this now, and I'm hitting a bit of a snag.

I'm getting to step 8, and something seems to be going wrong when I run 'sudo apt-get install grub'

```

root@ubuntu:/# sudo apt-get purge grub2 grub-pc
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub2 is not installed, so not removed
The following packages will be REMOVED:
  grub-pc*
0 upgraded, 0 newly installed, 1 to remove and 159 not upgraded.
After this operation, 1,786kB disk space will be freed.
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 116539 files and directories currently installed.)
Removing grub-pc ...
Purging configuration files for grub-pc ...
Processing triggers for man-db ...
root@ubuntu:/# sudo apt-get install grub
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  grub-doc mdadm
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 0 to remove and 159 not upgraded.
Need to get 903kB of archives.
After this operation, 1,974kB of additional disk space will be used.
Get:1 http://au.archive.ubuntu.com karmic/main grub 0.97-29ubuntu59 [903kB]
Fetched 903kB in 4s (183kB/s)
Preconfiguring packages ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Selecting previously deselected package grub.
(Reading database ... 116356 files and directories currently installed.)
Unpacking grub (from .../grub_0.97-29ubuntu59_amd64.deb) ...
Processing triggers for man-db ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up grub (0.97-29ubuntu59) ...

```

If I then go to /boot/grub, there is nothing in there:
```

root@ubuntu:/boot# cd grub
root@ubuntu:/boot/grub# ls
root@ubuntu:/boot/grub# 

```

Which makes me believe that something has gone wrong installing grub. Do I need to install dmraid or something when I'm under chroot?

Another quick question - Should step 9 read:
```
sudo chmod 777 /boot/grub/device.map
```
Since we're still under chroot? (or could it just be 'nano /boot/grub/device.map' without any change to the permissions?)

Either way, thanks for the help. I think my problem may lie in something going wrong with installing grub.  I will continue my investigation, but appreciate any advise you may have.

---

### Post by [Neurotic] on 2009-12-23
Okay, I'm getting somewhere.

It seems the steps that are missing are after 'sudo apt-get install grub', you also need to run:

```

sudo update-grub

```

While will create the menu.list

I'm not as familiar with grub, but it seem you also need to run:

```

grub-install /dev/mapper/nvidia_dhfedfae5

```

Which looks like it will fail, but will generate the device.map for you to edit.

Although I'm a little hazy on whether that should be aimed at the partition or the hdd itself. (i.e. remove the '5' at the end).

---

### Post by [Neurotic] on 2009-12-23
So still a little stuck... 

I can't seem to get grub-install to run correctly, so that stage1 & stage2 files get written to /boot/grub (and so that 'find /grub/boot/stage1' works from within the grub console).

I've updated my device.map to be the follwing configuration:
```

root@ubuntu:/boot/grub# cat device.map
(fd0)	/dev/fd0
(hd0)	/dev/mapper/nvidia_dhfedfae #was /dev/sda
(hd1)	/dev/sdb

```

Which looks to be correct.

If I attemt to run grub-install, I get:
```

root@ubuntu:/boot/grub# grub-install /dev/mapper/nvidia_dhfedfae
/dev/mapper/nvidia_dhfedfae does not have any corresponding BIOS drive.

```

I've tried running the code above against the partitions, but also get the same error :(

Is there a different commnd I should be running, or should I be doing this all through the grub console?

---

### Post by [Neurotic] on 2009-12-23
I got it to work ;o)

(Just documenting my process).

I went back to the original [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto#Install%20the%20Bootloader%20Package") guide

And realised you couldn't do a grub-install. So instead, copied over the files from cp /usr/lib/grub/<your-cpu-arch>-pc/

From there I could run through the grub console section perfectly.

The only change I needed to make was in my menu.lst, it had set up Ubuntu under (hd0,0), when in fact, it is (hd0,4).  Easy enough to fix.

Thanks for putting this post up, without it, there is no way I would have been able to do this on my own.

---

### Post by ashakeandfrys on 2009-12-24
Grub install worked for me. But as long as it works for you, that's all that matters. Interesting how different methods lead to the same result.

---

### Post by [Neurotic] on 2009-12-24
Yup too true.

Maybe in the final guide it should have the steps for using grub-install, and then if that fails, use the copy method instead.

---

### Post by DavidEllis2 on 2009-12-24
I'm still confused, probably because I'm extremely new to Linux. Steps 1 through 6 worked without a flaw. Steps 7 and 8 seemed to have a very similar problem as that posted by Neurotic. The deinstall included error "Can not write log, openpty() failed (/dev/pts not mounted?)" but otherwise seemed to have worked. The install gave the same error.
```
root@ubuntu:/# sudo apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  grub-doc mdadm
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 0 to remove and 159 not upgraded.
Need to get 407kB of archives.
After this operation, 946kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com karmic/main grub 0.97-29ubuntu59 [407kB]
Fetched 407kB in 1s (358kB/s)
Preconfiguring packages ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Selecting previously deselected package grub.
(Reading database ... 116959 files and directories currently installed.)
Unpacking grub (from .../grub_0.97-29ubuntu59_i386.deb) ...
Processing triggers for man-db ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up grub (0.97-29ubuntu59) ...

root@ubuntu:/# 

```There is nothing in /mnt - its an empty directory. Hence commands at step 9 are not working.

Is the missing /dev/pts only an error concerning in writing the log that can be ignored or is it symptomatic of why grub did not install?

Neurotic says to copy the GRUB files from /usr/lib/grub/<your-cpu-arch>-pc/. Do they have to go into /boot/grub or /mnt/root/boot/grub? Sorry to ask the obvious but my UNIX background is limited and also 20 years out of date.

---

### Post by [Neurotic] on 2009-12-24
I just did re-install using the above steps (Alienware m17x), and found the following:

After you have installed grub, do a 'sudo update-grub' as per usual.

This will give you your menu.lst.

I didn't need to set a device map, so don't worry about editing it (and the path on tht step should be /boot/grub/, not /mnt/root/boot/grub, chroot sets /mnt/root/ as your root when you invoke it)

From the, copy the files from '/usr/lib/grub/<your-cpu-arch>-pc/' to /boot/grub

This will give you the stage1 and stge2 files, and some other pieces that are neccesary.

Once you have done that, then you can call the grub console (grub), and continue as per the walkthrough describes.

I've done this install twice now on my machine, and it has worked like a charm.

---

### Post by DavidEllis2 on 2009-12-24
Well I ended up with an unbootable system! (No real problem as it is easily restored - hence this posting.)

I decided to try copying the Grub files into /boot/grub as that seemed the most logical. I then proceeded. First oddity I noticed was that device.map had four hard drives showing (hd0 to hd3). This system has four physical disks but the first two are the SATA fakeraid set so I would have expected to see only three entries in device.map. I looked at the system with gparted and it only showed the single SATA fakeraid set - i.e. only one hard drive. The fact that the last two are missing is not a problem at this point. They are two old SCSI disks and I do not need to worry about them or the SCSI controller at this time.

Anyway, I modified the device.map so that hd0 was identified according to what I saw in gparted. (That was also in agreement with what I saw with ls /dev/mapper so I figured hd0 was correct.) I ran the "update-grub" and "grub-install" commands posted by Neurotic a little earlier. Then I proceeded onto step 10 from the initial post in this thread. That seemed to work but with the following surprise. I setup "device (hd0)" as that is what was configured in device.map. Then "find /boot/grub/stage1" came back with (hd1, 7). The partition is correct but I was expecting to see hd0 as that is the configured device. Not being sure what to do I tried doing a "root (hd1,7)" and "setup (hd1)". 

Step 13 just gave an error but that is not critical at this point.

When I rebooted, the BIOS found Grub OK but GRUB was unable to find the Linux system to boot. All I got was the Grub menu and a file not found message.

The foregoing looks to me like the Grub is not correctly recognising the fakeraid. Ubuntu seems to interpret it correctly. Any ideas would be welcome.

---

### Post by [Neurotic] on 2009-12-24
What's the exact error that grub is returning to you when it attempts to load?

Also, can you post your menu.lst?

I know that when I did my install, the menu.lst that was generated wasn't correct, and I had to adjust where the root () calls where going to, as they were wrong.

---

### Post by DavidEllis2 on 2009-12-26
> What's the exact error that grub is returning to you when it attempts to load?I had posted a lengthy response earlier today but as I have since resolved the problem I have "edited" this reply to remove that post and replace it with "what went wrong". Put simply, I had not noticed and had overlooked your earlier comment about fixing the partition in menu.lst - in my case GRUB was looking at the wrong partition for vmlinuz.

Summary of what I ended up doing:

Follow steps 1 through 8 from the initial posting. (I ignored the errors about not being able to create the log files in steps 7 and 8.)

Then "sudo update-grub" as suggested by Neurotic. After that my attempt to get "grub-install" to work failed and, as suggested by Neurotic I just copied the files over.

Then step 9 required the edit to device.map being careful to remove references to the RAID disks as individual disks. i.e. My initial device map included four physical drives, each of which is found in /dev/ as an "sd" device. The first two of these are in fact the RAID discs which are found in /dev/mapper/. Hence I replaced (hd0) with the /dev/mapper/ value and deleted (hd1) which was the second disk in the RAID set leaving only the other two non-RAID disks.

Then in step 10, GRUB "find" command returned _**both**_ (hd0,7) and (hd1,7) - my system is installed in partition 7. I set root to (hd0,7) and setup GRUB on hd0. (_NOTE:_ If I set "root" to (hd1,7) GRUB setup failed saying it could not find the partition. This still looks to me as though GRUB doesn't understand fakeraid correctly)

Finally I had to edit menu.lst to change the vmlinuz partion from 0 to 7 and, in my case, to add in the section to dual boot to Windows ntldr.


I still am unable to lock down GRUB from updating and would welcome any explanantion:

```
root@ubuntu:/# echo "grub-hold" | sudo dpkg -set-selections
dpkg: conflicting actions -e (--control) and -s (--status)

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !

```

---

### Post by cgb223 on 2009-12-28
Wait if you can mount the entire install and login couldn't you theoretically cd into the /bin folder where the apt-get command is (at least I think that's where it is) and via the apt-get just install grub from there and remove grub2? That might work let me know what you think. (I'm probably wrong lol)

---

### Post by DavidEllis2 on 2009-12-28
A last and quick follow up to my problems with the command to stop GRUB updating (posting a little earlier). "set-selections" option requires two "--", not one. Also don't just copy and paste the command from the instructions at the beginning of this thread - they come across using 'smart quotes' which do not work. I think the original post was in correct but the HTML rendering in the forum has changed the visual appearance.

---

### Post by panton41 on 2009-12-28
I've followed the directions, but I'm running into a couple problems that I think might be keeping my install from working.

For starters I installed with the network cable plugged in and the installer figured out all the problems and installed grub instead of grub2, but not the boot loader. I followed the directions from an external hard disk and this is where I think I run into the problem. The command "find /boot/grub/stage1" returns (hd2,0) which I'm thinking is actually the external hard disk rather than the internal disk's identity, and commanding it to use (hd0,4) which is my best guess of where the Ubuntu installation is returns "Error 18: Selected cylinder exceeds maximum supported by BIOS". (It's a dual boot with Windows 7 with uses sets up three partitions by default, then the extended partition being #4 and Ubuntu set onto #5, and since grub starts at 0 it becomes Ubuntu becomes 4.) I'd try it from the live disk except it uses nVidia graphics and there's severe corruption without the official driver.

This is a fairly new computer, but it's a laptop and I'm wondering if the BIOS (actually EFI) is hurt by the fact that a couple years ago when it was made there weren't (and still aren't) terabyte laptop drives and perhaps the BIOS can't map that large without the fakeraid and grub looks at the raw BIOS not the fakeraid cludge to make it work.

Edit: After Googling the issue it became more obvious. During boot the BIOS loads the boot loader in the MBR, which does little more than tell it where to look for the rest of the boot loader. Apparently the BIOS can't jump from the first sector to however many sectors away 465GBs is. Short of breaking the raid and reinstalling Windows onto one drive and Linux onto the other there's not much I can do to make this work. It's simply a limitation of the BIOS.

---

### Post by cedric.driard on 2010-01-02
I tried to install with this how to but I had a problem

I think it's the message : sudo: unable to resolve host ubuntu which is the problem

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

STEP 2
ubuntu@ubuntu:~$ sudo mkdir /mnt/root

STEP 3
ubuntu@ubuntu:~$ ls /dev/mapper
control                 
isw_diiebajfbe_Volume0  
isw_diiebajfbe_Volume01  
isw_diiebajfbe_Volume05 
isw_diiebajfbe_Volume06  
isw_diiebajfbe_Volume07 
isw_diiebajfbe_Volume08
isw_diiebajfbe_Volume09

STEP 4
ubuntu@ubuntu:~$ sudo mount /dev/mapper/isw_diiebajfbe_Volume07 /mnt/root

STEP 5
ubuntu@ubuntu:~$ sudo chroot /mnt/root/

STEP 6
root@ubuntu:/# sudo apt-get update
sudo: unable to resolve host ubuntu
Err http://security.ubuntu.com karmic-security Release.gpg
  Ne parvient pas à résoudre « security.ubuntu.com »
Err http://security.ubuntu.com karmic-security/main Translation-fr
  Ne parvient pas à résoudre « security.ubuntu.com »
Err http://security.ubuntu.com karmic-security/restricted Translation-fr
  Ne parvient pas à résoudre « security.ubuntu.com »
Err http://security.ubuntu.com karmic-security/universe Translation-fr
  Ne parvient pas à résoudre « security.ubuntu.com »
Err http://security.ubuntu.com karmic-security/multiverse Translation-fr
  Ne parvient pas à résoudre « security.ubuntu.com »
Err http://fr.archive.ubuntu.com karmic Release.gpg
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Err http://fr.archive.ubuntu.com karmic/main Translation-fr
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Err http://fr.archive.ubuntu.com karmic/restricted Translation-fr
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Err http://fr.archive.ubuntu.com karmic/universe Translation-fr
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Err http://fr.archive.ubuntu.com karmic/multiverse Translation-fr
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Err http://fr.archive.ubuntu.com karmic-updates Release.gpg
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Err http://fr.archive.ubuntu.com karmic-updates/main Translation-fr
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Err http://fr.archive.ubuntu.com karmic-updates/restricted Translation-fr
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Err http://fr.archive.ubuntu.com karmic-updates/universe Translation-fr
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Err http://fr.archive.ubuntu.com karmic-updates/multiverse Translation-fr
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Lecture des listes de paquets... Fait
W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-fr.bz2  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-fr.bz2  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-fr.bz2  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-fr.bz2  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-fr.bz2  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-fr.bz2  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-fr.bz2  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-fr.bz2  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg  Ne parvient pas à résoudre « security.ubuntu.com »

W: Impossible de récupérer http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-fr.bz2  Ne parvient pas à résoudre « security.ubuntu.com »

W: Impossible de récupérer http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-fr.bz2  Ne parvient pas à résoudre « security.ubuntu.com »

W: Impossible de récupérer http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-fr.bz2  Ne parvient pas à résoudre « security.ubuntu.com »

W: Impossible de récupérer http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-fr.bz2  Ne parvient pas à résoudre « security.ubuntu.com »

W: Le téléchargement de quelques fichiers d'index a échoué, ils ont été ignorés, ou les anciens ont été utilisés à la place.


STEP 7
root@ubuntu:/# sudo apt-get purge grub2 grub-pc
sudo: unable to resolve host ubuntu
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Le paquet grub2 n'est pas installé, et ne peut donc être supprimé
Le paquet grub-pc n'est pas installé, et ne peut donc être supprimé
Les paquets suivants ont été installés automatiquement et ne sont plus nécessaires :
  grub-common
Veuillez utiliser « apt-get autoremove » pour les supprimer.
0 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.


STEP 8
root@ubuntu:/# sudo apt-get install grub
sudo: unable to resolve host ubuntu
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Aucune version du paquet grub n'est disponible, mais il existe dans la base
de données. Cela signifie en général que le paquet est manquant, qu'il est devenu obsolète
ou qu'il n'est disponible que sur une autre source
E: Aucun paquet ne correspond au paquet grub
root@ubuntu:/# 

STEP 9
root@ubuntu:/# sudo chmod 777 /mnt/root/boot/grub/device.map
sudo: unable to resolve host ubuntu
chmod: ne peut accéder `/mnt/root/boot/grub/device.map': Aucun fichier ou dossier de ce type
root@ubuntu:/# sudo apt-get install grub
sudo: unable to resolve host ubuntu
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Aucune version du paquet grub n'est disponible, mais il existe dans la base
de données. Cela signifie en général que le paquet est manquant, qu'il est devenu obsolète
ou qu'il n'est disponible que sur une autre source
E: Aucun paquet ne correspond au paquet grub

root@ubuntu:/# sudo chmod 777 /mnt/root/boot/grub/device.map
sudo: unable to resolve host ubuntu
chmod: ne peut accéder `/mnt/root/boot/grub/device.map': Aucun fichier ou dossier de ce type


root@ubuntu:/# sudo update-grub
sudo: unable to resolve host ubuntu
sudo: update-grub: command not found
root@ubuntu:/# 
```so after these steps, I opened synaptics and I saw grub-pc was installed so I uninstall it and install grub with synaptic, I started again the how to and I saw approximately the same problems

after I research on internet : unable to resolve host ubuntu I applied this how to [http://www.linux-pas-a-pas.org/astuces/ubuntu/sudo-unable-to-resolve-host-ubuntu](http://www.linux-pas-a-pas.org/astuces/ubuntu/sudo-unable-to-resolve-host-ubuntu) 
and I restarted the how to install 9.10 on fakeraid. The update (sudo apt-get update) was better but the command ls /dev/mapper saw to much HD, so I think the raid is out of order

I think I have to make a new installation of ubuntu but how to don't have the same problem, If you have any idea I'm ready

If these informations can help you,
 - motherbord : asus P5QPRO
 - raid : fakeraid 1 (miror)
 - southbridge controller : ICH10R
 - HD : 2HD 500Go SATA
 - OS : WXP SP3 / maybe Ubuntu in the futur :)

---

### Post by [Neurotic] on 2010-01-02
My french is pretty poor.. but it looks like you have no access to the internet?

If you have no access to the internet, you won't be able to install packages from apt.

---

### Post by cgb223 on 2010-01-02
speaking of no internet i have hit that exact place in the process, is there a way to connect to a wireless network via iwconfig or ifconfig? the network has wpa2 personal encryption. I know the pass phrase. is this possible? if so how?

---

### Post by cedric.driard on 2010-01-03
And my English is very poor, but the connection with Internet was ok I'm sure (firefox work well and the download with synaptic was ok to)
 I'm connect with a wire (RJ45) on a network with a DHCP active so no more easily

I post a "Google translate" of the code, I'm sorry I forget I'm french but no you :lolflag:

```
To run a command as administrator (user "root"), use "sudo <command>. 
See "man sudo_root" for details. 

STEP 2 
ubuntu @ ubuntu: ~ $ sudo mkdir / mnt / root 

STEP 3 
ubuntu @ ubuntu: ~ $ ls / dev / mapper 
control 
isw_diiebajfbe_Volume0 
isw_diiebajfbe_Volume01 
isw_diiebajfbe_Volume05 
isw_diiebajfbe_Volume06 
isw_diiebajfbe_Volume07 
isw_diiebajfbe_Volume08 
isw_diiebajfbe_Volume09 

STEP 4 
ubuntu @ ubuntu: ~ $ sudo mount / dev/mapper/isw_diiebajfbe_Volume07 / mnt / root 

STEP 5 
ubuntu @ ubuntu: ~ $ sudo chroot / mnt / root / 

STEP 6 
root @ ubuntu: / # sudo apt-get update 
sudo: unable to resolve host ubuntu 
Err http://security.ubuntu.com karmic-security Release.gpg 
  Fails to resolve "security.ubuntu.com" 
Err http://security.ubuntu.com karmic-security/main Translation-fr 
  Fails to resolve "security.ubuntu.com" 
Err http://security.ubuntu.com karmic-security/restricted Translation-fr 
  Fails to resolve "security.ubuntu.com" 
Err http://security.ubuntu.com karmic-security/universe Translation-fr 
  Fails to resolve "security.ubuntu.com" 
Err http://security.ubuntu.com karmic-security/multiverse Translation-fr 
  Fails to resolve "security.ubuntu.com" 
Err http://fr.archive.ubuntu.com karmic Release.gpg 
  Fails to resolve "fr.archive.ubuntu.com" 
Err http://fr.archive.ubuntu.com karmic / main Translation-fr 
  Fails to resolve "fr.archive.ubuntu.com" 
Err http://fr.archive.ubuntu.com karmic / restricted Translation-fr 
  Fails to resolve "fr.archive.ubuntu.com" 
Err http://fr.archive.ubuntu.com karmic / universe Translation-fr 
  Fails to resolve "fr.archive.ubuntu.com" 
Err http://fr.archive.ubuntu.com karmic / multiverse Translation-fr 
  Fails to resolve "fr.archive.ubuntu.com" 
Err http://fr.archive.ubuntu.com karmic-updates Release.gpg 
  Fails to resolve "fr.archive.ubuntu.com" 
Err http://fr.archive.ubuntu.com karmic-updates/main Translation-fr 
  Fails to resolve "fr.archive.ubuntu.com" 
Err http://fr.archive.ubuntu.com karmic-updates/restricted Translation-fr 
  Fails to resolve "fr.archive.ubuntu.com" 
Err http://fr.archive.ubuntu.com karmic-updates/universe Translation-fr 
  Fails to resolve "fr.archive.ubuntu.com" 
Err http://fr.archive.ubuntu.com karmic-updates/multiverse Translation-fr 
  Fails to resolve "fr.archive.ubuntu.com" 
Reading package lists ... Made 
W: Failed to fetch http://fr.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg Fails to resolve "fr.archive.ubuntu.com" 

W: Failed to fetch http://fr.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-fr.bz2 Fails to resolve "fr.archive.ubuntu.com" 

W: Failed to fetch http://fr.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-fr.bz2 Fails to resolve "fr.archive.ubuntu.com" 

W: Failed to fetch http://fr.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-fr.bz2 Fails to resolve "fr.archive.ubuntu.com" 

W: Failed to fetch http://fr.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-fr.bz2 Fails to resolve "fr.archive.ubuntu.com" 

W: Failed to fetch http://fr.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg Fails to resolve "fr.archive.ubuntu.com" 

W: Failed to fetch http://fr.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-fr.bz2 Fails to resolve "fr.archive.ubuntu.com" 

W: Failed to fetch http://fr.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-fr.bz2 Fails to resolve "fr.archive.ubuntu.com" 

W: Failed to fetch http://fr.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-fr.bz2 Fails to resolve "fr.archive.ubuntu.com" 

W: Failed to fetch http://fr.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-fr.bz2 Fails to resolve "fr.archive.ubuntu.com" 

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg Fails to resolve "security.ubuntu.com" 

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-fr.bz2 Fails to resolve "security.ubuntu.com" 

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-fr.bz2 Fails to resolve "security.ubuntu.com" 

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-fr.bz2 Fails to resolve "security.ubuntu.com" 

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-fr.bz2 Fails to resolve "security.ubuntu.com" 

W: Downloading some index files failed, they have been ignored, or old ones used instead. 


STEP 7 
root @ ubuntu: / # sudo apt-get purge grub-pc grub2 
sudo: unable to resolve host ubuntu 
Reading package lists ... Made 
Building dependency tree 
Reading state information ... Made 
Grub2 The package is not installed, and therefore can not be deleted 
Package grub-pc is not installed, and therefore can not be deleted 
The following packages were automatically installed and are no longer necessary: 
  grub-common 
Use 'apt-get autoremove' to remove them. 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 


STEP 8 
root @ ubuntu: / # sudo apt-get install grub 
sudo: unable to resolve host ubuntu 
Reading package lists ... Made 
Building dependency tree 
Reading state information ... Made 
No version of package grub is available, but it exists in the database 
data. This usually means that the package is missing, it became obsolete 
or is only available from another source 
E: No package matches the package grub 
root @ ubuntu: / # 

STEP 9 
root @ ubuntu: / # sudo chmod 777 / mnt / root / boot / grub / device.map 
sudo: unable to resolve host ubuntu 
chmod: can not access `/ mnt / root / boot / grub / device.map ': No such file or folder of this type 
root @ ubuntu: / # sudo apt-get install grub 
sudo: unable to resolve host ubuntu 
Reading package lists ... Made 
Building dependency tree 
Reading state information ... Made 
No version of package grub is available, but it exists in the database 
data. This usually means that the package is missing, it became obsolete 
or is only available from another source 
E: No package matches the package grub 

root @ ubuntu: / # sudo chmod 777 / mnt / root / boot / grub / device.map 
sudo: unable to resolve host ubuntu 
chmod: can not access `/ mnt / root / boot / grub / device.map ': No such file or folder of this type 


root @ ubuntu: / # sudo update-grub 
sudo: unable to resolve host ubuntu 
sudo: update-grub: command not found 
root @ ubuntu: / #
```I dislike stay on an error so I try many thing (I'm a Windows user so I try and I try again) and now with a new installation (and at the question keep something mounting I say yes) ubuntu boot with a menu list without windows (I think the mbr is out of horder) and I think the raid is ok. that's a good thing !!! 

cedric@cedric-desktop:~$ sudo dmraid -s
[sudo] password for cedric: 
*** Group superset isw_diiebajfbe
--> Active Subset
name   : isw_diiebajfbe_Volume0
size   : 976767232
stride : 128
type   : mirror
status : ok
subsets: 0
devs   : 2
spares : 0

cedric@cedric-desktop:~$ sudo dmraid -r
/dev/sdb: isw, "isw_diiebajfbe", GROUP, ok, 976773166 sectors, data@ 0
/dev/sda: isw, "isw_diiebajfbe", GROUP, ok, 976773166 sectors, data@ 0
cedric@cedric-desktop:~$ ^C
cedric@cedric-desktop:~$ 

Can you say me if this response would say the mirroring is ok, the response GROUP in place of MIRROR is maybe no so good

Now I'm going to try to repair Windows mbr (I'm better in Windows) if it's possible
When I repair windows MBR, I come again with no ubuntu boot and I have the same problems when I try to do again this how to

Many thanks for your help

---

### Post by gilson585 on 2010-01-03
Thanks for the replies. I'm sorry it hasn't worked for some of you. I'd love to hear more success stories from this post. I've fixed the chmod section as it is under chroot and also fixed the grub no-update lines so its just cut and paste now. Now as for the grub prompt not working I'm not so sure why some people have problems here. grub-install never worked for me cause I had to specify device (hd0) from the grub prompt to proceed so I wrote the instructions as such. It obviously won't work if you don't substitute your device in there and mines there as an example. Also sorry I have been away for a while and haven't been around to help but glad to see it got some of you going in the right direction. [cedric.driard]("http://ubuntuforums.org/member.php?u=980096") you need to somehow get your internet working first as it won't even allow you to remove grub2 let alone install grub legacy. If it works with ethernet in windows try setting your ip address in ubuntu to mirror the one in windows. It may just be you dont have the proper drivers for your card to work at all, which I assume is the case. I advise looking elsewhere on the forums for wireless or ethernet issues. Other than that your output of dmraid states it is in good shape and the Raid1 config does indeed work. Though I suggest checking nautilus to be sure that the filesys works and is installed. Best of luck to all and any suggestions or success stories are much appreciated. Also note there are some tips for step 10 at the end of the first post now. Hope it helps.

---

### Post by gilson585 on 2010-01-03
I apologize the instructions were missing a two critical steps, *grub-install*, and *update-grub*, it has been fixed as well as some other minor changes.

---

### Post by DavidEllis2 on 2010-01-04
> **gilson585 said:**
> Thanks for the replies. I'm sorry it hasn't worked for some of you. I'd love to hear more success stories from this post. 

It worked well for me after a few minor distractions. My final result is in reply #20 in this thread. I did also fix it so that Grub didn't automatically update. I forget the precise details but it was something minor to do with permissions or "sudo". All my difficulties can be attributed to having forgotten most of the UNIX that I ever new.

Thanks very much for all the help.

---

### Post by jpichie on 2010-01-05
Does anyone know if the GRUB2 fix has been implemented into the daily builds? or if it will be in Alpha 2 of 10.04?

---

### Post by gilson585 on 2010-01-05
Not a clue but I sure am excited about it. Hope it makes it in time for release.

---

### Post by cedric.driard on 2010-01-07
The Frenchy have always a problem but this one after many installation stay the same

I think the problem is here but I didn't see any response on the forum[INDENT]root@ubuntu:/# grub-install /dev/isw_diiebajfbe_Volume0
Probing devices to guess BIOS drives. This may take a long time.
[COLOR=Red]/dev/isw_diiebajfbe_Volume0: Not found or not a block device[/COLOR].
[/INDENT]ubuntu@ubuntu:~$ ls /dev/mapper
control..............................                           isw_diiebajfbe_Volume05 ... isw_diiebajfbe_Volume08
isw_diiebajfbe_Volume0....   isw_diiebajfbe_Volume06....  isw_diiebajfbe_Volume09
isw_diiebajfbe_Volume01..  isw_diiebajfbe_Volume07

But for me I don't understand why 

the full code is here if it can help
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

**ubuntu@ubuntu:~$ sudo mkdir /mnt/root**
**ubuntu@ubuntu:~$ ls /dev/mapper**
control                            isw_diiebajfbe_Volume05  isw_diiebajfbe_Volume08
isw_diiebajfbe_Volume0    isw_diiebajfbe_Volume06  isw_diiebajfbe_Volume09
isw_diiebajfbe_Volume01  isw_diiebajfbe_Volume07

[B]ubuntu@ubuntu:~$ sudo mount /dev/mapper/isw_diiebajfbe_Volume07 /mnt/root
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/root/dev
ubuntu@ubuntu:~$ sudo mount -t proc proc /mnt/root/proc
ubuntu@ubuntu:~$ sudo mount -t sysfs sys /mnt/root/sys
ubuntu@ubuntu:~$ sudo mount -t devpts devpts /mnt/root/dev/pts
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/root/etc/resolv.conf
ubuntu@ubuntu:~$ sudo chroot /mnt/root /bin/bash
root@ubuntu:/# apt-get update[/B]
Atteint http://fr.archive.ubuntu.com karmic Release.gpg
Atteint http://fr.archive.ubuntu.com karmic/main Translation-fr                       
Atteint http://fr.archive.ubuntu.com karmic/restricted Translation-fr                  
Atteint http://fr.archive.ubuntu.com karmic/universe Translation-fr                    
Atteint http://fr.archive.ubuntu.com karmic/multiverse Translation-fr                  
Réception de : 1 http://fr.archive.ubuntu.com karmic-updates Release.gpg [189B]        
Ign http://fr.archive.ubuntu.com karmic-updates/main Translation-fr                    
Ign http://fr.archive.ubuntu.com karmic-updates/restricted Translation-fr              
Ign http://fr.archive.ubuntu.com karmic-updates/universe Translation-fr                
Ign http://fr.archive.ubuntu.com karmic-updates/multiverse Translation-fr              
Atteint http://fr.archive.ubuntu.com karmic Release                                    
Réception de : 2 http://fr.archive.ubuntu.com karmic-updates Release [44,1kB]           
Réception de : 3 http://security.ubuntu.com karmic-security Release.gpg [189B]          
Ign http://security.ubuntu.com karmic-security/main Translation-fr               
Ign http://security.ubuntu.com karmic-security/restricted Translation-fr         
Ign http://security.ubuntu.com karmic-security/universe Translation-fr           
Ign http://security.ubuntu.com karmic-security/multiverse Translation-fr         
Réception de : 4 http://security.ubuntu.com karmic-security Release [44,1kB]          
Atteint http://fr.archive.ubuntu.com karmic/main Packages                               
Atteint http://fr.archive.ubuntu.com karmic/restricted Packages
Atteint http://fr.archive.ubuntu.com karmic/main Sources
Atteint http://fr.archive.ubuntu.com karmic/restricted Sources
Atteint http://fr.archive.ubuntu.com karmic/universe Packages
Atteint http://fr.archive.ubuntu.com karmic/universe Sources
Atteint http://fr.archive.ubuntu.com karmic/multiverse Packages
Atteint http://fr.archive.ubuntu.com karmic/multiverse Sources
Réception de : 5 http://fr.archive.ubuntu.com karmic-updates/main Packages [128kB]
Réception de : 6 http://security.ubuntu.com karmic-security/main Packages [45,1kB]
Réception de : 7 http://security.ubuntu.com karmic-security/restricted Packages [14B]  
Réception de : 8 http://security.ubuntu.com karmic-security/main Sources [12,5kB]      
Réception de : 9 http://fr.archive.ubuntu.com karmic-updates/restricted Packages [14B]
Réception de : 10 http://fr.archive.ubuntu.com karmic-updates/main Sources [39,3kB]
Réception de : 11 http://security.ubuntu.com karmic-security/restricted Sources [14B]  
Réception de : 12 http://security.ubuntu.com karmic-security/universe Packages [19,3kB] 
Réception de : 13 http://fr.archive.ubuntu.com karmic-updates/restricted Sources [14B]
Réception de : 14 http://fr.archive.ubuntu.com karmic-updates/universe Packages [77,9kB]
Réception de : 15 http://fr.archive.ubuntu.com karmic-updates/universe Sources [18,8kB] 
Réception de : 16 http://fr.archive.ubuntu.com karmic-updates/multiverse Packages [6 942B]
Réception de : 17 http://fr.archive.ubuntu.com karmic-updates/multiverse Sources [3 831B]
Réception de : 18 http://security.ubuntu.com karmic-security/universe Sources [3 367B]
Réception de : 19 http://security.ubuntu.com karmic-security/multiverse Packages [1 666B]
Réception de : 20 http://security.ubuntu.com karmic-security/multiverse Sources [575B]
446ko réceptionnés en 1s (243ko/s)                 
Lecture des listes de paquets... Fait

**root@ubuntu:/# apt-get purge grub2 grub-pc**
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Le paquet grub2 n'est pas installé, et ne peut donc être supprimé
Le paquet grub-pc n'est pas installé, et ne peut donc être supprimé
0 mis à jour, 0 nouvellement installés, 0 à enlever et 170 non mis à jour.

[B]root@ubuntu:/# rm -r /boot/grub
root@ubuntu:/# apt-get install grub[/B]
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
grub est déjà la plus récente version disponible.
0 mis à jour, 0 nouvellement installés, 0 à enlever et 170 non mis à jour.

**root@ubuntu:/# grub-install /dev/isw_diiebajfbe_Volume0**
Probing devices to guess BIOS drives. This may take a long time.
[COLOR=Red]/dev/isw_diiebajfbe_Volume0: Not found or not a block device.[/COLOR]

[B]root@ubuntu:/# chmod 777 /boot/grub/device.map
root@ubuntu:/# nano /boot/grub/device.map
root@ubuntu:/# chmod 744 /boot/grub/device.map
root@ubuntu:/# grub --no-curses[/B]
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

**grub> grub> device (hd0) /dev/mapper/isw_diiebajfbe_Volume0**
grub> device (hd0) /dev/mapper/isw_diiebajfbe_Volume0

Error 27: Unrecognized command

```my device.map before and after change if someone can confirm if it's ok to[INDENT](fd0)    /dev/fd0
(hd0)    /dev/sda     
(hd1)    /dev/sdb

(fd0)    /dev/fd0
(hd0)    /dev/isw_diiebajfbe_Volume0        

other informations
- motherbord : asus P5QPRO
 - raid : fakeraid 1 (miror)
 - southbridge controller : ICH10R
 - HD : 2HD 500Go SATA
 - OS : WXP SP3 / maybe Ubuntu in the futur 

[/INDENT]If someone have any idea !
thanks

---

### Post by gilson585 on 2010-01-07
I've read somewhere that the ICH10R chipset and its built-in raid is somewhat flaky in linux. Not sure why it had worked in 9.04 but not 9.10 in your case. I'm gonna take a wild guess here but I would like to believe dmraid can't make sense out of the metadata defining your array. The only way to prove that would be start the array from scratch. I'm sure you dont want to backup all your data and try that just to get linux, I don't blame you. Maybe wait a lil while longer for 10.04 and see if that works for you. It may also be that the command used for device is not english on your sys try typing help at the GRUB CMD line.

---

### Post by cedric.driard on 2010-01-08
I tried to install ubuntu since now 2 years (with others problems at starting ;)), and I really want to use linux

So I would like to try a other method[INDENT]- at the install with the live CD after partitionning HD there is a advance menu where I can choose[INDENT]"install boot" on dev/isw_diie..... my raid controleur is detected
"install boot" on dev/sda
"install boot" on dev/sdb
[/INDENT]- if someone have an other idea with no scratch
- with the tuto [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) as like 9.04
[/INDENT]If there is no solution with that, I will be happy to contribute to Linux community (and not only ask questions), I will be ok to scratch all my data (the weather will no be good this week end so I will just have to play snow with my soon), my backup is nearly ok and since I maked a new installation of WXP 2 weeks ago and I didn't take time to install all programs

But to do this, I would like someone say me what to do precisely in simply english word because I speak well in Windows but not in Linux neither in english however I will better after


Trying is the better way to learn

---

### Post by [Neurotic] on 2010-01-08
cedric - if you see my previous replies, you can see that I've run into a similar issue, as grub-install didn't work with my system either. With an update-grub, and some copying of default grub files, it worked perfectly. I didn't have to bother messing around with the device.map.  Check out my previous responss for more details.

(This should probably be added to the walkthrough if grub-install fails).

---

### Post by gilson585 on 2010-01-08
Before you go and remove everything I want you to look at this [http://grub.enbug.org/MirroringRAID?highlight=%28raid%29]("http://grub.enbug.org/MirroringRAID?highlight=%28raid%29") now after following my instructions up to step 8 you should try to follow whats in that link. It just may be that me and eveyone else here using raid 0 are fine but raid 1 requires a diff way to do things. Don't leave out step 13 though. Lemme know what happens.

---

### Post by cedric.driard on 2010-01-10
[SIZE=3]_**First test**_[/SIZE]
- at the install with the live CD after partitionning HD there is a advance menu where I can choose :[INDENT]"install boot" on dev/isw_diiebajfbe_Volume0 # this is my raid controleur
"install boot" on dev/sda
"install boot" on dev/sdb
[/INDENT]With this installation on dev/isw_diiebajfbe_Volume0 ubuntu can boot with a menu list but without a Windows choice

In Ubuntu I can see (I put many things, because I don't now what can I put to be sure the system is ok in raid1) :[INDENT]1. Grub2 is not install but grub 0.97 is install instead
2. In the files navigator program, I see only 1 HDD
3. cedric@cedric-desktop:~$ ls /dev/mapper[INDENT]control                  isw_diiebajfbe_Volume05  isw_diiebajfbe_Volume08
isw_diiebajfbe_Volume0   isw_diiebajfbe_Volume06  isw_diiebajfbe_Volume09
isw_diiebajfbe_Volume01  isw_diiebajfbe_Volume07
[/INDENT]4. cedric@cedric-desktop:~$ sudo dmraid -s[INDENT]*** Group superset isw_diiebajfbe
--> Active Subset
name   : isw_diiebajfbe_Volume0
size   : 976767232
stride : 128
type   : mirror
status : ok
subsets: 0
devs   : 2
spares : 0
[/INDENT]5. cedric@cedric-desktop:~$ sudo dmraid -r[INDENT]/dev/sdb: isw, "isw_diiebajfbe", GROUP, ok, 976773166 sectors, data@ 0
/dev/sda: isw, "isw_diiebajfbe", GROUP, ok, 976773166 sectors, data@ 0
[/INDENT]6. grub> find /boot/grub/stage1[INDENT] (hd0,6)
 (hd1,6)
[/INDENT]7. cedric@cedric-desktop:~$ sudo gedit /boot/grub/device.map[INDENT](fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb
[/INDENT][/INDENT]Do you think a can make a test after this installation (for example do this how to, or test if [COLOR=Red]/dev/isw_diiebajfbe_Volume0: Not found or not a block device[/COLOR]. is already down or disconnect 1HD to see if the system is ready to boot and the other)

[SIZE=3][U][B]Second test Gilson585
[/B][/U][/SIZE][INDENT]I would like to be sure before testing this method, You want I do this ?[INDENT]install ubuntu
execute the step 1 to the step 8 of your How to
execute the how to [http://grub.enbug.org/MirroringRAID?highlight=%28raid%29]("http://grub.enbug.org/MirroringRAID?highlight=%28raid%29")
execute the step 13 to the step 14 of your How to (here I'm not sure)
[/INDENT][/INDENT][SIZE=3][U][B]Third test Neurotic
[/B][/U][/SIZE][INDENT]I'm not good enough in english and in linux language to try to make a similar test than you (for example I don't understand very well what is the command mount) for the moment
[/INDENT]

---

### Post by gilson585 on 2010-01-10
Are you saying you got it to work? There are ways to add windows to the grub menu it's not that big of a deal. So i'm going to ask how you got to this point. Did you just choose /dev/sda for install rather than the /dev/mapper device? Being that it's Raid 1 that kinda makes sense. My suggestion is from an older set of instructions and may not be required in 9.10 if you could just test each disk individually to assure they both work as planned in a mirrored setup that would be great. If they don't we can work on this. I'd like to add the results of this to my how-to so that other users with a mirrored setup don't run into issues. Thanks for your time and effort.

---

### Post by cedric.driard on 2010-01-10
for your first question : I have just do what is writen on my previous post

But I don't like to wait, so I try a other installation with this tuto [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) and your tuto to see differences and I think this installation work well (I have a boot with the menu.lst and windows and ubuntu work)

I will post tomorrow what I do exactly and maybe do some test if you want
rapidely, I installed with the live CD without boot sequence (as write at § 3.1.2) and I changed "/target/" to "/mnt/root/" (with a mkdir /mnt/root/ before) and changed "x86_64-pc" to "i386-pc" that all :D:D:D:D:D:D:D

My full install with this tuto [https://help.ubuntu.com/community/FakeRaidHowto#Live%20CD%20Installation%20%28Ubiquity%20graphical%20installer%29](https://help.ubuntu.com/community/FakeRaidHowto#Live%20CD%20Installation%20%28Ubiquity%20graphical%20installer%29)

[IMG]https://help.ubuntu.com/htdocs/ubuntunew/img/alert.png[/IMG] **MAKE SURE YOU BACK UP ANYTHING OF IMPORTANCE!!!** 
This Section shows you how to install Ubuntu using the Ubiquity graphical installer found on the Live CD. 


[LIST=1]
[*]Modify the bios to boot on the Live CD
[*]Begin the install process
[LIST]
[*]creat the raid partition for ubuntu.
[*]On the last step before installing, click the *Advanced options* and uncheck the install boot loader option. We will install grub (the boot loader later).
[*]After installer finishes, close ubiquity installer and reboot the machine.
[/LIST]
 
[*]Start on the Live CD where you choose use Ubuntu without any change
[*]Open a terminal
[*]Now check that you can view the partitions in the raid array with this command
[LIST=1]
[*]$ ls -l /dev/mapper/
[LIST]
[*]OUTPUT:  control             isw_beeaakeeaa_fivewe will be using the array */dev/mapper/isw_beeaakeeaa_five* in this example.
[*]We used */dev/mapper/isw_beeaakeeaa_five5* partition as Ubuntu root partition in this example.
[/LIST]
 
[/LIST]
 
[*]Install dmraid and grub in your new Ubuntu installation:
[LIST=1]
[*]$ sudo mkdir /mnt/root
[*]$ sudo mount /dev/mapper/isw_beeaakeeaa_five5 /mnt/root/
[LIST]
[*]**if this fails maybe the /target directory is already mounted** if not then some debuging will be required.
[/LIST]
 
[*]$ sudo mount --bind /dev /mnt/root/dev/
[*]$ sudo mount -t proc proc /mnt/root/proc/
[*]$ sudo mount -t sysfs sys /mnt/root/sys/
[*]$ sudo cp /etc/resolv.conf /mnt/root/etc/resolv.conf
[*]$ sudo chroot /mnt/root/
[*]# apt-get update
[*]# apt-get install -y dmraid
[*]# apt-get install -y grub
[*]# mkdir /boot/grub
[*]# cp /usr/lib/grub/i386-pc/* /boot/grub/
[*]# grub --no-curses you will now be at the grub prompt *grub>*
[LIST=1]
[*] grub> device (hd0) /dev/mapper/isw_beeaakeeaa_five
[*] grub> find /boot/grub/stage1
[LIST]
[*]OUTPUT: find /boot/grub/stage1
(hd0,4)
[/LIST]

[LIST]
[*]**make a note of the output from this command it will be needed later.** in my case I have my linux partition as the first extended partition you most likely will have different results (remember that grub starts partition numbers in zero, so partition 5 for linux is partition 4 for grub).
[/LIST]
 
[*] grub> root (hd'x','x')
[LIST]
[*]**replace 'x' with the partition number from the previous step **
[/LIST]
 
[*]Install grub on your disk (or partition if you prefer boot your computer with another boot manager)
[LIST=1]
[*] grub> setup (hd'x')
[LIST]
[*]**replace 'x' with the values gathered in the previous step **
[/LIST]
or 
[LIST]
[*]grub> setup (hd'x','x') to install grub on the partition.  
**YOU WILL NEED ANOTHER BOOT MANAGER TO START YOUR COMPUTER**
[/LIST]
 
[/LIST]
 
[*] grub> quit
[/LIST]
 
[*]# update-grub
[LIST]
[*]say yes to creating a menu.lst
[/LIST]
 
[*]now open the newly created menu list and make the following changes. Any editor can be used it is not required that you use nano # nano /boot/grub/menu.lst
[LIST=1]
[*]Change
[LIST]
[*]# groot=(hd0,0) TO # groot=(hd0,'x') 
root option in the boot entries  to root (hd0,'x') Replace the 'x' with the partition that was found earlier
[/LIST]
 
[*]Add the Windows boot entry if need be. 
  title                 Windows
  rootnoverify (hd0,0)   # use the correct partition for Windows, of course
  makeactive
  chainloader +1
[*]For all Ubuntu-related boot entries, such as 
   title         Ubuntu ...
   root          (hd0,0)
   ...change (hd0,0) to (hd'x','x') (in my case, Linux partition was not the first one, and without these changes I would get grub "Error 17" after reboot). You can use the uuid of the mapped raid partition in a grub menu.lst uuid field instead of the root (hd'x','x') field; look in /dev/disk/by-uuid with 'ls -l'.
[*]Save and exit nano. or what ever text editor you are using.
[/LIST]
 
[*]# update-grub
[/LIST]
 
[*]make sure the new install of Ubuntu loads the raid module kernel
[LIST=1]
[*]# echo dm-raid4-5 >> /etc/initramfs-tools/modules
[*]# update-initramfs -u
[*]# nano /etc/modules
[LIST]
[*]and add 'dm-raid4-5' if not exists
[/LIST]
 
[/LIST]
 
[*]Reboot
[*]Modify the bios to boot on your HDD
[*]Start and verify both Ubuntu and the existing Windows partition boot if Windows is installed.
[/LIST]

---

### Post by gilson585 on 2010-01-11
Thats great, no rush though. I may just go ahead and try it myself in Raid 1 to confirm your results. Afterwards I'll work on adding these instructions to the Ubuntu wiki. Thanks again for your input.

---

### Post by cedric.driard on 2010-01-12
No problem, I'm very happy to had contibuted and if you want me to do some test it's possible this week end (I'm not a home this week) 
The thing I saw which is particular is I don't have a device.map, do you think it's normal ?

So, do I have pass my test to grow up the step newbee in linux ;)

Again many thanks for your help, I'm very happy to become a linux user

---

### Post by phillw on 2010-01-12
> **jpichie said:**
> Does anyone know if the GRUB2 fix has been implemented into the daily builds? or if it will be in Alpha 2 of 10.04?


Grub v1.98 has been released for the alpha1 of 10.04 - it fixes various RAID issues.

burg is another possibilty - like grub, but spelt differently - lol
for a quick chat on burg & raid --> [http://ubuntuforums.org/showthread.php?t=1378951](http://ubuntuforums.org/showthread.php?t=1378951)

and burg in general [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)  Section 8
or [http://ubuntuforums.org/showthread.php?t=1371288](http://ubuntuforums.org/showthread.php?t=1371288)

That's as up to date information as I have it. Please feel free to pass it on !

Regards,

Phill.

---

### Post by datman on 2010-01-13
Thank you to [cedric.driard]("http://ubuntuforums.org/member.php?u=980096")!!!!

I have an Alienware M17x laptop with nvidia raid 0, dual booting Ubuntu and Win 7. After Win 7 died, I had to use the repair partition to recover it and naturally it wiped out my grub bootloader.

After a whole frustrating day trying to recover grub, your instructions worked!

---

### Post by cedric.driard on 2010-01-18
Datman, I'm happy that "my" instuctions work for you, but for Windows I thinks use the repair partition is very long, if windows doesn't boot, try to make a fixmbr (I do it many times during trying install Ubuntu in fakeraid and it worked all the time and take 5 minutes)

boot on windows CD
choice installation
F6 to install raid driver
choice R for repair
at the terminal
choice your HDD where is windows
write : fixmbr
write a new mbr, say yes :)

---

### Post by gilson585 on 2010-01-23
bump
Need more people with Raid 1 mirrored setups reporting this method works and if not we need to figure out how to make it work so this can be added to the Ubuntu fakeraid wiki.

---

### Post by glee on 2010-01-25
I am attempting a fresh 9.10 install on new Dell precision T1500 (Intel P55 fakeraid), RAID 1. 

Following Cedric.Driad's instructions (post #40, this thread), and adjusting step 12 to x86_64, everything seems as expected up to 13.2:

Unknown partition table signature
(hd1,6)

My / filesystem is indeed on the 7th partition, but it surprised me that this is reported as the second disk. I had been assuming that the '0' in 'hd0' was being used as a shorthand to refer to the raid array, rather than the disk (in this case /dev/sda). So does the reference to 'hd1' mean that during installation only partition 7 on the second disk was used?

---

### Post by gilson585 on 2010-01-26
I'm sorry but the best guess I can give is that you may have not provided the correct device for (hd0) at the Grub cmd line. I also did not realize cedric had modified his post to include steps from the Ubuntu wiki. Now I would normally go ahead and verify then add his steps to my guide and giving credit where due but I need to be up early. On top of this my server happens to be the only sys here with raid and it cannot go down during the day so I'll need to do this the following night. It provides critical functions here and no failover is in place for its absence. I know he had fought with his setup for a while. Knowing that he had a mashup of how-to's in front of him and you may be missing just one lil step that he had taken. I'm sure at one point he performed my instructions steps 7, 8, and 9 which is not part of post 40 nor can you forget my last part, blocking updates to Grub. Neurotic also commented that he was stuck until he ran update-grub and then finished installing grub. At what point I am unsure. I also tried helping cedric before he got his to work. I asked him to try some pointers from a link although I am unsure it actually helped. The information is generic and does not apply to Ubuntu specifically. It's listed in post 37. Best of luck lemme know what happens.

---

### Post by glee on 2010-01-26
Just so we're clear: Prior to the issue mentioned, I executed the following with no apparent problem: 

# grub --no-curses 
   1. grub> device (hd0) /dev/mapper/<my-raid-device-root-partition>

I did follow through with the remainder of the instructions, and grub-update(s) produced no errors, but obviously there are issues to be resolved elsewhere.

---

### Post by Objekt on 2010-02-02
> **gilson585 said:**
> I've read somewhere that the ICH10R chipset and its built-in raid is somewhat flaky in linux. Not sure why it had worked in 9.04 but not 9.10 in your case. I'm gonna take a wild guess here but I would like to believe dmraid can't make sense out of the metadata defining your array. The only way to prove that would be start the array from scratch. I'm sure you dont want to backup all your data and try that just to get linux, I don't blame you. Maybe wait a lil while longer for 10.04 and see if that works for you. It may also be that the command used for device is not english on your sys try typing help at the GRUB CMD line.

I can tell you that the ICH10R chipset is not only "flaky" in Linux, it's flaky and annoying under Windows XP.  I gave up on running a RAID 1 setup with my ICH10R not only because I couldn't figure out how to install Ubuntu 9.10 on it, but also because it was lousy under Windows XP as well.  The next time I want to run a RAID, I'll shell out the extra $200-$300 for a true, hardware-implemented RAID card.  The ICH10R's "RAID" features are perhaps an educational toy at best.

---

### Post by yosune on 2010-02-08
Hi, I'm writing this post because I'm trying to install karmic on my desktop with motherboard's fakeraid but I can't.
My configuration:
MSI Motherboard with AMD CPU
3 GB Ram
two 750 GB HD configured in RAID1 from BIOS

I've got two partitions:
the first ext3 with karmic installed
the second NTFS with some data and backups

dmraid -r output:
/dev/sdb: pdc, "pdc_gdiiejfie", mirror, ok, 1465017984 sectors, data@ 0
/dev/sda: pdc, "pdc_gdiiejfie", mirror, ok, 1465017984 sectors, data@ 0

After karmic installation the system show me grub menu, but doesn't start and show me a blinking cursor. I've tries your guide, but:

On step 7 the system reply that grub2 is not installed

On step 8 the system reply:
[B]root@ubuntu:/# grub-install /dev/mapper/pdc_gdiiejfie
expr: non-numeric argument
/dev/mapper/pdc_gdiiejfie1 does not have any corresponding BIOS drive.

[/B]So I've edit device.map file and modify with this:
(fd0)    /dev/fd0
(hd0)    /dev/mapper/pdc_gdiiejfie

but grub still doesn't install

I've tried many guides found on internet but without results.

Please help me if you can.

Thank you.

---

### Post by aesnxs on 2010-02-09
Yeah exactly the same problem. 

```
root@ubuntu:/# grub-install /dev/mapper/pdc_bbeeagcegj
Probing devices to guess BIOS drives. This may take a long time.
/dev/mapper/pdc_bbeeagcegj does not have any corresponding BIOS drive.

```

should probably start a new thread since this isn't solved.

---

### Post by hfvisser on 2010-02-10
Confirmation how to install 9.10 on a raid 1 disk

@ gilson585 Thank you for your instruction and the following threads. With these helps I confirm the succesfull multiboot installation of 9.10 and windows 7 on a  raid 1. This after 3 days of installing all kind of combinations of installations of 9.4 CD, 9.4 alternate CD, 9.10 and 9.10 alternate and W7.

My procedure:

1 I have a MSI P45 Neo 3 MB with 2 harddisc 
2 In the Bios I setup a fakeraid 1 for these 2 drives giving 40 GB of space.
3 I installed W7 in a 20 GB partition and after several reboots checked that it was working OK
4 I started the  Ubuntu 9.10 Desktop version as a life CD, This CD was downloaded today.
5 On the desktop I started the icoon Install Ubuntu
6 In the partitioning windows I specified Manual
6.1 In the Freespace under the line /dev/mapper/isw.... I added
      15 GB Ext4 mountpoint /
        4 GB swap  Note that /dev/mapeer/isw.. is show automatically, eg the raid 1 disk is recognised and treated properly in the installer 
7. I complete the installation of 9.10
8. After the reboot Grub (and not Grub2) presented itself without W7
9 In a Terminal sudo update-grub made no difference, file /boot/grub/menu/lst was not changed.
10 In a Terminal sudo gedit. With File, Open I went to map Filesystem/boot/grub.
10.1 I opened menu.lst, copied from examples the # lines for windows  to the end of the file -1 line, removed the # and filled in the partition number so :

title        Windows 95/98/NT/2000
root        (hd0,2)
makeactive
chainloader    +1

### END DEBIAN AUTOMAGIC KERNELS LIST

Note that the partition number must be the 100 MB partition not the W7 installation partition

11 after saving and reboot I can now start or Ubuntu of W7

I hope this is additional useful information. If you want further details or lists from my PC please let me know.

---

### Post by planetLars on 2010-02-12
Hello,

first: at step 7: grub2 wasn't installed, at step 8: grub was installed already


Now, at step 8 grub-install didn't work out like already mentioned by someone else. Additionally I got an "Unknown partition table signature" error.
Still, I copied the grub boot files manually as mentioned already. Then, wanting to use grub, I get the "Unknown partition table signature" error again. I guessed to edit the device.map after which I tried grub-install again. Now I get an "expr: ..." error and the "does not have any corresponding BIOS drive" error points to my Ubuntu partition 5 instead to my entire harddrive as before (no number after sil_bgacbicbfeae).

I tried grub again but I still have the "Unknown partition table signature" error and find results in "Error 15: File not found.".

My dual OS is Windows 7 which I installed first. I'm on a RAID0.

How do I get grub or any bootloader to install (even Windows one if possible)? My system defaults to boot Windows 7 immediately at the moment (or right before I tried the steps, I hope Win 7 still boots at least). I write from the Live CD. Help much appreciated.

Thank you.

---

### Post by planetLars on 2010-02-14
see [http://neosmart.net/forums/showthread.php?t=5761](http://neosmart.net/forums/showthread.php?t=5761) for a solution using NeoGrub for Multi Boot systems with a Windows installation.

---

### Post by Deihmos on 2010-02-16
I was able to install Ubuntu 9.10 to bios raid 0 on the Intel ICH10 chipset with no issues. When I installed it I got Grub Legacy and not Grub 2. Is there any way to use Grub 2 with a raid 0 config or do I have to stay with Grub Legacy?

---

### Post by planetLars on 2010-02-16
Hi, as far as I know Grub 2 doesn't work with RAID yet. That's why we have to deal with setting up Grub Legacy here in the first place! :-)

---

### Post by Deihmos on 2010-02-16
Ubuntu loads a bit slow from Raid 0. Takes almost 30 seconds until I see the boot screen.

---

### Post by Stason on 2010-02-17
> **phillw said:**
> Grub v1.98 has been released for the alpha1 of 10.04 - it fixes various RAID issues.

Sadly, I can confirm that GRUB2 still wont install on fake raid as of 10.04 Alpha 2. I had to follow the procedure to replace it with original grub as described in this thread.

---

### Post by Stason on 2010-02-17
> **aesnxs said:**
> Yeah exactly the same problem. 

```
root@ubuntu:/# grub-install /dev/mapper/pdc_bbeeagcegj
Probing devices to guess BIOS drives. This may take a long time.
/dev/mapper/pdc_bbeeagcegj does not have any corresponding BIOS drive.

```

should probably start a new thread since this isn't solved.

It is SOLVED! Use cedric.driard instructions in post #40 instead of post #1. ;)
[http://ubuntuforums.org/showpost.php?p=8643812&postcount=40](http://ubuntuforums.org/showpost.php?p=8643812&postcount=40)
Just skip part 7 if you are on 10.04 A2.

And also Run these commands to keep it from upgrading automatically:
echo "grub hold" | sudo dpkg --set-selections
echo "grub-common hold" | sudo dpkg --set-selections

---

### Post by Anhedonia on 2010-02-21
[LEFT]**This shows nothing for me, im still stuck. Ive followed every fix on the forums so far with no fix.**
**** 
 [/LEFT]
3. **ls /dev/mapper**
In this example the output would have shown "nvidia_cffbdeda, nvidia_cffbdeda1, nvidia_cffbdeda2" where nvidia_cffbdeda is the hdd. All the others listing a # on the end are the partitions. If you don't know what partition is the root of your installation check out *gparted*. I will use nvidia_cffbdeda1 in the following steps as an example for mounting and chrooting into the installation.
 
 
**Here is what happens when i try to use dmraid from liveDVD**
 
root@ubuntu:/dev# dmraid -ay
ERROR: isw device for volume "RAID" broken on /dev/sda in RAID set "isw_ccjcchchhd_RAID"
ERROR: isw: wrong # of devices in RAID set "isw_ccjcchchhd_RAID" [1/2] on /dev/sda
ERROR: isw device for volume "RAID" broken on /dev/sdb in RAID set "isw_ceebgdgjii_RAID"
ERROR: isw: wrong # of devices in RAID set "isw_ceebgdgjii_RAID" [1/2] on /dev/sdb
RAID set "isw_ccjcchchhd_RAID" was not activated
RAID set "isw_ceebgdgjii_RAID" was not activated

---

### Post by Anhedonia on 2010-02-21
I have done that, i took me 9 hours to get Vista back to an level woth taking an image. And dmraid still didnt work >.< lol.
 
I have two RAID arrays set up because i love organization. One for linux one for NTFS.
 
ICH10R chipset doesnt seem to work to well your right.
 
> **gilson585 said:**
> I've read somewhere that the ICH10R chipset and its built-in raid is somewhat flaky in linux. Not sure why it had worked in 9.04 but not 9.10 in your case. I'm gonna take a wild guess here but I would like to believe dmraid can't make sense out of the metadata defining your array. The only way to prove that would be start the array from scratch. I'm sure you dont want to backup all your data and try that just to get linux, I don't blame you. Maybe wait a lil while longer for 10.04 and see if that works for you. It may also be that the command used for device is not english on your sys try typing help at the GRUB CMD line.

---

### Post by CedricMC on 2010-02-25
I have successfully installed Ubuntu x64 9.10 (Karmic Koala) on a fakeraid 1 (mirror) volume following this thread. Thank you very much for this clear and easy How-to. In my opinion, this will work for any type of fakeraid 0, 1, 0+1, etc. Despite of this, I have some comments to do:

Introduction: use gparted to create the partitions on your fakeraid volume (I've used ext4); run the installation; on the advanced options select "No grub installation"; after installation you can begin the process.

1. No comments.

2. No comments.

3. No comments.

4. No comments.

5. No comments.

6. No comments.

7. No comments.

8. After installing legacy GRUB 0.97, you will need to copy the stage files to the /boot/grub directory. If you do not, point 10 will fail. Thus,
[B]apt-get install grub
cp /usr/lib/grub/<architecture>/stage1 /boot/grub
cp /usr/lib/grub/<architecture>/stage2 /boot/grub
cp /usr/lib/grub/<architecture>/<partition_type>_stage1_5 /boot/grub[/B]

9. Check /boot/grub/device.map. The file permissions should be 644.
**grub-install /dev/mapper/<fakeraid_volume>**

10. Don't know why, but I had to manually edit /boot/grub/menu.lst to point correctly to the booting partition.

13. Here "sudo" is not needed.
[B]echo "grub hold" | dpkg --set-selections
echo "grub-common hold" | dpkg --set-selections[/B]

14. No comments.

---

### Post by wiredsoul on 2010-03-05
I had success using OP's instructions and Neurotic's additional notes on grub-update, grub-install failure, etc.  Running Ubuntu 9.10 server on AMD 64 w/Nvidia SATA RAID controller, configured for RAID 0.

---

### Post by Kzin on 2010-03-05
I found a pretty hacker workaround.

-I ran the Ubuntu Alternate installer (regular one doesn't work with my video card)
-Got to the point where it drops out of the install due to grub2 install failure.
-Went thru steps in post one, but as installer is running, chrooting to /target
-moved my /etc/apt/sources.list to /etc/apt/sources.bak
-created new sources.list with
deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) lucid main
-apt-get update
-apt-get install grub-pc

Worked like a charm, I was able to select my nvidia raid instance instead of /dev/sd0 /dev/sd1. Secret is grub2 that comes with 9.10 is 1.97beta4 or something, lucid had 1.98 stable =)

---

### Post by jonnovision on 2010-03-07
Figure I could add some details to this thread from my travails over the wknd (started my RAID-1 install Friday night,  just minutes ago finally got it working).  Not multi-OS system here, single boot. 

Summary - grub1.98 fixes the issue(s) that spawned this thread, from my experience anyway...

(gilson585 - tx a million for your post, informative and definitely educational, your lines are inserted below where I used them)

Here's what worked for me (mb = xfx sli 750a, fakeraid 1), at least to the best that my memory serves:

- assumes you configure an internet link off your live cd/usb 

1) Create RAID-1 array via BIOS (x2 320GB SATAII drives)
2) Boot the live 9.10 CD
3) Terminal -> '**sudo dmraid -r**' and '**sudo dmraid -s**' both report the mirror looks AOK.
4) Run through installer, installed OS onto RAID-1 array
- manually created 2 partitions, swap and /
- unchecked the install boot loader via advanced options on the last screen
5) Mount your install and login**, **
Terminal,[B]
sudo mkdir /mnt/root[/B]
[B]ls /dev/mapper
[/B]In this example the output would have shown "nvidia_cffbdeda, nvidia_cffbdeda1, nvidia_cffbdeda2" where nvidia_cffbdeda is the hdd. All the others listing a # on the end are the partitions. If you don't know what partition is the root of your installation check out *gparted*. I will use nvidia_cffbdeda1 in the following steps as an example for mounting and chrooting into the installation.
**sudo mount /dev/mapper/nvidia_cffbdeda1 /mnt/root**
*If this fails use *nautilus* (*thunar* in xbuntu) to mount your Ubuntu root partition then use **mount** to find the mount location. This location will be used in place of **/mnt/root** in the following steps.
**sudo mount --bind /dev /mnt/root/dev**
**sudo mount -t proc proc /mnt/root/proc**
**sudo mount -t sysfs sys /mnt/root/sys**[B][COLOR=#000000]
[/COLOR][/B]**sudo mount -t devpts devpts /mnt/root/dev/pts**[B]
sudo cp /etc/resolv.conf /mnt/root/etc/resolv.conf[/B]
**sudo chroot /mnt/root /bin/bash**
**apt-get purge grub2 grub-pc**
[B]apt-get update
apt-get dist-upgrade
mv /etc/apt/sources.list /etc/apt/sources.bak
echo deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) lucid main > /etc/apt/sources.list
[/B](thanks Kzin)
[B]apt-get install grub-common
apt-get install grub-pc 
[/B]- select default options,  pick your RAID array for the boot device in the last screen of the setup
[B]upgrade-from-grub-legacy
[/B]6) Confirm grub version...
[B]grub-install -v
[/B](should report back 1.98)
6) Reboot
Nice to know this is/will be worked out for 10.04.  Great stuff.

---

### Post by dubsides on 2010-03-08
FINALLY got this working on an ICH7R in RAID0!   I tried to do this years ago and could never get anywhere.

I had problems because of how I set up the partitions, which led me to use a combination of this thread and the  [FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto#Live%20CD%20Installation%20%28Ubiquity%20graphical%20installer%29") starting at 8

[**IMPORTANT** - I found that all of my problems have been from trying to make too many partitions for /usr, /var, etc - there might be a way to do it but I couldn't figure out how to mount more than one partition or move files around and then be able to get anything to work; it finally worked when I just had swap, root, tmp, and home partitions]

I just want to thank all of the posters on here who added all of this content, I would have never made this work with as little experience as I've had (basically just simple kubuntu/ubuntu setups)

Sorry if I haven't followed the proper forum guidelines, first post and all that....

---

### Post by nutznboltz on 2010-04-03
> **jonnovision said:**
> 
echo deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) lucid main > /etc/apt/sources.list

You forgot to mention "apt-get update" after that.

Plus you never say what to do about the sources.list after that.

---

### Post by nutznboltz on 2010-04-04
I'm posting this to be a bit more complete near the end of the list of steps:

1) Create RAID array via BIOS (I've only tested this with RAID-1 but RAID-0 should also work)
2) Boot the live 9.10 CD
3) Terminal -> 'sudo dmraid -r' and 'sudo dmraid -s' both report the mirror looks AOK.
4) Run through installer, installed OS onto RAID-1 array
- manually created 2 partitions, swap and /
- unchecked the install boot loader via advanced options on the last screen
5) Mount your install and login,
Terminal,
[B]sudo mkdir /mnt/root
ls /dev/mapper[/B]
In this example the output would have shown "nvidia_cffbdeda, nvidia_cffbdeda1, nvidia_cffbdeda2" where nvidia_cffbdeda is the hdd. All the others listing a # on the end are the partitions. If you don't know what partition is the root of your installation check out gparted. I will use nvidia_cffbdeda1 in the following steps as an example for mounting and chrooting into the installation.
**sudo mount /dev/mapper/nvidia_cffbdeda1 /mnt/root**
*If this fails use nautilus (thunar in xbuntu) to mount your Ubuntu root partition then use mount to find the mount location. This location will be used in place of /mnt/root in the following steps.
[B]sudo mount --bind /dev /mnt/root/dev
sudo mount -t proc proc /mnt/root/proc
sudo mount -t sysfs sys /mnt/root/sys
sudo mount -t devpts devpts /mnt/root/dev/pts
sudo cp /etc/resolv.conf /mnt/root/etc/resolv.conf
sudo chroot /mnt/root /bin/bash
[/B]6) Install Grub2 from Lucid[B]
apt-get purge grub2 grub-pc
apt-get update
apt-get dist-upgrade
mv /etc/apt/sources.list /etc/apt/sources.bak
echo deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main > /etc/apt/sources.list
apt-get update
apt-get install grub-common
apt-get install grub-pc[/B]
- select default options, pick your RAID array for the boot device in the last screen of the setup
**upgrade-from-grub-legacy**
7) Confirm grub version...
**grub-install -v**
(should report back 1.98)
8) Hold packages
[B]echo "grub-common hold" | debconf-set-selections
echo "grub-pc hold" | debconf-set-selections[/B]
9) Restore sources.list
[B]mv /etc/apt/sources.list.bak /etc/apt/sources
apt-get update[/B]
10) Reboot

---

### Post by Nattereri on 2010-04-24
It worked for me with Ubuntu 9.10 server 64 bit. I have a custom modified HP Pavilion E9200Z. I had to copy the files using  cp /usr/lib/grub/<your-cpu-arch>-pc/ and ignored any error messages I recieved. Now to try gnome, didn't have luck with it in debian.

---

### Post by H.E.C. on 2010-06-25
> **nutznboltz said:**
> 8. Hold packages
**echo "grub-common hold" | debconf-set-selections**
**echo "grub-pc hold" | debconf-set-selections**
9) Restore sources.list
**mv /etc/apt/sources.list.bak /etc/apt/sources**
**apt-get update**
 
Everything worked GREAT on my ASRock ION 330 HT-BD with just following two changes / corrections:
 
8. Hold packages
**echo "grub-common hold" | dpkg --set-selections**
**echo "grub-pc hold" | dpkg --set-selections**
9) Restore sources.list
**mv /etc/apt/sources.bak /etc/apt/sources.list**
**apt-get update**
 
Thanks everyone for a great guides and all the tips - finally after several day I've got my RAID 0 working on this amazing beast - OCed to 2.1 MHz, upgraded to 4 GB RAM and added 2nd hard drive to create RAID - this RAID was stopping me to install and enjoy XBMC ... thanks again to all!

---

### Post by marketing promotion on 2012-01-16
You will have to consider aspect inside an important challenge for one from all of the most beneficial blog sites for all of the net. I actually can suggest blog.edirectories.info !

---

