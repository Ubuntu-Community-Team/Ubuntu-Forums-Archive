---
title: "Installation Confusion"
date: 2013-08-06
forum: Installation &amp; Upgrades
---

### Post by Dexon on 2013-08-06
Hello,
As the title suggests, I am having a bit of trouble installing Ubuntu 12.04 or if possible, 13.04 onto my Laptop PC.
I currently run an HP Pavilion g6 with Windows 8 Pre-Installed onto it.
I have an AMD A8-4500M APU with Radeon™ HD Graphics 1.90GHz, also I have 4.00 GB of RAM.
My system type is 64 Bit.
I am wondering if anyone can give me some help on how to install Ubuntu on this PC.
I have tried installing Ubuntu, without knowing what would happen, on this PC before. It didn't work out so well so I have uninstalled it.
My Windows 8 works perfectly fine.
Any help available?
Thanks.

*~Da Dexon~*

---

### Post by Doomspark on 2013-08-06
First question:  do you want to keep your Windows 8 installation and run a dual boot configuration, or do you want to go completely Ubuntu?

If the former, someone else will have to pitch in; I don't speak Windows 8 well enough to help.

If the latter, download whichever distribution you want to use, and either burn a bootable CD or set up a bootable USB drive.  Boot the laptop from whichever one you made.  

At this point, you should have the option to "Try Ubuntu" or "Install Ubuntu".  I would choose Try Ubuntu so you can test things out.  It *will* be slower.   Once you confirm that everything is working, reboot the laptop again and this time do the Install.

---

### Post by Dexon on 2013-08-06
> **Ilaraxys said:**
> First question:  do you want to keep your Windows 8 installation and run a dual boot configuration, or do you want to go completely Ubuntu?

If the former, someone else will have to pitch in; I don't speak Windows 8 well enough to help.

If the latter, download whichever distribution you want to use, and either burn a bootable CD or set up a bootable USB drive.  Boot the laptop from whichever one you made.  

At this point, you should have the option to "Try Ubuntu" or "Install Ubuntu".  I would choose Try Ubuntu so you can test things out.  It *will* be slower.   Once you confirm that everything is working, reboot the laptop again and this time do the Install.

I do want to keep Windows 8 and run a dual boot, even though you don't seem to know how to help me, thanks for the reply.

---

### Post by orioles_fan on 2013-08-06
First of all, your "wtf" keyword made me laugh pretty hard.

If you don't mind me asking, what "didn't go so well" the first time around? I've got a Lenovo U310 I'm going to try to install Ubuntu on tonight but that is somewhat complex because of the Intel Rapid Storage setup with the small 24GB cache SSD in addition to the traditional hard drive.

---

### Post by Dexon on 2013-08-06
> **orioles_fan said:**
> First of all, your "wtf" keyword made me laugh pretty hard.

If you don't mind me asking, what "didn't go so well" the first time around? I've got a Lenovo U310 I'm going to try to install Ubuntu on tonight but that is somewhat complex because of the Intel Rapid Storage setup with the small 24GB cache SSD in addition to the traditional hard drive.

What didn't go too well was whenever I tried to run the Ubuntu, I have to go into the boot menu to find it, but there are two. The first one just takes me to the OS Boot manager again. The second one takes me to this really glitchy screen that I'm guessing is supposed to be the Ubuntu boot menu. Whenever I click the first option, it loads Ubuntu but a few minutes after my mouse glitches and the computer shuts off, so I uninstalled it.

---

### Post by orioles_fan on 2013-08-06
> **Dexon said:**
> What didn't go too well was whenever I tried to run the Ubuntu, I have to go into the boot menu to find it, but there are two. The first one just takes me to the OS Boot manager again. The second one takes me to this really glitchy screen that I'm guessing is supposed to be the Ubuntu boot menu. Whenever I click the first option, it loads Ubuntu but a few minutes after my mouse glitches and the computer shuts off, so I uninstalled it.

I've had that happen with other Linux distributions in the past where it's create multiple boot entries in GRUB. Drove me nuts and still never really figured it out.

Anyway, here's what I'm planning to do with my U310. Your HP might be different, especially if it doesn't use a cache SSD drive. Only difference is I'm going to attempt 13.04 instead of 12.04.
[http://ubuntuforums.org/showthread.php?t=2129157&p=12591671#post12591671](http://ubuntuforums.org/showthread.php?t=2129157&p=12591671#post12591671)

It's still a mildly terrifying process. I've decided to just come to terms with the idea of loosing Windows completely for now.

---

### Post by Dexon on 2013-08-06
> **orioles_fan said:**
> I've had that happen with other Linux distributions in the past where it's create multiple boot entries in GRUB. Drove me nuts and still never really figured it out.

Anyway, here's what I'm planning to do with my U310. Your HP might be different, especially if it doesn't use a cache SSD drive. Only difference is I'm going to attempt 13.04 instead of 12.04.
[http://ubuntuforums.org/showthread.php?t=2129157&p=12591671#post12591671](http://ubuntuforums.org/showthread.php?t=2129157&p=12591671#post12591671)

It's still a mildly terrifying process. I've decided to just come to terms with the idea of loosing Windows completely for now.

Alrighty then.
I'm not sure if my HP uses a Cache SSD, but I don't want to lose Windows. It has my Sony Vegas on it. ;)

---

### Post by orioles_fan on 2013-08-06
> **Dexon said:**
> Alrighty then.
I'm not sure if my HP uses a Cache SSD, but I don't want to lose Windows. It has my Sony Vegas on it. ;)

I know the feeling. My Windows partition has Ableton, Traktor, Komplete 8, etc. There's a lot to lose there!

