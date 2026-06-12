---
title: "Could someone in authority tell us the truth?"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by Silvertones on 2010-05-12
Karmic works flawlessly however I would like to update just because. It appears that LL 10.04 is really plagued with issues.
Does LL 10.04 need to go back into testing or should all of us that are not total geeks just wait for 6 months?
Thanks

---

### Post by blueyelabs on 2010-05-12
I've found that 10.04 works perfectly for me. No bugs whatsoever and it has been better than anything I've had previously: no user switch bug, no sound config problems, no flash problems...
Much faster to boot.

In short: no problems, it's better than it ever has been.

---

### Post by Grenage on 2010-05-12
Minor issues on 'some' programs.  I'd personally wait a month or two, but most users won't have a problem.

---

### Post by dino99 on 2010-05-12
> **Silvertones said:**
> Karmic works flawlessly however I would like to update just because. It appears that LL 10.04 is really plagued with issues.
Does LL 10.04 need to go back into testing or should all of us that are not total geeks just wait for 6 months?
Thanks

the quick answer for you is: boot with a live-cd to see if you have issues

---

### Post by Silvertones on 2010-05-12
Dino that sounds like a good plan. If the live works fine then I shold be OK. I DL the alt CD to do the update. I'm waiting for the Live to come in the mail.

---

### Post by dino99 on 2010-05-12
> **Silvertones said:**
> Dino that sounds like a good plan. If the live works fine then I shold be OK. I DL the alt CD to do the update. I'm waiting for the Live to come in the mail.

a small howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by Envy Life on 2010-05-12
I've had 2 flawless upgrades.  The third is a relative disaster with the nvidia driver, and it was a new install.  The installer is not putting it in the right place, thus it's not loading, and thus I get segfaults out of Firefox and most other video dependent applications.  

Really, truly an awful experience on that box...to the point where if I can't get it working in a week I'm putting on windows.   I've opened 2 threads on these forums with tons of information without a single response.  Pretty frustrated.  This is an issue you will not find using the live CD.

---

### Post by fargle on 2010-05-12
Not a single issue here - I did a reload from Karmic and Lucid's even better.  My install is pretty complicated with multiple encrypted volumes, Truecrypt, multiple monitors, you name it, and the entire reload and resetup took a couple of hours.  Loving it!

There have already been a bunch of updates from upstream, but wait a week or so if you want to be surer.

---

### Post by Silvertones on 2010-05-12
I think I'll head off to the library tomorrow and DL the Live CD instead of waiting for the mail. If the live runs OK I'll update with the Alt CD I burned.

---

### Post by daemoncat on 2010-05-12
> **dino99 said:**
> the quick answer for you is: boot with a live-cd to see if you have issues

That is unless you have a radeon x-series video card (x700 through x1950, IIRC). Then the CD works beautifully, but you will either lock up after the install, or have to use a console and do some really kludgey stuff that's way past the casual home user's level.

I'm really disgusted with this. No warning what-so-ever. Yet, the x-series radeons are supported by Windows 7.

---

### Post by eigojoe on 2010-05-12
> **blueyelabs said:**
> I've found that 10.04 works perfectly for me. No bugs whatsoever and it has been better than anything I've had previously: no user switch bug, no sound config problems, no flash problems...
Much faster to boot.

In short: no problems, it's better than it ever has been.

That's great blueyelabs, but since this is a support forum it's a fair bet that others haven't been quite as fortunate as you. Personally all I've been able to get is a blank screen!  ](*,)

---

### Post by efflandt on 2010-05-13
I did a regular install of 64-bit Lucid to a USB hard drive **first**, and it is a good thing I did.  Although, that worked flawlessly with my Toshiba A105 from 2006, I had an occasional video boot glitch on a Dell laptop of the same age, which worked fine if I got past that.  But I could not get Lucid to boot on my desktop from either of 2 USB drives, including one drive that booted 64-bit Karmic fine.

Apparently the Asus motherboard on my HP desktop from 2004 does not like the new partition alignment.  So I had to use **partman/alignment=cylinder** parameter when reinstalling Lucid on the USB drive. Then it booted fine on my desktop.  Suspend did not work, but I thought it was just because the drive was external (maybe not).

Once installed on the desktop, suspend or hibernate still did not work, and even with desktop effects disabled, some types of video movements were sluggish.  Apparently my ATI X1300 did not like the new kernel mode KMS video driver.  **nomodeset** kernel parameter made video as snappy as Karmic, and resolved the suspend/hibernate issue.

My Logitech diNovo Edge Bluetooth keyboard/mousepad did not work in Lucid on any system at all, which is strange, because it is normally totally OS independent (works for CMOS set up and BIOS password).  I resolved that by simply commenting out the Logitech section of /lib/udev/rules.d/70-hid2hci.rules (which had changed slightly from Karmic).

So everything is resolved for me.  But such issues could frustrate a new user who might be totally lost, and possibly lose the ability to boot their precious Windows.

---

