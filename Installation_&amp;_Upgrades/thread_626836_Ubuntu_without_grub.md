---
title: "Ubuntu without grub?"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by GoldenH on 2007-11-29
Just want to make sure that I can install Ubuntu without loading Grub. I want to just have it start when I put the CD in, stay in its partition without changing anything since my laptop has a nonstandard MBR and I want to keep it that way.

Can I use the live CD? or do I have to use the alternative disk?

thanks.

---

### Post by confused57 on 2007-11-29
> **GoldenH said:**
> Just want to make sure that I can install Ubuntu without loading Grub. I want to just have it start when I put the CD in, stay in its partition without changing anything since my laptop has a nonstandard MBR and I want to keep it that way.

Can I use the live CD? or do I have to use the alternative disk?

thanks.

You can use the live cd and install grub to the root partition, which you may need to do anyway for your "nonstandard MBR" to boot Ubuntu.  There's an "Advanced" button that you need to click on that allows you to select where to install grub's IPL...during partitioning & install, make a note of your root partition's designation, e.g. /dev/sda3.  You would then type in /dev/sda3, instead of using the default (hd0)...(hd0) would install grub to the mbr, which you don't want.

The alternate install cd can also be used...at the last step where it asks if you want to install grub to the mbr, select "No", then you will be presented with another screen where you can type in /dev/sda3, or whatever your root partition is.

---

### Post by GoldenH on 2007-11-29
hmm, putting stuff in the boot partition is probably out too. I don't think i can make a bit-perfect copy of my hard drive as it is right now, and I can't restore it, (maybe I could with dd? I don't know how though) so I don't want to mess around with it, especially as I know the computer won't work right if it gets changed. (lol acer)

isn't there a .zip file floating with loadlin in it that i can configure and fire off?

F8 command line loadlin gooooo

---

### Post by GoldenH on 2007-11-29
hmm could I use this? I just paste these files right, i can delete them at any time, they don't overwrite anything. And the configuration to the boot loader options probably won't hurt it...
[http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Booting_GRUB_for_DOS_via_the_Windows_Vista_boot_manager](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Booting_GRUB_for_DOS_via_the_Windows_Vista_boot_manager)

Or this, it seems to be exactly what I want. I just make a batch file, boot to command line and run it.
[http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Starting_GRUB_for_DOS_from_DOS](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Starting_GRUB_for_DOS_from_DOS)

---

### Post by Herman on 2007-11-29
You can use Grub for DOS, here is a web page I made about how I think it is supposed to be used, with WinGRUB, [WinGRUB Page]("http://users.bigpond.net.au/hermanzone/p9.html").

I don't think yo should really be installing anything in that computer at all, actually, if you're that frightened of everything. 
You should probably just use Linux from a Live CD.
What if something goes wrong with disc partitioning on you? Disk partitioning problems are far more serious than mere boot loader problems.
I have a very good how-to about Knoppix with a persistent /home is a USB flash memory disk. It's even encrypted for security. You can use most of the same software with Knoppix as you will find in Ubuntu, Knoppix is based on Debian just as Ubuntu is.
Knoppix is for more conservative types who worry about their MBRs, while Ubuntu is for more adventurous people. Live CDs tend to run a little more slowly than hard-disk-installed operating systems though. [Knoppix Page]("http://users.bigpond.net.au/hermanzone/p20.html").

Another idea is to just install Ubuntu the regular way like everyone else does, but use the Ubuntu Live CD to make a backup of your MBR first, it's easy to backup and restore with a 'dd' command. [MBR backup and restore]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd").
That will make a perfect backup of your MBR, and you can restore it perfectly the same way as it was again later too. 

What kind of MBR do you have anyway? :)

Regards, Herman :)

---

### Post by GoldenH on 2007-11-30
Acer MBR. So I'll lose some neat features I guess? Not sure how far the bios-mbr integration goes. And yeah, made a disc image, I can plug the drive into another computer and restore the image if worst comes to worst, but that's a pain in the butt! and won't get Linux running :) I think i've got the utilities that will restore the MBR all ready to go but, new computer and all that. 

The plan is to install ubuntu, if it fries the MBR then I'll find out if my utilities work and install XP too :)

I've installed ubuntu before and stuff so its not like I'm completely new to this, but ubuntu seems to loooove grub more than some other distros i've used.

