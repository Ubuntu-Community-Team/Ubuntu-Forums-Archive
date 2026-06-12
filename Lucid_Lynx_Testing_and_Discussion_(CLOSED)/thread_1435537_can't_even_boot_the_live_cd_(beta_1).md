---
title: "can't even boot the live cd (beta 1)"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by priegog on 2010-03-21
So... That's pretty much it. I've searched the forum to see what was going on. The cd's not the problem, since I've burned a bunch of them, and also tried them on my brother's computer (on which they work).
I suspect it has something to do with the video card (maybe the new nouveau driver?), because it actually seems to boot (for instance if I press the ENTER key the cd will start spinning again as if I've hit something)but the screen only shows a garbled mix of images from the BIOS splash screen and the plymouth splash screen. 

The video card is an nVidia GeForce G102M, BTW

Got any ideas? I tried booting with the acpi=off option, but same deal. I also tried both 64 and 32 versions, with identical results.

---

### Post by phillw on 2010-03-21
> **priegog said:**
> So... That's pretty much it. I've searched the forum to see what was going on. The cd's not the problem, since I've burned a bunch of them, and also tried them on my brother's computer (on which they work).
I suspect it has something to do with the video card (maybe the new nouveau driver?), because it actually seems to boot (for instance if I press the ENTER key the cd will start spinning again as if I've hit something)but the screen only shows a garbled mix of images from the BIOS splash screen and the plymouth splash screen. 

The video card is an nVidia GeForce G102M, BTW

Got any ideas? I tried booting with the acpi=off option, but same deal. I also tried both 64 and 32 versions, with identical results.

Don't know what others would suggest, but I'd suggest using the Alternate CD to install with.

Regards,

Phill.

---

### Post by wilee-nilee on 2010-03-21
As a long shot switch the drive type in bios from sata (ahci) to ide and see if this works.

---

### Post by priegog on 2010-03-21
Hmm, I was hoping I could use the live enviroment to test the compatibility with my hardware beforehand... But in either case, I find it worrying that at a beta stage this thing doesn't work with what is fairly modern (+/- 1 year) hardware. Specially since it isn't (AFAIK) very exotic hardware (it works pretty well with karmic). Come the final release, if it still doesn't work, I will have to give the alternate CD a try, but i was hoping this was an issue that could be resolved beforehand... Is my video card so rare ? AFIK it isn't at least not here in europe.
I'm still open for more suggestions...

---

### Post by howefield on 2010-03-21
There have been quite a few posters with issues booting the Beta 1 disc, me included. You're not alone ;-)

First "real" issue I've had, having said that - installing Alpha 3 and updating doesn't give me a problem.

Have a look at some of the other threads, not sure if anyone has posted any solutions other than trying the alternate cd.

---

### Post by ranch hand on 2010-03-21
These things can not be resolved unless the people with hardware that has a problem actually test the bugger.

If it is not working on your box at release go to the mirror, look yourself in the eye, and congratulate yourself for staying out of testing.

---

### Post by priegog on 2010-03-21
Well, that's what I'm trying to do, test it. But since in the FAQs and guidelines (where I've looked) there doesn't seem to be a way to troubleshoot booting issues... I'm kind of stuck. I'm willing to help, submit bugs, etc, I just don't know how to find the problem!

---

### Post by wilee-nilee on 2010-03-21
With earlier daily releases of Lucid some would not burn and boot with a CD but would load to a thumb with unetbootin and work fine. Also the linux usb loader as well.

---

### Post by VMC on 2010-03-21
> **priegog said:**
> ...
I suspect it has something to do with the video card ...
The video card is an nVidia GeForce G102M, BTW

Got any ideas? I tried booting with the acpi=off option, but same deal. I also tried both 64 and 32 versions, with identical results.
Try pushing F6, use "nomodeset". Also remove the "quiet" from the string.

If that doesn't work try recovery mode. F6 then add "single"

---

### Post by priegog on 2010-03-22
none of it worked, but thanks guys :)

---

### Post by ShadowDragon on 2010-03-22
Well, I'm kinda experiencing similar problems with my nvidia card aswell.

Booting the liveCD "nomodeset", makes things actually worse on my system, since the system halts with flickering diagnostic leds all over the place...

Booting the liveCD without "nomodeset" results in a running system, but an unusable screen. Switching VT's with Ctrl+Alt+F[1-9] doesn't work eighter...

I'm suspecting nouveau since it's default for nvidia card now. Is there any possibility to disable loading nouveau by specifying some sort of boot-option the thread-starter and I could use? I think we both are more then willing to test, but we are just out of options and need some input on how to test/debug the damm bugger.

I also found out that mmiotrace isn't in Lucid yet, so that a dead end too...

**Update:** Booting the most recent liveCD (20100322) with "single", results in a running system, but there is almost no difference than without the option, the screen keeps being a graphical-colored mess...

---

### Post by priegog on 2010-03-22
Precisely. It's not that I mind installing from the alternate CD come release time, but if the live cd can't boot with a reasonably common video card, I'd say that's a problem. What's your video card, by the way?

---

### Post by ShadowDragon on 2010-03-22
> **priegog said:**
> Precisely. It's not that I mind installing from the alternate CD come release time, but if the live cd can't boot with a reasonably common video card, I'd say that's a problem.
Agree.
> **priegog said:**
> What's your video card, by the way?
Also a very common one for laptops: Nvidia 8400M GS

BTW: if I run the same .iso in a virtual environment, like VMWare, it's working like a charm. Probably because the .iso uses the hardware-abstraction of VMWare instead of running directly on the graphics-card.

---

### Post by priegog on 2010-03-22
> **ShadowDragon said:**
> Agree.

Also a very common one for laptops: Nvidia 8400M GS

BTW: if I run the same .iso in a virtual environment, like VMWare, it's working like a charm. Probably because the .iso uses the hardware-abstraction of VMWare instead of running directly on the graphics-card.

Yup, AFAIK.
Also, I actually believe our video cards are based on the same chip... or something. LOL I can't really remember, but when I bought this lappy I looked into all of it and realised the video card thing is a crazy mess. But yeah, what a shame. Oh, well...

---

### Post by ShadowDragon on 2010-03-22
Done some more testing based on the [BootOptions](https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options)-page in the Community Ubuntu Documentation:

The breakpoint: "break=top" is the first thing ever that was able to produce a type-able terminal to put commands in :) If I only would know which command I need to type to continue the execution...
All the other breakpoints, like modules,premount,mount,bottom and init resulted in eighter on static gray-screen with no VT's to type in, or they had no effect and the liveCD booted to some scrambled colored-screen with propably should be the desktop...

Boot-option "vesa video=vesafb" didn't had any effect.

Boot-option "xforcevesa" is one of the first things that had a visual effect after the console is gone. It resulted in a totally different, but still corrupted screen, but I saw the same artifacts as some others on the forums have posted.

Boot-option "rdblacklist=nouveau" didn't had any effect.

I see some nouveau-dmesg-output flying by (after the break=top breakpoint), but it's to quick to read and I tried video-recording it with my cell-phone and playing it with mplayer with still-frames each 0.1ms, but the only things (6 lines out of the presumable 50) I could decipher weren't useful at all, just standard output-info...

---

### Post by ShadowDragon on 2010-03-23
@priegog: What's your screen signal? LVDS?

System > NVIDIA X Server Settings > GPU 0 > DFP-0 > Flat Pannel Information > Signal:

---

### Post by priegog on 2010-03-23
Yup, LVDS. Don't know what that means tho. Care to say what is it you're thinking?

---

### Post by ShadowDragon on 2010-03-23
I didn't want to give you any false hopes, that's why I posted the question without elaborating. :)

