---
title: "Weird story: A setting in bios blocks every OS install except Vista!?"
date: 2008-04-01
forum: Installation &amp; Upgrades
---

### Post by BoilingFrogs on 2008-04-01
Ok so I’ve got a Dell Dimension E520. I don’t have the specs right now but it’s a decent machine. However, I happened to buy this pc right on the week that Dell stopped shipping XP and switched to shipping exclusively Vista. Like anybody that wants to use his or her pc, the first order of business was to get rid of vista. I attempted to install XP, but it insisted the hard drive was corrupt or missing altogether. Vista would reinstall every time without a problem. I tried formatting, partitioning, reformatting… over and over with the vista CD. No matter what, the Vista could install, but none of the three xp CDs I had would work. So I grabbed a copy of mandrake I had sitting around, since I figured Linux could push through anything. Well that didn’t work either. It had the same problems XP had. I think I even tried OSx86 at one point. Eventually I dug through the Bios and found the setting for ‘SATA Operation’. I switched it from ‘RAID on’ to ‘RAID Autodetect/ ATA’. Then magically XP installed with no problem. 

It’s been a bit more than a year now and I was just fed up with XP and was lured back to Linux. I downloaded the most recent appropriate Ubuntu install CD. I attempted a dual boot without removing my original xp installation, but Ubuntu’s partition tool made an insane mess of my hard drive; it created like 6 unusable partitions. It eventually gave up and I found my xp installation was toast. So now I’m back to trying to install Ubuntu & xp. I have the same problem as before; I change that setting in the bios and nothing but Vista installs… I change it back and xp installs with no problem. However no matter what I do Ubuntu refuses to install. I’ve never seen xp handle an odd problem that Linux couldn’t.

This is what Ubuntu does when it attempts to install:
After the initial loading screen and before it loads the GUI, it runs through that list of stuff it has to do. In the midst of that it fills up the screen with lots of variations of these two lines:

“Buffer I/O error on device sr0 logical block 306443”
“SQASHSHFS error: unable to read cache block”
(Paraphrased)

It soldiers on through the list and gets a few more things to get the ‘OK’ and spits out a few more errors like that and one that says its unable to create some folder or something. Finally it loads the UI. I attempt to install, just for kicks and it starts out fine. Then it tries to load the Partition tool. It freezes at 6% when loading. It stays like that for at least 10-15 minutes. Once the partition tool opens and it shows my hard drive, it doesn’t matter because it says it is unable to write to the drive anyway. I’ve changed settings in the bios, I’ve formatted it, run tests on the HD, etc. No matter what I do Ubuntu refuses to work and does essentially the same thing every time. Yet for some reason if I change that one setting in the bios, xp installs fine. 

So that’s my story. I was fed up with windows so I got Ubuntu. My first try destroyed my xp installation and a years worth of customization and work (130 Gb) and now Ubuntu wont even install on my PC, but the lesser xp installs fine. Right now I’m typing this on my friends Laptop, because I have nothing on my computer working right now… and this thing is running Vista! Please somebody help!!!

PS I had a few other problems with the dell initially and convinced them to credit me $100 and send me a new pc about a month after I got it, but the setting in the bios remained a constant problem in both computers.

---

### Post by mrsteveman1 on 2008-04-01
This is an SATA controller problem, the setting you changed puts the SATA controller into emulation mode so that native SATA drivers aren't needed for XP.

The old XP disks didn't have the SATA driver for the chipset, so they couldn't see the hard drive, but putting the chipset into emulation mode usually works, though you don't want to do this if you can avoid it.

Linux is likely the same situation, there might not be a driver for your chipset on the older livecds, and perhaps even the newer livecds have drivers but they might not work well, perhaps some kernel boot options are needed to fix things.

What chipset is this anyway? You can find out in Windows vista or XP by going into the device manager and looking around. It is likely an ICH-8/9 intel chip, or an Nvidia MCP.

---

### Post by twright on 2008-04-01
have you tried wubi?

you can just install XP normally and put ubuntu in a folder on the same partition, just run wubi.exe off the ubuntu disk