Thanks though! I was reading through your site yesterday, it looked great! Looks like I missed those pages though, I'll see how they are after work. Am a little worried about what I'll do if the bootloader goes beyond the first sector but grub won't overwrite that anyhow right?

---

### Post by Herman on 2007-11-30
Hello GoldenH,
If you install GRUB to MBR, Grub will install to the MBR and the next fifteen sectors of the first track of the hard disk right after the MBR as well as the Ubuntu partition.

If you know you have something in the first track of the hard disk, you can install LiLo instead, (if you use the 'Alternate' CD), which will make a backup of your MBR before it installs, and will not touch the rest of the fist track. [LiLo Page]("http://users.bigpond.net.au/hermanzone/p4.html").
Or you can use WinGRUB as already mentioned, or you can use GAG boot Manager from a floppy disk, [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm"). 

You can install GRUB to somewhere other than the MBR using the 'Alternate' CD, 
[Installing a Boot Loader for Ubuntu]("http://users.bigpond.net.au/hermanzone/p6.htm#Installing_a_Boot_Loader_for_Ubuntu").
                                            
[                                       If you choose <Yes>]("http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_Yes__to_Install_GRUBs_IPL_to_MBR") ( to Install GRUB's IPL to MBR)
                                            
[                                       If you choose <No>]("http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location") ( to Install GRUB's IPL to a custom location)
                                            
[                                       If you choose <Go Back>]("http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_Go_Back__to_Install_LILO_Boot_Loader") ( to Install LILO Boot Loader)
                                            

It's rare to have anything in the first track of the hard disk to worry about. 
In some models of Toshiba laptop there's the 'Express Media Player', and 'On Track Disk Manager, software for helping Windows users overcome BIOS hard disk drive limitations, might also be occupying the first track of the hard disk, but that's not very common anymore these daya and in any case, you won't need it after you install Linux. Presumeably you'll be installing Linux beyond the  BIOS hard drive BIOS limit with a /boot partition inside the limit.

I don't know very much about RAID or LVM, or Mac mother boards.
For most people with a standard PC, it's easiest and best to install GRUB to MBR when you install Ubuntu.

What kind of MBR do you have and do you have something in the first track of the hard disk?
> Acer MBR. So I'll lose some neat features I guess? Not sure how far the bios-mbr integration goes. And yeah, made a disc image, I can plug the drive into another computer and restore the image if worst comes to worst, but that's a pain in the butt! and won't get Linux running  An Acer MBR? All the Acers I have here come with a 'DOS' type MBR. You shoudln't have anything to worry about at all. I have an Acer Aspire 3003WLmi laptop, and Acer Aspire 16422WLMi laptop, and two Acer Aspire T310 Desktop computers all running Ubuntu just fine. I have also installed Ubuntu in several other Acer computers for friends without any problems at all.
As far as I know Ubuntu works very well in Acer computers and GRUB does too. In fact Ubuntu and GRUB are a huge improvement to them.

Unless you have something new and strange that I haven't heard of in this neck of the woods yet... (or actually in the Australian Outback really, but I don't think we're all that far behind these days), you will have nothing to worry about.

It's good that you made a backup though, everyone should always do that. 

>  The plan is to install ubuntu, if it fries the MBR then I'll find out if my utilities work and install XP too :smile: If it FRIES the MBR? Good gosh man! 

I've installed ubuntu before and stuff so its not like I'm completely new to this, but ubuntu seems to loooove grub more than some other distros i've used.

Regards, Herman :)

---

### Post by Herman on 2007-11-30
Hello GoldenH,
If you install GRUB to MBR, Grub will install to the MBR and the next fifteen sectors of the first track of the hard disk right after the MBR as well as the Ubuntu partition.

If you know you have something in the first track of the hard disk, you can install LiLo instead, (if you use the 'Alternate' CD), which will make a backup of your MBR before it installs, and will not touch the rest of the fist track. [LiLo Page]("http://users.bigpond.net.au/hermanzone/p4.html").
Or you can use WinGRUB as already mentioned, or you can use GAG boot Manager from a floppy disk, [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm"). 

You can install GRUB to somewhere other than the MBR using the 'Alternate' CD, 
[Installing a Boot Loader for Ubuntu]("http://users.bigpond.net.au/hermanzone/p6.htm#Installing_a_Boot_Loader_for_Ubuntu").
                                            
[                                       If you choose <Yes>]("http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_Yes__to_Install_GRUBs_IPL_to_MBR") ( to Install GRUB's IPL to MBR)
                                            
[                                       If you choose <No>]("http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location") ( to Install GRUB's IPL to a custom location)
                                            
[                                       If you choose <Go Back>]("http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_Go_Back__to_Install_LILO_Boot_Loader") ( to Install LILO Boot Loader)
                                            

It's rare to have anything in the first track of the hard disk to worry about. 
In some models of Toshiba laptop there's the 'Express Media Player'.
In a few older computers, 'On Track Disk Manager, software for helping Windows users overcome BIOS hard disk drive limitations, might also be occupying the first track of the hard disk, but that's not very common anymore these days and in any case, you won't need it after you install Linux. Presumably you'll be installing Linux beyond the  BIOS hard drive BIOS limit with a /boot partition inside the limit.

I don't know very much about RAID or LVM, or Mac mother boards.
For most people with a standard PC, it's easiest and best to install GRUB to MBR when you install Ubuntu.

What kind of MBR do you have and do you have something in the first track of the hard disk?
> Acer MBR. So I'll lose some neat features I guess? Not sure how far the bios-mbr integration goes. And yeah, made a disc image, I can plug the drive into another computer and restore the image if worst comes to worst, but that's a pain in the butt! and won't get Linux running  An Acer MBR? All the Acers I have here come with a 'DOS' type MBR. You shoudln't have anything to worry about at all. I have an Acer Aspire 3003WLmi laptop, and Acer Aspire 16422WLMi laptop, and two Acer Aspire T310 Desktop computers all running Ubuntu just fine. I have also installed Ubuntu in several other Acer computers for friends without any problems at all.
As far as I know Ubuntu works very well in Acer computers and GRUB does too. In fact Ubuntu and GRUB are a huge improvement to them.

Unless you have something new and strange that I haven't heard of in this neck of the woods yet... (or actually in the Australian Outback really, but I don't think we're all that far behind these days), you have nothing at all to worry about.

It's good that you made a backup, everyone should always do that before they install.

>  The plan is to install ubuntu, if it fries the MBR then I'll find out if my utilities work and install XP too :smile: "If it FRIES the MBR"? Good gosh man! What a ridiculous statement!
 Most of us around where  I live install Ubuntu and delete XP, but do as you like.
If you are going to have XP, then it's a little easier to have that installed first and then install Ubuntu after it, but you can do it either way.
>  I've installed ubuntu before and stuff so its not like I'm completely new to this, but ubuntu seems to loooove grub more than some other distros i've used. GRUB is the world's best boot loader and boot manager. What else would we want but the best? 
However, you have many other choices available to you if you want to use some alternative arrangement.

Regards, Herman :)

---

### Post by lvleph on 2007-11-30
You could use [Wubi](http://wubi-installer.org/). Not sure if it is the best solution, but it won't mess with your MBR. It only changes your boot.ini.

---

### Post by GoldenH on 2007-11-30
Yeah I saw WUBI, it looks neat, though i'd want to use LVPM to put it on its own partition, of course. It'll be great when it's all automated for me though! ;) I am a little bit worried about it having configuration problems due to not seeing my "actual" hard disk, but I can see myself using it when 8.04 comes.

> **Herman said:**
> Hello GoldenH,
If you install GRUB to MBR, Grub will install to the MBR and the next fifteen sectors of the first track of the hard disk right after the MBR as well as the Ubuntu partition.

If you know you have something in the first track of the hard disk, you can install LiLo instead, (if you use the 'Alternate' CD), which will make a backup of your MBR before it installs, and will not touch the rest of the fist track. [LiLo Page]("http://users.bigpond.net.au/hermanzone/p4.html").
Or you can use WinGRUB as already mentioned, or you can use GAG boot Manager from a floppy disk, [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm"). 

You can install GRUB to somewhere other than the MBR using the 'Alternate' CD, 
[Installing a Boot Loader for Ubuntu]("http://users.bigpond.net.au/hermanzone/p6.htm#Installing_a_Boot_Loader_for_Ubuntu").
                                            
[                                       If you choose <Yes>]("http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_Yes__to_Install_GRUBs_IPL_to_MBR") ( to Install GRUB's IPL to MBR)
                                            
[                                       If you choose <No>]("http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location") ( to Install GRUB's IPL to a custom location)
                                            
[                                       If you choose <Go Back>]("http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_Go_Back__to_Install_LILO_Boot_Loader") ( to Install LILO Boot Loader)


hmm maybe LILO? I hear I have to update it everytime I change the kernal though, I'm not sure I'm into that. But if I back up the entire first track via dd or another program, it doesn't matter which one i use, right? At this point it looks like I'll be using the WinGRUB, it seems to be what I want.   

> **Herman said:**
> It's rare to have anything in the first track of the hard disk to worry about. 
In some models of Toshiba laptop there's the 'Express Media Player'.
In a few older computers, 'On Track Disk Manager, software for helping Windows users overcome BIOS hard disk drive limitations, might also be occupying the first track of the hard disk, but that's not very common anymore these days and in any case, you won't need it after you install Linux. Presumably you'll be installing Linux beyond the  BIOS hard drive BIOS limit with a /boot partition inside the limit.

I don't know very much about RAID or LVM, or Mac mother boards.
For most people with a standard PC, it's easiest and best to install GRUB to MBR when you install Ubuntu.

What kind of MBR do you have and do you have something in the first track of the hard disk?
[quote=GoldenH]Acer MBR. So I'll lose some neat features I guess? Not sure how far the bios-mbr integration goes. And yeah, made a disc image, I can plug the drive into another computer and restore the image if worst comes to worst, but that's a pain in the butt! and won't get Linux running

An Acer MBR? All the Acers I have here come with a 'DOS' type MBR. You shoudln't have anything to worry about at all. I have an Acer Aspire 3003WLmi laptop, and Acer Aspire 16422WLMi laptop, and two Acer Aspire T310 Desktop computers all running Ubuntu just fine. I have also installed Ubuntu in several other Acer computers for friends without any problems at all.
As far as I know Ubuntu works very well in Acer computers and GRUB does too. In fact Ubuntu and GRUB are a huge improvement to them.

Unless you have something new and strange that I haven't heard of in this neck of the woods yet... (or actually in the Australian Outback really, but I don't think we're all that far behind these days), you have nothing at all to worry about.

It's good that you made a backup, everyone should always do that before they install.[/quote]

always make a backup ;) I've already made a backup with dd from the live CD, but I don't know if i can trust it...

My Laptop's actually came preinstalled with Vista on it. It's a Aspire 4720z. My research suggests
- Acer's Vista MBR is integrated with the Bios so that when you press ALT + F10 on the bios screen, it will load a special repair partition. 
- Installing XP or any other program which changes the MBR (including 3rd party boot apps, commercial or open source like GRUB) not only disables ALT + F10, AND prevents you from using the built in restoration software, it ALSO means that you can't use the Acer Restore DVD to restore Vista if for some reason you want it back.
- Acer provides no way to back up or restore this MBR, nor original installation disks for Vista, and the drivers won't seem to install on a fresh install (I've tried, don't understand this myself)
- It doesn't have a fit if you repartition (via GParted or other means) or if you change the boot options.

So basically unless I don't want Vista, EVER, I gotta keep the MBR or at least be able to restore it. And actually I do want it.

some links:
[http://global.acer.com/support/winvista/faq.htm#q0049](http://global.acer.com/support/winvista/faq.htm#q0049)
[http://forum.notebookreview.com/showthread.php?t=11476](http://forum.notebookreview.com/showthread.php?t=11476)

> **Herman said:**
> 
[QUOTE=GoldenH]The plan is to install ubuntu, if it fries the MBR then I'll find out if my utilities work and install XP too  :)
 "If it FRIES the MBR"? Good gosh man! What a ridiculous statement!
 Most of us around where  I live install Ubuntu and delete XP, but do as you like.
If you are going to have XP, then it's a little easier to have that installed first and then install Ubuntu after it, but you can do it either way.
[/QUOTE]

fries = overwrites ;) 

I will be keeping Vista because Acer only provides Vista drivers and I've had serious problems with Linux before not having drivers for my computer. Booting it in live CD certainly doesn't recognize anything it seems. Linux is great but not so much when it's crippled and I'm not awesome enough to write my own device drivers yet.

I am however pretty big into coding, big reason I got the laptop was to upgrade to a DX10 / 9c graphics card, play with XNA and Managed DirectX and stuff. Sorry but I don't think Linux's IDEs really compare with Windows', especially for forms-based applications. (Gnome and GTK+ make me sad :()

And of course certain programs that I love like mIRC, and Wine isn't perfect.

Linux has alot I do like of course, so don't take my ranting too badly ;) I'm really hoping that XEN works on this computer!


Well XP only should rewrite the first sector, so that's probably a 100% able to fix with dd. Maybe I should just cross my fingers ;) but I care less about XP than ubuntu.


> **Herman said:**
> 
[quote=GoldenH]
I've installed ubuntu before and stuff so its not like I'm completely new to this, but ubuntu seems to loooove grub more than some other distros i've used.

GRUB is the world's best boot loader and boot manager. What else would we want but the best? 
However, you have many other choices available to you if you want to use some alternative arrangement.

Regards, Herman :)[/QUOTE]

GRUB is pretty cool and i'd definately be using it if acer weren't enormous jackasses. However I don't want to take the chance of it not getting pass the BIOS screen because acer decided that it would be neat if they kept part of the bios in the mbr or something. Its got Software modem and Software network card and Software every other damn thing so I wouldn't put it beyond them to have Software BIOS, i've heard they exist.

But besides our ideological differences thanks for your help its been enormously useful!

---

### Post by Herman on 2007-11-30
Okay then, thanks for all that information, I'll be a little more understanding from now on when the next person comes along and has the same problem. 
I guess I am a little behind the times with technology and didn't realize it. Although, I wouldn't call making things incompatible an improvement at all.

There is one last possibiity that might interest you, this one's a really good one too, look into  [EasyBCD]("http://neosmart.net/dl.php?id=1"), (also linked to from my website),
[> ]("http://neosmart.net/dl.php?id=1")[EasyBCD]("http://neosmart.net/dl.php?id=1") is NeoSmart Technologies' multiple award-winning answer to tweaking the new Windows Vista bootloader. With EasyBCD, almost anything is possible. Setting up and configuring Windows boot entries is simple, and there is no easier way to quickly boot right into Linux, Mac OS X, or BSD straight from the Windows Vista bootloader - on the fly, no expert knowledge needed!
I'll bet you'll like [EasyBCD]("http://neosmart.net/dl.php?id=1")! 

Regards, Herman :)

---

### Post by Herman on 2007-11-30
Computerguru, the developer of [EasyBCD]("http://neosmart.net/dl.php?id=1"), is also a member of this web forum and I know he really provides good support for his product too. EasyBCD also has its own web forum.
Try [EasyBCD]("http://neosmart.net/dl.php?id=1"), I think that's just what you are looking for! :)

---

### Post by GoldenH on 2007-12-01
already made a copy of my mbr with that, i dunno if it works tho!

---

### Post by GoldenH on 2007-12-01
So last night I went and installed ubuntu via alternative cd on the end of the drive. all went well but when it asked me where to install grub I used Go Back to try and look at the partition list again, but then it had a fit and wouldn't let me go back without deleting the partitions and starting over. That was pretty lame but I did it and then I got grub installed on my linux partition. So then I rebooted, went to windows and I added it in EasyBCD. I didn't really expect that to work without any other installs but it did! pretty sweet.

Turns out it runs fine, except for my wireless card (here we go again....) which is much better than I expected!

---

### Post by Herman on 2007-12-01
Okay good! :)

You might have some fancy new wireless card too, but mine only took me five minutes to set up, here's how I did it, [Setting up my Acer Aspire Notebook for Wireless Networking in Ubuntu]("http://users.bigpond.net.au/hermanzone/p11.htm#wireless_network_configuration") :)

Regards, Herman :)

---

### Post by GoldenH on 2007-12-01
ah, broadcom! how I loathe thee. I had that on my last laptop. Something different this time, but I got it to work. still had to use ndiswrapper of course, the hard part was finding the driver.

looks like a bunch of stuff doesn't even *have* drivers yet (including the modem, which is bad as we don't have broadband out here), but the system is usable.

I've noticed some weird problems (after installing linux, the bios did NOT detect the hard drive), fortunately booting into acer restore and then canceling seems to have done whatever it needs to do to fix that.

---

### Post by Herman on 2007-12-01
I like Acer computers, the ones I have are all well supported by Ubuntu and Open Source software, I guess I'm just lucky.
My new computer is not an Acer, it's a custom made one without any Windows in it at all. It's quite modern and I was able to afford much better hardware by buying the parts separately and assembling them myself.  It worked out a lot cheaper without a proprietary operating system. Even though they pretend Windows comes free with a new factory built computer I really doubt that. Now that I'm reading your posts I am really thinking I made the right decision. Although it's a shame, because I did like Acer computers.

Bye for now, 
Regards, Herman :)

---

