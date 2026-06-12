---
title: "Ubuntu 16.04 install without converting to UEFI"
date: 2016-06-13
forum: Installation &amp; Upgrades
---

### Post by kenm2 on 2016-06-13
There are many conversations online regarding Ubuntu with Windows in UEFI mode. I see nothing, clear at least, describing the same in legacy mode.
 
So a very basic question: How do you install Ubuntu 16.04 64-bit onto a prepared unformatted partition alongside Windows 7 64-bit without it converting the current legacy BIOS setup to UEFI?

My Windows 7 is installed on the very first partition (no small recovery partition exists). I need Ubuntu on the next partition, and then an old Windows XP 32-bit on a third partition. Previously it had been the Windows 7, ubuntu (32-bit), and XP.

There are a few scare-stories of people installing the new Ubuntu and ending up with UEFI.

So, other than the 64-bit, I need to keep it old-school: BIOS and MBR - not UEFI and GPT. This way I can keep my new and old software and peripherals on one computer. Is this possible?

Thanks. You folks are very appreciated!!

---

### Post by oldfred on 2016-06-13
How you boot install media, for both Windows & Ubuntu is how it installs.
So just be sure to boot Ubuntu installer in BIOS/Legacy/CSM boot mode.

But if you have newer system, you should be using AHCI for drives. But unless you slipstream drivers into XP when you install, you cannot turn on AHCI with XP.
It really is time to retire XP.

About 5 years ago I still had my XP on a BIOS/MBR drive, but had Ubuntu in BIOS boot mode on a gpt partitioned drive. Later started converting all drives to gpt and including both bios_grub for BIOS and ESP - efi system partition for UEFI, so drive could be moved to newer UEFI system and not have to be totally erased/repartition/reformatted.

You do have 4 primary partition limit. And Windows only boots from a primary partition. Alway best to have Windows in primary partitions and use the extended/logical partition for Ubuntu.

Show 14.04, but 16.04 essentially the same.
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html) 
      
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[URL="https://help.ubuntu.com/community/Grub2/Installing"]https://help.ubuntu.com/community/Grub2/Installing