---

### Post by BoilingFrogs on 2008-04-01
Wow, its such a relief to at least see somebody make some sense of it. Those Dell folks told me it was impossible and that I must be lying. It'd be amazing if there was a solution too... that included Ubuntu.

I can't get to my specs for at least another hour, cuz i currently don't have an OS installed. I'm pretty sure its an Intel PentiumD @ 2.8GHz if that helps at all.

---

### Post by BoilingFrogs on 2008-04-01
This is the first I've heard about wubi. I'm pretty new to Linux in general and totally new to Ubuntu. I just go through cycles once a year or so, i get ticked and install a random Linux distro. Eventually I fall back into xp. I was hoping this would be the last time.I'll give this wubi a try though.

---

### Post by kushykush on 2008-04-01
I do not understand why anyone would like to uninstall a system that came with the machine.  It is basic that you cannot uninstall an operating system. I also did not understand that if you had to go back to Windows XP then why did you not let Vista remailn intact.  After all Vista is a vast improvement over XP especially when it comes to working with newer hardware.

I will not comment on your other situations.  All I know is that I had Vista installed on my first drive. I installed Unbuntu on my second Sata drive.  Ubuntu's GRUB recognized Vista and left it alone.  Contrast this with Suse and Fedora which needlessly messed with Vista's MBR.  The result was I lost my Vista and Suse could not boot from the hard drive either.  Then I got Ubuntu because on one of the websites the guy explained how Ubuntu would install the GRUB properly.  It did.  Ubuntu's GRUB menu brings up both Vista and the Ubuntu installs.  I have since then edited the /boot/grub/menu.lst to make Vista as the default because children prefer that. 

The only drawback is that Ubuntu is now occupying all of my second Sata drive (160 gig of real estate).  I installed Gpart.  It shows both my drives.  It correctly shows the Windows NTFS partition on the first drive and it shows the Ubuntu partitions on the second drive.

But Gpart will not let me shrink the Ubuntu partition on the second drive.  Why is that so?  Can someone tell me how to shrink this partition and make room for more Linux distros?  Do not get me wrong.  I love Ubuntu, but I just want to experiment with SUSE.

Also how do I identify the root partition if I am able to shrink and install?

---

### Post by BoilingFrogs on 2008-04-03
So what are these kernel boot options? I got wubi to work and its definitely a cool idea, I'm using it right now actually... but i would really like to install this thing properly if its at all possible.

---

### Post by mrsteveman1 on 2008-04-03
What boot options are you referring to? The BIOS setting?

---

### Post by BoilingFrogs on 2008-04-03
> **mrsteveman1 said:**
> ... and perhaps even the newer livecds have drivers but they might not work well, perhaps some kernel boot options are needed to fix things.


Thats the tip i was referring to, maybe i just misunderstood. At this point I'll try anything though, even if i am utterly confused.

---

### Post by mrsteveman1 on 2008-04-03
Ahh ok.

I'm actually curious about this error you posted before:
```

Buffer I/O error on device sr0 logical block 306443
SQASHSHFS error: unable to read cache block

```

That sounds like the cd is corrupt, perhaps you should try burning it again at a lower speed? You can also try running the cd check when the cd itself boots, it should tell you if it is ok.

---

### Post by BoilingFrogs on 2008-04-03
Yeah those two lines were the bulk of the errors. Also i left out that each line was actually preceded with numbers similar to an ip adress 23.004 etc. It just repeated those two lines over and over with the numbers gradiually going up each time until it finally loads the gui. Then it ends up freezing when it tries to partition the disc. 

I'll definitly download and burn a fresh copy right now, and run the check too. I saw that option the first time, but thought it'd all work out. 

Thanks for the advice, I hope it works out. The only thing that keeps me from getting my hopes up right now though,  is that Mandrake couldn't install either and I've never had a computer that wouldn't let me at least install the operating system Ive wanted, but then again Ive never had a Dell. [crosses fingers]

---

