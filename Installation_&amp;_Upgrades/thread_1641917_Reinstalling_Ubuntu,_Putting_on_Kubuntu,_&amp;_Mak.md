---
title: "Reinstalling Ubuntu, Putting on Kubuntu, &amp; Make a Data Partion Seprate from the OSes"
date: 2010-12-09
forum: Installation &amp; Upgrades
---

### Post by corrytonapple on 2010-12-09
Hello Ubuntu Communtiy!
After having some issues with my sound not working and at this point there being no way to truly fix Pulseaudio, or get Skype to launch, and KDE not always displaying correctly, I think I might truly need a reinstall. Now I don't know, so tell me if you think this is necessary. Skype will appear in the system processes for two seconds then it gets out. I have also not found a version that works, nor the Windows version in Wine. Then Pulseaudio appears when I use the volume wheel on the front of the laptop showing the volume level, but upon it working the sound stops working, even with the commands. If there are any way to fix the two biggest problems, please tell me. As for KDE, sometimes the login Window won't display and apps crash a fair amount. Now, during the reinstall I would do the one major thing on my list. That is make a OS partion for the Ubuntu OS and applications, and a partion for Windows and applications. Then make a data partion with the rest of the space. Will this be done pretty safely or is the partionor just gonna mess the Windows OS up? Also I will be using Kubuntu 10.04 64-Bit on a USB Drive to reinstall on a Toshiba L455. It has a 250GB HDD, 4GB RAM, and a dual core 2.2GHz Intel Pentium processor.
Thanks!

---

### Post by corrytonapple on 2010-12-12
Bump. It must just be a bad time, that's all...........

---

### Post by dabl on 2010-12-12
sound/Pulseaudio
Skype
some KDE display issue
Wine performance
unnamed apps crashing
partitioning question
new Windows installation
new install on Tosh L455


Which problem are you wanting to deal with?

---

### Post by oldfred on 2010-12-12
I will present a answer a few questions.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

Some say you can share /home, but I do not recommend it. Others say you can share by having different user ids, that will work but I think it defeats the purpose of sharing. If sharing /data between Linux installs you can leave /home in / (root) and make the / install somewhat larger.

It is slightly easier to install windows first (saves reinstalling grub). It does have to be installed to a primary partition.

---

### Post by corrytonapple on 2010-12-13
> **oldfred said:**
> I will present a answer a few questions.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

Some say you can share /home, but I do not recommend it. Others say you can share by having different user ids, that will work but I think it defeats the purpose of sharing. If sharing /data between Linux installs you can leave /home in / (root) and make the / install somewhat larger.

It is slightly easier to install windows first (saves reinstalling grub). It does have to be installed to a primary partition.
I do not know what anything / means, except for /home.  I already have Windows installed, so that is OK.
> **dabl said:**
> sound/Pulseaudio
Skype
some KDE display issue
Wine performance
unnamed apps crashing
partitioning question
new Windows installation
new install on Tosh L455


Which problem are you wanting to deal with?

Well, the first three, and then #6. I don't know what you mean by new install on Toshiba L455, unless it means new Ubuntu install. Windows is fine the way it is. I would like to leave Windows untouched. Apps crashing in KDE only, and Wine is fine. I just need to update it. I will have to see if this laptop can USB boot. What other ways would it be called to USB boot in the BIOS?
Thanks for helping so far.

---

### Post by dabl on 2010-12-13
Open a terminal and

```
sudo apt-get update && sudo apt-get dist-upgrade
```

```
sudo apt-get install paman padevchooser pavucontrol
```

First, right-click the speaker icon on your panel, choose "show mixer window", and make sure the main channel is not muted.

Next, Alt-F2 "pavucontrol" with no quote marks. Start with the "Configuration" tab and set it to something appropriate for the sound system/chip that you have. I have an onboard hda Intel chip, so mine is set to "Internal Audio > Analog surround 5.1 Output + Analog Stereo Input".  The "Input Devices" tab can be a mic or line-in, as you wish.  The "Output Devices" should reflect your "configuration" choice, and the volume sliders need to be at least halfway.  Note the little mute icons -- you don't want them muted.

Finally, go to "System-Settings > Multimedia" which should open on the "Music" tab. In the right panel, you should see, as a minimum, "Pulseaudio Sound Server".  Highlight it, and click the "Test" button at the bottom of the panel. It should play the tones.  If there are other devices showing, you can test them, but probably you want the Pulseaudio Server on top of the list (use the "Prefer" and "Defer" buttons to adjust).