[/URL]
 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/](http://www.multibooters.com/) 

[URL="https://help.ubuntu.com/community/Grub2/Installing"]
[/URL]

---

### Post by grahammechanical on 2016-06-14
UEFI is a boot system. It is a program in an integrated circuit on the motherboard. The Ubuntu installer does not convert to UEFI mode. The user has to make a setting in the UEFI boot system utility to switch between EFI boot & BIOS/Legacy boot.

GPT partitioning is part of the UEFI specification. If the hard drive has GPT partitioning then the Ubuntu installer will make use of it. The installer will not change the partition table from GPT to MBR. Or, the other way around. The user has to do that using a partition utility.

The specification includes backward compatibility with motherboards that have BIOS boot systems. So, we can have GPT partitioning with a BIOS motherboard.

If the motherboard has a BIOS boot system then Ubuntu will not, in fact cannot, convert the installation into a UEFI install. There is only one install mode with a BIOS motherboard.

I have a BIOS motherboard. Do you? I have Ubuntu installed on a hard drive with MBR partitioning and also on a hard drive with GPT partitioning. With MBR partitioning I think about Primary, Extended and Logical partitions. With GPT it is a matter of having the partitions I need and a bios_boot partition.

The situation changes if we have a UEFI motherboard.

> Having a PC with UEFI firmware does not mean that you need to install Ubuntu in UEFI mode. What is important is below:  


[LIST]
[*]if  the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too. 
[*]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. 
[*]if  Ubuntu is the only operating system on your computer, then it does not  matter whether you install Ubuntu in UEFI mode or not. 
[/LIST]



[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by kenm2 on 2016-06-14
oldfred and grahammechanical: Your responses are really appreciated, and some of your links are valuable in that they haven't turned up in my extensive Googling. 
 
Yes, I have 32-bit XP on an install DVD to which I slipstreamed AHCI. I *would* retire XP, except I can't afford to upgrade my Photoshop 6 and Premiere 6 software, nor replace my two old scanners, one which scans photo slides, which I'm still digitizing. I'm retired, so I can't afford retiring my toys! (GIMP, etc, are goals, but I'm studying 3D animation with Daz3D and Carrara - my brain is at its limit). 
 
The 4 primary partition limit isn't a problem because I use a second HD for regularly-used data.  
 
Apparently the scare-stories of a 64bit Ubuntu installation automatically converting users' systems to UEFI were the fault of the users, not Ubuntu. So I'll take the info you folks have offered here - and then do a test run by cloning Win7 to a clean drive and trying to add Ubuntu there... I trust you, I just don't trust myself! Thanks everyone!

---

### Post by oldfred on 2016-06-15
If you have multiple drives, often best to keep Windows on one drive and Ubuntu on another drive.
But if a shiny new SSD, then you may want both systems on same drive.

Only if newer hardware that is UEFI and CSM can you install in both or either boot mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

### Post by kenm2 on 2016-06-15
(I'll repost elsewhere if this is the wrong place, since I declared it "Solved"):

oldfred: I exchange data drives depending on the work. Each job involves using Windows (without security junk) for offline work and Ubuntu for online. It's hard to describe in brief, but really, this is the quickest way. The case would become a bit crowded, anyway, with 3 drives.

OK, now for the biggie: This may not be worth fixing, but my curiosity... I went ahead and installed Ubuntu, without testing first on a spare drive. 
 
This is a desktop (i5-2500K, 8G RAM, GTX-750Ti) which has had Windows 7, 64bit, dual-booted with Ubuntu 14.04, 32bit, for a couple of years. All's been fine.

In Win7, I deleted all the non-C: partitions. I then fixed the resulting boot problem with Boot-Repair, and then installed Ubuntu 16.04, 64bit, via "Something Else." (40G root, then 8G swp). It worked fine until I let it install some large security (etc) updates. When it was finished, the screen went blank. No mouse clicks or keyboard taps brought it back.

I waited at least 10 minutes. I forced a restart, and it came up blank. I put the DVD back in and rebooted. The option for Live Session came up but when I chose it and waited, it resulted in the same blank screen. Black.

So I swapped that DVD for my Ubuntu 14.04 32bit DVD. Its Live Session worked fine, as always. I then tried the installed Ubuntu again. Same blackness.

Any clues there? Windows, swp and root are all on their own primary partitions. That's not a clue; I just thought I'd mention it.

Way back in Ubuntu 12.04, I tried 64bit and it had the CPU usage meters pegging, so I've used 32bit since. Is that a clue? I don't think so.

Does anyone have any thoughts about this? If it's a bum video driver update, I'll give up for sure - it's a bad sign for the future. But how could that effect the Live Session? Very Curious.

Thanks for any thoughts you folks might have. Cheers.

---

### Post by oldfred on 2016-06-15
Not sure if you got video driver update.
It used to be a big issue with the 750Ti nVidia.
Did you install the nVidia driver from repository or add ppa to get a very new nVidia driver?

Can you boot second entry or recovery mode? That already has nomodeset. 
If that works add nomodeset or from recovery mode add ppa and new nVidia driver.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown and other boot parameters
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Even newer nVidia card, only could install with Intel video, then convert to nVidia.

 Ubuntu 16.04 LTS installation problem with GA-Z170X-UD5 TH & GTX 1080

These are now older, as standard Ubuntu 16.04 has many of the updates needed.

 Maxwell 750 - kernel 3.15 or newer required
[http://ubuntuforums.org/showthread.php?t=2300218](http://ubuntuforums.org/showthread.php?t=2300218)
[http://ubuntuforums.org/showthread.php?t=2292419](http://ubuntuforums.org/showthread.php?t=2292419)
[http://ubuntuforums.org/showthread.php?t=2214805](http://ubuntuforums.org/showthread.php?t=2214805)
[http://ubuntuforums.org/showthread.php?t=2265505](http://ubuntuforums.org/showthread.php?t=2265505)
Usually better to use PPA.
[http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)
[http://ubuntuforums.org/showthread.php?t=2257506](http://ubuntuforums.org/showthread.php?t=2257506)
[http://ubuntuforums.org/showthread.php?t=2261714](http://ubuntuforums.org/showthread.php?t=2261714)
[http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1](http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1) 


[http://ubuntuforums.org/showthread.php?t=2327648](http://ubuntuforums.org/showthread.php?t=2327648)

---

### Post by kenm2 on 2016-06-16
oldfred: 
After installing Ubuntu 16.04, the only thing I did was allow the large update to occur. I only assumed there was a video driver update at fault.

I saw your response this morning and decided to try the recovery mode, as you suggested. Well, instead, it booted up fine without any added steps. I'm currently running the beautiful new X. Xerus, or Xenial X.

But before it came up, there was a split-second grainy-white screen with text in the upper left. I could only catch "Clearing original..." I think it was repeated several times.

BTW, I added System Monitor, and so far the CPU usage is very low - no spiking meters! (unlike 14.04 64bit).

I thank you so much for your response(s). Your latest links should help with future problems if they occur. I'll study them soonly, whatever the case.

However, if this isn't stable and does require much added work, I 'll go back to 14.04 for a few months, instead. I'm so far behind in my *real* studies that I'm already forgetting basic need to knows (old brain doesn't retain).

Thanks again! Cheers.

---

### Post by kenm2 on 2016-06-17
Just a comment to finalize this thread. I'm going back to 14.04. 

Most of my bootups lock on a black screen, requiring a restart and recovery mode. Other times I get a grainy white screen which sits there for varying amounts of time and eventually becomes the normal screen. This is not stable enough for me.

I'm keeping oldfred's links and suggestions for the future, but I prefer not to trust 16.04 until it's a lot more stable. But there are other reasons.

I do a lot of wysiwyg html editing as part of my various studies and tutorial preps. Kompozer is not available from "Ubuntu Software," nor can I figure out how to force it to appear, much less than work, via Synaptic. It was beautiful in 14.04. It was clean without so much as a single line of unnecessarily added junk. LibreOffice is pathetic with the junk. Seamonkey installed but showed up nowhere.

I love everything else so far with 16.04, but too much time has been lost fighting this thing. There are other small complaints, some silly, but things I got used to with 14.04 (like creating a document on the desktop and not having it appear far from the spot where you clicked for it to appear). 

So thank you very much oldfred and the other folks who offered advice. You are appreciated. This new version, though, should be left to those who have more time to learn Linux in detail than I have. Cheers.

---

