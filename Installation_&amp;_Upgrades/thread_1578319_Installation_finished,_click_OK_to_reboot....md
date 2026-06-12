---
title: "Installation finished, click OK to reboot..."
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by PaulyD.uk on 2010-09-20
Hey all,
 
First post and still a bit new to Ubuntu though have played around with it a little in the past (about 5-6 years ago!)
 
Issue I'm having is trying to install ubuntu 10.04, when i get to the end and it asks you to click OK to reboot it never does, it sits there and never reboots (left for an hour!), forcing a shutdown and starting up then results in no GRUB coming up to dual boot (windows 7, installed on a seperate HDD)
 
This previously worked fine but I got rid of ubuntu to try a different flavour (which didn't install successfully, couldn't find the disk drive I wanted to install it on but I had already wiped ubuntu off for a fresh install)
 
I have formatted the partition i made (30gb partition) and manually created space for root and a partition from that for a swap file but this made no difference. I have used a partition manager and completely got rid of the partition (resizing the drive back up to full amount) and let the ubuntu installer do the partition itself but again the same problem. 
 
I'm not sure what it is doing at this stage when going to reboot, i'm guessing installing GRUB and terminating the processes for the reboot, which never completes. I have also tried installing GRUB on the partition which said "Windows 7 loader" but that made no difference. I will try fixboot and fixmbr commands in windows recovery console in case it can't overwrite the boot sector for any particular reason tonight.
 
Any help appreciated, will be able to give more information once in front of the machine tonight - just baffled as this was previously working perfectly before :confused:

---

### Post by gnush on 2010-09-20
Have you tried to dd the hard drive you want to use for Ubuntu? Since you mentioned something about a previous error with another distribution, there might be something wrong with the MBR or something like that.

```
dd if=/dev/zero of=/dev/sda bs=1M
```The above command will completely erase any data on the drive (sda in the example, change it to the proper hdd), including the MBR. **Be cautious** though, you might lose data if you select the wrong hard drive.

---

### Post by PaulyD.uk on 2010-09-20
I haven't and can't either. I should have explained my hdd setup better.
 
The previous issue was with Sabayon, it wouldn't detect my hdd at one stage but later copied the files across fine, was a bit strange. the 1tb has been tested though and is working fine (I too thought of a drive issue)
 
I have a 500gb and 1tb drive. I use the 500gb for windows and although i can nuke this drive and start afresh it won't really make a difference and i want to keep the 500gb just for windows itself.
 
The 1tb is my storage drive where i keep all my backups, music, films etc on, i partitioned off 30gb of that for ubuntu use.
 
First time I installed ubuntu I chose this disk, made a 30gb partition in the installer and everything worked fine - GRUB loaded and i had all the options for both OS.
 
I didn't have to before but last few times of loading i have tried installing GRUB on different devices but it never loads at boot. I'm more concerned that the installer halts after clicking OK and nothing is working because of this. I will be running the fixboot and fixmbr commands from windows recovery console in case something weird is going on with the MBR causing this issue.
 
Previous issue I had was a different hdd causing the problem (I think as it was part of a RAID array and was never formatted properly afterwards - have read a thread on here where someone had to do a low level format after being in a RAID array to get it recognised) which I swapped out for this 500gb in there, this problem also affected installing windows too.

---

### Post by PaulyD.uk on 2010-09-21
Solved the problem.
 
When I changed the boot priority to CD it strangely changed the boot order of my HDD's so was pointing towards my 500gb windows disk rather than the 1tb with Ubuntu on there, changed the order back and now GRUB loads and can access Ubuntu fine.
 
However selecting windows just leads me to a flashing cursor, think will just need to edit the GRUB config file to point to the right place so a bit more reading and i will get there.

Thanks for your response :)

---

### Post by mörgæs on 2010-09-21
Good, please mark the thread 'solved'.

---

### Post by wilee-nilee on 2010-09-21
> **PaulyD.uk said:**
> Hey all,
 
First post and still a bit new to Ubuntu though have played around with it a little in the past (about 5-6 years ago!)
 
Issue I'm having is trying to install ubuntu 10.04, when i get to the end and it asks you to click OK to reboot it never does, it sits there and never reboots (left for an hour!), forcing a shutdown and starting up then results in no GRUB coming up to dual boot (windows 7, installed on a seperate HDD)
 
This previously worked fine but I got rid of ubuntu to try a different flavour (which didn't install successfully, couldn't find the disk drive I wanted to install it on but I had already wiped ubuntu off for a fresh install)
 