---

### Post by ScottyD135 on 2010-12-13
> **corrytonapple said:**
> I do not know what anything / means, except for /home.

The "/" refers to your ROOT partition.  This is where all of your OS, config, and application files (...at least I think the applications are there...) are stored.  In a default Ubuntu installation, the OS is setup to create only basic partitions, / (root) and SWAP.  

In order to create an install that is more "friendly" to someone who prefers to upgrade regularly, or who tinkers with the system but can't fix everything (...like myself), you can install a third partition with a mount point of /home.  This lets you reinstall the OS in your root partition, /, without having to reload all of your personal files.

Additionally, you could format another new partition with a mountpoint of /data that could be shared between linux installs.

I haven't experienced any of the problems you have been having and don't use KDE, so hopefully another member can weigh in on those issues.

When I have run the ubuntu partitioner from the live CD, I have never lost any data from Windows partitions, but that doesn't mean it couldn't happen.  Be sure to backup anything that's important to you.  Secondly, always delete any unnecessary files and defrag your windows drive a few times prior to running the partitioner.

Hope that helps.

---

### Post by Ganton on 2010-12-13
> Pulseaudio [...] Also I will be using Kubuntu 10.04  [...] 
It will be much better for you if you install the latest version, the 10.10.

---

### Post by corrytonapple on 2010-12-13
> **dabl said:**
> Open a terminal and

```
sudo apt-get update && sudo apt-get dist-upgrade
``````
sudo apt-get install paman padevchooser pavucontrol
```First, right-click the speaker icon on your panel, choose "show mixer window", and make sure the main channel is not muted.

Next, Alt-F2 "pavucontrol" with no quote marks. Start with the "Configuration" tab and set it to something appropriate for the sound system/chip that you have. I have an onboard hda Intel chip, so mine is set to "Internal Audio > Analog surround 5.1 Output + Analog Stereo Input".  The "Input Devices" tab can be a mic or line-in, as you wish.  The "Output Devices" should reflect your "configuration" choice, and the volume sliders need to be at least halfway.  Note the little mute icons -- you don't want them muted.

Finally, go to "System-Settings > Multimedia" which should open on the "Music" tab. In the right panel, you should see, as a minimum, "Pulseaudio Sound Server".  Highlight it, and click the "Test" button at the bottom of the panel. It should play the tones.  If there are other devices showing, you can test them, but probably you want the Pulseaudio Server on top of the list (use the "Prefer" and "Defer" buttons to adjust).
I received the error "Connection failed: Connection refused", upon the application opening. It may be because I use OSS, don't have PulseAudio installed, and upon the machine going to sleep, I need to wake the machine and type "sudo soundoff" and then "sudo soundon".  Also, I can tell by the code you guys all want me to upgrade. If I am correct, and correct me if I am wrong, when you upgrade to any version that is not a LTS, and they come up with a new version, you will only be offered to upgrade to the latest. I don't really want the newest features, and the security updates are fine. I will decide later if I will upgrade. If I can fix these issues by upgrading I will, and if we can fix these issues without reinstalling that would be great. Another issue that is quite major: When I start up and am in Windows for more than a day, I will go to start Ubuntu, and I will get a error about the drives can't mount. Then I hit "S" for Skip, but it says /tmp is not ready. I press "F" to auto fix it, and then I reboot and all is fine. I can't get a picture of it, but it would not break. :). Here is the output when I go to the Terminal and type "Skype".
```

corrytonapple@toshiba-laptop:~$ skype
skype: ../../../src/pcm/pcm_null.c:130: snd_pcm_null_start: Assertion `null->state == SND_PCM_STATE_PREPARED' failed.
Aborted
corrytonapple@toshiba-laptop:~$ 

