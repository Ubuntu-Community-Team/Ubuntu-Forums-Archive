---
title: "Lucid Lynx Alpha 1 Released"
date: 2009-12-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by 23meg on 2009-12-10
Alpha 1, the first milestone of the Lucid Lynx development cycle leading to Ubuntu 10.04, has been released. Refer to the links below for more information:

[list] [*] [Release announcement]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-December/000651.html")
[*] [Technical Overview]("http://www.ubuntu.com/testing/lucid/alpha1")[/list]

---

### Post by philinux on 2009-12-10
> **23meg said:**
> Alpha 1, the first milestone of the Lucid Lynx development cycle leading to Ubuntu 10.04, has been released. Refer to the links below for more information:

[list] [*] [Release announcement]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-December/000651.html")
[*] [Technical Overview]("http://www.ubuntu.com/testing/lucid/alpha1")[/list]

Thanks Murat, I've been waiting for the official announcement.

I think I'll wait till the manual partitioning bug is fixed.

---

### Post by MacUntu on 2009-12-10
I guess I can now stop installing for Alpha 1 testing. :D

---

### Post by kansasnoob on 2009-12-10
> **philinux said:**
> Thanks Murat, I've been waiting for the official announcement.

I think I'll wait till the manual partitioning bug is fixed.

If you want to install with the CD you have it can be done. 

I wanted to install to two existing partitions, one as / and the other /home so instead of choosing format during manual installation I went to gparted and chose to format the / partition.

I then ran through the installation same as usual but left format unticked for both / and /home. I didn't plan on formatting /home anyway and I'd already formatted / using gparted.

A bit of a pain but it succeeded.

---

### Post by Gina on 2009-12-10
> **kansasnoob said:**
> If you want to install with the CD you have it can be done. 

I wanted to install to two existing partitions, one as / and the other /home so instead of choosing format during manual installation I went to gparted and chose to format the / partition.

I then ran through the installation same as usual but left format unticked for both / and /home. I didn't plan on formatting /home anyway and I'd already formatted / using gparted.

A bit of a pain but it succeeded.Thanks for the tip :)  I'll do that :)

---

### Post by Gina on 2009-12-10
> **23meg said:**
> Alpha 1, the first milestone of the Lucid Lynx development cycle leading to Ubuntu 10.04, has been released. Refer to the links below for more information:

[list] [*] [Release announcement]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-December/000651.html")
[*] [Technical Overview]("http://www.ubuntu.com/testing/lucid/alpha1")[/list]
Thanks very much for that :):)

---

### Post by philinux on 2009-12-10
> **kansasnoob said:**
> If you want to install with the CD you have it can be done. 

I wanted to install to two existing partitions, one as / and the other /home so instead of choosing format during manual installation I went to gparted and chose to format the / partition.

I then ran through the installation same as usual but left format unticked for both / and /home. I didn't plan on formatting /home anyway and I'd already formatted / using gparted.

A bit of a pain but it succeeded.

Spot on with diagnosis. Only needed to format / .

I'm installing from the cd now. :P

Nothing like a clean install for testing.

---

### Post by omgbots on 2009-12-10
I tried upgrading from karmic on a test box instead of a fresh install.  I saw in the notes that hal has been removed so I attempted to remove it and got:

```

~$ sudo dpkg --purge hal
dpkg: dependency problems prevent removal of hal:
 gnome-volume-manager depends on hal (>= 0.5.5.1); however:
  Package hal is to be removed.
 gnome-mount depends on hal; however:
  Package hal is to be removed.
 gnome-device-manager depends on hal.
 hwdb-client-common depends on hal.
 landscape-client depends on hal.
 sound-juicer depends on hal.
dpkg: error processing hal (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 hal

```

Were all of those dependencies removed from Lucid as well?  What about policykit and other hal packages like hal-info, libhal-storage1, and libhal1?

---

### Post by Psumi on 2009-12-10
bye-bye xfburn! You will not be missed. (it requires full hal support. It does not work in 9.10)

---

### Post by philinux on 2009-12-10
Successful install of alpha 1.

