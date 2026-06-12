---
title: "Karmic Koala Alpha 2 Released"
date: 2009-06-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nhandler on 2009-06-11
[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-June/000578.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-June/000578.html)

> Hello Ubuntu developers,

Welcome to Karmic Koala Alpha-2, which will in time become Ubuntu 9.10.

Pre-releases of Karmic are *not* encouraged for anyone needing a stable
system or anyone who is not comfortable running into occasional, even
frequent breakage.  They are, however, recommended for Ubuntu developers and
those who want to help in testing, reporting, and fixing bugs.

Alpha 2 is the second in a series of milestone CD images that will be
released throughout the Karmic development cycle.  The Alpha images are
known to be reasonably free of showstopper CD build or installer bugs, while
representing a very recent snapshot of Karmic. You can download it here:

  [http://cdimage.ubuntu.com/releases/karmic/alpha-2/](http://cdimage.ubuntu.com/releases/karmic/alpha-2/) (Ubuntu)
  [http://cdimage.ubuntu.com/kubuntu/releases/karmic/alpha-2/](http://cdimage.ubuntu.com/kubuntu/releases/karmic/alpha-2/) (Kubuntu)
  [http://cdimage.ubuntu.com/xubuntu/releases/karmic/alpha-2/](http://cdimage.ubuntu.com/xubuntu/releases/karmic/alpha-2/) (Xubuntu)

See [http://wiki.ubuntu.com/Mirrors](http://wiki.ubuntu.com/Mirrors) for a list of mirrors.

Alpha 2 includes a number of software updates that are ready for large-scale
testing.  Please refer to [http://www.ubuntu.com/testing/karmic/alpha2](http://www.ubuntu.com/testing/karmic/alpha2) for
information on changes in Ubuntu.

This is quite an early set of images, so you should expect some bugs.  For a
list of known bugs (that you don't need to report if you encounter), please
see:

  [http://www.ubuntu.com/testing/karmic/alpha2](http://www.ubuntu.com/testing/karmic/alpha2)

If you're interested in following the changes as we further develop
Karmic, have a look at the karmic-changes mailing list:

  [http://lists.ubuntu.com/mailman/listinfo/karmic-changes](http://lists.ubuntu.com/mailman/listinfo/karmic-changes)

We also suggest that you subscribe to the ubuntu-devel-announce list
if you're interested in following Ubuntu development. This is a
low-traffic list (a few posts a week) carrying announcements of
approved specifications, policy changes, alpha releases, and other
interesting events.

  [http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce)

Bug reports should go to the Ubuntu bug tracker:

  [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Enjoy,
-- 
Steve Langasek
On behalf of the Ubuntu release team

---

### Post by frustphil on 2009-06-11
DLing Kubuntu...:)

---

### Post by novafluxx on 2009-06-11
Still to early for me to jump on board! I still run a Windows and I want to try out grub2!

Congrats on the release though!

---

### Post by inportb on 2009-06-12
Nothing wrong with using Grub2 with Windows ;)

---

### Post by meeples on 2009-06-12
mmm karmic

---

### Post by andrewabc on 2009-06-12
I tested liveusb and it worked fine. Nothing much different that I could tell from jaunty. I guess it is all background stuff.

UXA is not running by default, so I have no idea how to get it running when on liveusb/cd. So I won't be able to test that until it is by default. I'm not going to install karmic on anything until alpha 5 or 6, depending if jaunty keeps working fine.

I'll keep testing the alphas (livecd/liveusb) on computers to make sure it boots up fine and stuff works.

So UXA is not enabled by default, but is DRI2 running by default? And I presume intel drivers are fixed (from regressions in jaunty)? So there should be performance enhancements, assuming you had regression in jaunty?

Also, I presume 10.04 is going to be LTS, so I'm guessing they are going to cram as much technology into 9.10 to make 10.04 more stable? As shown by choosing newest kernel for release, grub2, ext4, intel changes?

---

### Post by psyke83 on 2009-06-12
> **andrewabc said:**
> I tested liveusb and it worked fine. Nothing much different that I could tell from jaunty. I guess it is all background stuff.

UXA is not running by default, so I have no idea how to get it running when on liveusb/cd. So I won't be able to test that until it is by default. I'm not going to install karmic on anything until alpha 5 or 6, depending if jaunty keeps working fine.

I'll keep testing the alphas (livecd/liveusb) on computers to make sure it boots up fine and stuff works.

So UXA is not enabled by default, but is DRI2 running by default? And I presume intel drivers are fixed (from regressions in jaunty)? So there should be performance enhancements, assuming you had regression in jaunty?

Also, I presume 10.04 is going to be LTS, so I'm guessing they are going to cram as much technology into 9.10 to make 10.04 more stable? As shown by choosing newest kernel for release, grub2, ext4, intel changes?

The release notes on the Intel driver appear to be inaccurate (perhaps merely pasted from alpha 1). The fact is that the current 2.7.99x testing driver has completely removed support for DRI1/EXA; UXA/DRI2 is now the only choice.

UXA and DRI2 depend on each other, so your system is definitely using them.

---

### Post by whoop on 2009-06-12
> **novafluxx said:**
> Still to early for me to jump on board! I still run a Windows and I want to try out grub2!

Congrats on the release though!

You can test grub2 without touching your hd (iow, without changing anything on your machine).
You will need some usb-storage-device and boot this image from it:
[http://people.ubuntu.com/~cking/grub2-boot-tests/bootable-grub2-2.5GB.img.bz2](http://people.ubuntu.com/~cking/grub2-boot-tests/bootable-grub2-2.5GB.img.bz2)

Instructions:
[http://people.ubuntu.com/~cking/grub2-boot-tests/README.txt](http://people.ubuntu.com/~cking/grub2-boot-tests/README.txt)

---

### Post by andrewabc on 2009-06-12
> **psyke83 said:**
> The release notes on the Intel driver appear to be inaccurate (perhaps merely pasted from alpha 1). The fact is that the current 2.7.99x testing driver has completely removed support for DRI1/EXA; UXA/DRI2 is now the only choice.

UXA and DRI2 depend on each other, so your system is definitely using them.

Thanks for the info! Very good to know. Now I will put livecd in all my old intel machines (i845/915/945) to see what happens.

EDIT:
On pentium4 1.7ghz, the floppy drive kept making noises, trying to read from it, even though no media inserted. This was a constant tick tick tick with light on.
There is still shutdown internal speaker beep bug. Wireless seemed to work really well (better reception than jaunty?).
Did not shutdown properly, last thing on screen said acpi or something and I had to manually press power button. I think same happened on my new computer.

---

### Post by xXchibidudeXx on 2009-06-12
> **andrewabc said:**
> I tested liveusb and it worked fine. Nothing much different that I could tell from jaunty. I guess it is all background stuff.

UXA is not running by default, so I have no idea how to get it running when on liveusb/cd. So I won't be able to test that until it is by default. I'm not going to install karmic on anything until alpha 5 or 6, depending if jaunty keeps working fine.

I'll keep testing the alphas (livecd/liveusb) on computers to make sure it boots up fine and stuff works.

So UXA is not enabled by default, but is DRI2 running by default? And I presume intel drivers are fixed (from regressions in jaunty)? So there should be performance enhancements, assuming you had regression in jaunty?

Also, I presume 10.04 is going to be LTS, so I'm guessing they are going to cram as much technology into 9.10 to make 10.04 more stable? As shown by choosing newest kernel for release, grub2, ext4, intel changes?

go to a terminal and edit the xorg file
```
sudo gedit /etc/X11/xorg.conf
```at your default xorg under device should look like this
```
Section "Device"
    Identifier    "Configured Video Device"
```then go and add the UXA option.
```
Option        "AccelMethod"        "uxa"
```now the device section should look like this
```
Section "Device"
    Identifier    "Configured Video Device"
    Option        "AccelMethod"        "uxa"
```I have a intel card and use UXA on 9.04 and it works well. It makes things go much faster and flash video is much better too.

---

### Post by psyke83 on 2009-06-12
> **xXchibidudeXx said:**
> go to a terminal and edit the xorg file
```
sudo gedit /etc/X11/xorg.conf
```at your default xorg under device should look like this
```
Section "Device"
    Identifier    "Configured Video Device"
```then go and add the UXA option.
```
Option        "AccelMethod"        "uxa"
```now the device section should look like this
```
Section "Device"
    Identifier    "Configured Video Device"
    Option        "AccelMethod"        "uxa"
```I have a intel card and use UXA on 9.04 and it works well. It makes things go much faster and flash video is much better too.

There's no need to do that anymore. The default (and only) option is UXA now.

---

### Post by vaibhav on 2009-06-12
Compiz not working for me. Appearance -> Visual Effects shows "None". Trying to set it to "Normal" displays error "Desktop effects could not be enabled". Attached is the X log file. This worked for me in Hardy and Intrepid, but stopped working since Jaunty. I was hoping the recent Intel driver improvements would have solved this issue. Any pointers?

---

### Post by Anfanglir on 2009-06-13
Is the gma500 supposed to be suported by this intel driver? 

Compiz not working on my system either (running alpha 2 from usb_stick, Fujitsu u820, gma500).

---

### Post by xXchibidudeXx on 2009-06-16
xcompmgr works well with uxa and the intel cards. its not compiz, but it does at some effects.

---

### Post by Jekshadow on 2009-06-16
For those of us who want to keep our current setups, I think you can just do this to update to karmic from jaunty:

1) type "sudo update-manager -d" in a terminal

2) It should say "New distrobution release '9.10' is availible". Just click "Upgrade" and it will upgrade you from 9.04 to 9.10. 

3) Enjoy (and report bugs)

---

### Post by psyke83 on 2009-06-17
> **Jekshadow said:**
> For those of us who want to keep our current setups, I think you can just do this to update to karmic from jaunty:

1) type "sudo update-manager -d" in a terminal

2) It should say "New distrobution release '9.10' is availible". Just click "Upgrade" and it will upgrade you from 9.04 to 9.10. 

3) Enjoy (and report bugs)

If you like your current setup so much, think twice before upgrading it. Alpha 2 is still quite early in the development process and breakage is possible.

---

### Post by jerrylamos on 2009-06-18
> **psyke83 said:**
> If you like your current setup so much, think twice before upgrading it. Alpha 2 is still quite early in the development process and breakage is possible.

That's why I run triple boot.  One that works, jaunty or even intrepid on the Thinkpad R31 since jaunty & karmic "smear" fonts on the i830 video chip.  See bugzilla 21415 caching fix which is not on Ubuntu (yet? ever?),

One karmic that works more or less,

One karmic to put updates on.

This triple boot ran into trouble with Grub 2 (1.96 really) but the forums came through see the "Please help test Grub 2" thread.

Jerry

---

### Post by GeorgeVita on 2009-06-29
Hi,
I would like to test *Karmic Koala Alpha 2* and report a bug if any found. I am using a mobile broadband connection and it would be easier (less data) to upgrade than to download a full .iso file.

Is the 'upgraded' state the same as the 'Alpha 2 installation'? Will my 'bug report' be useful or I must have the same starting point with developers using the installation method?

Thanks,
George

---

### Post by andrewabc on 2009-06-29
> **GeorgeVita said:**
> Hi,
I would like to test *Karmic Koala Alpha 2* and report a bug if any found. I am using a mobile broadband connection and it would be easier (less data) to upgrade than to download a full .iso file.

Is the 'upgraded' state the same as the 'Alpha 2 installation'? Will my 'bug report' be useful or I must have the same starting point with developers using the installation method?

Thanks,
George

I wouldn't download alpha 2, since it is quite outdated (unless you got lots of bandwidth to get extra 200mb updates). I'd download dailycd.
[http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)

If you upgrade your jaunty to karmic, yes you will be using latest version. Although you could have more problems with the upgrade. Maybe download/burn the dailycd, and upgrade jaunty. If jaunty upgrade explodes you can install daily cd. :)

Be aware that testing karmic at the moment can be dangerous and expect to format the partition a couple times when things go wrong (usually easier solution than editing config files from command line).

I'm not sure what is up with the more than month between alpha 2 and 3. I guess alpha 3 should be the point when it gets a bit safer to use.

---

### Post by psyke83 on 2009-06-29
> **jerrylamos said:**
> That's why I run triple boot.  One that works, jaunty or even intrepid on the Thinkpad R31 since jaunty & karmic "smear" fonts on the i830 video chip.  See bugzilla 21415 caching fix which is not on Ubuntu (yet? ever?),

One karmic that works more or less,

One karmic to put updates on.

This triple boot ran into trouble with Grub 2 (1.96 really) but the forums came through see the "Please help test Grub 2" thread.

Jerry

That bug is fixed if you use the drivers from the xorg-edgers repository. For Jaunty you also need to upgrade to the 2.6.30 kernel, though.

---

### Post by zika on 2009-06-29
> **andrewabc said:**
> Be aware that testing karmic at the moment can be dangerous and expect to format the partition a couple times when things go wrong (usually easier solution than editing config files from command line).? To format the partition? Couple of times? Am I using the same Karmic You are talking about? People do call this "boring" version ... :)
Ususally easier solution than editing config files from command line ... ?
I must say here: -1 ...

---

### Post by GeorgeVita on 2009-06-29
> **andrewabc said:**
> I wouldn't download alpha 2, since it is quite outdated (unless you got lots of bandwidth to get extra 200mb updates). I'd download dailycd.
[http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)
...

As my intention is to do some tests, I will download/use the "daily" image. The target desktop is only for tests so I do not care about possible troubles.

Thanks,
George

---

### Post by andrewabc on 2009-06-29
> **zika said:**
> ? To format the partition? Couple of times? Am I using the same Karmic You are talking about? People do call this "boring" version ... :)
Ususally easier solution than editing config files from command line ... ?
I must say here: -1 ...