```
It brought up the login window, I typed my password and username, and then the process closed and the Terminal output that.

---

### Post by Ganton on 2010-12-14
In the first message you said
> After having some issues with my sound not working and at this point there being no way to truly fix Pulseaudio [...] 
and later you say
> I don't really want the newest features 
but as is written in [http://www.kubuntu.org/news/10.10-release](http://www.kubuntu.org/news/10.10-release)
> Kubuntu now uses the PulseAudio sound server by default. Building on the efforts of Ubuntu over the last several release cycles, this system is now used by Kubuntu to give users enhanced configurability, flexibility and ease of use. System Settings and KMix have been updated to enhance Pulseaudio control integration
and also if you use the newest version (that comes also with Klipper running by default) you get rid of the effects of 
"MASTER Copy-Paste doesn't work if the source is closed before the paste"
[https://bugs.launchpad.net/ubuntu/+bug/11334](https://bugs.launchpad.net/ubuntu/+bug/11334)
which is really irritating.

---

### Post by corrytonapple on 2010-12-14
So I am getting I should upgrade to 10.10? Doesn't that mean that when they go to upgrade to 11.04 I will be unsupported and will need to upgrade or sit on a unsupported release with the only updates being to completely go up a version? If not, what is the point in a LTS?

---

### Post by dabl on 2010-12-14
Only _you_ can decide whether the benefits of upgrading to a newer version outweigh the (ostensible) advantages of staying with the LTS version.  The good thing about LTS is, it's really stable.  The bad thing is, you get no new software versions, with a rare exception.  So it gradually ages, and ages, and ages ...

Of course, rushing to the newer version is not always the right answer, but if the newer software does your task better, then it might be.

There's no cost to make a 10.10 Live CD, boot it, and play with it -- does audio work great?  Display OK?  Your favorite apps hold up?  In that case, you might rather install the new version and keep it for the next 18 months, rather than suffer with an LTS that doesn't do what you need it to do.

---

### Post by corrytonapple on 2010-12-15
I think I will try a Live USB on this laptop with 10.10 on it. I beta tested 10.10, late in the beta and did not find much to upgrade to. By chance, what else would a USB boot be called on a modern Toshiba laptop? Also, what do you understand from the Skype code that I don't understand? I see that something is aborting Skype from going past logining in. This was before I installed KDE and I do not remember installing anything besides updates. 
Thanks!

---

### Post by oldfred on 2010-12-15
My 3 to 4 year old Toshiba Satellite A105 just has a choice for USB Memory and it works to boot from a USB flash drive. F12 is boot options on first screen for me. I use grub2 to boot my flash drives.

---

### Post by dabl on 2010-12-15
I have tried Skype on several Linux distributions, including Kubuntu, and found it a bit "iffy", especially since I run the 64-bit OS.  It sounds like it is trying to auto-load at startup, on your system, and then crashes.

I've been running Skype on a Win 7 VM, using VMware Player, for about a year now -- it's very reliable that way, and the VM is "portable", so that cuts down the re-installation/re-configuration a lot.  Of course, a Win 7 VM is not for a marginal CPU and memory setup -- you need plenty of GHz and GB.

---

### Post by corrytonapple on 2010-12-15
Here is what I have decided to do:
[INDENT]**Kubuntu/Ubuntu and 10.04 LTS or 10.10?**
[/INDENT]
[LIST]
[*]I will go with Ubuntu 10.04 from the CD, just as I had when I first installed, then I will upgrade and possibly install XFCE and KDE later on.
[/LIST]
[INDENT][B]HDD Disc Spacing and Data Partion
[/B][/INDENT]
[LIST]
[*]I will create a 40GB System Partion for Ubuntu, 60GB partion for Windows, and 130GB (What is left over otherwise) for data.
[/LIST]
Everything else will be fixed upon reinstalling. I have all data backed up on Dropbox and Flash storage and will begin the process tomorrow morning or repartioning and then reinstalling. 
Thank you all. If I have any issues I will be reporting back to this thread. :) Have a good day.

---

### Post by corrytonapple on 2010-12-16
Upon looking around at the partitions and not knowing what to do, I am here to ask for help. I have attached a screenshot for you guys to reference to. I have my currently 53GB Ubuntu system, 64GB or whatever size it is Windows partition, a recovery partition, and a Windows Boot partition or some boot partition. Now I ask, how do I go about doing all of this. It is scary playing around with my data (Which is backed up) and system. I want to delete the old Ubuntu partition, create an extended partition with my new Ubuntu system and Windows system on the inside, and they have my other partition be data, with the other two partitions being the same. How do I go about doing this? I really need this in exact order of steps, since I do not want to take a chance. Thanks

---

### Post by dabl on 2010-12-16
Yeah, you've got a problem, because you've already used your 4 primary partitions and left unallocated space in the middle of the drive.

I'd say try to resize the extended partition to use the unallocated space -- it should work.  Then you can install Ubuntu and swap and a separate data partition in there if you want.

For future reference, it's not a great idea to leave unallocated space between partitions on a drive.  You want to "build from the left", graphically speaking, and leave unallocated space on the right end as you look at it.

I hope you didn't mean it where you wrote "... and Windows system on the inside", with regard to the extended partition.  You need to leave Windows untouched, unless there's something wrong with it.

Here's good partitioning guidance:  [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by corrytonapple on 2010-12-16
I assume I should probably delete the other Ubuntu partion then? If so, then I might as well create the data partion and Ubuntu partion together that way.
Also, that link is good. I also saw it when I searched for help in Google.

---

### Post by dabl on 2010-12-16
I would try to resize the extended partition, to include all of the unallocated space.

If that works, then I would leave the *buntu partition the same size, and simply do "format to" on it, and make it ext4.  That will have the effect of deleting the prior Ubuntu OS.

Then you can make another logical partition for your data.  All within the extended partition.

---

### Post by corrytonapple on 2010-12-17
I am about to do the install. While I am in Gparted, I see that there are three unallocated partitions, one 3.1MB, another 1.34GB, and the other 1MB. All I can do is format them, or get information on them. Upon formating them with ext2, ext3, or ext4, I get a message saying:
```

 A partition cannot have a length of -63 sectors.