---

### Post by VMC on 2009-12-10
> **philinux said:**
> Successful install of alpha 1.
Same here, although I had a couple of Ubiquity crashes along the way. Eventually I first deleted the partition I wanted lucid on and it went without any troubles.

---

### Post by kansasnoob on 2009-12-10
I'm amazed at how stable the installed system seems to be.

On reboot I have blinding blocks of color while the system goes down but otherwise it seems great.

I even tried Brasero and it burned a good iso. I've never been able to get Karmic to do that!

The newest grub packages also seem to find existing OS's better.

For an Alpha 1 it's looking good!

I've just been thinking how retro I'll feel when I test the iso's for 8.04.4 in a few weeks :)

---

### Post by kevpan815 on 2009-12-10
I Installed Alpha 1 As An Upgrade From 9.10 Gold Using The Alternate CD Image As The Upgrade Mechanism, Worked Like A Charm, Just FYI.

---

### Post by ranch hand on 2009-12-10
Got it up and running here too.  FF seems to be a little buggy but everything else seems fine.

---

### Post by alexfish on 2009-12-11
> **kansasnoob said:**
> I'm amazed at how stable the installed system seems to be.

On reboot I have blinding blocks of color while the system goes down but otherwise it seems great.

I even tried Brasero and it burned a good iso. I've never been able to get Karmic to do that!

The newest grub packages also seem to find existing OS's better.

For an Alpha 1 it's looking good!

I've just been thinking how retro I'll feel when I test the iso's for 8.04.4 in a few weeks :)

  Screen Shots Screen Shots PLEEEEASE

---

### Post by Gina on 2009-12-11
> **ranch hand said:**
> Got it up and running here too.  FF seems to be a little buggy but everything else seems fine.I've had problems with FF crashing now and again for some time on my 64 bit system.

---

### Post by rbmorse on 2009-12-11
Had a mostly good install, too.  Grub-update took _forever_ and I had to wait for more than 30 mins for the language packs to download...is this necessary since I specified a language when the installer started?  I saw the skip button, but was afraid I'd leave the installation in an indeterminate state and I didn't want to do that. 

Couple of things:

Evolution's ability to import Outlook .pst files is broken.  Could be because the source file is from the Microsoft Office 2010 beta.  This worked in Koala with Office 2007 files. Investigating.

Takes a LONG time before Grub posts the boot menu.  I'll check launchpad, but this could be a holdover bug where the boot MBR is on one physical device and the rest of the boot code is on another. This was a problem in Koala, but I thought it had been solved. 