I'll let you know how it goes tonight and maybe have some pointers.

---

### Post by Dexon on 2013-08-06
> **orioles_fan said:**
> I know the feeling. My Windows partition has Ableton, Traktor, Komplete 8, etc. There's a lot to lose there!

I'll let you know how it goes tonight and maybe have some pointers.

Alrighty then.

---

### Post by orioles_fan on 2013-08-07
Alrighty, I just got Ubuntu 13.04 installed, dual booting with Windows 8 in a weird, roundabout sort of way.

First, I went ahead and created a backup of everything on the Windows side. I already had my Ubuntu USB ready to go. I also deleted an unused partition on my SSD and shrank my Windows OS partition to make room. Sadly, the Windows partition was such a hog that I could only shrink it 22GB. Once that was done, I booted into my BIOS and turned off the Intel Rapid Storage Technology system (the one that uses the SSD as a cache drive). For whatever reason, my SATA setting was already set to ACHI so I didn't mess with that. I left UEFI on since 13.04 supports UEFI booting.

Next, I booted into Ubuntu (I did Try Ubuntu) first, just to make sure everything was working ok. From there, I ran the installer. I created my root folder on the SSD, the home folder on my HD, as well as a swap folder. Ran the installer, no problem. Once I restarted, GRUB showed up with several options, Ubuntu obviously being the first. However, there are two Windows options, neither of which work. Both throw up errors and kick back to the GRUB menu. I can, thankfully, get to Windows by selecting "System Setup" option, which bumps me to the Boot Menu and allows me to pick "Windows Boot Manager". Selecting this will get me into Windows like normal.

Still haven't turned on the Rapid Storage stuff yet. Might just leave it off.

---

### Post by Dexon on 2013-08-07
> **orioles_fan said:**
> Alrighty, I just got Ubuntu 13.04 installed, dual booting with Windows 8 in a weird, roundabout sort of way.

First, I went ahead and created a backup of everything on the Windows side. I already had my Ubuntu USB ready to go. I also deleted an unused partition on my SSD and shrank my Windows OS partition to make room. Sadly, the Windows partition was such a hog that I could only shrink it 22GB. Once that was done, I booted into my BIOS and turned off the Intel Rapid Storage Technology system (the one that uses the SSD as a cache drive). For whatever reason, my SATA setting was already set to ACHI so I didn't mess with that. I left UEFI on since 13.04 supports UEFI booting.

Next, I booted into Ubuntu (I did Try Ubuntu) first, just to make sure everything was working ok. From there, I ran the installer. I created my root folder on the SSD, the home folder on my HD, as well as a swap folder. Ran the installer, no problem. Once I restarted, GRUB showed up with several options, Ubuntu obviously being the first. However, there are two Windows options, neither of which work. Both throw up errors and kick back to the GRUB menu. I can, thankfully, get to Windows by selecting "System Setup" option, which bumps me to the Boot Menu and allows me to pick "Windows Boot Manager". Selecting this will get me into Windows like normal.

Still haven't turned on the Rapid Storage stuff yet. Might just leave it off.

Alright then, do you know any way that I can tell if I have an SSD cache drive?

---

### Post by codemaniac on 2013-08-07
I have removed one of the tags from this thread. 

From forum CoC which you have agreed upon joining.

> Profanity: We have users of all age groups and of all tolerance levels where profanity is concerned. A language filter is in place to catch most major forms of profanity that may accidentally be used. Do not attempt to circumvent the language filter by using variations or slight misspellings of profanities.

---

### Post by Dexon on 2013-08-07
That doesn't really seem to help me in any way with my confusion, but alrighty then.

---

### Post by orioles_fan on 2013-08-07
If you boot into your BIOS, there should be an entry somewhere for Intel Rapid Storage Technology or something similar. Another way to see is to go to Computer, right click and select Manage. Go to Disk Management. If an SSD is there, you'll see a 24GB-32GB drive there in addition to your regular hard drive.

For what it's worth, I just said "screw it" and erased Windows completely. I'm a web designer so all of my audio pipe dreams were just taking up space. :P Ubuntu is the perfect environment for me to code and design.

---

### Post by Dexon on 2013-08-07
Alright. I have four partitions, one is recovery, one is EFI, one is NTFS, and the other is OEM.

---

### Post by orioles_fan on 2013-08-07
Makes sense. Recovery partition is just that; a Windows recovery partition. EFI is your boot info (best not to touch). NTFS is your Windows OS. OEM is probably just some random bloatware.

The first step would be to shrink your NTFS partition (the other partitions are usually small anyway) since that's what Windows uses and most of the free space will be. If you go to Disk Management inside Windows (instructions on how to get there are in my previous post), you can right click on the NTFS partition and click "Shrink Volume". It'll run its check to see how much space can be given up and then it'll let you decide how much to split off into free space. Then the install should be pretty straight forward. Not sure if you'll have to mess with the SATA mode or UEFI mode in the BIOS but double check just in case. These shouldn't be an issue since you only have one drive.

---

### Post by Dexon on 2013-08-07
That was the way I tried, and it didn't work.

---

### Post by Dexon on 2013-08-07
I always call NTFS Not That File System for any reason. Haha

---

### Post by oldfred on 2013-08-07
Several threads with HP.
 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

More info on UEFI installs in link in my signature.

---

### Post by Dexon on 2013-08-07
I'm not sure, but I think I run EFI. Theres an EFI partition that I have.

---

### Post by Dexon on 2013-08-08
Alrighto, I tried putting Ubuntu 64 Bit onto my disc, but it would not read it. Whaaaaa...

---

