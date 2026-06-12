---
title: "Ati Issues, Again =("
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by [S]Duke on 2009-10-12
First let me start off by saying I'm perfectly aware this is a beta, not the final release, and that things are bound to be imperfect.

HOWEVER, my concern is (and has been with Ubuntu for the past 3 or 4 releases) that drivers for my ATI card (Radeon HD 2600Pro) are just impossible.

Whenever I install a new version of Ubuntu(I do a fresh install every time), I ALWAYS get black screens with the default radeon driver. It loads, I hear the sounds, but the screen is black.

I had luck with the fglrx drivers from the ati site with 9.04 in that I was able to install those manually and get desktop effects (and more importantly emerald) to work, though with errors.

But in 9.10 it seems that the drivers from the ati website (9.9) don't work, installing them manually from the site (using recovery console, and wget) loads Ubuntu, but no support at all for any desktop effects.

I tried installing fglrx from the repos(since that supposedly is a pre-release of 9.10) but it freezes right after the white ubuntu logo.

So I'm stuck with black screen (radeon default drivers), no desktop effects and heavily laggy performance(manually installing the 9.9 drivers from the ati website), or freezing and never loading (fglrx drivers from the repos).

Is there anything I can do?

P.S. I follow this guide to install my drivers manually: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually)

---

### Post by alphacrucis2 on 2009-10-12
> **'[S]Duke said:**
> First let me start off by saying I'm perfectly aware this is a beta, not the final release, and that things are bound to be imperfect.

HOWEVER, my concern is (and has been with Ubuntu for the past 3 or 4 releases) that drivers for my ATI card (Radeon HD 2600Pro) are just impossible.

Whenever I install a new version of Ubuntu(I do a fresh install every time), I ALWAYS get black screens with the default radeon driver. It loads, I hear the sounds, but the screen is black.

I had luck with the fglrx drivers from the ati site with 9.04 in that I was able to install those manually and get desktop effects (and more importantly emerald) to work, though with errors.

But in 9.10 it seems that the drivers from the ati website (9.9) don't work, installing them manually from the site (using recovery console, and wget) loads Ubuntu, but no support at all for any desktop effects.

I tried installing fglrx from the repos(since that supposedly is a pre-release of 9.10) but it freezes right after the white ubuntu logo.

So I'm stuck with black screen (radeon default drivers), no desktop effects and heavily laggy performance(manually installing the 9.9 drivers from the ati website), or freezing and never loading (fglrx drivers from the repos).

Is there anything I can do?

P.S. I follow this guide to install my drivers manually: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually)

You need the Catalyst 9.10 driver to get compatibility with the Karmic kernel. You may have noticed that this version hasn't yet been released by ATI. No problem as ATI have made a prerelease available to Ubuntu. Just install the fglrx driver from the Karmic repos - it's Catalyst 9.10.

---

### Post by [S]Duke on 2009-10-12
> **alphacrucis2 said:**
> You need the Catalyst 9.10 driver to get compatibility with the Karmic kernel. You may have noticed that this version hasn't yet been released by ATI. No problem as ATI have made a prerelease available to Ubuntu. Just install the fglrx driver from the Karmic repos - it's Catalyst 9.10.
Like I said in my post, I tried installing the fglrx drivers off the repos, it leads to the screen freezing after the white ubuntu logo.

---

### Post by alphacrucis2 on 2009-10-12
> **'[S]Duke said:**
> Like I said in my post, I tried installing the fglrx drivers off the repos, it leads to the screen freezing after the white ubuntu logo.


Did you do the usual

> sudo aticonfig --initial

---

### Post by [S]Duke on 2009-10-12
> **alphacrucis2 said:**
> Did you do the usual
Yep, it goes to the white logo, then flashes, and then leaves a multi-colored line across the screen and freezes there.

---

### Post by metallica1788 on 2009-10-12
I experience the same issue:S
I've tried to install a the daily built from 10 october.
And on boot i first get a black screen with an ubuntu logo, then on the point where the new xsplash should appear i get a black screen with lines of al kind a colors.

---

### Post by emarkay on 2009-10-12
Is it an AGP card?

I have posted about this a few days ago - the AGP Aperture must be set for 256 Mb or more.  A bug has been filed on this.

---

### Post by [S]Duke on 2009-10-12
> **emarkay said:**
> Is it an AGP card?