I'm going with experience I've had with previous versions of ubuntu alphas. I don't have karmic installed. But people did have problems last week where they could not login and had to use command line to fix things.

---

### Post by zika on 2009-06-29
> **andrewabc said:**
> I'm going with experience I've had with previous versions of ubuntu alphas. I don't have karmic installed. But people did have problems last week where they could not login and had to use command line to fix things.
That is what "command line" is there for ... :) Even in stable state of a distribution "command line" is not something scary ... or is it ... ?

---

### Post by andrewabc on 2009-06-29
> **zika said:**
> That is what "command line" is there for ... :) Even in stable state of a distribution "command line" is not something scary ... or is it ... ?

yes it is scary, because if you have no other computer for internet connection you are screwed. How do you get to ubuntuforums in command line when you have no X environment to open firefox? non linux people would have no clue what to do. Hell if my computer went into command line only tomorrow, I'd have to come to the forums to complain and get help on another computer (or another OS partition). Much like lots of people did last week when an update broke their install.

---

### Post by zika on 2009-06-29
> **andrewabc said:**
> yes it is scary, because if you have no other computer for internet connection you are screwed. How do you get to ubuntuforums in command line when you have no X environment to open firefox? non linux people would have no clue what to do. Hell if my computer went into command line only tomorrow, I'd have to come to the forums to complain and get help on another computer (or another OS partition). Much like lots of people did last week when an update broke their install.You always have a LiveCD ... Great safety net ...