### Post by Envy Life on 2010-05-13
Yes, ATI really rubbed me the wrong way by recently dropping support for my 9600XT in their Linux driver... it's why I did not buy another ATI card to replace it because they'll probably make it obsolete in a few years too.   However now I'm caught with a bad Nvidia driver installation too, which is a Ubuntu issue... stuck between a rock and a hard place.

---

### Post by llawwehttam on 2010-05-13
I use ubuntu 9.10 on my laptop with no issues at present. However on my desktop I tried to install Xubuntu 10.04 and it acted as if the 'a' key on the keyboard was stuck down. (its fine in arch linux) and this issue was the same with any of the 10.04 variants.

I'm going to wait a few months to see how 10.04 turns out before trying it again.

---

### Post by wkulecz on 2010-05-13
If it ain't broke, don't fix it!

Is 9.10 doing all you require?

Does 10.04 have something you need but can't get for 9.10 -- like Long Term Support?

If not, best I see is you waste some time upgrading and "break even" at the risk of major hassles should some obscure critical problem affect your system.

So far 10.04 has been very good for me, although Glade3 is still a missing piece for me. I only use LTS releases so I'm moving from 6.06 and a few 8.04 systems to 10.04 this summer on all systems.

---

### Post by Mark Phelps on 2010-05-13
> **daemoncat said:**
> ... Yet, the x-series radeons are supported by Windows 7.

Well ... yes and no.  I'm running an X-series and the latest ATI Win7 video driver is the "legacy" driver and it's Catalyst version 10.3.

So while, technically, Win7 does support the X-series, the drivers do not provide the same capabilities as do the current ATI 10.x Win7 drivers.

Which, when you think about it, is not a lot different than in Linux -- where the open source drivers support the X-series but do not provide all the features of the fglrx drivers.

---

### Post by MisfitI38 on 2010-05-13
The truth: bugs and regression will always be part of the upgrade process, due in large part to the overall GNU/Linux/FOSS development model.

It can be advantageous to become more intimately familiar with your operating system of choice. Familiarity and competence will allow you to solve such breakage issues when they occur. 
It might also be time well invested to try a rolling release distribution, at least temporarily, which will require OS adjustments and configuration changes in smaller increments and leading to an accumulation of knowledge and resources that will help you to manually tweak the nuts and bolts of any related system.
If you choose to use a UNIX-like system, it will help in the long run to make the machine work for you, rather than be at the mercy of recommendations or the upgrade path and experiences of others.
Good luck.

---

### Post by Silvertones on 2010-05-15
Well I did the upgrade and ended up with the BSOD. Got PO'd and uninstalled the whole thing. I'm now back to a fresh install of 9.1. It runs better then before as I'm now smarter about it. When the CD comes I'll run the live and see if I even like it. Hopefully the BSOD issue will be fixed.
If I hadn't uninstalled 10.04 and waited a day and did some research I would have seen my error. I found the fix. It said when grub loaded to hit e and then add  i915 modeset = 1 "after "splash screen" so I made an entry JUST like that and of course it didn't work. In the line that had "splash screen" I needed it to be edited to read "splash screen i915 modeset = 1"
Because I'm on dialup and have a Samba network it's a lot of work to do a fresh install.

---

### Post by dodderer on 2010-05-15
I have just updated to lucid . while using(?) 9.10 I had so many hang-ups,freezes , crashes that I went back to 8.04 in which I had no problems. Now I am back to numerous random hang-ups. Is there something innately wrong with post 8.04 issues . or is it me? What happens now is the screen just goes black then flashes then flashes a series of black and white vertical stripes about 6/7 mm wide across the top third of my screen. The only cure is to switch off and reboot. then wait for the next crash.

---

### Post by Silvertones on 2010-05-16
Is this the type of issue that'll get fixed or are we destined to work around hell. If it's going to get fixed I'll wait. we've got a year.

---

### Post by wandalalakers on 2010-05-16
I've been using kubuntu since 7.10 and I love kde.  After 7.10 I installed 8.04.  Since I prefer LTS versions, I waited until kubuntu 10.04 arrived.  I even did a fresh install and I'm still having problems.  
Here are the problems I'm having:

Kubuntu 10.04 when I insert an audio cd in my lite on dvd rom, I get a read error.  I can't quick format DVD-Rws.  I can't continue a multisession DVD-R that was created with k3b 1.04 in kubuntu 8.04.
Ubuntu 10.04 when I insert an audio cd, it shows up on the desktop.
Kubuntu  I can't quick format DVD-Rws.
I'm beginning to think that kde 4.x does not like my computer.
I even tried Suse 11.1 and I can't get an audio cd to load on my dvd rom drive.
With kubuntu 8.04 I can continue my multisession DVD-R.
I even installed Debian 5.04 kde and I can't quick format DVD-RWs or continue my multisession DVD-R.
I'm an LTS girl and I hate to have to go back to kubuntu 8.04.  On 8.04 I couldn't quick format DVD-Rws either.
Someone on launchpad says it's because I need the original cdrecord.
I even tried that and still couldn't quick format DVD-Rws.
As of right now, I'm pretty bummed out.
I really hate to have to go out and buy windows 7.
I'll probably just wait it out and see if these bugs in kubuntu 10.04 are fixed in two months.

---