I'm having a bug-report running on Launchpad about Nvidia cards with LVDS-sync-problems: [Bug #539878](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539878) Maybe you should read it through to see if it applies to your case as well. If so, feel free to subscribe yourself to the bug, so you would get updates if a developer is posting some additional information. ;)

The bug-report got triaged with high-priority some hours ago, so I'm hoping I can provide some useful debug-info so the devs can fix it without to much trouble. :)

---

### Post by priegog on 2010-03-24
Ahh thanks, man, as far as I can tell this is EXACTLY what's going on with me also; I've been able to duplicate everything that is described. *subscribed*

---

### Post by marfal on 2010-03-24
Same thing for me, tried to run Alpha 3 and Beta 1 as live CD on two PCs both with nvidia graphics cards*. One is an AMD processor the other a Intel. neither will run the live cd although I can run from the cd on my work Dell laptop with ATI graphics card.
PCs have Ubuntu 9.10(Intel) and Mint 8(AMD) both run great with advanced graphics turned on.
I would be very hesitant to install from "alternate Disc" without a successful test from a live cd first.

*(Correction - AMD processor PC has an ATI graphics card installed)

---

### Post by ShadowDragon on 2010-03-24
@marfal: Have you tried booting the liveCD with the "nomodeset" option?

---

### Post by marfal on 2010-03-24
> **ShadowDragon said:**
> @marfal: Have you tried booting the liveCD with the "nomodeset" option?
Thanks, I've never had to use the F6 options for booting a live CD before - everything usually just works (pretty much)....
I have used the "nomodeset" option on both PCs and can successfully boot both to a live session.
Incidently I was wrong, the AMD processor PC has an ATI graphics card installed. once I'd used the "nomodeset" option everything was peachy.
The nvidia card required the proprietary drivers to get a reasonable resolution.

