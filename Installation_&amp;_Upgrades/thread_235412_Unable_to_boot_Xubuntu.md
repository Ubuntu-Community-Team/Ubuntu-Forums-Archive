---
title: "Unable to boot Xubuntu"
date: 2006-08-13
forum: Installation &amp; Upgrades
---

### Post by haider on 2006-08-13
Hi,
New here and a bit new with Linux as well. To the point. I finished downloading Xubuntu yesterday and prepared my PC to have both XP and XU together. I left 10GB for XU and got the rest of the Hard up and running for XP.

Once I finished downloading the iso (xubuntu-6.06-i386 Desktop Version) I performed an md5sum check to see if everything was hunkydory and it matched the one on the net so I figured everything was ok and got to burning it to disk. I burned at as low as possible to make sure no errors came in my way.

I'm finished with XP and got the partitions all set up for it and have now placed the Xubuntu cd in the drive. XP immediately detects it increasing my enthusiasim! I reboot and find myself facing something I had never expected. On booting from CD I saw the booting process started as two lines of text came at the bottom of the screen one saying something about Debian and the other started with extracting. I couldn't note the entire line as right after that in like a milisecond the entire screen went blank and the CD stopped being read by my Drive and the PC's processing light wasn't blinking.

Somethin' Wron' Here! What gives? I tried it on my brothers PC and those two lines didn't even come up the Drive just kept on spinning that CD to oblivion! The CD is still alive though and I'm still getting those two lines followed by Linux's Void! What do I do?? I want to use Ubuntu and I downloaded that iso in like a week :(

Is there anyway to install Xubuntu from the Hard Drive? I hear theres some software called instlux that installs Linux from Windows is that good and will it solve my problem?

Reply Please :(:(:(

---

### Post by randell6564 on 2006-08-13
> **haider said:**
> Hi,
New here and a bit new with Linux as well. To the point. I finished downloading Xubuntu yesterday and prepared my PC to have both XP and XU together. I left 10GB for XU and got the rest of the Hard up and running for XP.

Once I finished downloading the iso (xubuntu-6.06-i386 Desktop Version) I performed an md5sum check to see if everything was hunkydory and it matched the one on the net so I figured everything was ok and got to burning it to disk. I burned at as low as possible to make sure no errors came in my way.

I'm finished with XP and got the partitions all set up for it and have now placed the Xubuntu cd in the drive. XP immediately detects it increasing my enthusiasim! I reboot and find myself facing something I had never expected. On booting from CD I saw the booting process started as two lines of text came at the bottom of the screen one saying something about Debian and the other started with extracting. I couldn't note the entire line as right after that in like a milisecond the entire screen went blank and the CD stopped being read by my Drive and the PC's processing light wasn't blinking.

Somethin' Wron' Here! What gives? I tried it on my brothers PC and those two lines didn't even come up the Drive just kept on spinning that CD to oblivion! The CD is still alive though and I'm still getting those two lines followed by Linux's Void! What do I do?? I want to use Ubuntu and I downloaded that iso in like a week :(

Is there anyway to install Xubuntu from the Hard Drive? I hear theres some software called instlux that installs Linux from Windows is that good and will it solve my problem?

Reply Please :(:(:(

What exactly do you mean "XP detects it"? XP should not be detecting anything if you are just putting the xubuntu cd into your cdrom and booting.

You should be booting right to the xubuntu cd!  Is your bios configured to boot from cd first?  Because you should not see any references to XP when you boot from your xubuntu cd. Xubuntu will however recognize XP and then, I believe will ask you questions pertaining to the Grub boot loader.

---

### Post by haider on 2006-08-13
> **randell6564 said:**
> What exactly do you mean "XP detects it"?
Xp detects it as in XP can read the CD clearly i.e. I can view all the contents of the CD and so can 2000 (on my brothers PC) but when I put the CD in for booting I can't boot from it, those two prelimanary booting lines come up and then a blank screen.

My PC is set to boot from CD first then from HD I've had it set like that ever since I got it. I tried booting Suse LiveCD and that worked but still Xubuntu doesn't.

My PC's specs are like so:

Pentium 3 933MHz
256MB RAM
40GB HD

I'm certain Xubuntu can work on this machine but so far it's not.

---

### Post by randell6564 on 2006-08-13
> **haider said:**
> Xp detects it as in XP can read the CD clearly i.e. I can view all the contents of the CD and so can 2000 (on my brothers PC) but when I put the CD in for booting I can't boot from it, those two prelimanary booting lines come up and then a blank screen.

My PC is set to boot from CD first then from HD I've had it set like that ever since I got it. I tried booting Suse LiveCD and that worked but still Xubuntu doesn't.

My PC's specs are like so:

Pentium 3 933MHz
256MB RAM
40GB HD

I'm certain Xubuntu can work on this machine but so far it's not.

So you mean that you logged onto your XP desktop and viewed the contents of the xubuntu cd?  Because that would be the only way that XP would come into the mix here.

This xubuntu cd.,is it an Iso file that you burned to a cd?

Because all you have to do with a linux installation is put the cd into the drive and it should boot.  Windows has absolutely nothing to do with it.

---

### Post by Tom Brokaw on 2006-08-13
How long are you giving it to spin?  Live CDs take a long time to load.  And, it doesn't sound like this is the problem, but you burned the ISO as a disk image, not as data, right?

---

### Post by randell6564 on 2006-08-13
One more thing.  Are you saying that you installed xubuntu and then after rebooting, you could not boot to xubuntu?  Because after the install you need to remove the xubuntu cd before rebooting.

I'm just not quite sure what exactly you are doing.

---

### Post by haider on 2006-08-13
From the start.

I downloaded Xubuntu ISO from Ubuntu Site.

I checked the md5sum of the iso using fsum and the result was positive.

I burned the iso in the form of disk image to cd at the lowest possible speed.

I wanted to have XP and Linux on the same HD so I cleaned the HD and partitioned for Windows leaving space for Linux.

I Installed XP and formatted the FAT32 partitions to make them active.

I placed the Xubuntu CD into the drive and saw that XP was able to access the CD, I could see all the contents of the CD.

I restarted the PC and saw that instead of booting to linux it stopped in between (those two lines).

After that all I could see was a blank screen. I could not install Linux because I can't do anything all that I have in front of me is a black screen.

Right now I have only Windows installed no Linux that is the problem i can't boot the cd actually the appropriate thing to say is that the cd is being booted but it stops as soon as the booting process starts.

What do I do?!

---

### Post by haider on 2006-08-13
I think I might have just found out what the problem is. I copied the CD and burned another one on a different brand of writable disks and xubuntu actually booted on my brothers PC!

I immediately took it out and checked it on my PC, nothing there. Same ol' problem! Now I placed that CD back in my brother's PC and selected the option where it checks whether the CD is ok. The screen turned to the xubuntu loader screen and everything on the cd was being checked out to see if they were ok. A few things came up as *mismatch* instead of *ok* so I guess the download was to blame or the cd I wrote to in the first place.

Well I don't have the xubuntu iso anymore so I'm downloading ubuntu instead. I can convert ubuntu to xubuntu right? Just need to add xfce instead of gnome or kde right??

---

### Post by llamakc on 2006-08-13
Yes. After you have installed you can add the metapackage xubuntu-desktop which will provide all of the necessary packages you need.

---

### Post by orb9220 on 2006-08-13
And it is always good idea starting out to be able to boot into two  different desktops.

Since you will most likely doing something to mess it up. Happens alot when learning and configuring things that you quite not have a full understanding.

I have my Gnome desktop which I like but have a xfce desktop too.

---

