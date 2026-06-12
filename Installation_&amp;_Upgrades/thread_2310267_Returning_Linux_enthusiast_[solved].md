---
title: "Returning Linux enthusiast [solved]"
date: 2016-01-17
forum: Installation &amp; Upgrades
---

### Post by pjnoxon2 on 2016-01-17
Hi,

I was going to install Ubuntu on my Asus K55 i5 Win7 6GbRAM laptop a few years ago, but because I would
stick with the installed UEFI Win7 on the 750Gb HD, and there were many reports of troubles installing Ubuntu
in this type of environment I got cold feet and never did it. I was overseas for a couple years and recently got
back to where a reliable internet connection has tempted me to revisit Ubuntu. I have the 14.04.1 install DVD
but I see now there is 14.04.4 as the current LTS. Here's my HD:
[ATTACH=CONFIG]266810[/ATTACH]
p.s. there is a hidden Q: partition that has the starter versions of Word and Excel etc. (why do they do that?)

Question 1) Is there a better handle on installing Ubuntu to live alongside a Win7 UEFI in the 14.04.4 release?
(as in should I 'retire' the 14.04.1 DVD I have here and burn a new 14.04.4 DVD)

Question 2) Once installed alongside Win7, if I am just sticking with Win can I just close the lid into sleep mode
(this is not the dreaded Hibernate mode) and later open the lid back into Win7?

I expect at first I will be doing this mostly and when I need Ubuntu I will use 'shut down' to access the dual boot.

thanks a lot - PJ

---

### Post by deadflowr on 2016-01-17
1: Your a month too early to be installing 14.04.4, as it is non-existent.
It comes out Feb 4.
So if your hardware can support 14.04.1, use it.
To better understand what I may mean, looky here:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

2: I am not sure how Ubuntu would ever affect Windows sleep/wake modes.
I multi-boot various linux/buntu distros and use suspends here and there and never woke up in another distro.
But that is neither here nor there, I guess.

Also, tidbit, is to be aware of installation bugs like this:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by pjnoxon2 on 2016-01-17
Hi and thanks, I meant 14.04.3
Hate to admit I wouldn't know a Precise kernal from a Trusty. My fear is more mundane. I have a lot of
applications I have used over the past 3 years and wouldn't be able to re-install them all, but probably
don't need them all anyway. For example I have one that converts from PDF to DOC and back, pretty
handy sometimes but lost the install disk. I have all my data files backed up, but Win applications, no.

Reading the forums and other Linux forums there were horror stories when UEFI came along with Win7.
I don't think have the secure boot fortunately, but for example there is this horrifying note from Old Fred:

[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

That part where it says "Do not use any older versions of Installer as it had major bug that erased all partitions"
Now that would certainly ruin my whole day. Would'nt the 14.04.1 DVD I have be 'an older version of Installer'?

"Turn off Windows fast startup in Windows" - I couldn't find fast startup in my Win7 - maybe it's only in Win8?

Thanks for answering my second question. - pj

---

### Post by Bucky Ball on 2016-01-18
If they're Windows apps they are not going to work natively in Ubuntu. You must restart your machine to enter the OS you are no using. The two OSs do not run concurrently. You are either booted into Win or Ubuntu. Closing the lid and opening makes no difference. You would need to manually restart the machine and choose another OS if you want to change OS.

Ubuntu wiping your drive would ruin your day, yes, but it would destroy it if you don't have a back-up of your current system, or at least valued data. If you don't do that NOW, PRIOR to making any attempt to install Ubuntu. You are doing this at your own risk so up to you to take precautions in case things go pear-shaped.

The safest way is to choose 'Something Else' at the partitioning section of the install and partition manually. That's a little more involved by there's info out there. [This page]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352") will give you some clues. Doing it this way, you can see the Win partitions already present on the disk. Just avoid doing anything to them. They will be NTFS and you will also have a FAT EFI partition if your Win is booting in UEFI mode (and if Win was preinstalled on the machine it would probably be). Check by booting into the BIOS.

---

### Post by oldfred on 2016-01-18
Fast start up and the Secure boot are only in Windows 8 or later. So you will not find those settings in Windows 7.
If you have updated UEFI/BIOS to newest version, you may have a setting like "Windows" and "other". Windows means secure boot which Windows 7 does not support. So use other if you have that.

Just do not use hibernation with Windows 7. Not really recommended with any dual boot as it keeps partitions mounted and any activity from any other system (including another Windows install) is lost or may corrupt hibernated system, if trying to write into the NTFS hibernated partition(s).

Deadflower's link is to the bug report on the issue of partitions getting erased. I would only use the newest available versions. But if you always used Something Else and partitioned in advance, you would not erase the partitions. It was only the auto install options with the older installs that caused the issue.

And you should have a full image backup of Windows. You may want that anyway as Microsoft is starting to nag you to update to Windows 10. A few have issues with that and have to restore Windows 7, or good backups always required even if not installing Ubuntu.
       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by pjnoxon2 on 2016-01-22
Wow, thanks a lot, very good information.

re: "If you have updated UEFI/BIOS to newest version" - I have periodically run the windows update, although
this is sometimes a scary process as it will require several reboots after with crossed fingers. So I don't really
know if I have updated UEFI/BIOS, at least I did not do anything manually which specifically related to those.

Would it be possible to make a USB stick that has the ability to store and restore my entire C: drive along with
whatever needs to be done to the 200Mb EFI partition? I have seen truly enormous USB drives coming along.
That kind of safety blanket would make me feel really warm and fuzzy.

I put Mint on this ancient Sony laptop (1Gb RAM, 88Gb HD, Pentium M 2Ghz) we found when moving out of my
old house, and it is working well (better than WinXP was - like swimming upstream in cornstarch) so no hurry to
get Ubuntu on my ASUS now. Just want to learn more all the time here.

- PJ

---

### Post by oldfred on 2016-01-22
I did buy a new Dell SFF about a year ago, it had Windows 8.
I did not plan on using Windows so shrank it to 40GB. On a couple of reboots it just about filled the 40GB. And NTFS needs about 30% free to work well. 
Then I found I could watch Comcast DVR shows remotely on computer but only Windows 8 worked. So expanded Windows to 100GB and updated to Windows 10. Did not have any major issues.

When I first got Dell I followed my own suggestions on Windows backups. But ended up with several DVDs & two flash drives one 8GB and one 32GB.  I have a Dell backup, a Windows repair CD, a Full backup with Macruim with two DVDs to boot into Macruim, one Windows and one Linux. And that was with brand new system before any data.

After Windows 10 update, I re-installed Ubuntu. I have separate data partition and a partition just for / with no data.

UEFI update is a BIOS update, as some still call it. You need to go to vendor site for your model system and check on most current UEFI. It also should have instructions on how to update. Most can update from a FAT32 flash drive. A few only update from Windows. Some say not to update unless having issues, but I never have had an issue but am careful on doing it.

Windows updates took at least all afternoon. But it took a long time to download. WiFi not as fast as hard wired. And do not know Windows commands so just about had to look everything up as I went.

And Ubuntu total reinstall took 10 min. :)
But I had downloaded to USB3 flash drive separately, and with separate / (root) it was already partitioned so just launched reinstall. Updates took some additional time also, so not totally fair comparison.

---

