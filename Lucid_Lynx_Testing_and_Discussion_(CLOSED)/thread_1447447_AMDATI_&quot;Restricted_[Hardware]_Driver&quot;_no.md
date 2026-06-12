---
title: "AMD/ATI &quot;Restricted [Hardware] Driver&quot; now available."
date: 2010-04-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by emarkay on 2010-04-05
The Proprietary FGLRX now can be installed with System > Administration > Hardware Drivers. This installs the ATI Catalyst Control Center, also.

Here is a list of the open bugs, sorted by date, newest first:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bugs?field.searchtext=&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bugs?field.searchtext=&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=")

Let's ensure this is solid by RC.

Also here's a recent comparison between the Restricted ATI Driver and the Open Source Mesa (I presume this is also the "Radeon"?) driver:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_fglrx_open&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_fglrx_open&num=1)

Remember, you have to console:
*sudo aticonfig --[I]initial*[/I]
then reboot.

---

### Post by emarkay on 2010-04-05
Ah, the joys of Beta Testing.  :)

I get:
[I]"Found fglrx primary device section
Unable to find any supported Screen sections"
[/I]
fglrxinfo gives:
*Segmentation fault (core dumped)*

and I get an Apport "Application Problem" for fglrxinfo.

Just a FYI.

The Apport bug has already been submitted on this:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/555158](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/555158)

---

### Post by aviramof on 2010-04-05
i don't see anything for some reason is there something i need to do?

---

### Post by coffeecat on 2010-04-05
Warning to ATI HD4200 Graphics users: you don't want to go there! At least not yet. :wink:

Activated the fglrx driver and rebooted so that I could watch a broken Plymouth and be told that there was a problem with the xserver, and which option did I want to choose? I went for the first - "run Ubuntu in low-graphics mode" - which unexpectedly worked, so that I was able to disable the fglrx driver in the GUI. Which was nice.

I'm now back with the OS ATI driver with an unbroken Plymouth, and a proper desktop complete with compiz and flashy effects. Which is nice. :p

All done in the spirit of beta testing don'cha know, but I think I'll stick with the OS driver.

---

### Post by praveenmarkandu on 2010-04-05
im using the Open Souce Radeon drivers. Im getting video tearing with metacity (compositing enabled) but perfect effects and video with compiz. i would much rather use metacity. can someone tell me whats up? i have a HD4330

---

### Post by ktmom on 2010-04-05
> **coffeecat said:**
> Warning to ATI HD4200 Graphics users: you don't want to go there! At least not yet. :wink:


I have an integrated HD4200 chipset on a Gigabyte GA-MA785GM-US2H motherboard.  I just installed the Proprietary FGLRX driver and it seems to be working fine.  At least for now...

---

### Post by gradinaruvasile on 2010-04-05
> **praveenmarkandu said:**
> im using the Open Souce Radeon drivers. Im getting video tearing with metacity (compositing enabled) but perfect effects and video with compiz. i would much rather use metacity. can someone tell me whats up? i have a HD4330

Metacity and its own compositing activated (also true in Xubuntu) will result in tearing with any hardware - i have nvidias in all comps and i cant watch movies without tearing if the Metacity compositor is enabled. Also the CPU usage skyrockets if i move a playing movie's window.
This was in Ubuntu/Xubuntu 9.10 but its true for Debian Testing too, i suppose the Metacity compositor is software-based unlike the Compiz one that has the option to bypass the compositing for movies. Anyway the best results are obtained without Compiz + disabling the X compositing altogether.

---

### Post by coffeecat on 2010-04-05
> **ktmom said:**
> I have an integrated HD4200 chipset on a Gigabyte GA-MA785GM-US2H motherboard.  I just installed the Proprietary FGLRX driver and it seems to be working fine.  At least for now...

Mine is on an Acer Aspire 7540 laptop. Curious how things vary. In Karmic, the backported ath9k wireless driver broke fglrx on this laptop. The Lucid ath9k driver is the same as the Karmic backported one (I believe), so perhaps I'm seeing the same issue.

Ah well. As the OP said: "the joys of beta testing." :p

---

### Post by aviramof on 2010-04-05
i'm asking again why don't i get anything in System > Administration > Hardware Drivers?

---

### Post by Autie on 2010-04-05
Can't install it here:
```
SystemError: installArchives() failed
```
System:
ATI Technologies Inc RV730 PRO [Radeon HD 4650]
Linux thanatos 2.6.32-19-generic #28-Ubuntu SMP Thu Apr 1 10:39:41 UTC 2010 x86_64 GNU/Linux
Intel(R) Core(TM) i7 CPU 920  @ 2.67GHz
lucid.

Any ideaa why?

---

### Post by praveenmarkandu on 2010-04-05
> **gradinaruvasile said:**
> Metacity and its own compositing activated (also true in Xubuntu) will result in tearing with any hardware - i have nvidias in all comps and i cant watch movies without tearing if the Metacity compositor is enabled. Also the CPU usage skyrockets if i move a playing movie's window.
This was in Ubuntu/Xubuntu 9.10 but its true for Debian Testing too, i suppose the Metacity compositor is software-based unlike the Compiz one that has the option to bypass the compositing for movies. Anyway the best results are obtained without Compiz + disabling the X compositing altogether.


