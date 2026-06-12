---
title: "Dual Boot install OS not found"
date: 2019-12-26
forum: Installation &amp; Upgrades
---

### Post by jgwphd on 2019-12-26
I just purchased a DELL XPS 8930 with a 256GB SSD and a 1T HDD. It has a NVIDIA GeForce GTX 1650 graphics card installed. It came with Windows 10 installed. I have done a number of dual boots on prior machines for myself and friends and family using the live CD/USB. Sometimes I just erase windows other times I do a dual boot (but this is the first time with two storage devices: SSD and HDD). 

The Bios boot menu tells me that "Boot mode is set to: UEFI; Secure boot: ON". BTW, in Bios under UEFI options it shows 5 boot choices: 

windows boot manager, 
onboard nic (IPV4), 
onboard nic (IPV6), 
USB1 - UEFI OS (Generic Flash Disk 8.07) and  
USB2 - UEFI OS (Generic Flash Disk 8.07). 

I find the last two UEFI boot option entries strange in that they appear to be duplicates. I only have a single copy of Ubuntu 19.10 on a USB drive plugged in (if I pull out the USB drive the last two entries don't show up under UEFI options). With the USB drive plugged in I can use either of the last two UEFI boot menu options to get to GNU GRUB version 2.04. Then i have to use the "safe graphics" option or else I get a bunch of unreadable dots, dashes and lines on my screen.  Also, using windows (Dell Update) I updated all the firmware when I first turned on the machine. 

 I generally spend 99.999% of my time in Ubuntu but I occasionally use Windows for an old application I use (every few years). I'd like to keep windows around (just in case) and use dual boot in this configuration. But, When I bring up the Ubuntu installer it doesn't detect any OSes and during the attempted install I get a message "This computer currently has no detected operating systems"[COLOR=#000000] (that's as far as I got and I cancelled the install at that point). What is the easiest and simplest way to get a dual boot installed for my configuration?  I appreciate any help and suggestions. [/COLOR]

---

### Post by CatKiller on 2019-12-26
> **jgwphd said:**
> It has a NVIDIA GeForce GTX 1650 graphics card installed.... Ubuntu 19.10... I get a bunch of unreadable dots, dashes and lines on my screen.  

The 19.10 install image *contains* the proprietary driver, but it can't *use* the proprietary driver: if it did it wouldn't work with non-nvidia graphics. You'll still need to use nomodeset for the actual install.

> **jgwphd said:**
> It came with Windows 10 installed.... When I bring up the Ubuntu installer it doesn't detect any OSes and during the attempted install I get a message "This computer currently has no detected operating systems"

You need to turn off Fast Startup in Windows and shut it down properly for the windows partitions to show up. You'll also likely need to install an AHCI driver in Windows and set the drive to AHCI in the BIOS.

---

### Post by oldfred on 2019-12-26
In addition Dell often needs UEFI update & SSD firmware update.

        Installing Ubuntu 18.04.2 on Dell 8930 with dual boot win10
[https://ubuntuforums.org/showthread.php?t=2413145](https://ubuntuforums.org/showthread.php?t=2413145)

Issues are often common by brand, with bigger differences if AMD or Intel based.

       
 Dell XPS 8920 desktop GTX 1060, needed UEFI/BIOS update
[https://ubuntuforums.org/showthread.php?t=2370434](https://ubuntuforums.org/showthread.php?t=2370434)
Dell XPS 8920 & Nvidia GTX 1060 & PCIe M2 drive Raid change to AHCI
[URL="https://ubuntuforums.org/showthread.php?t=2360929"]https://ubuntuforums.org/showthread.php?t=2360929
      [/URL]
 Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en) 
    [URL="https://ubuntuforums.org/showthread.php?t=2360929"]
[/URL]

---

### Post by jgwphd on 2019-12-26
Some additional questions where CatKiller mentioned "...You'll still need to use nomodeset for the actual install."... is this what the GNU GRUB version 2.04 does for me when I use the "safe graphics" option?   ...or is this something I have to set somewhere else? 

If I turn off "Fast Startup in Windows" do I leave it off permanently? 

AHCI driver (Advanced Host Controller Interface)    ...I can't find it in Windows for the "Drives"  (...I suspect because it is not there) but I don't see any mention of it in Bios either. Bios does say "SATA Operation     [RAID on]" if that matters? Do I still need to install this driver? 

I assume that having "Boot mode is set to: UEFI; Secure boot: ON" is NOT a problem ...so I don't need to change these options and use legacy boot? Just checking because I am not completely sure what all these boot options do, ...and when I am not clear about how something works it's always easy to blame it for the problem  :-)

---

### Post by crip720 on 2019-12-26
Can turn on "fast start up" after, but with it on you cannot read or write to window partition from ubuntu.  I think you need "raid" off, but have someone else check this, had to turn raid off with my dell, but it had ahci option in bios.  Secure boot can be off or on, I like it to be off.  Leave UEFI on, windows is loaded that way and you will have problems if you don't load ubuntu the same way.

---

### Post by oldfred on 2019-12-26
Several sets of instructions on Windows AHCI. Mostly similar.

       Windows AHCI instructions
[https://askubuntu.com/questions/1148120/ubuntu-18-0x-not-detecting-windows-ssd-during-installation](https://askubuntu.com/questions/1148120/ubuntu-18-0x-not-detecting-windows-ssd-during-installation) & 
[https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on#963100](https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on#963100)
[https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/](https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/)
AHCI enable - May have to unlock bitlocker if used
[https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243](https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243)
[https://www.tenforums.com/tutorials/22631-enable-ahci-windows-8-windows-10-after-installation.html](https://www.tenforums.com/tutorials/22631-enable-ahci-windows-8-windows-10-after-installation.html)

---

### Post by jgwphd on 2019-12-26
Holy cow! ..this is complicated. So now I have to screw with windows ....which is what I am trying to get away from. ....Ok, ...I guess I'm stuck and hopefully won't make a mistake :-)   So far, I found fast startup and figured out how to turn it off (it was hidden under power button definitions and greyed out etc... I hate windows).   

My steps will be: critiques appreciated.     BTW, how do I know if "bitlocker" is being used (indicated by oldfred)?  I am very cautious and want to do this in independent stages (check and make sure the system works after each stage). First stage fix AHCI windows issue (using instructions at: [https://askubuntu.com/questions/1148...g-installation]("https://askubuntu.com/questions/1148120/ubuntu-18-0x-not-detecting-windows-ssd-during-installation") from oldfred)

 
[LIST]
[*]Boot to Windows with your current SATA controller configuration 
[*]Open Device Manager 
[*]Expand Storage Controllers and identify the Intel SATA RAID Controller 
[*]View properties of the identified controller 
[*]On the Driver tab, click the Update driver&#8230; button 
[*]Browse my computer&#8230;, Let me pick&#8230; 
[*]Uncheck Show compatible hardware 
[*]Select Microsoft as manufacturer 
[*]Select Microsoft Storage Spaces Controller as model # 
[*]Accept that Windows cannot confirm that this driver is compatible 
[*]Save changes, reboot to BIOS and change RAID SATA Controller to AHCI 
[*]Save changes and reboot normally, hopefully to Windows 
[/LIST]
  Now you should be able to install Ubuntu in a dual-boot configuraion

Did the above and now I am stuck in an "**inaccessable_boot_device**" situation ...... HELP!

UPDATE: **CAUTION: The above instructions will leave you with a system that won't boot! ** ...and I did each listed bullet item **exactly**. Trying all the variations I could in BIOS with SATA options of RAID and AHCI did not help. The only silver lining to this effort is that Dell has a system restore facility available in the boot menu that has repair options which I tried and didn't work only the selection, of last resort, to reinstall the latest and greatest windows version finally recovered my system. Before I did this I left the BIOS settings to AHCI anticipating (and hoping) that when windows was reinstalled by the Dell recovery it would install the the correct drivers for SATA AHCI. Which looks like it happened.

---

### Post by crip720 on 2019-12-26
Did have similar experience trying to install Ubuntu on my new refurb dell.  By the time googleing and doing boo-boos, ended up deleting windows and then installing Ubuntu.  Left space on ssd to install windows in the future if needed.  If remember correctly, think three different bios options had to be changed, ahci, a fast startup option and I think a usb option.  Was not used to a bios having so many options.

---

### Post by jgwphd on 2019-12-26
I left an update in _**my**_ previous post: 
 
UPDATE: **CAUTION: The above instructions will leave you with a system that won't boot! ** ...and I did each listed bullet item **exactly**.  Trying all the variations I could in BIOS with SATA options of RAID and  AHCI did not help. The only silver lining to this effort is that Dell  has a system restore facility available in the boot menu that has repair  options which I tried and didn't work only the selection, of last  resort, to reinstall the latest and greatest windows version finally  recovered my system. Before I did this I left the BIOS settings to AHCI  anticipating (and hoping) that when windows was reinstalled by the Dell  recovery it would install the the correct drivers for SATA AHCI. Which  looks like it happened.

---

### Post by jgwphd on 2019-12-26
crip720 - Since you mentioned USB, did you see two strange UEFI boot option entries in that they appear  to be duplicates, similar ro what I found: 

USB1 - UEFI OS (Generic Flash Disk 8.07) and  
USB2 - UEFI OS (Generic Flash Disk 8.07). 

I only have a single copy of Ubuntu 19.10 on a USB  drive plugged in (if I pull out the USB drive the last two entries don't  show up under UEFI options). With the USB drive plugged in I can use  either of the last two UEFI boot menu options to get to GNU GRUB version  2.04. very strange but now you have me wondering if I need to change some setting that effects USB??? Anyone else have any experience with this situation?

---

### Post by crip720 on 2019-12-27
I think I had to adjust something in bios for it to see/read the installer USB, but did not have your boot options.  It might be saying you can use the USB as USB speed 1 or USB speed 2.  If it was a USB 3 stick, maybe three options would show up, but does seem weird.  I am just guessing, so I might be way off base on what is happening.  It is seeing the USB as bootable, so I would not change any bios USB settings.

---

### Post by jgwphd on 2019-12-27
Thanks crip720 that covers my Bios questions - which, BTW, my BIOS does have settings to make the USB ports bootable and they were already on. 

**One more question for anyone.** With my 'first" dual drive situation (SSD and HDD). I have windows using up all my SSD and the Ubuntu installer only gives me the HDD as an option of where to install Ubuntu. Do I need to first make some free space on the SSD for the Ubuntu installer to offer that as an installation choice (and allow the drive to be adjusted for space)? if I don't need to make free space then how do I get the installer to see the SSD as an installation choice if windows occupies all the space. And if free space is necessary for the installer to identify the SSD as a choice, can I make the free space using Gparted or Disks (available on the installer USB) or should I do that using windows (just to be cautious). Thanks for any assistance.

---

### Post by crip720 on 2019-12-27
If possible I would recommend using windows tools to shrink/fix windows.  If windows not booting, just delete/format and use gparted to make partitions.  / on ssd and /home on HD.  Leave free space on ssd to install windows after.  This for a new windows computer with no data on it.  Leave EFI partition alone, unless you want to make a new one.  / partition I recommend more than 25GBs.  The installer should also give option to install over windows.  I usually use the "something else"  option to give more control(sometimes bad idea).

---

### Post by oldfred on 2019-12-27
We always suggest using Windows to shrink NTFS partitions. Occasionally users get a corrupted Windows when using gparted. Then they blame Linux. But if shrinking with Windows and issue, then we know it originally was a Windows issue anyway.

Have you updated UEFI & SSD firmware. Often firmware updates are required for installer to see SSD.

You are the first one I have seen with issues on conversion to AHCI. 
But the Dell user in post #3 used the other safeboot method in some of the posts that have two methods.  I will make sure to suggest that in future.

---

### Post by jgwphd on 2019-12-27
Thanks for all the help. I have now cleared space on the SSD and installed Ubuntu. Windows comes up fine. Now I have two situations: 

First, when I am plugged into the HDMI Nvidia card for Ubuntu boot, I only get a flashing curser on the screen. I did click on the radio button to install proprietary drivers and  during the install.  I saw messages about Nvidia being configured and  installed.  BTW, I am using a Samsung 32" 4K display (3840x2160 67.4Khz 30Hz) if that makes any difference? ...I tried plugging in a 1080P display with the same results from the Nvidia card.

Second, When I plug into the mother board HDMI port I get to the purple Ubuntu log in screen but it won't let me log in. I do not get a GRUB screen and goes directly to Ubuntu (It seems my machine has primary and secondary video ports, NVIDIA is primary the other display ports are secondary - for example I can only see the BIOS from the primary NVIDIA ports ...FWIW). When I enter my password the screen flashes and comes right back to the PW prompt on the purple screen. ...I also  tried plugging in a 1080P display with the same results too.   ...a little desperation   :-)  

Also during install I got a new (to me) "Perform MoK management" screen. Do I need to enroll MOK, key or hash or continue boot? I just selected continue boot (maybe that is part of my PW problem). I reinstalled Ubuntu twice with the same problems (I was thinking I put in the wrong PW that first time). But I am stuck either way using NVIDIA or not. Any suggestions on which way to proceed?

---

### Post by CelticWarrior on 2019-12-27
> **jgwphd said:**
> (...) Do I need to enroll MOK, key or hash or continue boot? I just selected continue boot (maybe that is part of my PW problem). I reinstalled Ubuntu twice with the same problems (I was thinking I put in the wrong PW that first time). But I am stuck either way using NVIDIA or not. Any suggestions on which way to proceed?

Yes or, much simpler, disable Secure Boot in UEFI settings. One or the other enables loading the proprietary Nvidia drivers that you need and likely already installed but not being loaded due to Secure Boot. Yes, this is also the reason why you can't login properly.

---

### Post by CatKiller on 2019-12-27
> **jgwphd said:**
> Thanks for all the help. I have now cleared space on the SSD and installed Ubuntu. Windows comes up fine. Now I have two situations:  

Which should go in new posts: those who might help with an installation question aren't necessarily the same people that might help with a graphics question or a secure boot question, and people that come later looking for solutions to their problems aren't going to find them in a sprawling thread that covers multiple topics. 

> First, when I am plugged into the HDMI Nvidia card for Ubuntu boot, I only get a flashing curser on the screen. I did click on the radio button to install proprietary drivers and  during the install.  I saw messages about Nvidia being configured and  installed.  BTW, I am using a Samsung 32" 4K display (3840x2160 67.4Khz 30Hz) if that makes any difference? ...I tried plugging in a 1080P display with the same results from the Nvidia card.

Second, When I plug into the mother board HDMI port I get to the purple Ubuntu log in screen but it won't let me log in. I do not get a GRUB screen and goes directly to Ubuntu (It seems my machine has primary and secondary video ports, NVIDIA is primary the other display ports are secondary - for example I can only see the BIOS from the primary NVIDIA ports ...FWIW). When I enter my password the screen flashes and comes right back to the PW prompt on the purple screen. ...I also  tried plugging in a 1080P display with the same results too.   ...a little desperation   :-)   

That's a symptom of your X server crashing; the login screen is the first thing that gets shown so, when you log in and the X server crashes that's where you start again. There's currently something hinky with your graphics setup, potentially around Optimus or the nvidia driver failing to load, but you probably guessed that already. 

> Also during install I got a new (to me) "Perform MoK management" screen. Do I need to enroll MOK, key or hash or continue boot? I just selected continue boot (maybe that is part of my PW problem). I reinstalled Ubuntu twice with the same problems (I was thinking I put in the wrong PW that first time). But I am stuck either way using NVIDIA or not. Any suggestions on which way to proceed?

The Machine Owner's Key is a way to cryptographically sign modules loaded at boot time for secure boot. You can either disable secure boot or go ahead and tell your machine that the key you're using is legit. Depending on how strict your secure boot implementation is it might either just put up a warning message about an unsigned module, or it might prevent it from being loaded at all. The lack of that module could be the cause of your hinky graphics.

---

### Post by jgwphd on 2019-12-27
@CelticWarrior Many Thanks ...a question about Ubuntu installer and some recent changes. I noticed during the install that if I checked "install third-party software for graphics..." It has a sub-question to check for "Configure Secure Boot" and then requires a password (I did this before). This time around I am reinstalling Ubuntu without checking "configure secure boot". Will that give me the same result that you are suggesting by disabling secure boot in BIOS?

---

### Post by CelticWarrior on 2019-12-27
No.

Either disable Secure Boot or configure it (MOK). *without checking "configure secure boot" *will result in the exact same situation as before.
Also please read carefully the much more informative CatKiller's post and the suggestions about how to better use the forum.

---

### Post by crip720 on 2019-12-27
Found with 19.10 logon asks for user name first, then password.  Confusing at first when for years you just put in password.  Something to look for.

---

### Post by jgwphd on 2019-12-27
**Success!** Once I finally turned off Secure Boot in BIOS (as CelticWarrior suggested). FYI, this triggered security/re-authentication activity in windows. Once I got past that windows authentication issue, then both systems now boot and display fine.   :-) 

Many Thanks and BTW, I agree with CatKiller's post. I was wondering during this installation exercise if I should start a new question on part of an ongoing series of problems relating to an install attempt on a different forum thread because I am having issues in a different system area. I decided that it would be confusing since "the whole story" is in one thread and maybe what I did prior to the "next problem" showing up once I got past the old one is the root cause. You guys are suggesting that is a bad idea and that if I have a series of issues during an attempted install, I should treat each one as a separate forum question to tap into the best expertise. 

During this install I had to get into windows, resize partitions, BIOS and Ubuntu to get to the system configuration I wanted. I am now a quasi-expert on windows recovery, BIOS trial and error and Ubuntu installer options ....at least for a day or two  :-)     

Finally, **I sincerely appreciate everyone's help and patience** with my questions. You guys are awesome for the assistance you provide on the forum. **Many Many thanks!!!!!!**
 
BTW, Dell saved my butt by having a robust recovery program. I have learned that the  end result of attempting to change windows storage device drivers combined WITH new BIOS changes will likely  result in a reinstall of windows and all the associated headaches etc. Also, I think I should start any future dual boot install by first turning off secure boot.

---

### Post by CatKiller on 2019-12-27
Glad to hear you're up and running. 
> **jgwphd said:**
> 
Many Thanks and BTW, I agree with CatKiller's post. I was wondering during this installation exercise if I should start a new question on part of an ongoing series of problems relating to an install attempt on a different forum thread because I am having issues in a different system area. I decided that it would be confusing since "the whole story" is in one thread and maybe what I did prior to the "next problem" showing up once I got past the old one is the root cause. You guys are suggesting that is a bad idea and that if I have a series of issues during an attempted install, I should treat each one as a separate forum question to tap into the best expertise. 

It's a judgement call. The priories here are that the poster should get help with their issue and that later people with the same issue should be able to find solutions that work.

So if there are a cluster of related issues with an underlying cause they can go in the same thread, or a poster can refer to a prior thread and link to it to catch people up to where they are. 

A new issue should go in a new thread so that people that *just* have that issue can find it later, and so that people that know how to fix the issue can find it, too.

Making solved threads as Solved also helps later forum users to find the solutions that work.

---