### Post by mrsteveman1 on 2008-04-04
Find out what chipset the system has, if its really new its probably an ICH8/9 if its an intel chipset.

You probably don't have to download the iso again, you can check it to see that its ok by getting the md5 from the ubuntu site and checking it against the iso you have, if you are using Windows there are a few programs that will hash files for you, [hashtab]("http://beeblebrox.org/hashtab/") is one, another is [winmd5]("http://www.blisstonia.com/software/WinMD5/").

This will tell you if the ISO is ok so you dont have to grab another one.

---

### Post by BoilingFrogs on 2008-04-04
So i think i finally dug up the chipset: ICH8   So, what does this mean for me... am i screwed or is there a common fix/ workaround?

---

### Post by SteveHillier on 2008-04-04
> **BoilingFrogs said:**
> Ok so I’ve got a Dell Dimension E520. I don’t have the specs right now but it’s a decent machine. However, I happened to buy this pc right on the week that Dell stopped shipping XP and switched to shipping exclusively Vista. Like anybody that wants to use his or her pc, the first order of business was to get rid of vista. I attempted to install XP, but it insisted the hard drive was corrupt or missing altogether. Vista would reinstall every time without a problem. I tried formatting, partitioning, reformatting… over and over with the vista CD. No matter what, the Vista could install, but none of the three xp CDs I had would work. So I grabbed a copy of mandrake I had sitting around, since I figured Linux could push through anything. Well that didn’t work either. It had the same problems XP had. I think I even tried OSx86 at one point. Eventually I dug through the Bios and found the setting for ‘SATA Operation’. I switched it from ‘RAID on’ to ‘RAID Autodetect/ ATA’. Then magically XP installed with no problem. 


I never expected to find the answer to a WIndows prolem on a Linux forum.
I have a similar situation on a Fujitsu machine that was brought in.  The customer wanted Vista removed and XP put on.  It would go through all the oinstall OK but then not see a boot disk.
You are a star!!

---

### Post by SteveHillier on 2008-04-04
> **kushykush said:**
> I do not understand why anyone would like to uninstall a system that came with the machine.  It is basic that you cannot uninstall an operating system. I also did not understand that if you had to go back to Windows XP then why did you not let Vista remailn intact.  After all Vista is a vast improvement over XP especially when it comes to working with newer hardware.
Vista may be OK in a standalone setup and I have shipped a few copies like that but it is a pig in a mixed platform network, slow, cumbersome, overweight.
Vista just isn't for everyone and the problem is when you buy from one of the big boys the O/S comes preinstalled and you are not in control.
I detest recovery disks that zap everything rather than allowing you to repair the O/S without hitting user data.  I detest the way they partition disks so that they use 40Gb of an 80Gb disk for system and the other half for recovery.  On laptops they often have left the disk formatted with FAT32 when NTFS would be more appropriate.
I don't like running a machine according to someone elses ideas, I like to set it up for myself and this is where Ubuntu comes in.

---

### Post by mrsteveman1 on 2008-04-04
The last release of Ubuntu, Gutsy 7.10, should support the ICH8 chipsets completely, since they predate Gutsy by a fair margin. If the os can see the disks, I'm sure thats not the problem. I think the best thing to do is verify you have a good ISO file with the md5 available from the ubuntu download site, burn the disk again at low speed making sure the burner verifies the disk, then when you boot the new CD, select the option to check the disk from the boot menu. If that all works ok, go on to installing ubuntu again and it should be ok.

Linux is better about chipset support than XP was at one point, you either had to use the recovery disks that came with the box, which is not an acceptable option in an circumstance, or you had to customize the CD with drivers slipstreamed into it just to get the installer to see your hard drives.  XP has some serious issues with SATA drivers and installing windows, because XP predates a lot of common SATA controllers, so XP disks have no drivers for them and can't be easily installed in native mode. Thats what the bios setting changes, it causes the chipset to emulate IDE which XP understands.

Be really careful with that bios setting though, if you set it to IDE mode and then install windows, and change it back to SATA native later, windows will refuse to boot.

---