thanks for clearing this up. i would prefer nearly zero effects. but i NEED compositing because notify-osd looks retarded without it. but since compiz is super smooth in Lucid, i have less problems with it than in Karmic. which is always a good thing.

---

### Post by Longinus00 on 2010-04-05
> **praveenmarkandu said:**
> thanks for clearing this up. i would prefer nearly zero effects. but i NEED compositing because notify-osd looks retarded without it. but since compiz is super smooth in Lucid, i have less problems with it than in Karmic. which is always a good thing.

You can try manually enabling compiz and manually disabling most of the effects via compizconfig-settings-manager as a workaround. I don't think that many effects are enabled by default in 'normal' mode.

---

### Post by BrokeMahPC on 2010-04-05
I found it listed under System - Administration - Hardware Drivers, yesterday.
ATI Radeon HD4670
Viewsonic Monitor 1920x1080
Clicked to activate it and rebooted and things did not go well.
Suddenly remembered to do.
code:
sudo aticonfig --initial -f

It was fine after this but Plymouth (which was working fine under the open source ATI driver) went into some 640x480 low res mode and looked awful. after a read of the "what's up with plymouth?" thread I found this document:
/usr/share/doc/plymouth/README.Debian

It mentions something about the proprietry driver doing this (the Nvidia people are having problems as well) as there is a problem with suspend/resume in higher resolutions. It also suggests a few lines of code to fix the problem if you are not concerned about suspend/resume. I tried them and it worked, don't use suspend so someone might want to test that.
I don't get plymouth full screen though - there is a black border around it but the buttons under the ubuntu logo do change from white to orange in sequence on startup and shutdown. 
Is there a way of changing resolution in Plymouth?
I suspect it might be my HD monitor 1920x1080 - not a common res?

---

### Post by emarkay on 2010-04-05
Yea, I "removed" it and am back to the default Radeon for now...

---

### Post by djchandler on 2010-04-06
> Yea, I "removed" it and am back to the default Radeon for now...

Yesterday I had problems booting after updates, which included a kernel patch and some plymouth upgrades before this driver became available via the Hardware Drivers menu. Reverting back to the xorg radeon driver fixed it in the short term. Then I went to bed.

Today I finally got to my laptop running the beta during the NCAA Division 1 Basketball championship. Just for grins, after applying all other available updates, I went to the hardware drivers menu and to my surprise, not having read the lead post, saw the fglrx driver available.

Those that are having problems may want to revert to the radeon driver before installing the ATI driver from the System>Administration>Hardware Drivers menu. Ironically it applies the same packages I removed about 24 hours ago, but without need to jump through the other hoops we have been, i.e., sudo aticonfig --initial, then restarting gdm. You get the restart prompt, so you really do need to restart gdm, but the configuration is being created properly now.

The only problem I'm having now is the splash screen. But everything else, including compiz, looks great.

I have a Radeon 3100 IGP (AMD 780V).

---

### Post by joebrueske on 2010-04-06
I got a little excited when I saw the topic, but it's not available for me to change in Karmic. :( Oh, well. I remember how much trouble I had when I first got Ubuntu. As a certain clock use to say, "If it's not Baroque, don't fix it!" So, I'll wait. :P

---

### Post by screaminj3sus on 2010-04-06
If you want some kind of compositing with ati and no tearing use mutter (used in gnome shell by default) the only compositing that doesnt tear on ati that I've found.

---

### Post by aviramof on 2010-04-08
i still don't understand why i don't get anything maybe because my hd3650 ddr2 512mb agp is shappire card and not main ati card?

---

### Post by emarkay on 2010-04-08
> **aviramof said:**
> i still don't understand why i don't get anything maybe because my hd3650 ddr2 512mb agp is shappire card and not main ati card?

Didn't answer because I don't know - is your card AGP, built in (laptop) PCI or what?  Is it still officially supported - (look at the ATI/AMD Windows list of supported cards - if it's not there, it sure won't be supported in Linux.)  They have obsoleted a fair number of cards in the past year or so. Do you dual boot in Win?  Is thw Win driver updated - if so what version is it? I recall Sapphire and others used ATI chips, and if it came with any ATI branded software it's a legit ATI unit.

---

### Post by aviramof on 2010-04-08
My card is agp and i still have a driver in windows seven i'm using this driver:
[http://support.amd.com/us/kbarticles/Pages/CatalystAGPHotfix.aspx](http://support.amd.com/us/kbarticles/Pages/CatalystAGPHotfix.aspx)
and i think it still need to be supported but the question is does there a diffrence bwtween shappire and non shappire card.

---

### Post by aviramof on 2010-04-11
i can see it now but i can't install it with kernel 33 i can with 32 but i don't think it working very well there any way he said i need to check for the jocky log how can i do a bug report of this pacage?

---

