---
title: "Installer not recognizing drive (Intel Smart Response Technology)"
date: 2012-07-07
forum: Installation &amp; Upgrades
---

### Post by godgough on 2012-07-07
Hi

I am trying to dual boot Lubuntu on my new Dell 15R SE along with Windows 7.  It has a 32GB cache drive that uses Intel Smart Response Technology.  I managed to partition the drive using GParted on a live usb drive.  Windows 7 is installed and I have Intel Smart Response Technology set up.  For Intel Smart Response Technology to work it needs a RAID drive.  In the BIOS the SATA Operation is: 'Intel Smart Response Technology'.  The other options are 'ATA' and 'AHCI'.  I have read that ATA will work but I would like to keep the Smart Response working.  I have tried the alternate installation disc and it prompted me that it detected a RAID drive but did not show the drive at the partitioning step.  Any ideas of how to get it working?

Thanks

---

### Post by godgough on 2012-07-08
Just a thought, can I change the SATA Operation to ATA, install ubuntu and then change back to Intel Smart Response Technology?  Will the grub installation be affected?  Will Windows or Ubuntu be affected?

---

### Post by darkod on 2012-07-08
Actually AHCI is a better choice than ATA, but if it doesn't recognize the disk(s) correctly with ISRT, when you change it back I doubt it will recognize the ubuntu installation you made.

On the other hand, the alternate installer (or the live cd too) does seem to detect that there is a type of raid, but I guess it doesn't have the drivers to understand it properly. It's not even a raid in the true meaning of the word because it combines smaller disk with a larger one, not identical disks.

These machines seem to create issues for dual boot, I'm not sure what can you do about it.

---

### Post by godgough on 2012-07-08
> **darkod said:**
> Actually AHCI is a better choice than ATA, but if it doesn't recognize the disk(s) correctly with ISRT, when you change it back I doubt it will recognize the ubuntu installation you made.

On the other hand, the alternate installer (or the live cd too) does seem to detect that there is a type of raid, but I guess it doesn't have the drivers to understand it properly. It's not even a raid in the true meaning of the word because it combines smaller disk with a larger one, not identical disks.

These machines seem to create issues for dual boot, I'm not sure what can you do about it.

Okay, thanks for your answer.  I guess I will have to wait a while for this to get supported.  The live USB will have to do for now.

---

### Post by SvenSvenson on 2012-07-12
I had the same issue. I recently bought a Lenovo ideapad u410, it has a 500GB HDD and a 32GB SSD. Intel Smart Response and Intel Rapid Storage are pre installed and configured for Windows7.

I have made it to install Ubuntu on it, but now my Windows is f#@!ed Up =)
I removed the dmraid package within the Live-System and voila, Ubuntu recognizes the HDD. But I didn't make it that GRUB2 comes up at start. I put GRUB2 at MBR of my HDD and at the start of my ext4 partition, but only the windows bootmanager comes up. Because of this pre configured Intel stuff Windows boots from the SSD, when I tried to install GRUB2 on the SSD I got various errors. (Also Gparted shows the SSD as "unallocated"). I then knew nothing of the RAID Configuration.