---

### Post by ShadowDragon on 2010-03-25
So that means some ATI graphics card now also need the nomodeset work-around, yeey... Well that means you can go and install you systems, have fun testing!

I hope these things get fixed before beta2. Since the workaround don't have any effect on my system, I haven't even been able to decent test the beta. It would a shame that due to 1 bug, I can't test for other bugs during the test-period...

---

### Post by rj45 on 2010-03-26
Latest daily build Live CD boots fine for me when I used the "modereset" option.  Previously, Beta 1 would just hang with no activity at the boot graphic screen.
Nvidia 9500GT card

---

### Post by ShadowDragon on 2010-03-26
Hey rj45, thanks for dropping by, I shall see if I'm also so lucky later today.

---

### Post by priegog on 2010-03-26
Yeah I'm zsyncing my image right now to try it out tonight... Thanks.

---

### Post by ShadowDragon on 2010-03-26
Well, to bad, booting the 20100326 without 'nomodeset' is still the same visual trouble and booting with 'nomodeset' still makes my system crash with my diagnostic leds flashing on and off... not a good sign...

---

### Post by rj45 on 2010-03-26
> **ShadowDragon said:**
> Well, to bad, booting the 20100326 without 'nomodeset' is still the same visual trouble and booting with 'nomodeset' still makes my system crash with my diagnostic leds flashing on and off... not a good sign...

Puzzling, since Xubuntu 9.10 is running fine for you now.

What model Nvidia card do you have?

Try booting without the "quiet" boot param and maybe you'll
be able to get some kind of diagnostic. You might have to
toggle (Alt-F2 or something) to get to a text mode console
during boot.

I also suspect the new "noveau" Nvidia driver. The closed source
driver has been very stable for me.

---

### Post by ShadowDragon on 2010-03-26
Indeed, 9.10 is running like a charm. I'm having a 8400M GS.
Problem is that my system is too quick to read the output if I leave out the 'quick'-option. I've tried to video-capture the boot-messages and play it at rate of 0.1 msec still-frames, but the small part that's readable is just normal.

And Ctrl+Alt+F[1-6] doens't work either since nouveau doesn't allow to switch VT's on my grahics card, is already reported on a wiki-page.

So all I can do is being in stand-by mode for the case a developer wants some debug-info so he can fix it...

---

### Post by priegog on 2010-03-27
Well in my case all I got is that when I booted with nomodeset at the end of the booting sequence it dropped to the command line. I guess that's an improvement, but still not good enough.

---

### Post by amano on 2010-03-27
priegog, did you file a bug? Or is there an existing one already?

---

### Post by priegog on 2010-03-27
Yeah, the one ShadowDragon showed me [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539878](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539878)

---

### Post by priegog on 2010-04-14
OK, so I tried to install the system with the alternate CD beta-2 (I previously tried to boot the live CD, but the problem persisted), and I did, but when I boot the system, I have the same problem as with the live CD. Now this is a very serious problem, I think. The bug is already filed, what else can we do to get this fixed before release?

---

### Post by ShadowDragon on 2010-04-14
> **priegog said:**
> OK, so I tried to install the system with the alternate CD beta-2 (I previously tried to boot the live CD, but the problem persisted), and I did, but when I boot the system, I have the same problem as with the live CD.
That ain't good...
> **priegog said:**
> The bug is already filed, what else can we do to get this fixed before release?
I'm wondering the exact same question... Maybe you should ask [Scott James Remnant](https://launchpad.net/~scott) since he's the only one who seems to know what's going wrong... Keep me posted, will ya?

---

### Post by priegog on 2010-04-22
Crap... tried the RC today, and still no dice... even with the "nomodeset" option. What can I do at this point? I said I don't mind installing from the alternate, but that doesn't do any good if the installed system can't boot either. 
See what gets me is that this is a STUPID problem. The problem is with a driver that won't work with some cards, and it's preventing the system from BOOTING (well, not booting but from having a useable interface). The nouveau driver would ONLY be used temporarily, until the proprietary drivers could get installed. The system should be able to figure out the video driver isn't going to work and default to vesa graphics. It is stupid because it killed support for some (I'd guess quite a lot of)users to bring in the "in" OSS driver which I very much doubt a lot of people will stick with after the first boot anyways.
And to make matters worse there isn't a page where they help you troubleshoot these kinds of deals or at the very least the boot parameters needed to default to vesa graphics (which I'm sure DO exist... hope?)
To make matters worse the bug was reported with plenty of time but it just didn't get given the importance it should have. 
ARG!!! Can someone please help out some fellows here?

---

