---
title: "Returning to dual-booting after a hiatus"
date: 2020-06-30
forum: Installation &amp; Upgrades
---

### Post by heatopher2 on 2020-06-30
Hi Guys,
 
I'll start with an apology for how long this post is going to be, but of course that's just how it is sometimes, eh.
 
Having wanted to get a dual-boot system going for many years, I finally made it three and a half years ago. The thread immediately below this paragraph was part of the process. In a nutshell, I couldn't get Windows and Ubuntu to sit together harmoniously on the same disk, and so in the end I followed some clever advice to install grub at the beginning of the second hard disk. And yes, that worked! Eventually, anyway - I had to sweat plenty over it.
 
[https://ubuntuforums.org/showthread.php?t=2349225](https://ubuntuforums.org/showthread.php?t=2349225)
 
This is what the two disks look like. The two OSes on sda, all data and other gubbins on sdb, with some partitions at the beginning of sdb which I assume are related to grub, but maybe not all (you tell me please!):

[ATTACH=CONFIG]286370[/ATTACH]
[ATTACH=CONFIG]286369[/ATTACH]

Everything was fine until I made the tragic mistake of trying to upgrade Ubuntu from 16 to 18, about a year and half ago. Of course I knew that I was in trouble when the upgrade froze at the point when it was supposed to be updating grub. I couldn't do much else other than restart the computer. Well, I could have taken a picture and written a post here, but that would have all taken too long I suppose. Anyway, I expected the absolute worst, but remarkably I was able to boot into Linux for a little while, after some panicky rescue attempts. Clearly a lot of features had been lost (I can't remember in much detail any more!), and it was not satisfying. And anyway, soon enough grub just failed, and I saw this:
 
[ATTACH=CONFIG]286367[/ATTACH]
 
I did write a post on here at some point in the month or two after this happened:

