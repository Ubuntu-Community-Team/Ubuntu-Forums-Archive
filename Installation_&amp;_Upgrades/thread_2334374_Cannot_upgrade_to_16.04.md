---
title: "Cannot upgrade to 16.04"
date: 2016-08-19
forum: Installation &amp; Upgrades
---

### Post by BlacklightHalo on 2016-08-19
I'm trying to upgrade from Kubuntu 14.04 to 16.04 and having a great deal of trouble about it.

I became aware that a new version is available via popup notification on the desktop asking me if I want to upgrade to 16.04. I tell it "yes, update." It goes through a series of processes and ultimately gives me an error message saying I don't have enough space in some part of the hard drive, and to empty my trash and clean-out temporary files from old distros with 

```
sudo apt-get clean
```

I'm pretty sure that was the command. Either way, I did everything it asked and then tried again, with the same result. Insufficient space.

I tried to burn an iso image of the new distro onto a DVD-R, thinking that it might be simpler to use this method and just wipe-out everything (including the clutter apparently keeping me from having enough disc space to do this the standard way) and just starting from scratch with 16.04. 

I completed the boot disc, then I restarted the computer, but it didn't boot from the disc. My hard drive is encrypted and has been from setup, if that makes a difference in the ability to boot from disc. In any case, neither restarting the computer nor shutting it down completely, waiting 30 seconds to make sure and then turning it back on gets it to boot from the disc. I always just get asked for my encryption password, and when I've provided it, it takes me to the standard user-login form.

I don't know how many other options I've got for how to make this happen, and it seems that what's required in order to clear-out enough space in the specific part of my hard drive that's needed for this is too technical for my level of programming knowledge (which honestly, is next to none.) Does anyone have any ideas?

---

### Post by kansasnoob on 2016-08-19
Please post the output of:

```
df -H
```

Please, do use a capital H.

---

### Post by Kenzo on 2016-08-19
If you are on 14.04 and it is performing well the don' upgrade just yet. Leave it for a few more months until the bugs in 16.04 have been fixed.  There are lots of issues reported with printers and scanners, etc

---

### Post by Impavidus on 2016-08-19
If you're happy with 14.04, you can stay with that for a while. 16.04 still has some problems, although it's generally well usable.

You mention using an encrypted system. This means you have a separate /boot partition, which is, by default, rather small. Chances are you don't have enough free disk space there, which prevents you from upgrading to 16.04. It will also prevent you from doing normal upgrades to the kernel of 14.04.

Try autoremoving old packages. If that doesn't help, manually remove old kernels using the package manager.

And of course, make sure you have good backups of all your important files before upgrading. Especially on encrypted systems.

---

### Post by grahammechanical on 2016-08-19
The failure to load a live session has no connection to the fact that the hard disk is encrypted. The motherboard will look for an operating system on the device that has the boot priority as set in the BIOS/UEFI settings utility.

If the hard drive has a higher priority than the DVD drive then the motherboard will always look to the hard drive for an OS and finding a boot loader on the hard drive it will hand over control to the boot loader. That is what is happening with your machine. At this point in the process the motherboard is ignorant of the hard drive being encrypted.

You need to give the DVD drive a higher boot priority than the hard drive if you want to re-install.

Regards

---

### Post by BlacklightHalo on 2016-08-19
```
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G  4.1k  1.9G   1% /dev
tmpfs           370M  1.3M  369M   1% /run
/dev/dm-1       488G   42G  422G   9% /
none            4.1k     0  4.1k   0% /sys/fs/cgroup
none            5.3M     0  5.3M   0% /run/lock
none            1.9G  160k  1.9G   1% /run/shm
none            105M   29k  105M   1% /run/user
/dev/sda2       248M  229M  7.0M  98% /boot
/dev/sda1       536M  3.6M  533M   1% /boot/efi
```

^That^ is the output of df -H

I will wait awhile before upgrading so that 16.04 bugs can be fixed. Thank you for that information. In the meantime, thanks grahammechanical for the information about the default boot loader. I will look into how to adjust that and then try this again with the LiveCD after a few more months.

---

### Post by Impavidus on 2016-08-19
Your /boot partition is indeed full. Try to get some free space by running```
sudo apt-get autoremove
```As things are now, you're not only unable to upgrade to 16.04; you are even unable to install kernel upgrades to 14.04. Then check with df -H whether you got more free space in /boot. If not, you'll have to clean manually.

