---
title: "Ubuntu 16.04 (Clean Install)"
date: 2016-05-03
forum: Installation &amp; Upgrades
---

### Post by anon24 on 2016-05-03
I'm using an MSI GS70 Stealth

I had 16.04 running fine.

I installed Bumblebee and ran into getting stuck in the login menu.

I decided to do a clean install.

In doing so, I received an error: Executing 'grub-install dev/sda' failed.

I did look up this issue and someone said to make sure I was on WIFI

That ended up not being the issue because it did the same thing with WIFI

I'm using a live USB. 

I've used this drive several times and never had this issue.

I managed to use the "try Ubuntu without installing" option and that works at least.

---

### Post by Geoffrey_Arndt on 2016-05-03
It would help if you gave system specs - including video and storage (multiple ssd/hdd's??).    What OS's are on system now Win8-10, - - what does your partitioning scheme look like (use the live media to run gparted or disks and provide snapshot of what's actually installed).    Want to see what's on sda now, and how you responded to installer prompt for how to handle grub.

---

### Post by anon24 on 2016-05-03
My graphics card is NVidia GeForce GTX 970M

There is no other OS, just Ubuntu.

There are three SSD in RAID. This has never been a problem, it reads the three drives as one.

The partitioning scheme is whatever default that Ubuntu chose for my drives, I didn't do anything fancy or custom.

I will check Disks and get back to you on exact specs as far as partitions.

As far as the installer, I wasn't prompted on how to handle grub... It was going through the installation process and that error popped up.

Do you mean where I chose to install Ubuntu? It asks if you want to erase the disk or install alongside, I chose erase. That's pretty much the only prompt other than updates, choosing username & pass, and time zone.

---

### Post by mastablasta on 2016-05-04
is sda locked in any way? is it the correct disk?

also RAID is not default.

---

### Post by xubu2 on 2016-05-04
I ran into to same thing with the live install.
sda is your usb flash drive with the mini.iso, so try installing grub in sdb1 if it's a clean drive.
Worked for me.

Cheers.

---

### Post by anon24 on 2016-05-04
I have installed 15.10 twice and 16.04 twice. 

On every install it had read all three drives as one. 

I haven't done any extra partitioning or custom stuff in my installs. 

So, if that isn't default... I don't know what is.

I would try to install on "sdb", but that isn't listed as an option.

---

### Post by Bucky Ball on 2016-05-04
*Thread moved to **Installation & Upgrades**.*

---

### Post by anon24 on 2016-05-04
Here are some sceenshots of Disks:
[ATTACH=CONFIG]268854[/ATTACH][ATTACH=CONFIG]268855[/ATTACH][ATTACH=CONFIG]268856[/ATTACH][ATTACH=CONFIG]268857[/ATTACH][ATTACH=CONFIG]268858[/ATTACH]

---

### Post by anon24 on 2016-05-05
Does anyone have any ideas about this? I would like to get back up and running. I have no clue what to do.

---

### Post by ubu_dynamite on 2016-05-05
I assume this is a fakeraid setup the easiest way would be to create a boot partition on your 1TB HGST drive and install grub to that.

Other thing you could try is installing to /dev/dm-0 maybe never used fakeraid myself.
```
 grub-install /dev/dm-0
```

---

### Post by anon24 on 2016-05-05
Unfortunately, it won't let me select any drive or partition to install grub. 

That's part of the issue. 

When I go to click on any option, it won't let me click on OK. 

So, basically it's stuck there.

Is my only option to install without grub?

Also, if everyone thinks that the problem is RAID... Would it maybe fix the issue to wipe RAID and treat the three SSDs separately from here on out? I don't really care one way or the other.

Here are the partitions that it offers for me to install grub onto:

---

### Post by ubu_dynamite on 2016-05-06
You cant select "/dev/mapper/isw_bbaihhhjf_MSI_RAID" ?
That one should be linked to "/dev/dm-0"

---

### Post by anon24 on 2016-05-06
Nope, I literally selected every option listed and when I would click ok... Nothing happened.

---

### Post by oldfred on 2016-05-06
the only correct option is 
/dev/mapper/isw_bbaihhhjf_MSI_RAID

You can install from Live installer manually by mounting RAID partition with install and installing. If you have a separate /boot you have to mount it also.

 [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
"fakeRaid" with nVidia, note p1 is partition, without p1 is root of RAID volume
My example uses p1, which I just changed to 1 since it looks like you use just 1 not p1.

sudo mount /dev/mapper/isw_bbaihhhjf_MSI_RAID1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_bbaihhhjf_MSI_RAID

---

### Post by anon24 on 2016-05-06
When and where do I input this code? 

A) Do I select the install without grub, then input the code into terminal once Ubuntu is installed?

B) Do I do it during the install?

C) Or do I do it when "trying Ubuntu"?

