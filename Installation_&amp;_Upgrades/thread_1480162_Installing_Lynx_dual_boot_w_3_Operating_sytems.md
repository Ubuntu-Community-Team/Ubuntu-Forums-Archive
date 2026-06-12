---
title: "Installing Lynx dual boot w/ 3 Operating sytems"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by Benchrest on 2010-05-11
I am preparing to do a fresh install of lucid lynx dual boot with vist@ Currently I am running 9.04 in this configuration. The install guide for Lucid says the new grub2 doesn't support more than 2 operating systems. plus I apparently can't edit it either. Besides vist@ there is a hp recovery partition which has a seperate entry in my existing grub. Does this mean I can't use the lucid desktop disk for a fresh install because I would have 3 operating systems? Lynx, vist@ and HP recovery partition. 
I only have two applications left I am using on vist@, but I have no recovery disk, only an old image for my vist@. I am very concerned about this upgrade. 5.04 went smooth and each one since then has been a bit harder. I could not get 9.10 to run and had to go back to 9.04. I hope I am not at the end of the road. How about using grub instead of grub2?

---

### Post by Mark_in_Hollywood on 2010-05-11
Disclaimer: I have not done this. 

Answer:

Hack Attack: How to triple-boot Windows XP, Vista, and Ubuntu

[http://lifehacker.com/193474/hack-attack-how-to-triple+boot-windows-xp-vista-and-ubuntu](http://lifehacker.com/193474/hack-attack-how-to-triple+boot-windows-xp-vista-and-ubuntu)

---

### Post by darkod on 2010-05-11
Grub2 limited to two OSs??? I'm fairly new to ubuntu but this is the first time I'm hearing this. Are you sure about it?

Can someone confirm or deny please? I have only two OSs and it works fine.

Otherwise, it's not true you can't edit grub2. It's just that the standard way of editing directly menu.lst has changed. Not only that menu.lst doesn't exist any more (the file is called grub.cfg) but you are not encouraged to edit it directly. You edit other configuration files and with update-grub ubuntu creates new updated grub.cfg.

You can add manual entries too, besides the default os-prober which detects other OSs automatically.

---

### Post by dino99 on 2010-05-11
you only have to take care of the "hp" partition and the "vista" one (you may risk some issues if you move them or resize them).

there is no limit about grub capabilities, all the distro are welcome :P

look at this mini howto:

[http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

or if you install ubuntu on a separate hdd, unplug the hdd with vista and hp to install ubuntu, then plug back the other hdd

be aware that lucid use grub2 and we cant mix it with grub1 (issues)

---

### Post by oldfred on 2010-05-11
Grub will boot as many systems as you want, in fact with many systems you may want to modify grub to only show some. One user yesterday wanted to remove the recovery partition from the grub menu as he was afraid one of the kids might click on it and end up reformating the entire system.

I am not a fan of recovery partitions anyway. I did write a copy to CD 3 years ago when I bought my computer, but now there is no way that I am letting it erase my hard drive and convert back to as 'new'. I actually now have not booted XP on my laptop except to see if it works for quite a while. I do have one application on my Desktop that is still windows but I am (slowly) working on converting to a linux not quite equivalent.

---

### Post by darkod on 2010-05-11
> **oldfred said:**
> 
I am not a fan of recovery partitions anyway. I did write a copy to CD 3 years ago when I bought my computer, but now there is no way that I am letting it erase my hard drive and convert back to as 'new'.

That gets my vote immediately!!! I can't think of a single situation when if the OS gets corrupted I would like to use 'delete all and make it as new' approach. Even when I was using only windows I would never do that and lose all data on other partitions and the partitioning layout.

---

### Post by dino99 on 2010-05-11
no more windoz since 2002, and no need it anyway, wine (winhq) is able to run smootly the few windoz apps around. :P

---

### Post by Benchrest on 2010-05-11
First, Wine doesn't run Family Tree Maker, Front Page, or Works DataBase. I've tried. Also Ubuntu doesn't support my scanner correctly. it scans ok, but output looks like 1988 scanner, very low res with lines in the pictures. 

Also I am talking about problems with Grub2, not Grub.

The document I am referring to is: [http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu)

It says:   > Installing multiple OS on a single computer

Warning: The Ubuntu Desktop edition LiveCD installer no longer allows a custom installation of GRUB, and it now uses GRUB2 (which is difficult to customize). DO NOT USE the Lucid Lynx Desktop edition LiveCD as an installer if you use a boot partition, use more than 2 operating systems, or chainload bootloaders. The Ubuntu installer will overwrite your Master Boot Record and you will later be forced to recreate it. This is a serious flaw in both Karmic Koala and Lucid Lynx Desktop edition installers. Use the Ubuntu Server edition instead (and then later add the ubuntu-desktop).

If you want to install more than 2 operating systems on a single computer, "check out these tips." 

Now I reread it and went to the link of "check out these tips"

It looks like they use grub from 9.04 and don't install grub2 with the 10.04 disk. I'm going to have to read this some more. Would like to hear from someone who has actually done it.

I'm wondering that since I already have 9.04 installed if I can do 10.04 and skip the grub2 part. I would keep the same partitions, even though I would like to make Ubuntu a bit bigger. I have some time. June 8th is my target date. I just absolutely have to have my Works Data base running till then. If it screws up after that I will have some recovery time.

Thanks for all your replies.

---

### Post by oldfred on 2010-05-11
You can easily dual boot multiple windows with grub2. We have helped many configure mutiple installs of windows and/or other systems with grub2 since it came out. One nice thing about grub2 is the improvements in the osprober that finds most other (working) operating systems. Old grub often required manual editing of any windows that was not on the first drive or other differences.

Grub legacy has not been maintained for years and is obsolete. If you works for your system you can still use it. I have it still as my grub partition booting some of my older systems but use grub2 as my main boot. Some other distributions use grub legacy but their version usually is not compatible with ext4.

Grub2 is not quite as easy to edit as most of the settings with grub legacy were in menu.lst. But many edited it incorrectly and caused major booting issues. New grub2 has more features and is therefore more complex. While different it is not that difficult to edit once you learn the differences.

General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
drs305's hack to get hidden timeout to work:
[http://ubuntuforums.org/showthread.php?t=1319672](http://ubuntuforums.org/showthread.php?t=1319672)

Have you looked at Gramps, bluefish, or any of several databases available in linux?

HTML editors
[http://www.osalt.com/frontpage](http://www.osalt.com/frontpage)

You could also look at this project :
[http://www.kexi-project.org/](http://www.kexi-project.org/)
MySQL or PostgreSQL frontend
[http://www.vfront.org/index.php](http://www.vfront.org/index.php)
KDE but works in Gnome
[http://knoda.sourceforge.net/](http://knoda.sourceforge.net/)
Openoffice database

---

### Post by darkod on 2010-05-11
> **Benchrest said:**
> 
The document I am referring to is: [http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu)


WOW!!! The bad side of the internet I guess. :)

I don't think ubuntuguide.org has anything officially to do with Ubuntu. Does it??? And some of the things they wrote are way too dark pictured...

'A Windows installation usually occupies the entire hard drive' - rubbish. The windows installation will occupy the partition you give it. If it's a single partition taking the whole hdd, that's another story.

I think they tried to warn people of potential problems, but they over did it waaay too much.
Of course grub2 will take the MBR (unless you tell the installer otherwise in Advanced options). Where do other bootloaders get installed by the way?

You seem to be experienced with what you are doing. Ignore this rubbish. :)

They say 'don't use the 10.04 live cd if using more than 2 OSs'. I just installed 10.04 using that exact cd, as million others too. No issues at all. OK, I have only 2 Oss, but absolutely nothing would be different with 3, 4 or 5...

---

### Post by spydeyrch on 2010-05-11
I have three OSs: Win7 Pro x64, Mint 8 x32, and Ubuntu 10.04 x64. they work just fine. No problem at all ...... but then again I did it a different way and am not currently using GRUB2, unless Mint 8 uses GRUB2, not really sure but I don't think that it does, does it? 

But......... When I was using 9.10, prior to a fresh install of 10.04, I WAS using GRUB 2 with Mint 8 x32, Win7 Pro x64, and, at that time, Ubuntu 9.10 x64. It worked just fine, no issues.

If you have questions on how I did it, let me know. I have two different ways that I did it, depending on if it was 9.10 or 10.04. :)

-Spydey :guitar:

---

### Post by Benchrest on 2010-05-11
Thankyou! oldfred you have given me much to read. And others have given me some assurance. I will read these references and see what I can learn.

---

### Post by Benchrest on 2010-05-11
I think I have my questions answered. including how to add acpi=noirq to grub2
I tried converting my works database to OO 2 years ago. To complicated, but a new version is out.
FTM I have converted to gramps successfully.  But my dad is always sending new file. 36k entries whew! conversion never finished.  
I use Bluefish for my personal web site. But I maintain a site for my club that the space provider requires I use frontpage
Hopefully 10.04 will have newer software to solve my scanner issues. But I don't see the time I will be able to completely switch over as long as other people I work with use windows. My wife uses Ubuntu 99% of time and I do 90%.

---