---

### Post by jerrylamos on 2009-06-29
> **zika said:**
> You always have a LiveCD ... Great safety net ...

Live CD doesn't boot on my IBM ThinkCentre with intel i845 video graphics.  

Black screen, keyboard and mouse don't do a thing.

Alternate installed O.K.  Does not use Gnome.  After it is installed, boots from hard disk and runs O.K. for an Alpha, Gnome and all.

Logging in over the network to the "black screen" with openssh-server I can do a limited amount from the remote pc however there are no crash reports, no .xsession-errors, nothing in Xorg.0.log that looks alarming (I'm not a linux programmer).

The remote tty terminal permits /etc/init.d/gdm start, stop, and restart which get normal replies however the screen on the ThinkCentre remains totally black.  

Bug #385947.  Same CD booted and installed on IBM Thinkpads R31 and T40, and Compaq Presario.

?

Jerry

---

### Post by Gina on 2009-07-01
> **andrewabc said:**
> yes it is scary, because if you have no other computer for internet connection you are screwed. How do you get to ubuntuforums in command line when you have no X environment to open firefox? non linux people would have no clue what to do. Hell if my computer went into command line only tomorrow, I'd have to come to the forums to complain and get help on another computer (or another OS partition). Much like lots of people did last week when an update broke their install.If you haven't got another computer and no working Live CD then I definitely wouldn't recommend testing a development version!  You would be asking for trouble.  Development versions almost always break at some point.  You must be prepared to lose everything on the machine it's installed on.  Have everything of any importance backed up and be prepared to reinstall everything.

**This is a warning that seems to need repeating frequently!!**

---

### Post by GeorgeVita on 2009-07-01
Hi again, I used the Alpha 2 Desktop .iso, I made a live USB stick using 9.04 'USB Startup Disk Creator', boot from liveUSB and did the installation on the EeePC 1000H hard disk. I got connected via 3G (Huawei E169) and download 385 MBytes of updates. All above fine!

After update the xserver did not started so I boot the EeePC from my SDHC 9.04 installation and found help to this forum:
login using terminal mode, **startx**
I connected again, update some wrong packages (they were buggy for only 2 hours!) and all OK again.

System > Administration > Software Sources is NOT functioning! Asks/accepts password and then nothing. I will wait for a later fix but till then:
How can I change 'software sources' from terminal?
Is it better to use 'main server', 'USA server', or my local (Greece) mirror?

Thanks in advance,
George

---

### Post by zika on 2009-07-01
> **GeorgeVita said:**
> How can I change 'software sources' from terminal?
Is it better to use 'main server', 'USA server', or my local (Greece) mirror?
**sudo nano /etc/apt/sources.list**
I use *Main server* all the time because I think it is the most up-to date server.

---

### Post by zika on 2009-07-01
> **jerrylamos said:**
> Live CD doesn't boot on my IBM ThinkCentre with intel i845 video graphics.  

Black screen, keyboard and mouse don't do a thing.

Alternate installed O.K.  Does not use Gnome.  After it is installed, boots from hard disk and runs O.K. for an Alpha, Gnome and all.

Logging in over the network to the "black screen" with openssh-server I can do a limited amount from the remote pc however there are no crash reports, no .xsession-errors, nothing in Xorg.0.log that looks alarming (I'm not a linux programmer).

The remote tty terminal permits /etc/init.d/gdm start, stop, and restart which get normal replies however the screen on the ThinkCentre remains totally black.  

Bug #385947.  Same CD booted and installed on IBM Thinkpads R31 and T40, and Compaq Presario.

?

JerryI'm sorry to hear that. In that case using development version is really a risk ...
I must admit that I have several safety nets at my place so I'm rather casual about this. I apologize if anyone was offended by my attitude towards using experimental version ...

---

### Post by ranch hand on 2009-07-02
> **zika said:**
> I'm sorry to hear that. In that case using development version is really a risk ...
I must admit that I have several safety nets at my place so I'm rather casual about this. I apologize if anyone was offended by my attitude towards using experimental version ...

I don't think that anyone should be offended.

I am new to Linux (see join date) and I have 9.10 on my box in 3 installs (5 partitions).  None of them are on my main HDD and it is turned off when I am in 9.10.

If you are using a production box with an Alpha and it is on your only HDD you reap what you sow.  The installation process for 9.10 starts with a warning about it.  You have been warned.

Awful fun to play with and I think I am even learning something but not as much as i thought because this really is pretty stable.

As a side note, I do not see the CLI as scary.  I started out on MS-DOS and this CLI works a lot slicker than that ever did (it is more modern).  If you are going to play with a GUI intensive TESTING OS, you really should expect to have the GUI die on you.  This is why the CLI is so nice to have.

HAVE FUN

---