I have formatted the partition i made (30gb partition) and manually created space for root and a partition from that for a swap file but this made no difference. I have used a partition manager and completely got rid of the partition (resizing the drive back up to full amount) and let the ubuntu installer do the partition itself but again the same problem. 
 
I'm not sure what it is doing at this stage when going to reboot, i'm guessing installing GRUB and terminating the processes for the reboot, which never completes. **I have also tried installing GRUB on the partition which said "Windows 7 loader" but that made no difference.** I will try fixboot and fixmbr commands in windows recovery console in case it can't overwrite the boot sector for any particular reason tonight.
 
Any help appreciated, will be able to give more information once in front of the machine tonight - just baffled as this was previously working perfectly before :confused:

This will cause windows to not boot for sure. Post the bootscript in my signature. When you post it in the reply window; 1st click on the # then put the text in between the code tags . Grub should never go any where but the mbr unless you know what your doing.

---

### Post by PaulyD.uk on 2010-09-21
Cheers mate.
 
I did the following last night to do the reinstall:
 
1. Formatted and resized the partiton to a single 931gb one which had all my storage files on - clean start as I done before
 
2. Did windows startup recovery which found issues with the boot settings, it reconfigured the entries itself (put in windows boot manager and another entry fo recovery console that was missing - didn't go to that and do fixboot and fixmbr though)
 
3. Did fresh install of Ubuntu, installing side-by-side like i did the first time when it worked. After clicking OK to restart it actually froze - before I could move the mouse. Gave it a few mins before forcing shutdown.
 
When it still failed to load GRUB I thought I would go back to basics and check the simple things - such as boot order for hdd's :p
 
I'm pretty sure it will just be the entry pointing towards the windows partition is wrong. I might do a fresh install again tonight after deleting the partition and running the fixboot and fixmbr commands just so i know for sure it will be as close as possible to the existing windows setup I had before. I also borked the ATI driver install (i have read these are awful and NV are recommended but changing my card really is not an option) and these now dont want to uninstall and reinstall properly, again - had no issues on first attempt.
 
On a off note I have been extremely impressed with ubuntu, linux has really moved on far from when I first used it about 5 years ago, Can see me using it a fair amount of my windows install, esp as I have been reading up on Wine today and a fair amount of the games I play can be done through that.

---

### Post by wilee-nilee on 2010-09-21
Okey dokey.;)

You might run the script for your self and just look at the windows boot, in the actual partition, and if you see grub in it, take a look at this link. It sounds like your handy enough; but just passing on the stuff that might be pertinent.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by PaulyD.uk on 2010-09-21
> **wilee-nilee said:**
> Okey dokey.;)
 
You might run the script for your self and just look at the windows boot, in the actual partition, and if you see grub in it, take a look at this link. It sounds like your handy enough; but just passing on the stuff that might be pertinent.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
 
Its all appreciated mate, I'm fairly handy with PC's all round, last dealing with linux I had was whilst studying at university and we used slackware to setup a LAMP server, however forgotten a lot of the commands etc now that were handy then. Had to look up the command on how to install a .run file last night... :oops:
 
I will get there in the end and its all fun playing around with something new. Will run the script just to have a peek and see it - one thing I like about linux is you can delve right in and have a play
 
Again, thanks for your help :)

---

### Post by PaulyD.uk on 2010-09-24
Quick update as now all resolved - might help someone else with the same problem.

All fresh installs. Installed Win 7 to 500gb and then ubuntu to 1tb. Set default boot device to 1tb, grub loads and ubuntu is fine, however windows fails to launch - flashing cursor after selection. However it seems I had a bootloader for windows 7 on both the 500gb and the 1tb. If i set the the 500gb (win 7 drive) to default boot drive then windows was fine - obviously looking towards wrong entry.

Running the boot script file from wilnee nilee's [signature]("http://bootinfoscript.sourceforge.net/")  showed the following, note the UUID:

Device details (Storage is the 1tb drive, sdb1 is the 500gb - has old raid tag on there still):

```
Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1806FF4606FF2402                       ntfs       Storage                       
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0a8e3237-6160-4a69-9b17-99b9f911c847   ext4                                     
/dev/sda6        42472b5f-616d-4441-b8f6-e55b2ef2afd7   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B0C66C4DC66C163E                       ntfs                                     
/dev/sdb                                                isw_raid_member  ]
```Checking the UUID for the boot entry in GRUB shows pointing towards the 1tb drive. I changed this to B0C66C4DC66C163E

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1806ff4606ff2402 <---------------------
    chainloader +1
```Windows now boots fine from GRUB :)

---