[https://ubuntuforums.org/showthread.php?t=2409387](https://ubuntuforums.org/showthread.php?t=2409387)
 
Initially I got a reply, and a conversation started, but then the communication went dead, despite my shamelessly bumping myself up a few times. I suppose that the person who was replying either got sick or hopelessly busy with other stuff, and eventually I just gave up. I had enough other stuff going on, of course, and anyway, I could get Windows at least, by booting from the disk that both systems are on. Not ideal, obviously, but I survived until now. 

However, I do very much miss having Linux, and of course Windows is super-annoying sometimes (but I don't quite feel ready to let go completely), so I really would like to get Ubuntu back on. Being one of those people placed in a VERY long and strange furlough period, I've decided to devote a couple of weeks of this time to sorting this problem out, and getting back into the Ubuntu spirit. 

The way I see it, I have two options, which I will detail here, and seek advice from the collective:

..............
 
Option 1
 
Try to figure out what's wrong with GRUB, and get the original dual booting back:
 
I tried following this post:
 
[https://unix.stackexchange.com/quest...-mod-not-found](https://unix.stackexchange.com/quest...-mod-not-found)
 
Of course on that post they talk about normal.mod, Well, I'm apparently missing bufio.mod, and can't find anything online about what the difference is!!!
 
I've tried following the instructions as best I could, substituting bufio for normal (which of course I have no idea if it's right or wrong, but not too much to lose, eh). I can find the partition that (I guess) I need to be working on, as it's the only one that responds to 'ls': 

[ATTACH=CONFIG]286368[/ATTACH]

But following instructions from that previous link beyond that doesn't take me very far.

If it's really beyond salvage, no worries - I'll move on to Option 2 --->

...............

Option 2

... is to wipe the old Ubuntu partition and start again, with Ubuntu 20 this time. I've tried it off the USB, and can see some significant improvements, such as immediate detection of mount points, and I'm sure many other things that I don't know about yet. According to all the tutorials that I've found, it's all supposed to be child's play to get the dual boot to work. 

Well, not child's play exactly, but the tutorials say that Windows 10 should be detected by the installation process, but instead of that, I'm getting this:

[ATTACH=CONFIG]286366[/ATTACH]

Is that going to change if I just delete the Ubuntu 18 and Swap partitions? Like I said, I don't really mind too much about losing that corrupted system and starting again.

The other question relating to that (maybe!) is the Legacy BIOS - UEFI issue. I don't really understand how this affects dual booting, and haven't found the information to explain that properly. I've taken screenshots of my settings from the boot manager, and I'll just stick them on here to see if there's one magic bullet!

Ah, I see that I'm limited to five pictures per post, so I'll have to put a second post with those. Sorry!

---

### Post by heatopher2 on 2020-06-30
Here are the boot settings. Hopefully this is the right info anyway. Main setting here:

[ATTACH=CONFIG]286371[/ATTACH]

Plus some other stuff:

[ATTACH=CONFIG]286372[/ATTACH][ATTACH=CONFIG]286373[/ATTACH][ATTACH=CONFIG]286374[/ATTACH][ATTACH=CONFIG]286375[/ATTACH]

OK, that'll do for now. Sorry if there's anything missing :o

---

### Post by oldfred on 2020-06-30
Did you go back and look at previous suggestions in your old thread, including those by me?
I still suggest running Boot-Repair first. But do not run any autofix as Boot-Repair will want to install grub to all drives, and since you have more than one, better to have Windows boot in one & Ubuntu/grub boot in other.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

But you have complicated it by having a newer UEFI system, but Windows installed in the now 35 year old BIOS/MBR mode. Windows requires MBR partitioning for BIOS boot and gpt partitioning for UEFI boot.
And your sdb drive is over 2TiB and requires gpt partitioning as MBR designed 35 years ago has a hard limit of 2TB since even GB was not even a consideration back in early 1980's.

Also Microsoft has required vendors to only install Windows in UEFI boot mode to gpt partitioned drives since Windows 8 released in 2012.
But difficult to dual boot unless both systems are in same boot mode, so since Windows is BIOS, you have to use BIOS to boot Ubuntu.

Any consideration to full backup of Windows and total reinstall in UEFI boot mode?
If not, then set UEFI to only boot in Legacy boot mode. That setting is only for your installed systems and you have to only select to boot USB flash drives in Legacy/BIOS/CSM boot mode. You may have to turn on allow USB boot or full USB support.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

---

### Post by CatKiller on 2020-06-30
> **oldfred said:**
> Any consideration to full backup of Windows and total reinstall in UEFI boot mode?

This would be my recommendation. Install Windows (if you want it) in UEFI with GPT partitioning and then install (K)Ubuntu 20.04. Anything else just makes things harder for negative benefit.

Also, be aware that Windows by default (and after updates even if you turn it off) hibernates instead of shutting down properly, which means all of its partitions are dirty and won't be shown. They call it Fast Startup. You'll need to turn that off when you want the installer to know about your Windows partitions.

---

### Post by heatopher2 on 2020-06-30
Hey Guys!

Thank you so much for the super-quick replies, as usual :grin:

I'll have a proper look at all that, and report back soon!

---

### Post by heatopher2 on 2020-07-22
Hi Guys,

I haven't written anything back, because I've been away  from home for a few weeks, and so no way to do anything on that PC of  course. I'll be back next week, so thinking about this business again now, and just reading properly what you guys wrote. Starting at the end, in fact:

> **CatKiller said:**
> Also, be aware that Windows by  default (and after updates even if you turn it off) hibernates instead  of shutting down properly, which means all of its partitions are dirty  and won't be shown. They call it Fast Startup. You'll need to turn that  off when you want the installer to know about your Windows  partitions.

THIS might save me a massive amount of hassle. At least I hope so. I do  have Windows set up with Hibernate, so I really hope that that is the  reason why it's not showing up on the Ubuntu installer. I can't say now,  of course. If it's not that, I'll be back with a load more questions, I'm afraid.

But before that, to answer both of you...

> **oldfred said:**
>  Any consideration to full backup of Windows and total reinstall in UEFI boot mode?
If not, then set UEFI to only boot in Legacy boot mode. That setting is only for your installed systems and you have to only select to boot USB flash drives in Legacy/BIOS/CSM boot mode. You may have to turn on allow USB boot or full USB support.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

The answer is of course "YES"! :D If I can do that, and lose all the complications of boot repair all that UEFI/GPT stuff, yes yes yes yes yes. Of course. If it's not as simple as turning off hibernate on Windows, I would run Ubuntu off the Ubuntu 20 install USB, to grab any useful files that are in my Home directory on the PC, and then I would do a full reinstall of everything. I have Macrium Windows system backup, which I've used with no problems in the past. So in principle, of course it's a lot less hassle. However, I don't actually have a Windows 10 installer. I'd have to start again with Windows 7, and then reinstate the current system with Macrium (maybe via the Win 10 upgrade, which I do have, in .exe form?). Would that work in UEFI? Sorry if my questions are a bit ignorant at times. I'm trying to understand all this stuff.

---

### Post by oldfred on 2020-07-22
Do not know Windows, but any image backup that is in BIOS/MBR mode will not be able to restore to UEFI/gpt. 
Partitions are a lot different. 
It is more like a new install & restore your data & configuration which is relatively easy with Ubuntu. Have never tried with recent Windows.

BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by pbear42 on 2020-07-23
> **heatopher2 said:**
> ... I don't actually have a Windows 10 installer. I'd have to start again with Windows 7 ...
Last I heard, Microsoft is still permitting direct install of Win10, using a Win7 OEM license key to activate.  Haven't seen anything on the issue in a few months, but seems they've decided not to obsess over upgrades.  Start with this [ZDNet]("https://www.zdnet.com/article/heres-how-you-can-still-get-a-free-windows-10-upgrade/") article.  Go to [Microsoft]("https://www.microsoft.com/en-us/software-download/windows10").  Read instructions.  Download Media Creation Tool.  Open (runs as a portable, Windows only).  Select Create installation media.  Select language, version and architecture.  Select ISO.  Select download destination.  Download (4.2 GB) will commence automatically.  When complete, burn the ISO to USB drive.  Or save the ISO as a file and use Rufus to burn the USB drive. 

To be clear, I've not done exactly what you need to do, but I have used a variation of this procedure to install Win10 in VirtualBox, using my old Win7 OEM key.  That VM still updates without issue.  From which I infer that, if Microsoft monitors this at all, it's only to make sure each OEM key is requesting only one set of updates.  And it may be they're not monitoring it at all, relying instead on the registration process.  By the way, you will have to register the new install to get all features.  Use the same registration as you're using now, which you had to do when you did the original Win10 upgrade.

Important.  Before doing this, I would strongly recommend you take a system image of the hard drive's current state.  Macrium if you have it, or you can use the built-in Windows image backup tool.  That way, if something goes sideways, you can get back to where you are right now.  If the reinstall goes through, hold onto the image backup for a month or so, then at some point you can let it go and reuse the backup medium for something else.

Hope that helps.  Good luck.

---

### Post by heatopher2 on 2020-08-04
Hey Guys, 

Once again, sorry for my long absence. If I haven't fundamentally misunderstood something, I think that I may have found a source of hope that I can make this process not too painful:

[URL="https://kb.macrium.com/KnowledgebaseArticle50151.aspx"]https://kb.macrium.com/KnowledgebaseArticle50151.aspx

[/URL]If I can indeed still use my system images after switching over to UEFI it will be very useful. I'll try it over the next couple of days, and will report back.

---

### Post by heatopher2 on 2020-09-04
Finally I've come back. I've been back and forth quite a lot, and had lots of learning experiences along the way.

Soooooo, I do now have a more-than-dual-booting system, with Windows, Ubuntu and Linux Mint (to see which I prefer), and room on the SSD to experiment with a couple more, I guess. But none of that is thanks to Macrium. I tried several times (it felt like more than several!!) to follow their MBR-2-GPT method, so it can't be that I didn't at least one time do everything exactly in the right way. And it didn't work at all. Who knows why? But I can say from my experience that the claim that it's possible to do this is dubious at best, if not completely bogus. Maybe there's something that they've forgotten or neglected to put in the instructions. And maybe there's someone out there who has succeeded at doing this move. I'd love to know!

Whatever the case is, I concluded at the end of a whole day trying to do that stuff, that it really wasn't worth it. And so in the end I started again with a fresh UEFI Windows installation, which is tedious, true, but less enervating than what I had experienced up until then. I was reluctant to pay for a fresh Windows 10 code, but not much I could do. My old installation had come from Windows 7/BIOS, and then the upgrade.

The only thing that I still want to do is to install a nice pretty graphical boot loader, and as far as I understand things rEFInd is the preferred one. I tried installing it last night, but there was some problem with it knocking out the Windows boot. Maybe it was the fast startup that you guys mentioned, and which I hadn't got around to disabling yet, but maybe it's a bit more complicated than that, judging from bits and pieces that I've been looking at this morning. Let's see anyway. At least I've got the Windows backed up with Macrium Reflect, and have verified that the backup works after what happened with rEFInd last night.

Anyway, thanks very much for the help, as always. I'm sure that I'll be back soon, but for the time being sooooooo relieved to have this stuff working.

---

### Post by heatopher2 on 2020-09-04
> **pbear42 said:**
> Last I heard, Microsoft is still permitting direct install of Win10, using a Win7 OEM license key to activate.  Haven't seen anything on the issue in a few months, but seems they've decided not to obsess over upgrades.  Start with this [ZDNet]("https://www.zdnet.com/article/heres-how-you-can-still-get-a-free-windows-10-upgrade/") article.  Go to [Microsoft]("https://www.microsoft.com/en-us/software-download/windows10").  Read instructions.  Download Media Creation Tool.  Open (runs as a portable, Windows only).  Select Create installation media.  Select language, version and architecture.  Select ISO.  Select download destination.  Download (4.2 GB) will commence automatically.  When complete, burn the ISO to USB drive.  Or save the ISO as a file and use Rufus to burn the USB drive. 

To be clear, I've not done exactly what you need to do, but I have used a variation of this procedure to install Win10 in VirtualBox, using my old Win7 OEM key.  That VM still updates without issue.  From which I infer that, if Microsoft monitors this at all, it's only to make sure each OEM key is requesting only one set of updates.  And it may be they're not monitoring it at all, relying instead on the registration process.  By the way, you will have to register the new install to get all features.  Use the same registration as you're using now, which you had to do when you did the original Win10 upgrade.

Important.  Before doing this, I would strongly recommend you take a system image of the hard drive's current state.  Macrium if you have it, or you can use the built-in Windows image backup tool.  That way, if something goes sideways, you can get back to where you are right now.  If the reinstall goes through, hold onto the image backup for a month or so, then at some point you can let it go and reuse the backup medium for something else.

Hope that helps.  Good luck.

Thanks for this by the way. I just got a new DVD from one of these cheap suppliers. I don't know how legit they are, but eBay allows them to operate, so who am I to argue? :tongue:

---

### Post by heatopher2 on 2020-09-04
Whaddya know. I spoke too soon (I think that I very often do that). Windows booting OK, but Linux systems not booting right now. The boot options screen comes up, but both Ubuntu and LM stuck saying something about "initramfs". I need to go back and check properly, but a bit too tired to dive all the way in right now. Just thought I'd mention before you guys closed the thread completely :lolflag:

---