```How do I get rid of this partition, make it part of another, format it, doing anything with it?
Also, is it OK that I formated my old Linux Swap partition? I assume that it will make another upon reinstall (Or I Hope; LOL)
I notice I have been spelling partition wrong. I have been spelling it P-A-R-T-I-O-N, when it is really P-A-R-T-I-T-I-O-N. I am getting bad with computer terms. :)
Thanks a lot. ;)

---

### Post by oldfred on 2010-12-17
Those are just the gaps the new formating leaves. About 10 years ago they stopped using CHS cylinders, heads, sectors and converted to LBA Large Block Allocation since drives were too large for CHS. But drives were still formated on cylinder boundaries. If  you look at older partitions layouts with WinXP or Linux before recently, you see the first partition starting at sector 63. All new layout start at sector 2048 which works better with SSD, and very large drives.

---

### Post by corrytonapple on 2010-12-17
So there is no way I can take advantage of the 1.40GB of space just floating around there? If not, will I ever get that space back?

---

### Post by corrytonapple on 2010-12-17
OK. I don't really care about it. I just went ahead and installed and I am loving what I have been missing from my Ubuntu over the past month and a half. I am upgrading and updating, installing my applications that I really want, perfecting my partitions, and formating my data partition. I am now not as scared as messing with partitions, and now can spell partitions correctly. Hopefully this won't happen again. :)
I really owe all of my thanks to you guys. As a final question, I will ask can I hide my other partitions that I need to combine with my data partitions? There is about four of them, and I do not want to see them until I but them in place.
Thanks! :) ;)

---

### Post by oldfred on 2010-12-17
Actually the best way to hide a partition is to mount it with fstab but then make the correct settings. I forget details as I do not do that.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by kwtm2 on 2011-01-27
I see that you have already repartitioned and solved your problem, but for others reading this thread, I'd like to offer my own opinion on how to (re)partition the hard drive so that you can have two different versions of Linux (e.g. newer and older versions of Ubuntu) installed, while still sharing data.  I agree with having a separately mounted "/home" partition to share data.  I have two separate installations of Kubuntu each on partitions that are 8GB each in size.  That's all you need, since all the data is on a separate partition.

The main post is here:

[http://www.linuxquestions.org/questions/ubuntu-63/running-8-04-scared-to-upgrade-help-853094/#post4233703](http://www.linuxquestions.org/questions/ubuntu-63/running-8-04-scared-to-upgrade-help-853094/#post4233703)

The above thread is for a user using one LTS who is thinking about upgrading to another LTS.

Btw, regarding whether "/home" should be shared: I myself actually do *not* share "/home" between installations; instead, each installation has a separate "/home" in which almost everything is symlinked to the data drive.  For example, "~/.mozilla" is symlinked to "/mount/shared_data_partition/symlinks/mozilla", and that *is* shared between installations.  That way, if there is anything in /home needs to have two separate versions for the two installations, that is still possible.  However, for the novice user this is too complex to explain.  You may want to try it if you are familiar with symbolic linking.

---

### Post by corrytonapple on 2011-01-27
Thanks for that input.  I will take a look at that thread later.  Though, as of now my problem is solved. :)

---

