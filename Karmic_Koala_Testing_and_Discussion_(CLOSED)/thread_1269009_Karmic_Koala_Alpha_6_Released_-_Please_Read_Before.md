---
title: "Karmic Koala Alpha 6 Released - Please Read Before Testing"
date: 2009-09-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 23meg on 2009-09-17
Karmic Koala Alpha 6, the sixth milestone release leading to Ubuntu 9.10, has been released. Below are some basic points to remember before testing: 

[list][*] The milestone releases (alphas, the beta and the RC) are snapshots of the package archive at their predecided release dates. **If you have the latest updates installed on your testing installation, you don't have to remove your current testing installation and install Alpha 6**, unless you want to test installation-specific components (the installer, bootloader etc.), or your installation is affected by potential corner cases that may arise during the development cycle that require a reinstall to fix. 


[*] If you're just starting to test Karmic, please take a look at [this wiki page]("https://wiki.ubuntu.com/UbuntuDevelopment/UsingDevelopmentReleases") for information on various testing methods and good practices.


[*] Once you've started testing, **do not upgrade your installation blindly** - especially avoid partial upgrades offered by Update Manager unless you know precisely why it's offering a partial upgrade. Regardless of which tool (APT, Update Manager, Synaptic, Aptitude) you're using to upgrade your packages, **always check the list of packages to be removed, upgraded and installed before each upgrade**. If in doubt, check the changelogs ("Package > Download Changelog" in Synaptic, or "aptitude changelog package_name", or at [packages.ubuntu.com]("http://packages.ubuntu.com")) to see why a package may be being removed.


[*] If you run into problems, you're most likely not alone; do a bug search at the bug tracker and/or a forum search in this forum before starting new threads.[/list]

Here is Steve Langasek's announcement to the ubuntu-devel-announce mailing list:

> **Steve Langasek]Hello Ubuntu developers,

Welcome to Karmic Koala Alpha 6, which will in time become Ubuntu 9.10.

Pre-releases of Karmic are *not* encouraged for anyone needing a stable
system or anyone who is not comfortable running into occasional, even
frequent breakage.  They are, however, recommended for Ubuntu developers and
those who want to help in testing, reporting, and fixing bugs.