---

### Post by oldfred on 2016-05-06
If you cannot get grub to install correctly during install.
Then you need to use live installer and terminal mode to mount / (root) partition ( and /boot if separate or any other system partitions if separate) and install grub.

---

### Post by ubu_dynamite on 2016-05-06
Think there is a typo in the grub-install command shouldn,t
```
 sudo grub-install --root-directory=/mnt /dev/mapper/dev/mapper/isw_bbaihhhjf_MSI_RAID
```
be
```
 sudo grub-install --root-directory=/mnt /dev/mapper/isw_bbaihhhjf_MSI_RAID
```

---

### Post by anon24 on 2016-05-06
First off, when you say, "[L]ive [I]nstaller"...

Are you referring to holding -Shift- while powering up to access the USB drive and select the option: *Install Ubuntu*?


When, in the process of turning on my PC, do I access Terminal Mode?

A) As soon as the PC powers up.

B) After selecting *Install Ubuntu* on USB. / During the initial stage of installation process.

C) Only after having received the Grub error.


How do I access "[T]erminal [M]ode"?

---

### Post by oldfred on 2016-05-06
Correct entry.
Thanks ubu_dynamite for seeing typo. I copied it into an example incorrectly.

Instead of install, you choose the option to try Ubuntu.
Then from a working live installer, you can use terminal.

       Get a terminal by <ctrl_+alt+F1> & back to gui with ctrl alt f7