---

### Post by kansasnoob on 2016-08-21
```
Filesystem Size Used Avail Use% Mounted on
udev 1.9G 4.1k 1.9G 1% /dev
tmpfs 370M 1.3M 369M 1% /run
/dev/dm-1 488G 42G 422G 9% /
none 4.1k 0 4.1k 0% /sys/fs/cgroup
none 5.3M 0 5.3M 0% /run/lock
none 1.9G 160k 1.9G 1% /run/shm
none 105M 29k 105M 1% /run/user
**/dev/sda2 248M 229M 7.0M [COLOR="#FF0000"]98%[/COLOR] /boot**
/dev/sda1 536M 3.6M 533M 1% /boot/efi 
```

Your /boot is 98% full so you may have to manually remove old kernels. Do you know how to do that?

---

### Post by BlacklightHalo on 2016-08-22
> **kansasnoob said:**
> ```
Filesystem Size Used Avail Use% Mounted on
udev 1.9G 4.1k 1.9G 1% /dev
tmpfs 370M 1.3M 369M 1% /run
/dev/dm-1 488G 42G 422G 9% /
none 4.1k 0 4.1k 0% /sys/fs/cgroup
none 5.3M 0 5.3M 0% /run/lock
none 1.9G 160k 1.9G 1% /run/shm
none 105M 29k 105M 1% /run/user
**/dev/sda2 248M 229M 7.0M [COLOR=#FF0000]98%[/COLOR] /boot**
/dev/sda1 536M 3.6M 533M 1% /boot/efi 
```

Your /boot is 98% full so you may have to manually remove old kernels. Do you know how to do that?

I do not. I was under the impression that when a new version of Ubuntu is installed, the old kernel was simply replaced. Why would this not be the case? Will sudo apt-get autoremove just remove un-needed things? Is there a potential risk involved with using this command?

---

### Post by kansasnoob on 2016-08-22
> **BlacklightHalo said:**
> I do not. I was under the impression that when a new version of Ubuntu is installed, the old kernel was simply replaced. Why would this not be the case? Will sudo apt-get autoremove just remove un-needed things? Is there a potential risk involved with using this command?

At 98% full there is not enough space to facilitate the upgrade. It's all because of this bug:

[https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1357093)

You may find that you're not even updated to the latest Trusty kernel. 

They condensed some of the info here:

[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)

---

### Post by BlacklightHalo on 2016-08-22
I just did their recommended "sudo apt-get autoremove --purge" command, and it seems to have worked. To all appearances, my system is running a lot faster now too. I assumed the computer's sluggishness was due to it being over five years old and having seen extensive use, but I guess it was just the crowded hard drive. I'm going to take the above advice and wait awhile before upgrading to 16.04. I'm really not up for combating numerous bugs at this point in my Linux education.

---

### Post by BlacklightHalo on 2016-08-22
I'm noticing that since performing updates, several things are wonky here. For one thing, the internet browser's file-upload interface isn't working. It pops-up and gives me the expected choice of folders from which to choose files in the left-hand menu ("pictures," "desktop," etc.) but clicking on any of those tabs shows no files. I can still share pictures (for instance, to facebook by dragging and dropping them into the update field,) but the file selector itself is not behaving. For another thing, the backgrounds of websites (Google and Amazon most noticeably) are having color-scheme issues. I'm using the dark theme from Ubuntu Satanic Edition to keep things easy on my eyes, but this wasn't happening before I went into Muon Updater and applied some system updates.

---

### Post by BlacklightHalo on 2017-01-27
I have recently solved this problem. What I did was download "Systemback" and have it basically reinstall 14.04 and set things back to default. I was still getting "system problem detected" messages, but at least the process purged all the old kernel images that were taking-up space I needed to do the upgrade. It had been about five months since I'd gotten Kenzo's advice to wait for bugs to be worked out of 16.04 before upgrading, so I thought it would be safe to give it a go. I now realize I could (and should) have done some research to see what the current bug situation in 16.04 looks-like, because now I'm having all sorts of problems with 16.04 (the most concerning of which is that the computer seems to be altogether ignoring my "logout," "restart," "shut down" etc commands. They just don't do anything. All I can do is put it to sleep when I'm not using it. Yeesh...) But all that is a matter for another thread, I suppose. I will mark this problem as "solved." Just making a note that this thread's problem has been addressed using Systemback.

---