I have posted about this a few days ago - the AGP Aperture must be set for 256 Mb or more.  A bug has been filed on this.
How would I be able to check whether it is or not?

All I really know about it is that it is an ATI Radeon 2600HD Pro.

---

### Post by [S]Duke on 2009-10-12
Anyone with any ideas?

I hate to double post, but I'm pretty stuck right now D:

---

### Post by solnyshok on 2009-10-12
I had similar problems (black screen and freeze, nothing helped half a year ago when installing Jaunty on XT1950 (AGP). Cannot check the fix today, since I changed the machine to Core2Duo and HD4670, which works well with Karmic Koala.

---

### Post by emarkay on 2009-10-12
> **'[s]Duke said:**
> How would I be able to check whether it is or not?

All I really know about it is that it is an ATI Radeon 2600HD Pro.

Down load "sysinfo" using Synaptic, and reboot.  It will appear in "Applications > System Tools > Sysinfo"  There should be either "Hardware" or "ATI Display" there, and by clicking on it you will find if your card is PCI-e AGP or something else.

---

### Post by [S]Duke on 2009-10-12
> **emarkay said:**
> Down load "sysinfo" using Synaptic, and reboot.  It will appear in "Applications > System Tools > Sysinfo"  There should be either "Hardware" or "ATI Display" there, and by clicking on it you will find if your card is PCI-e AGP or something else.
Ah okay, no my card doesn't use the agp slot, it uses PCI-e(x16).

---

### Post by emarkay on 2009-10-12
OP, when you say " default radeon driver",  do you meant the one that  you install using "Administration > Hardware Drivers"?

If not, that is the ONLY ATI driver that will work in Karmic for older cards.  This has been batted about for a week here, but I don't remember seeing it spelled out like this:

[I][B]If you have an older ATI/AMD "Radeon" graphics card: 8500 and up, x300 and up, HD2400 and up, the ATI Catalyst Display Driver 9.9 from the official site will NOT work in Karmic due to the new Linux kernel.  Use ONLY the driver found in "Hardware Drivers", which is actually a pre-release of Catalyst 9.10.
[/B][/I]
How's that?  :)[B]
[/B]

---

### Post by Longinus00 on 2009-10-12
> **emarkay said:**
> OP, when you say " default radeon driver",  do you meant the one that  you install using "Administration > Hardware Drivers"?

If not, that is the ONLY ATI driver that will work in Karmic for older cards.  This has been batted about for a week here, but I don't remember seeing it spelled out like this:

[I][B]If you have an older ATI/AMD "Radeon" graphics card: 8500 and up, x300 and up, HD2400 and up, the ATI Catalyst Display Driver 9.9 from the official site will NOT work in Karmic due to the new Linux kernel.  Use ONLY the driver found in "Hardware Drivers", which is actually a pre-release of Catalyst 9.10.
[/B][/I]
How's that?  :)[B]
[/B]

No! If you have an older card (r500 and older) the ati proprietary won't work at all. Do not install the ATI proprietary drivers! The open source driver gets installed by default, don't mess with it.

---

To the OP, have you tried removing fglrx and then doing this?
[http://ubuntuforums.org/showpost.php?p=8053859&postcount=2](http://ubuntuforums.org/showpost.php?p=8053859&postcount=2)

---

### Post by emarkay on 2009-10-12
> **Longinus00 said:**
> No! If you have an older card (r500 and older) the ati proprietary won't work at all. Do not install the ATI proprietary drivers! The open source driver gets installed by default, don't mess with it. To the OP, have you tried removing fglrx and then doing this?[http://ubuntuforums.org/showpost.php?p=8053859&postcount=2](http://ubuntuforums.org/showpost.php?p=8053859&postcount=2)


I said these cards only:[I][B] 8500 and up, x300 and up, HD2400 and up. 
[/B][/I]I did not include "antique" cards as they are no longer supported by ATI.  This list was taken direct from their website.

---

### Post by Longinus00 on 2009-10-12
> **emarkay said:**
> I said these cards only:[I][B] 8500 and up, x300 and up, HD2400 and up. 
[/B][/I]I did not include "antique" cards as they are no longer supported by ATI.  This list was taken direct from their website.

I'm sorry but you are mistaken. The release notes on ATI's website plainly state what the supported cards are.
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_99_linux.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_99_linux.pdf)

---

### Post by ArtLaForge on 2009-10-12
> **'[s]Duke said:**
> How would I be able to check whether it is or not?

All I really know about it is that it is an ATI Radeon 2600HD Pro.

I believe it is a PCI express board, had one once upon a time.

---

### Post by emarkay on 2009-10-12
> **Longinus00 said:**
> I'm sorry but you are mistaken. The release notes on ATI's website plainly state what the supported cards are.
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_99_linux.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_99_linux.pdf)


I am only mistaken if they are.  Go here:
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
There are 28 cards listed under Radeon. 
 I listed the lowest model number per group and said, "and up".  
The page you say, which is the correct release notes, actually only list 21 Radeon cards....

Personally I would rather see it as a downloadable link then a note on a PDF file.  

For example, it lists ATI RadeonTM HD 4650 Series,  but you can't download a driver for it, only a 4600 or a 4700.  (Sure the links may all go to the same file, but if I was a noob, I'd think there was no download available for a 4650.)