I started to immerse myself in the Intel Smart Respone and Intel Rapid Storage topic.
It looks like dmraid is legacy (Just google "Intel Rapid Storage Technology Dualboot" and you'll find a pdf called Intel RST in Linux* )

---

### Post by godgough on 2012-07-21
I have found a solution.

To get the Ubuntu live installer (normal version) to detect the drive, in the 'Try Ubuntu before Installing' option, open a terminal and try the commands on this page:  [https://wiki.archlinux.org/index.php/Installing_with_Fake_RAID#Load_dmraid]("https://wiki.archlinux.org/index.php/Installing_with_Fake_RAID#Load_dmraid").  I think all that is needed is 
# modprobe dm_mod
# dmraid -ay
# ls -la /dev/mapper/
Then you can open the installer in the Live session and install.

You must also go back to Windows and open the 'Intel Rapid Storage Technology' application and go to the 'Accelerate' Tab.  Disable acceleration (this will not lose any data but will automatically back up some data if you are using maximised option).  Then you should be able to restart into GRUB.  You may need to try reinstalling GRUB (Google it).  If the GRUB screen is present then you can go back to Windows and re-enable acceleration in 'Intel Rapid Storage Technology'.

Hope this works for everyone else.

---

### Post by alphageek89 on 2012-07-25
> **godgough said:**
> I have found a solution.

To get the Ubuntu live installer (normal version) to detect the drive, in the 'Try Ubuntu before Installing' option, open a terminal and try the commands on this page:  [https://wiki.archlinux.org/index.php/Installing_with_Fake_RAID#Load_dmraid]("https://wiki.archlinux.org/index.php/Installing_with_Fake_RAID#Load_dmraid").  I think all that is needed is 
# modprobe dm_mod
# dmraid -ay
# ls -la /dev/mapper/
Then you can open the installer in the Live session and install.

You must also go back to Windows and open the 'Intel Rapid Storage Technology' application and go to the 'Accelerate' Tab.  Disable acceleration (this will not lose any data but will automatically back up some data if you are using maximised option).  Then you should be able to restart into GRUB.  You may need to try reinstalling GRUB (Google it).  If the GRUB screen is present then you can go back to Windows and re-enable acceleration in 'Intel Rapid Storage Technology'.

Hope this works for everyone else.

I tried something similar.

Firstly I Disabled Acceleration from Intel RST
Secondly on BIOS i changed RAID to AHCI

Windows is still booting up correctly.

Then when I go to install Ubuntu through the Live CD after doing 
apt-get remove dmraid

I installed
```
/ on /dev/sda1 which is 8GB and
/home on /dev/sda2 which is 22 GB
```

And I tried installing the bootloader on
/dev/sdb, /dev/sdb1, /dev/sdb2 differently. After all 3 attempts GRUB doesn't show up. 

Any pointers on what is wrong.

---

### Post by oldfred on 2012-07-25
The commands to remove the RAID meta-data on a drive:

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

If you installed grub to partitions, I hope you did not install to the Windows partition. Windows NTFS partition have to have NTFS boot signatures in them. But you can use testdisk to restore from a backup if only installed once.

May be best to run BootInfo and post link:
Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by alphageek89 on 2012-07-26
> **oldfred said:**
> The commands to remove the RAID meta-data on a drive:

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

If you installed grub to partitions, I hope you did not install to the Windows partition. Windows NTFS partition have to have NTFS boot signatures in them. But you can use testdisk to restore from a backup if only installed once.

May be best to run BootInfo and post link:
Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

I got it finally working. 

The Boot repair tool did the trick :)
Here is the output from it : [http://paste.ubuntu.com/1111467/](http://paste.ubuntu.com/1111467/)

Now my machine successfully dual boots.

I think when I said I had tried installing grub on the other partitions it had failed because of UFI.

---

### Post by alphageek89 on 2012-07-26
Short summary on how I achieved dual booting my system. Thanks everyone :)

Firstly I Disabled Acceleration from Intel RST
Secondly on BIOS I changed RAID to AHCI

used the live CD to boot into ubuntu and on terminal ran
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb


I then installed 
/ on /dev/sda1 which is 8GB and
/home on /dev/sda2 which is 22 GB

Then I followed the instructions here to install grub on /dev/sda

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Now I can dual boot successfully

I will blog in detail of these steps in a weeks time on [http://vthacker.in](http://vthacker.in)

---

### Post by omicron777 on 2012-08-24
Thanks alphageek89, your solution worked for me too!

---

### Post by pequenovitor on 2012-10-18
Guys, sorry if this is just slightly off topic, but it's the most related thread I found regarding my problem, and you guys seem to know what your talking about.
 
So, mine is much simpler, I think. I got the same 15r with the 32gbSSD and 1Tb Hd. It came with a pretty mediocre Windows and a lot of extra stuff, so I decided to format and start over.
 
Got to windows installation on boot, pressed custom (as opposed to upgrade), and it didn't find any HD's or the SSD. It said it had nowhere to install. So I go to BIOS, and swtich from Intel SRT to ATA, great. Install, but now I can't go back to ISRT. Try again with AHCI, great, but then I can't go back to Intel SRT.
 
Cost a lot more money to to have the 32gb, and theoretically makes things  alot faster. I'd like to keep it and not have it as dead weight inside my brand new baby.
 
Any thoughts?
 
Appreciate it. Not sure what to do at this point.
 
Thanks,
 
Vitor

---

### Post by godgough on 2012-10-18
> **pequenovitor said:**
> Guys, sorry if this is just slightly off topic, but it's the most related thread I found regarding my problem, and you guys seem to know what your talking about.
 
So, mine is much simpler, I think. I got the same 15r with the 32gbSSD and 1Tb Hd. It came with a pretty mediocre Windows and a lot of extra stuff, so I decided to format and start over.
 
Got to windows installation on boot, pressed custom (as opposed to upgrade), and it didn't find any HD's or the SSD. It said it had nowhere to install. So I go to BIOS, and swtich from Intel SRT to ATA, great. Install, but now I can't go back to ISRT. Try again with AHCI, great, but then I can't go back to Intel SRT.
 
Cost a lot more money to to have the 32gb, and theoretically makes things  alot faster. I'd like to keep it and not have it as dead weight inside my brand new baby.
 
Any thoughts?
 
Appreciate it. Not sure what to do at this point.
 
Thanks,
 
Vitor

I had no need to change between ISRT and AHCI to install Windows or Ubuntu.  I recommend just keeping it on ISRT if you intend to use it.  I would guess you may need to wipe the partition that you want to install Windows on.  You will have to do that with a live disk of some kind.  Not sure if the Windows install disk will do that.  Here is a quick post I wrote about a new install in a different forum: [http://forum.notebookreview.com/dell-inspiron-dell-studio/668584-dell-inspiron-15r-special-edition-7520-a-41.html#post8686919](http://forum.notebookreview.com/dell-inspiron-dell-studio/668584-dell-inspiron-15r-special-edition-7520-a-41.html#post8686919)

---

### Post by EricG1793 on 2012-11-28
I know this is old, but in response to the Windows installer not recognizing the HDD, that can be solved by pressing the key to load additional drivers when prompted when initializing the Windows installer. We had to do this at work with an Envy sleekbook. I don't remember where the driver came from -- either the manufacturer or Intel. Try looking for the Intel Rapid Storage Technology driver from the manufacturer.

---

### Post by IQRules on 2013-02-02
So this U410, shipped with Raid on?
And how is the original Win 7 and recovery paritions reside?

Is this 16GB RAM capable?

---