[https://help.ubuntu.com/community/UsingTheTerminal/](https://help.ubuntu.com/community/UsingTheTerminal/)
In Ubuntu you start a terminal window with ctrl + alt + t
or via the menu Program -- Accessories -- Terminal 
Or in dash search for terminal

---

### Post by anon24 on 2016-05-06
Ok, so what do I do after that?

Do I go ahead and double click the Install Ubuntu 16.04 LTS shortcut on the Desktop?

edit: I went ahead and tried to install after entering the code you suggested

Same issue...

I also get this error before asking if I want to unmount partitions or something?

No matter what option I select, it doesn't do anything.

Even when I click on Continue without Bootloader.

I can't even x out of it.

Literally nothing I do works, I just click and nothing happens.

---

### Post by oldfred on 2016-05-06
You have to install first, so the mount of the / partition will work.
Then manually install grub.

You can break RAID if you want, but I would be sure to back up everything first.
And you have to remove RAID meta-data from drive to fully convert to AHCI drives.

 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

### Post by anon24 on 2016-05-06
My main problem is that I can't install... What I'm saying is that the grub error is like a brick wall. 

Once it comes up, I can't do anything installation wise...

 The installation becomes stuck and no option works. 

So, I would love to install... But I can't. 

That's been the problem all along, not just that I can't install Bootloader.

You mention that there is a partition that returns the PC to factory settings?

Would that be the 1.4 GB Loop Device? 

How would I go about returning the laptop to these so called factory settings?

Maybe it would be easier to do that and then try to install Ubuntu from there?

I would kind of like to have a Windows partition anyway.

I chose to wipe Windows completely the first time.

Here is what I see when my PC powers up:

---

### Post by oldfred on 2016-05-06
Almost all systems now have the restore on the drive. So if you erased drive, just about the only way to restore Windows is from the backup you made before you erased it.
Some vendors will offer for nominal charge a DVD set to restore system. Others do not.

---

### Post by Geoffrey_Arndt on 2016-05-06
When you are doing the install - - are you selecting the "something else" option (e.g., which is a custom install) - - that will give you a prompt near the end of the install to install grub.

---

### Post by anon24 on 2016-05-07
Oldfred: I'm just trying to figure out the easiest way to get back up and running and I thought that you were saying that there was a recovery image on one of the partitions on my drive and I figured that would be the easiest way. 

Just let me know if you think of anything that I can do to solve this. I'd be happy to get Ubuntu up and running.

Geoff: I have not tried the something else feature ever. I always go through everything in a default fashion when installing. So, should I try the something else option?

---

### Post by oldfred on 2016-05-07
With multiple drives or any thing other than the standard one drive dual boot, I would never suggest auto install. Who knows what or where it is going to install.

I normally partition in advance, but with RAID you have to use RAID tools. I do not know now if gparted will work on your type of RAID or not. Too many different types of RAID and I do not understand them all.

Examples of Something else (but not RAID)
 Something Else install, but prefer larger / of 20 or 25GB. Not showing Windows
[http://www.tecmint.com/ubuntu-15-04-installation-on-uefi-firmware/](http://www.tecmint.com/ubuntu-15-04-installation-on-uefi-firmware/) 

 How To Install Ubuntu Linux Alongside Windows 10 (UEFI)
[http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html](http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html) 

      
 MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[URL="http://ubuntuforums.org/showthread.php?t=2297815"]http://ubuntuforums.org/showthread.php?t=2297815
[/URL]
 MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)
Recommended "libata.force=noncq"
[http://ubuntuforums.org/showthread.php?t=2298912](http://ubuntuforums.org/showthread.php?t=2298912) 

[URL="http://ubuntuforums.org/showthread.php?t=2297815"]
[/URL]

---

### Post by anon24 on 2016-05-07
The thing is that I'm not dual booting. I only have Ubuntu on this PC.

---

### Post by ubu_dynamite on 2016-05-07
If you just want linux on this pc i would recommend just using software raid or no raid0 at all will be safer for your data.

For the not installing maybe your install media is partly corrupt or not enough free disk space in beginning of the drives to install the bootloader?

---

### Post by anon24 on 2016-05-07
Yes, I took the drives out of RAID. I'm gonna give the install a shot after Disks deletes all of the data off of the drives.

---

### Post by anon24 on 2016-05-07
Hooray, it worked! 

I took all of my drives out of RAID, reformatted/erased everything on them and then performed the install.

The install worked flawlessly.

Thanks again, everyone!

Btw, Oldfred, I should have listened to you from the beginning and ditched the RAID.

---

### Post by oldfred on 2016-05-07
Glad you got it working.

RAID is not a backup, but is for speed. Some gamers want fast computers. And before SSD, you had to RAID hard drives to get that type of speed. But now SSD are so fast, you really do not need RAID for almost all uses. Of course there are exceptions where some still need that kind of speed.

But no matter how fast computer is, I find I cannot type any faster, so I do not get all that speed anyway.

---

### Post by anon24 on 2016-05-07
Me too, it was a pain, but I couldn't have done it without your help. 

I put all of my games on my 1TB SATA drive anyway and it runs games just fine. So, it really hasn't had any benefit for me either.

---

### Post by Geoffrey_Arndt on 2016-05-07
And I would suggest to use the "something else" install option in the future.

It doesn't matter one twit if Ubuntu is the only OS on the PC.    The custom install (aka "something else" option) is very easy, but gives you the control you need . . . . you're not installing using a magical "black box" as the auto-installers do.

---

### Post by anon24 on 2016-05-07
"Very easy" is relative. It didn't look "very easy" to me when I took a peak. There were all of these partitions that I had no clue what to do with and it was fairly intimidating.

I'm brand spanking new at most of this, so keep that in mind. If I have any issues from this install, I'll try doing the Something Else option. So far, it's working pretty well.

Thanks for your input and help throughout this!

---