Please check your facts in the future before being so blunt.

Thank you.

---

### Post by [S]Duke on 2009-10-12
Sorry, let me clarify, by "default radeon driver" I mean the one that is installed with the ubuntu install, the open-source driver I mean. NOT the restricted one (since I can't access the desktop at all =/).

---

### Post by emarkay on 2009-10-12
> **'[s]Duke said:**
> Sorry, let me clarify, by "default radeon driver" I mean the one that is installed with the ubuntu install, the open-source driver I mean. NOT the restricted one (since I can't access the desktop at all =/).

It can be done (I was curious about this a while ago...):
[http://ubuntuforums.org/showthread.php?t=1283706&highlight=restricted+drivers](http://ubuntuforums.org/showthread.php?t=1283706&highlight=restricted+drivers)

---

### Post by [S]Duke on 2009-10-12
Again, let me apologize in advance for double posting, but I wanted to make sure you guys noticed this is new information. A mod is free to merge if this is considered spam.

Let me tell you guys my steps:

1. Install Ubuntu 9.10 Beta 1 off the Alternate CD (Live CDs do not work with my computer)
2. Boot into Ubuntu, white logo, then black screen, hear sounds of desktop (this is what I call the "default radeon driver")
3. Restart (manually), boot into recovery console, use wget to download the ATI driver off ATI's website, install manually (9.9).
4. Boot into Ubuntu, successful display (only one that works), however, extremely laggy and no desktop effects.
5. Boot back into recovery console, purge fglrx.
6. Update/Upgrade
7. Install fglrx off distros (sudo apt-get install xorg-driver-fglrx)
8. Boot into Ubuntu, white logo, then black screen with colors, frozen, no boot.
9. Post here looking for help from laptop :P

Hopefully this will help.

Edit: Guess I didn't double-post after all :P

---

### Post by emarkay on 2009-10-12
OK, had  to go boot up the ATI machine.

I have a HD2600 XT which is basically the same card.

You need more "fglrx" files installed,  :) See attachment.

---

### Post by [S]Duke on 2009-10-12
I booted up into the recovery console again, purged all fglrx, then installed "xorg-driver-fglrx" , "fglrx-amdcccle" and "fglrx-kernel-source" (the distros don't seem to have "fglrx-modaliases"), but still no luck :(

I've attached a picture (taken with my phone, excuse the quality :P) of what I see after the white ubuntu logo.

P.S. I do appreciate all the help, sorry this is being such a pain =S

---

### Post by emarkay on 2009-10-12
I'm thinking "tear at perforated line..."  :)

There is the possibility of a hardware failure...

Do you dual boot into another OS to test?  If not, I presume your PC has some lame, crappy  "onboard" graphics?  

Carefully pull the ATI card, and output the good old legacy SVGA  (may need to look at BIOS to enable) and confirm that the SOFTWARE is OK.  This will also re-seat the graphics card.  Also a good time to dust/inspect.

Since I have an almost identical graphics card, and you have your system like mine in terms of the driver,  AND you couldn't even get the "basic" non-accelerated ATI display, unless there's something in the BIOS that you can tweak and test, I'll look around a bit more, but I pretty quickly got the AGP issue resolved and from there it worked fine.  I DID use the "onboard" SVGA as described above beforehand.

---

### Post by emarkay on 2009-10-12
Also I have "xserver-xorg-video-radeon" installed, too, about a 1200 mb file - I searched Synaptic for "Radeon".

"the distros don't seem to have "fglrx-modaliases" - Well I have it... :)   In "Software Sources > Ubuntu Software" all are checked except "Source Code, and I use the "Main Server".  "Other Software"  includes "http://archive.canonical.com/ubuntu". "Updates", all "Ubuntu updates"  are checked.

---

### Post by [S]Duke on 2009-10-12
> **emarkay said:**
> I'm thinking "tear at perforated line..."  :)

There is the possibility of a hardware failure...

Do you dual boot into another OS to test?  If not, I presume your PC has some lame, crappy  "onboard" graphics?  

Carefully pull the ATI card, and output the good old legacy SVGA  (may need to look at BIOS to enable) and confirm that the SOFTWARE is OK.  This will also re-seat the graphics card.  Also a good time to dust/inspect.

Since I have an almost identical graphics card, and you have your system like mine in terms of the driver,  AND you couldn't even get the "basic" non-accelerated ATI display, unless there's something in the BIOS that you can tweak and test, I'll look around a bit more, but I pretty quickly got the AGP issue resolved and from there it worked fine.  I DID use the "onboard" SVGA as described above beforehand.
I highly doubt it's hardware failure as I have that computer on Windows 7 right now (dual booting with the broken Ubuntu) and its accelerated Windows drivers work fine, as a matter of fact I use it to play games =P

Tbh, I'm not sure the onboard graphics card still works, I remember being pretty "ungentle" with it when I was putting in the ATI one, and it's about 5-6 years old.

Also, I had the radeon one installed already, that's why I didn't mention it in my post earlier. Weird about the modaliases thing though, I'll use nano to check my sources.list and see if I have anything disabled.

---

### Post by Longinus00 on 2009-10-13
> **emarkay said:**
> I am only mistaken if they are.  Go here:
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
There are 28 cards listed under Radeon. 
 I listed the lowest model number per group and said, "and up".  
The page you say, which is the correct release notes, actually only list 21 Radeon cards....

Personally I would rather see it as a downloadable link then a note on a PDF file.  

For example, it lists ATI RadeonTM HD 4650 Series,  but you can't download a driver for it, only a 4600 or a 4700.  (Sure the links may all go to the same file, but if I was a noob, I'd think there was no download available for a 4650.)

Please check your facts in the future before being so blunt.

Thank you.

The cards r500 and lower are all not supported in karmic with the proprietary driver. If you had clicked on the link you posted yourself, you would see that it takes you to a different driver if you choose say, the 8500 vs. the 4800 series (yes, they say series, not individual cards).

If you still don't believe me.
[http://www.linux-magazine.com/Online/News/AMD-Provides-Legacy-Driver-for-Old-ATI-Cards](http://www.linux-magazine.com/Online/News/AMD-Provides-Legacy-Driver-for-Old-ATI-Cards)
[http://en.wikipedia.org/wiki/Fglrx](http://en.wikipedia.org/wiki/Fglrx)
[http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy](http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy)
[http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.22&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.22&lang=English)

---

### Post by taavikko on 2009-10-13
> **'[S]Duke said:**
> I booted up into the recovery console again, purged all fglrx, then installed "xorg-driver-fglrx" , "fglrx-amdcccle" and "fglrx-kernel-source" (the distros don't seem to have "fglrx-modaliases"), but still no luck :(

I've attached a picture (taken with my phone, excuse the quality :P) of what I see after the white ubuntu logo.

P.S. I do appreciate all the help, sorry this is being such a pain =S

I have the same distortion on my laptop (ati HD3450) running free radeon driver.
It started after the latest updates to usplash and xsplash.
Cannot state for certain since there were also updates on mesa.

Is there any bugreports made?
If not, file one.

---

### Post by zika on 2009-10-13
> **'[s]Duke said:**
> I booted up into the recovery console again, purged all fglrx, then installed "xorg-driver-fglrx" , "fglrx-amdcccle" and "fglrx-kernel-source" (the distros don't seem to have "fglrx-modaliases"), but still no luck :(
I've attached a picture (taken with my phone, excuse the quality :P) of what I see after the white ubuntu logo.
P.S. I do appreciate all the help, sorry this is being such a pain =S+1 on a clean install. No fglrx ever touched this install. No PPA upgrades. Pure Karmic.

---

### Post by Kazade on 2009-10-13
> **'[S]Duke said:**
> Again, let me apologize in advance for double posting, but I wanted to make sure you guys noticed this is new information. A mod is free to merge if this is considered spam.

Let me tell you guys my steps:

1. Install Ubuntu 9.10 Beta 1 off the Alternate CD (Live CDs do not work with my computer)
2. Boot into Ubuntu, white logo, then black screen, hear sounds of desktop (this is what I call the "default radeon driver")
3. Restart (manually), boot into recovery console, use wget to download the ATI driver off ATI's website, install manually (9.9).
4. Boot into Ubuntu, successful display (only one that works), however, extremely laggy and no desktop effects.
5. Boot back into recovery console, purge fglrx.
6. Update/Upgrade
7. Install fglrx off distros (sudo apt-get install xorg-driver-fglrx)
8. Boot into Ubuntu, white logo, then black screen with colors, frozen, no boot.
9. Post here looking for help from laptop :P

Hopefully this will help.

Edit: Guess I didn't double-post after all :P

It sounds to me that when you install FGLRX and it appears to work, what is really happening is it's not working at all and you are falling back to VESA (that would explain the lagginess, lack of acceleration etc.)

You definitely don't want to use 9.9 in Karmic, it just won't work. Full stop. 

I would recommend you add the following PPAs:

```
ppa:xorg-edgers/ppa
ppa:ubuntu-x-swat/x-updates

```
The first one will give you cutting edge OSS drivers. The second one maybe will give you updated FGLRX. Just add them via software sources (by pasting each line into the add source box). Then run update/upgrade.

If you can't get into the UI, edit /etc/X11/xorg.conf and change the driver from fglrx (or ati) to vesa.

---

### Post by emarkay on 2009-10-13
> **Longinus00 said:**
> The cards r500 and lower are all not supported in karmic with the proprietary driver. If you had clicked on the link you posted yourself, you would see that it takes you to a different driver if you choose say, the 8500 vs. the 4800 series (yes, they say series, not individual cards).

If you still don't believe me.
[http://www.linux-magazine.com/Online/News/AMD-Provides-Legacy-Driver-for-Old-ATI-Cards](http://www.linux-magazine.com/Online/News/AMD-Provides-Legacy-Driver-for-Old-ATI-Cards)
[http://en.wikipedia.org/wiki/Fglrx](http://en.wikipedia.org/wiki/Fglrx)
[http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy](http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy)
[http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.22&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.22&lang=English)


So?  What's your  point?  I didn't list nor mention  "r500" or any "r" cards  - I am confused...  :confused:

Anyway, [S]Duke, how's it going?

---

### Post by ssri on 2009-10-13
> **emarkay said:**
> So?  What's your  point?  I didn't list nor mention  "r500" or any "r" cards  - I am confused...  :confused:

Anyway, [S]Duke, how's it going?

This list might help

[http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units](http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units)

BTW, you listed a R200 card (8500) in your post.  Furthermore, do not believe everything you read in ATI's release notes ([http://www.phoronix.com/forums/showthread.php?t=17736](http://www.phoronix.com/forums/showthread.php?t=17736))

---

### Post by [S]Duke on 2009-10-13
> **emarkay said:**
> So?  What's your  point?  I didn't list nor mention  "r500" or any "r" cards  - I am confused...  :confused:

Anyway, [S]Duke, how's it going?
Sorry I had work then sleeping =P

I guess I will try adding those two lines to the sources.list and maybe see if I have any luck there.

I'm glad to see I'm at least not the only person who is having these issues at least.

Edit: I'm also going to try doing a completely fresh install and taking it from there. Maybe by some magical force it'll randomly work =P

---

### Post by Longinus00 on 2009-10-13
> **'[S]Duke said:**
> Sorry I had work then sleeping =P

I guess I will try adding those two lines to the sources.list and maybe see if I have any luck there.

I'm glad to see I'm at least not the only person who is having these issues at least.

Edit: I'm also going to try doing a completely fresh install and taking it from there. Maybe by some magical force it'll randomly work =P

How well does the live cd work? Did your karmic install start having a black screen as soon as you boot for the first time?

---

### Post by [S]Duke on 2009-10-13
> **Longinus00 said:**
> How well does the live cd work? Did your karmic install start having a black screen as soon as you boot for the first time?
The Live CD doesn't work.

I'm not sure what driver that uses, but I get the black screen with sounds whenever I try to use it.

I've been doing my installs with the alternate cd for a few releases now.

And yes, black screen with sounds on first boot. Happened that way in Jaunty too.

Whatever Ubuntu uses as its default driver (I think it's an oper source driver?) doesn't work with my card for some reason.

---

### Post by emarkay on 2009-10-13
I had a poop-load of problems even on the Live CD ( no display) before the AGP Aperture solved it.  Have you been into your BIOS and looked around for ANYTHING that may have to do with the graphics??

---

### Post by [S]Duke on 2009-10-13
> **Kazade said:**
> It sounds to me that when you install FGLRX and it appears to work, what is really happening is it's not working at all and you are falling back to VESA (that would explain the lagginess, lack of acceleration etc.)

You definitely don't want to use 9.9 in Karmic, it just won't work. Full stop. 

I would recommend you add the following PPAs:

```
ppa:xorg-edgers/ppa
ppa:ubuntu-x-swat/x-updates

```
The first one will give you cutting edge OSS drivers. The second one maybe will give you updated FGLRX. Just add them via software sources (by pasting each line into the add source box). Then run update/upgrade.

If you can't get into the UI, edit /etc/X11/xorg.conf and change the driver from fglrx (or ati) to vesa.

Okay, I switched over to vesa and added those. I think (I couldn't necessarily read it, vesa was a rainbow of colors and the text was near impossible to see) the first one worked, since I did apt-get update and upgrade and I saw radeon things were being updated. However, I also saw something about a missing public key, so I'm guessing the second ppa needs a public key to work.

Sadly though, the updated radeon one led right back to black screen :(

On a clean install.

@emark: Yeah I just checked my bios and nothing really graphics related. I tried changing anything that even looked graphics related around but no change =/

Edit: Okay from the recovery console, I can see the error now:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic release: The following signatures couldn't be verified because the public key is not avaliable: NO_PUBKEY 3B22AB97AF1CDFA9

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic release: The following signatures couldn't be verified because the public key is not avaliable: NO_PUBKEY 4F191A5A8844C542

---

### Post by Akita on 2009-10-13
Dual monitors by any chance?

I had to unplug my second from the card until I had the driver installed, otherwise it would always come up on the first boot after the install with black screens.

Other than that I haven't seen a problem with an HD4670.

---

### Post by [S]Duke on 2009-10-13
Nope, single monitor setup.

---

### Post by emarkay on 2009-10-13
[S]Duke, what type of PC is it - a "brand name" or a "homebrew"?  If it's brand, what additions besides the display card (WIFI, Sound card, Bluetooth, etc.) and if it' homebrew, what's in there - Mainboard MFG and model, processor type and model number, memory, power supply type and wattage, drives and other storage...

This is getting weird!

---

### Post by [S]Duke on 2009-10-13
It's an HP(it's getting pretty dated now, but it's still not too bad), the only things I've changed on it are the graphics card, the dvd reader (since the one it had broke randomly), and the power supply (also broke). 

No wifi, no bluetooth, no other additions besides a better power supply (from 300W to 700W)

Oh, and added some RAM (from 1g to 2)

---

### Post by Longinus00 on 2009-10-13
Can you output what you get when you type this?
```
lscpi -vvv
```

---

### Post by emarkay on 2009-10-13
> **'[s]Duke said:**
> It's an HP(it's getting pretty dated now, but it's still not too bad), the only things I've changed on it are the graphics card, the dvd reader (since the one it had broke randomly), and the power supply (also broke).  No wifi, no bluetooth, no other additions besides a better power supply (from 300W to 700W) Oh, and added some RAM (from 1g to 2)

Gimme a model number...  I will do some deep Googling and see if there are any similar issues "out there" that may give a clue.

Confirm that it's a PCI-e HD2600Pro - do you know what brand the card was?

---

### Post by [S]Duke on 2009-10-14
> **emarkay said:**
> Gimme a model number...  I will do some deep Googling and see if there are any similar issues "out there" that may give a clue.

Confirm that it's a PCI-e HD2600Pro - do you know what brand the card was?
It's an HP Pavillion a1430n. 

Brand? Aside from it being an ATI Radeon HD2600 Pro PCI-e x16, I'm not sure what other brand it has.

@Long: Apparently GRUB didn't really appreciate my messing with the BIOS, so I'll have to fix that (currently using the desktop for some work stuff) but I'll post the output as soon as I can.

---

### Post by Kazade on 2009-10-14
[S]Duke - It might be worth going to #radeon on IRC (Freenode) and explaining your problem - that's where the OSS driver (default giving you a black screen) devs live. They might know about the problem, or they might be able to get the information from you they need to fix it.

It does sound to me like this is a hardware/bios/kernel issue, because 2 different drivers (fglrx and oss ati) are failing - it seems lower level than the driver itself.

They will need the /var/log/Xorg.0.log file and probably a few others. To get this, use the default driver (e.g. move/etc/X11/xorg.conf somewhere) then reboot. You will probably be greeted by the black screen you love so much. Then press CTRL+ALT+F1 to get to a terminal (hopefully that will work). Log in, then run: 
```

cp /var/log/xorg.0.log ~/ 

``` 
to copy it to your home folder. Then move xorg.conf back, set the driver to "vesa" and reboot again.

Then you should get into your desktop, and be able to look at the log file or send it to us/the devs.

---

### Post by [S]Duke on 2009-10-14
> **Kazade said:**
> [S]Duke - It might be worth going to #radeon on IRC (Freenode) and explaining your problem - that's where the OSS driver (default giving you a black screen) devs live. They might know about the problem, or they might be able to get the information from you they need to fix it.

It does sound to me like this is a hardware/bios/kernel issue, because 2 different drivers (fglrx and oss ati) are failing - it seems lower level than the driver itself.

They will need the /var/log/Xorg.0.log file and probably a few others. To get this, use the default driver (e.g. move/etc/X11/xorg.conf somewhere) then reboot. You will probably be greeted by the black screen you love so much. Then press CTRL+ALT+F1 to get to a terminal (hopefully that will work). Log in, then run: 
```

cp /var/log/xorg.0.log ~/ 

``` 
to copy it to your home folder. Then move xorg.conf back, set the driver to "vesa" and reboot again.

Then you should get into your desktop, and be able to look at the log file or send it to us/the devs.

On the matter of Atl+F1 on blackscreen, yeah I tried that when it came up (this isn't my first driver-hell rodeo =P) but it leads to a multicolored sceen that freezes.

Is there an alternative?

I'm almost certain it's not a hardware issue though, like I said, the ATI drivers downloaded on Windows 7 work perfectly fine and even run games without any issues.

---

### Post by Kazade on 2009-10-14
> **'[S]Duke said:**
> On the matter of Atl+F1 on blackscreen, yeah I tried that when it came up (this isn't my first driver-hell rodeo =P) but it leads to a multicolored sceen that freezes.

Is there an alternative?

I'm almost certain it's not a hardware issue though, like I said, the ATI drivers downloaded on Windows 7 work perfectly fine and even run games without any issues.

You could try this:

[LIST=1]
[*]Start with the default driver (ati)
[*]When you hit the black screen, reset the PC
[*]In Grub, select the "Recovery console" and then when it prompts say "Root prompt without networking" or whatever
[*]Copy the Xorg.0.log
[*]Edit the xorg.conf to be vesa
[*]Reboot
[/LIST]

---

### Post by [S]Duke on 2009-10-14
> **Kazade said:**
> You could try this:

[LIST=1]
[*]Start with the default driver (ati)
[*]When you hit the black screen, reset the PC
[*]In Grub, select the "Recovery console" and then when it prompts say "Root prompt without networking" or whatever
[*]Copy the Xorg.0.log
[*]Edit the xorg.conf to be vesa
[*]Reboot
[/LIST]
Alright, I'll try that tomorrow.

I have work, class and sleep to do, so it'll probably be 15-20 hours before I can come back on, but rest assured as soon as I can I will post the output of all the above.

---

### Post by zika on 2009-10-14
Did You try simple:```
sudo dpkg-reconfigure -phigh xserver-xorg
``` to get You back on the tracks...?

---

### Post by emarkay on 2009-10-14
[S]Duke, nothing stands out on searches other than "HP BIOS sux; limted options" and that hte Power Supply in that PC is marginal in wattage.  I wonder if there are any things in Karmic that may be drawing an extra watt or two?

---

### Post by [S]Duke on 2009-10-14
Got a quick window in to reply:

@zika: Of course I did =P No luck there either =S

@emark: I know the built in power supply isn't enough to power a decent computer, that's why I changed it a few months back.

---