Alpha 6 is the sixth in a series of milestone CD images that will be
released throughout the Karmic development cycle.  The Alpha images are
known to be reasonably free of showstopper CD build or installer bugs, while
representing a very recent snapshot of Karmic. You can download it here:

  [http://cdimage.ubuntu.com/releases/karmic/alpha-6/](http://cdimage.ubuntu.com/releases/karmic/alpha-6/) (Ubuntu)
  [http://uec-images.ubuntu.com/releases/karmic/alpha-6/](http://uec-images.ubuntu.com/releases/karmic/alpha-6/) (Ubuntu Server for UEC and EC2)
  [http://cdimage.ubuntu.com/ports/releases/karmic/alpha-6/](http://cdimage.ubuntu.com/ports/releases/karmic/alpha-6/) (Ubuntu ARM)
  [http://cdimage.ubuntu.com/kubuntu/releases/karmic/alpha-6/](http://cdimage.ubuntu.com/kubuntu/releases/karmic/alpha-6/) (Kubuntu)
  [http://cdimage.ubuntu.com/xubuntu/releases/karmic/alpha-6/](http://cdimage.ubuntu.com/xubuntu/releases/karmic/alpha-6/) (Xubuntu)
  [http://cdimage.ubuntu.com/ubuntustudio/releases/karmic/alpha-6/](http://cdimage.ubuntu.com/ubuntustudio/releases/karmic/alpha-6/) (UbuntuStudio)
  [http://cdimage.ubuntu.com/mythbuntu/releases/karmic/alpha-6/](http://cdimage.ubuntu.com/mythbuntu/releases/karmic/alpha-6/) (Mythbuntu)
  [http://cdimage.ubuntu.com/edubuntu/releases/karmic/alpha-6/](http://cdimage.ubuntu.com/edubuntu/releases/karmic/alpha-6/) (Edubuntu)

See [http://wiki.ubuntu.com/Mirrors](http://wiki.ubuntu.com/Mirrors) for a list of mirrors.

Alpha 6 includes a number of software updates that are ready for large-scale
testing.  This is an early set of images so you should expect some bugs said:**
> http://www.ubuntu.com/testing/karmic/alpha6[/url]

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

### Post by MacUntu on 2009-09-17
On [http://www.ubuntu.com/testing/karmic/alpha6](http://www.ubuntu.com/testing/karmic/alpha6) the paragraph 'GRUB 2 by default' should contain information on how to access the GRUB menu, which (under certain circumstances) is hidden by default. If you don't know about the Shift key and the kernel doesn't like your system, you're screwed.

---

### Post by novafluxx on 2009-09-17
Yes! Here's to another milestone release!:popcorn::guitar::):P:mrgreen:

---

### Post by popejeremy on 2009-09-17
Is it reasonable to assume that it's now as safe as can be expected to hit apt-get update && apt-get upgrade? I know that it's an Alpha and that therefore I'll be using it at my own risk, but I'd like to feel like there's a reasonable chance that if I upgrade, that I'll avoid the complete and total borking that some users have been experiencing in the past few days.

---

### Post by ranch hand on 2009-09-17
Why on earth would you want to assume something like that?

Recent history is against this as a safe assumtion.

---

### Post by megamania on 2009-09-18
> **popejeremy said:**
> Is it reasonable to assume that it's now as safe as can be expected 
NO. 

Sorry. :-)

---

### Post by grandtoubab on 2009-09-18
Hello all,
That is because some people "take the risk to upgrade" thet the system improve, don't you think?
If everybody sat and wait no progress!:lolflag:
In a famous french movie someone says " a nut in movement go further than an intellectuel sat down":guitar::P:P:P:P

---

### Post by megamania on 2009-09-18
> **grandtoubab said:**
> Hello all,
That is because some people "take the risk to upgrade" thet the system improve, don't you think?
If everybody sat and wait no progress!

People say "wait" to people who ask if Karmic is stable.

If you want to test it, fine. If you want a stable system, wait.

I'm testing it.

---

### Post by VMC on 2009-09-18
> **megamania said:**
> People say "wait" to people who ask if Karmic is stable.

If you want to test it, fine. If you want a stable system, wait.

I'm testing it.

Same here! I look at it this way - Its a test kitchen, If I get a bad recipe I tell the the cook, and the next batch will improve. I'm not wanting a test distro to be stable until its final release. I want to test the hell out of it, report any damages then test some more. I use Jaunty for stability.

---

### Post by rajeev1204 on 2009-09-18
> **popejeremy said:**
> Is it reasonable to assume that it's now as safe as can be expected to hit apt-get update && apt-get upgrade? I know that it's an Alpha and that therefore I'll be using it at my own risk, but I'd like to feel like there's a reasonable chance that if I upgrade, that I'll avoid the complete and total borking that some users have been experiencing in the past few days.

Technically speaking,the repos will have been updated with the newer packages ,so you wont face the serious breakaga from a few days ago.

Other than that, the comments of the other posters to your question is valid.

Stay sharp.Stay safe. :)

---

### Post by popejeremy on 2009-09-18
Well, I'm going for it with an apt-get dist-upgrade. Hopefully I come out on the other side.

---

### Post by popejeremy on 2009-09-18
apt-get dist-upgrade worked! I got some slightly cranky messages on boot, but it starts-up into gnome and everything is copacetic. The new boot graphics are slicker, Empathy works now. On my EEE 1005HA, it's an improvement!

---

### Post by kansasnoob on 2009-09-18
Just getting back to my testing. To those adventurous among us, this torrent is about 4 times faster for me than the main server:

[http://cdimage.ubuntu.com/releases/karmic/alpha-6/karmic-desktop-i386.iso.torrent](http://cdimage.ubuntu.com/releases/karmic/alpha-6/karmic-desktop-i386.iso.torrent)

Found that at Distrowatch :)

---

### Post by executorvs on 2009-09-18
moved to a more appropriate spot.

---

### Post by Copernicus1234 on 2009-09-19
Alpha 6 doesnt work in Virtual Box. After install of files, it hangs in a loop after reboot.

Perhaps its just me. But alpha 5 worked perfectly.

---

### Post by IgorKossak on 2009-09-19
> **Copernicus1234 said:**
> Alpha 6 doesnt work in Virtual Box. After install of files, it hangs in a loop after reboot.

Perhaps its just me. But alpha 5 worked perfectly.
Me too.

---

### Post by Szise on 2009-09-20
With this release i hope will be fixed the problems with the black screen at startup and/or old ATI drivers, ugly fonts, fonts not respecting the real size and font family of the visited site.

---

### Post by sdowney717 on 2009-09-20
I did a dist-upgrade and it put the text on flipped over backwards and mirrored.
So, I formated and did a fresh install of alpha6 and it is working good. My ati x1300 actually has 3d support now.

---

### Post by ELD on 2009-09-20
I still think it's annoying you didn't mention the ATi issue on the release page, i asked about it last time and it is still not mentioned, we keep getting threads about it.

---

### Post by 23meg on 2009-09-20
> **ELD said:**
> I still think it's annoying you didn't mention the ATi issue on the release page, i asked about it last time and it is still not mentioned, we keep getting threads about it.

I checked the progress with [the bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/419126") before the release of Alpha 6, when it seemed the solution was established to be simply disabling DRI on R600, and Alberto Milone had attached a debdiff which did that. Assuming that it would go through before the release, I omitted adding it to the known issues. Apparently it didn't (it needed sponsoring), and the bug was milestoned for the beta anyway, but it should be fixed in the last two daily builds.

---

### Post by ELD on 2009-09-20
The solution was there but it was not implemented or marked as fixed until after the alpha, so it is an issue with the alpha6, the daily build cd's are old too (so i am updating a jaunty install to finally test :)).

---

### Post by Gina on 2009-09-22
I installed Alpha 6 64 bit version today on my AMD64 and so far everything seems fine.  Remains to be seen if a problem I've been having with 8.04 where the system either reboots itself or locks up, has been cured.  I realise it could be a hardware problem as Ubuntu 9.04 is fine on my other machines (32 bit).  

I run the AMD64 24/7 to upload webcam images to my weather website.

---

### Post by Gina on 2009-09-23
I still have the problem - system crashed overnight.  I'll investigate further, starting with installing the 32 bit version instead of the 64 bit, I think.

---

### Post by tyk on 2009-09-25
Hi just tried the alpha-6 on my amd64 system. It did give some boot up errors but managed to get to the splash screen. Thereafter it failed to load up X and screen blanked and came back to splash many times. One time it showed the toolbars on top and bottom without anything else. But didn't amount to anything so gave up.
System specs:
AMD Turion RM74
4GB DDR2 Ram
ATI HD4570

What might be the cause of this? As far as I can see, the system works with bugs but at least boots up for other people here. And two: I originally wanted to download the Xubuntu flavour.. there were no seeders at all!! And 3: GRUB didn't see my previous installs of Jaunty at all. Is this repairable with 'grub-install'? Need a pointer on this. Thanks.

---

### Post by VMC on 2009-09-25
> **tyk said:**
> .. Thereafter it failed to load up X and screen blanked and came back to splash many times. ...
System specs:
AMD Turion RM74
4GB DDR2 Ram
ATI HD4570

And 3: GRUB didn't see my previous installs of Jaunty at all. Is this repairable with 'grub-install'?

You should check ATI driver regarding xorg issues. 

You said grub didn't see jaunty, but it appears your now using grub2. If so run ```
sudo update-grub
```

---

### Post by tyk on 2009-09-27
Hi VMC,
thanks for the reply. My mistake I didn't mention that this was the liveCD. So I actually didn't get to the point of finding out how it reacted to the ati card. I tried the same cd with safe graphics and got pretty much the same result. Since I was trying to install Karmic on a deparate partition just to test if it read and could use my ati card, the point in case is settled as such. Thereafter, I installed another jaunty copy to do all the testing for the ati card. No luck there but it read all my installs of jaunty.
Muchos gracias in any case :)
Cheers.

---

