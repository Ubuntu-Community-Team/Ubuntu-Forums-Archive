---
title: "Thought I knew what I was doing...."
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by dylbud on 2010-10-25
So, I've installed Ubuntu quite a few times over the last few years, several times onto a Windows machine creating a dual boot. Every time, I just used the GUI, had no problems, and great luck.

Well, now I'm trying to install 10.04 onto my sister's Vista machine (Compaq presario) I run into a problem at the install screen that says "prepare disk space."

Now, quick side note...According to [this tutorial (click here)]("http://www.unixmen.com/linux-tutorials/973-ubuntu-1004-lucid-lynx-step-by-step-installation-for-newbies-howto"), which I found in couple of different places, the "prepare disk space" screen I mention above should provide a few different options. These are "erase and use the entire disk," and "specify partitions manually (advanced)," and one more option SHOULD show up IF you are on a windows machine, and that is the simple option to install ubuntu alongside windows.

Well, this third option is NOT showing up on the "prepare disk space" screen. Could this have anything to so with the fact that the Windows Vista operating system is suffering some serious problems? (which is why I'm trying to install ubuntu in the first place)

I tried to manually partition, but I don't really know what I'm doing. There is sda1 (which is very big) and sda2 (which is relatively small). My understanding was that I need to make the bigger one smaller so it frees up space, then make a new partition from the new space. But when I tried to "change" them, sda1 doesn't give the option to change it's size, while sda2 does. I ended up cancelling out, because I couldn't find guidance on the web.

Oh, and here is the other thing. Before it went to the "prepare disk space" screen, it said that the existing partitions were mounted, and asked if I wanted to try and unmount them before proceeding and I said yes. I didn't know if it had anything to do with it, but Windows Vista has not been about to shut down properly at all. 

So...THEN.. I started Vista in safe mode and shut it down properly. Then I tried to install ubuntu again. This time it didn't give me the message about the existing partitions being mounted. It went straight to the "prepare disk space" screen. But this time it said the computer had no operating systems on it! Like in the attached picture.

I always see people on here asking these questions, and people asking them for more detail, so I hope that all makes sense. Please feel free to ask me anything else and thanks for any help!

PS: the reason I'm doing this is I'm just trying to get my sister's computer up and running so she can do her schoolwork. But I don't want to overwrite vista, because when she finishes the term and gets more moolah she will probably upgrade to windows 7, and I'm assuming she'll still need a copy of windows vista to do the upgrade to 7.

---

### Post by Moozillaaa on 2010-10-25
I think if you choose "Manual; select partitions to install", it will show you partitioned disk space, and probably the NTFS partition as it is. Then you can install to the the empty space, maybe best as root partition, with swap space separately, and you should be ok.

If at the next step, the NTFS partition is not recognized, there could be a problem. But even then, I think only the COA sticker on bottom is necessary for upgrade, not the data itself...

---

### Post by dylbud on 2010-10-25
Thanks for the reply. Although unfortunately I don't really understand all of what you are saying. I searched the web and the forum for more detailed on manual partitioning, looking for something more step-by-step. Couldn't really find much.

For example, you are correct in that I did choose manual, and it did show me the partitions. However, it did not give me the option to change the size of the Vista partition. 

I've seen "swap" mentioned many times, and even have a vague idea of what it means, but again I'm sort of looking for more step-by-step type instructions. Is there any such detailed source of info for manually partitioning an existing Windows partition?

Like I mentioned, I'm not really a newbie to Ubuntu, but until now it's always been very easy and straightforward.

Of course there is an update to this situation, and that is that today, windows Vista appears to be functioning more or less properly, whereas yesterday it could not even start except in safe mode (go figure).

I'd still like to get ubuntu on there so my sister has a viable option for doing schoolwork when Vista inevitably fails again.

Thanks again! I will keep trying.

---

### Post by Megaptera on 2010-10-25
Have you tried shrinking Vista's partition using Vista's disk management to create free space?
Guide with screenshots:

[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

Will Ubuntu then "see" that free space at install? I'm not sure ... it did when I installed Ubuntu 10.04.

---

### Post by akand074 on 2010-10-25
Not sure why it doesn't say install along side Windows, it does on my Ubuntu 10.04 disk I downloaded from the Ubuntu website.

Any ways here is instructions about installing manually:

1. Shrink your Windows Partition (Right click and then Edit or Change. Then put the new size you want). Though I hear from some people that their windows becomes unable to boot if you do it through the Ubuntu installer sometimes. I have never had that problem, I do it through the installer all the time but if you want to be safe, boot into Windows and in the control panel theres an option to resize your partition, you can shrink it from there.
2. Next up make a new partition from the unused space equal to the amount of RAM you have (ex 4GB) and set its type as SWAP, that't all you'll need to do for that one.
3. Take all the rest of the unused space you have, Set it as EXT4, Primary, Beginning, Check the format box, and mount point as "/" without the quotations.

That's really all you need click next and let it do the install and its all done.

---

### Post by dylbud on 2010-10-25
Thanks, Megaptera -- the problem last night at least was that windows vista wasn't working at all except in safe mode. So if the windows partition editor can be accessed in safe mode, I may try that.

akand074 thanks for these instructions -- problem is, when I clicked on "change" on the windows partition in the ubuntu installer, it did not give the option to enter a new size. That field was completely missing. I've seen it before and seen screenshots of it -- the other three fields were there ("use as", "format" and "mount point") but the field to specify the new partition size was just plain missing.

However, regarding "format" -- in your instructions, would you say to check that "format" box?

Thanks again

---

### Post by Old_Grey_Wolf on 2010-10-25
Are you are using VMware to install Ubuntu as a VM? The screenshot you attached suggests that you are. If you are not intending to use VMware, then you need to stop what you are doing and find out more about her computer setup.

Your post suggests that you didn't know that VMware is running on the computer. I would suggest that you do some research at this point.

The How-To you linked to is for a dual boot. It doesn't apply to using virtualization.

VMware would have created a shell for your VM. When you created the VM shell you allocated (provisioned) cpu, memory, and a virtual disk. When you install an OS on the virtual disk created for the VM shell, the Ubuntu installer only sees the virtual disk. The Ubuntu installer is unaware of the actual hard disk architecture or partitioning. The screenshot you provided shows only the 10 GB virtual disk you provisioned for the VM shell. That as it should be. If you are indeed installing as a VM then selecting "Erase and use entire disk" should only use the 10 GB virtual disk and not affect the other partitions on you hard drive.

However, it is alway a good idea to make a backup of important files before making any significant changes to your computer. Especially if you aren't intending to use VMware.

---

### Post by akand074 on 2010-10-25
> **dylbud said:**
> Thanks, Megaptera -- the problem last night at least was that windows vista wasn't working at all except in safe mode. So if the windows partition editor can be accessed in safe mode, I may try that.

akand074 thanks for these instructions -- problem is, when I clicked on "change" on the windows partition in the ubuntu installer, it did not give the option to enter a new size. That field was completely missing. I've seen it before and seen screenshots of it -- the other three fields were there ("use as", "format" and "mount point") but the field to specify the new partition size was just plain missing.

However, regarding "format" -- in your instructions, would you say to check that "format" box?

Thanks again

Odd, there should be a new size section if I remember correctly.. I would probably burn a new ISO directly from the Ubuntu website (I'd go for [10.10]("http://www.ubuntu.com/desktop/get-ubuntu/download") if I were you, might as well it really shouldn't have any big issues but doesn't matter) Or just go into windows and shrink the partition using their partition manager, then go back to the installation and install Ubuntu in the unpartitioned space you've made. And yes format the UBUNTU partition (you'll have too) but do NOT format your Windows partition that will delete everything on your windows partition, so do NOT. But for the Ubuntu partition it needs to be an EXT partition and right now its just unallocated space so you will have to format it.

---

### Post by kansasnoob on 2010-10-25
The new ubiquity (AKA: Live Installer) is totally different. Some of us think it has flaws:

[http://ubuntuforums.org/showthread.php?t=1595807](http://ubuntuforums.org/showthread.php?t=1595807)

Going back further:

[http://ubuntuforums.org/showthread.php?t=1562714](http://ubuntuforums.org/showthread.php?t=1562714)

I even filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

And since then I brought it up at Ayatana:

[https://lists.launchpad.net/ayatana/msg03909.html](https://lists.launchpad.net/ayatana/msg03909.html)

It formatted improperly but I'm just a stupid end user/iso-tester so what do I know?

I do know that if I'm the only one complaining nothing will get improved :)

ATM I'm nearly the only one whining about the new ubiquity because devs don't read the forums.

---

### Post by efflandt on 2010-10-25
The likely problem is that gparted or other things in Linux tend to refuse to change anything on a Windows partition that they think is corrupt.  Obviously something is wrong if Vista cannot even boot itself normally, so you can understand why Linux may be afraid to touch it.

From Safe Mode have you tried going to Computer, right click on C:, click properties, and on the Tools tab, check the boxes to check the disk and fix errors (and possibly the more thorough test to check for bad sectors)?  It will tell you that it will have to do that next boot, so click OK, and reboot (that will take awhile).  When it reboots after that, see if Vista will boot normally.

For Vista or Win7 it is generally recommended (safest) to use computer management in that OS itself to shrink the Windows system partition.  So it would be a good idea to get Windows working before trying to shuffle partitions on that drive.

Ubuntu can be run from USB flash or hard drive.  But for Startup Disk Creator for bootable USB flash, you need assess to the install iso.  Or for a regular install, you need to make sure you put grub on the USB drive (for 10.04 or earlier versions the **Advanced** button in the summary screen after you configure your user, before actual installation begins.

---

### Post by dylbud on 2010-10-28
Thanks Old Gray Wolf -- The screenshot was just one I got off the web as an example of that screen in the installation sequence, sorry about the confusion there. No, I'm trying to do a dual-boot, which I've done several times before but always on an XP machine, not Vista. 

Anyway, right now after a series of extremely lenghty restarts, the machine is running correctly again (it fixed itself!) So we're putting the whole thing on hold until the end of the term, so any snafus won't occur when papers are due the next day! However, I'm showing her how to use the live CD for when Vista starts running like crappolla again :)

akand074 -- Yeah I know it was weird! There were actually two partitions labeled Vista. Sda1 which was around 200 GB, and sda2 about 10 GB. Sda2 DID have the option to enter a new size, but sda1 did not.  My gut told me not to reduce the size of sda2, and the options would allow me to increase it. I wish I had attached actual screenshots, but didn't really think about it until now.

Thanks to everyone else also for responding!

---