My new, shiny ATI HD5850 video card is not supported by the default video driver for ATI cards. 2D at the desktop works, just at the wrong resolution (which can't be adjusted).  I suppose I could fix this manually. 

Other than that, the Lynx appears to be off to  great start!  Congratulations to the dev teams.

---

### Post by PaulInBHC on 2009-12-11
On my second reinstall of Karmic, I thought I could click the "skip" button to skip the language packs BUT instead it stops the install and takes you to the livecd desktop. Yes it took 30 minute for the packs, about an hour total.
Lucid (112009 version) did not take as long, maybe 1/2 hour +.

I have an old Radeon 7000 that does not have an ATI linux driver. I am using the xorg edgers without problems that I know of.

---

### Post by s_raghu20 on 2009-12-11
Hi,

I am Vista Business with Virtual Box 3.x

Downloaded the alpha cd image and attempted the installation. Few observations- 

1. During the isntallation process, there are still references to Karmic 9.x.. 

2. the whole experience is very very slow.. I have tried Ubuntu and other OSs in the same way (Vista + Virtual Box) earlier, but none has been as slow as this...  Should I be expecting the alpha to be slow anyway... or something is wrong ?  I wasnt sure, so I didnt go and log a bug about that.

Even installation of Virtual Box Additions took about 10+ minutes.

Can someone help understand pls...

regards
raghav..

---

### Post by VMC on 2009-12-11
> **rbmorse said:**
> ...is this necessary since I specified a language when the installer started?  I saw the skip button, but was afraid I'd leave the installation in an indeterminate state and I didn't want to do that.  I wondered that myself. Why install language other than the one selected.

> **PaulInBHC said:**
> On my second reinstall of Karmic, I thought I could click the "skip" button to skip the language packs BUT instead it stops the install and takes you to the livecd desktop.  I was going to try the "skip" button for the language but decided not to. Lucky I didn't. That button shouldn't be called "skip", but rather "abort". Makes more since.

---

### Post by s_raghu20 on 2009-12-11
> **VMC said:**
> I wondered that myself. Why install language other than the one selected.

 I was going to try the "skip" button for the language but decided not to. Lucky I didn't. That button shouldn't be called "skip", but rather "abort". Makes more since.

For me the behaviour was diff. I pressed skip and it actually skipped. It was dead slow (see my previous post), but it did not abort and continued installing.. and did finish successfully...

---

### Post by ranch hand on 2009-12-11
I disconnected from the "net" and had no problems at all.

Updated when done and didn't see the language packs in the list.  I thought that they may have dropped that crap.

---

### Post by Gina on 2009-12-11
We never used to have that extended download before so why now?  That's what I wonder.

Nothing should NEED downloading during installation.  Many people will want to install on a box away from their router and only have a wireless connection.  In which case everything, including wireless drivers etc. must be installed before the wireless settings are carried out and a connection made.  I have two or three friends who have tried Ubuntu in the past and are in this situation.  Because they weren't able to get wireless running OOTB they gave up.  They were not impressed by my "complicated" work-around of downloading stuff on another computer and installing it manually. they still use MS software!

---

### Post by VMC on 2009-12-11
> **ranch hand said:**
> I disconnected from the "net" and had no problems at all.

Updated when done and didn't see the language packs in the list.  I thought that they may have dropped that crap.

Oh god! That's what I should have done, now that I think about it. Maybe I will re-install just to prove a point. That language nonsense takes the most of the install time.

---

### Post by Gina on 2009-12-11
> **VMC said:**
> Oh god! That's what I should have done, now that I think about it. Maybe I will re-install just to prove a point. That language nonsense takes the most of the install time.Yes indeed!!  Something I didn't think of either.  We are having a change round of rooms and I shall have one desktop in a room without network cabling.  I would prefer not to run a loose cable round the house.  I'll try a reinstall on my AMD64 first and see how it goes.

---

### Post by andrewabc on 2009-12-11
Yah, I installed ubuntu 9.04 to an SSD of mine back late October.

I timed the installation. I had livecd, so the time it takes to get to livedesktop +
10 minute to install to SSD
10 minutes to scan the mirror
2 minutes to finish the installation (last 10% or so after scan mirror)

Not sure if in scan mirror was the language stuff (probably named different in 9.04 compared to 9.10).

---

### Post by rbmorse on 2009-12-12
> **rbmorse said:**
> 

Takes a LONG time before Grub posts the boot menu.  I'll check launchpad, but this could be a holdover bug where the boot MBR is on one physical device and the rest of the boot code is on another. This was a problem in Koala, but I thought it had been solved. 


Well, this morning it would not get past "starting GRUB" even though I left it sitting while I took the Border Collies' for their morning run. Any O/S that can't boot in the time it takes me to run a couple of miles is broken.

---

### Post by kevpan815 on 2009-12-12
I Just Tried A Clean Install Using The Alternate CD, And The Darn Machine Is Stuck At Setting Up Users And Passwords, With No Hard Disk Drive Activity! Anyone Else Having The Same Problem?

---

### Post by kevpan815 on 2009-12-13
I Am Now Trying An Upgrade From 8.04.3 RTW, Using The Alternate CD, Which Is NOT Going As Smoothly As My Previous Upgrade From 9.10 RTW, Just FYI!

---

### Post by ssulaco on 2009-12-17
Runs fine live on an Emachine with Nvidia Geforce,installed restricted driver (live)....attempted to log out and it locks up,cant log back in to activate driver.
it actually loads pretty quick live.

It does the same thing on a Dell GX260 with Nvidia Geforce

---

### Post by Dougie_Fresh on 2009-12-19
just finished the download of the iso! clean install on my old comp in t-minus 10 minutes! and theres gonna be no hal? what is hal?

---

### Post by VMC on 2009-12-19
> **Dougie_Fresh said:**
> just finished the download of the iso! clean install on my old comp in t-minus 10 minutes! and theres gonna be no hal? what is hal?

[Hardware Abstraction Layers]("http://www.open-mag.com/features/10_02feats/HAL/HAL.htm") :P

---

### Post by mlnease on 2009-12-19
Hello,

Just finished downloading 9.10 Alpha 1 via Transmission bittorrent client.  It took several days (running all night every night) with my backwoods ISP but was well worth it.  Burned the image in Gnomebaker (since Brasero still won't burn data discs in Karmic).  Restarted and thought it had hung but after a minute or two it booted up nicely (except for the same garbled sound accompanying the Ubuntu splash screen as in Karmic).

I'm keen to upgrade and am well enough backed up to chance it.  A couple of questions:

(a) Should it work well to install it side by side with Karmic for dual boot (and will Ubuntu handle the partitioning automatically?  I've no experience partitioning).

(b) If I add the live DVD to repositories in Karmic, can I upgrade directly from the live DVD?

and (c) I think there's an official forum thread somewhere for discussion of the upgrade experience (s there is for Karmic) but can't seem to put my finger on it.  Can anyone advise me?

Looks great so far, thanks and congrats to the dev teams.

mike

---

### Post by ranch hand on 2009-12-19
You would be doing well to dual boot.  This is early days.  Expect breakage.

We would have to know a lot more about your system to give advise on partitioning.

What size is your HDD?  What is on it?  How was it installed?  Little things like that.

A screen shot of gparted at full screen would be nice.

---

### Post by mlnease on 2009-12-19
> **ranch hand said:**
> You would be doing well to dual boot.  This is early days.  Expect breakage.

We would have to know a lot more about your system to give advise on partitioning.

What size is your HDD?  What is on it?  How was it installed?  Little things like that.

A screen shot of gparted at full screen would be nice.

Thanks RH.  As you can probably see, I'm not a particularly sophisticated user.  Here's the screenshot--I appreciate your time and patience.

mike

---

### Post by ranch hand on 2009-12-19
Can you get us a shot of the whole thing?  That one doesn't give much info.

Or you could run this script and post the results that you will find on your desktop;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

or both.

If your image is too big you can use gimp and reduce the size of the file by saving at a lower quality.  This is all in the "save as" stuff that pops up when you save a file there.  Pretty easy to get hold of by experimenting.  Just leave your origanal alone and always save to a slightly different name so that you can go back to the first one.  Just try the things out on your desktop to see how they will look on the screen.

Check the size of the image in the "image" menu on the top bar of the image in gimp.  Down at the bottom of that menu is "Image Properties" that will tell you the size of the file.

You can drop it a long ways without really noticing any difference on a monitor.  The files are large to start with as you may want to print them and that is more demanding.

To open your screen shot in gimp will be tough.  Right click on the image and then click on open with gimp.

---

### Post by VMC on 2009-12-20
> **mlnease said:**
> Hello,

Just finished downloading 9.10 Alpha 1 via Transmission bittorrent client.  ...
Hopefully that's a typo or you wasted all the those days downloading. 9.10 is Karmic and its been released. Far from the alpha days.

If that was a typo and you did in fact download 10.04 Lucid alpha, then I would suggest making another partition and install it there.

I noticed that you don't have any Windows installed. That's a plus.

BTW- we have the same system except mine is 2.6mhz.

---

### Post by ptitlouis on 2009-12-20
Hi there


i'm new to the board

i need help to install ati driver for my fresh install of Kubuntu 10.04

First of all my card is a HD4870 vaporx 2go and my mainboard is a Msi P45D3 Platinum

For example on Ubuntu 9.10 i successfully installed drivers via envy or via System/Driver hardware but my movies never played smoothly, always some kind of horizontal bars/split during fast/action scenes

I guess the HD4870 isn't good enough for Linux even if she show very good results on recents games under windows vista/7...

Do i need to create a new topic to get some help to install correctly my ati drivers on Lucid (i alreday tried with envy, but never reboot so i -just- made a fresh re-install) or would anybody help me here ?

Thanks from France

And sorry for poor english !

Edit: just ftried the gutsy guide method: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Gave me the following error: "The distribution Kubuntu is not supported Removing temporary directory: fglrx-install.mxYbTL"

---

### Post by VMC on 2009-12-20
> **ptitlouis said:**
> ...i'm new to the board...Why are you starting out with a development testing distro and not a more mature released one, like Jaunty or even Karmic?

Are you an experience Linux user?

---

### Post by Cam42 on 2009-12-20
Anyone tried to install it in Virtual Box? I'm considering trying Kubuntu Lucid as a Guest on a Windows XP host (School stuff requires XP)

---

### Post by childresspta on 2009-12-20
I just installed from disk, installation went great, but I am getting that color grid when I pull up system monitor like we did when 9.10 came out.

---

### Post by PaulInBHC on 2009-12-20
> **childresspta said:**
> I just installed from disk, installation went great, but I am getting that color grid when I pull up system monitor like we did when 9.10 came out.

For me in Karmic, that was an ATI driver problem. In Lucid I am now using the xorg-edgers stuff. I haven't seen the grid at all with Lucid though.

---

### Post by cookiecruncher on 2009-12-30
Attempted to run the Kubuntu 64bit version of LL (live), but get nothing but command prompt.  I then downloaded the Ubuntu 386 version and get the same result.


My hardware:--->
Nvidia 9600GT
Monitor: LG Flatron L192WS (1440 x 900)
CPU E7400 C2D 2.8GHz
MSI MoBo (G31M3-F V2)
3 GB RAM
Logitech USB mouse
PS2 Keyboard


Rather weird :confused:

Installed the Ubuntu LL i386 edition in Virtualbox...no problems.

Currently have Kubuntu 9.10 installed and working well.

---

### Post by ranch hand on 2009-12-30
Was this the A1 release or a daily build.  There are problems with both, depending on your hardware, so you may want to try the daily.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by cookiecruncher on 2009-12-30
> **ranch hand said:**
> Was this the A1 release or a daily build.  There are problems with both, depending on your hardware, so you may want to try the daily.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)


I downloaded the latest release today (30/12/2009) from the above link and get the same results :( ... low graphics mode.

EDIT:
Removed my graphics card (Nvidia 9600GT) and connected the monitor to the onboard graphics (intel) and now I get as far as a login screen, but no matter what I enter, I get no further.  Do I need to enter a login name?   CTRL-ALT-F1 gives me usable command line with 'ubuntu@ubuntu'.

---

### Post by kevpan815 on 2010-01-01
> **Cam42 said:**
> Anyone tried to install it in Virtual Box? I'm considering trying Kubuntu Lucid as a Guest on a Windows XP host (School stuff requires XP)  The Ubuntu Staff requested that we install alpha 1 on actual machines, just fyi.

---

### Post by kevpan815 on 2010-01-01
> **kevpan815 said:**
> The Ubuntu Staff requested that we install alpha 1 on actual machines, just fyi. P.S. You might try a Dual Boot if you don't have 2 computer's.

---

### Post by kevpan815 on 2010-01-01
I finally had a successfull clean install of Alpha 1 today after I re-downloaded it today.

---

### Post by tad1073 on 2010-01-02
sure has pretty quiet in the Alpha 1 forums so far, other than video driver problems and samba!!!

---

### Post by Gina on 2010-01-03
Lucid is continuing to work flawlessly on my laptop - I'm using it all the time I'm on that machine.  I did have to use legacy grub as grub2 refused to work.

As for my AMD64 (the other machine I use for testing) I haven't been able to get it working due to the graphics problem.  I'm not trying anything that's not in the standard Lucid repositories.

While this situation continues I have nothing new to report.

---

### Post by jerrylamos on 2010-01-03
2.6.32-7 and 2.6.32-9 both boot to black screen on this i845G video graphics.  Can't get them to go nohow.  Period.

The Lucid daily build CD at 2.6.32-7 level only boots if I key in a xorg.conf with driver "vesa".

Installed 2.6.33rc2 from
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
as detailed in bug #420594

After a "freeze", took batch buffer dump, and a couple failed boots now running O.K.

?

Jerry

---

### Post by rbmorse on 2010-01-05
How we lookin' for Alpha TWO on the 14th?  Any rumors?

---

### Post by hyde0429 on 2010-01-06
So in the upcoming LTS release, would it be possible for the issue of legacy ATI display issues to be resolved? I have a machine that I am leaving on Intrepid unfortunately until the Mobility Radeon 9600 chipset in it can be supported with a decent driver. 

I've been banging my head as much as everyone else about that one. Machine is a laptop, so a vid upgrade is out of the question.

Any thoughts or anything known about this?

---

### Post by vrkalak on 2010-01-06
I have been using Xubuntu Lucid, since it first went into Alpha 1.
_Upgraded_ from Xubuntu-Karmic via Terminal.

I have had absolutely no problems with Xubuntu-Lucid ... in fact, I find Lucid to be more stable than Karmic ever was.  And, it's still in Alpha 1.

I'm looking forward to going into Alpha 2 in a few days.  :P

---

### Post by Ibidem on 2010-01-08
I've run Lucid in Virtual Box (Netboot install); I can only install from a sub-500 MB image, so I wanted to make sure it would boot & that there were no major issues before spending the hours on a network install (if only I could do those over wireless!).
"Plymouth" is broken there; I know that ath5k for kernel 2.6.32 works, but not *sure* about my intel 945 graphics.  
So  perhaps I'll try it soon on hardware.

---

### Post by kevpan815 on 2010-01-09
> **Ibidem said:**
> I've run Lucid in Virtual Box (Netboot install); I can only install from a sub-500 MB image, so I wanted to make sure it would boot & that there were no major issues before spending the hours on a network install (if only I could do those over wireless!).
"Plymouth" is broken there; I know that ath5k for kernel 2.6.32 works, but not *sure* about my intel 945 graphics.  
So  perhaps I'll try it soon on hardware.

I am running Lucid on a Dell XPS 630I and a NVIDIA GeForce 8800GT with the 195.30 Beta Device Driver 4 it from [http://www.nvidia.com/](http://www.nvidia.com/) and have only 2 miner problems (and 1 of them is indeed with Plymouth NOT working)!

---

### Post by kevpan815 on 2010-01-09
> **rbmorse said:**
> How we lookin' for Alpha TWO on the 14th?  Any rumors?

According 2 the Lucid release schedule we should in indeed see Alpha 2 on the 14th as long as there are no show stopper bugs preventing a Mile Stone Alpha release!

---

### Post by kevpan815 on 2010-01-09
> **jerrylamos said:**
> 2.6.32-7 and 2.6.32-9 both boot to black screen on this i845G video graphics.  Can't get them to go nohow.  Period.

The Lucid daily build CD at 2.6.32-7 level only boots if I key in a xorg.conf with driver "vesa".

Installed 2.6.33rc2 from
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
as detailed in bug #420594

After a "freeze", took batch buffer dump, and a couple failed boots now running O.K.

?

Jerry

Are you aware that RC3 is now available on the website that you just mentioned? Just FYI!

---

### Post by Ibidem on 2010-01-11
I installed Lucid on real hardware a few days back; it works very well.  The "Plymouth" issue is very minor; the audio was muted on first boot.  I needed usbmount to access flash drives, but...
AA1/ZG5 AR5007 wireless reported as AR5001 (wrong, but not significant), Realtek 8102E ethernet, Realtek ALC268 audio, i945GME graphics, 160 GB HDD; running multiboot (LL, Kuki, TCL, FreeDOS, XP, recovery).

---

