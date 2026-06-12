---
title: "Ubuntu 6.10 Live CD won't Boot.."
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by dBLiSS on 2006-10-26
Trying to install Ubuntu 6.10, the Live CD freezes after the new splash screen does it's thing. Had a similar problem with 6.06 but when I used the safe graphics mode in worked fine. Not so in 6.10, I've tried everything recommended in the help section of the live cd. I am GUESSing it has something to do with my ATI video card (radeon 9800), but I dunno.. any help?

---

### Post by skabber on 2006-10-26
Mine Edgy Live CD is also freezing right after the Gnome splash screen.  But I have an NVIDIA card.  Safe graphics mode is also a no go for me.

---

### Post by Téragone on 2006-10-26
Same here with the AMD64 version.

Edit: the Live CD boot in a virtual machine with vmware server

---

### Post by unisol on 2006-10-26
trry downloading the alternate installcd from:[http://ftp.osuosl.org/pub/ubuntu-releases/edgy/](http://ftp.osuosl.org/pub/ubuntu-releases/edgy/)

---

### Post by jheffernan on 2006-10-26
It worked for me on my new MacBook 2.0Ghz, 2 gigs of ram.  Took forever and a day to boot though.  I just kept hearing the CD rom spinning, so I waited, (black screen for a while).  I didn't time it, but it definitely takes longer than 6.06 to boot.

Thought I'd add that in case it isn't freezing up but rather taking a long long long time.  :).

-J

New to linux and Mac.  Nothing like diving in and dual booting right off the bat!  Loving Ubuntu too...easy distro.

---

### Post by Corgan on 2006-10-26
Hey. I'm a user of Ubuntu on a slower machine, (366MHz Celeron). Dapper works fine, but the Edgy Eft install did not start up properly. I can't judge about Dapper because it was already installed on the drive when I placed it in this machine, but the lack of response to this thread concerns me. Any one have any luck with the alternative?

---

### Post by wolphin on 2006-10-26
Same here with an ATi Mobility Radeon X700XL - I just get a black screen after the new bootsplash... It's been like that for about 15 minutes now and still nada :(

I guess I'll have to go for the alternate install (*sigh* another 700MB download...)

[edit] Is there a bug report for this? I can't find one. [https://launchpad.net/distros/ubuntu/](https://launchpad.net/distros/ubuntu/)

---

### Post by Corgan on 2006-10-26
Alright, an update, if you'd like. I've done the alternate install, 3 minutes in. And sliiiiick. Time to play.

---

### Post by Shay Stephens on 2006-10-26
The live cd hangs for me trying to open gparted to manually edit the partition tables.  I am downloading the alternate cd now.

---

### Post by firey on 2006-10-27
I'm having this problem with ATI X850 Pro (agp) card. Same symptoms, 6.06 hangs with normal install but safe mode works - 6.10 doesn't work with either of the install methods.

Downloading the alternate installation later to see if it helps.

---

### Post by thecdn on 2006-10-27
Same problem with my ati X800XL video card. Did no one test this with ati cards? Or at least give us a warning that it just doesn't work and save the time/bother and download the alternate first.

I know there are issues with ati cards and their drivers but this is only the second distro (with Sabayon) out of many that I've tried that won't even boot up. I had no problems with previous versions of ubuntu, why the step backward?

---

### Post by wolphin on 2006-10-27
^ Exactly what thecdn said.

I've installed it with the alternate CD, and now I get the black screen after the installed version's bootsplash.. Great. I might have to chroot in from a live CD and install the ATi driver like that before it'll work!

---

### Post by thecdn on 2006-10-27
Great. So you're saying that you can install from the alternate cd but when you boot from the hd install you just get a black screen?

Let me know how your chroot attempt goes and if it works how to do it.

Last weekend after the same problems with the 6.10 rc disk I reinstalled a clean dapper and did all the updates including adding 3d ati drivers. Then I updated to 6.10 using the instructions on the wiki and it went great, except that it broke the 3d drivers. I followed the instructions for installing them on 6.10 to the letter but it didn't work.

---

### Post by kirian on 2006-10-27
I am running a Savage graphics card on an IBM Thinkpad. I had the same problem as many of you. I would get to a certain point on loading the live cd and then it would just hang on a black screen.

My final solution was to download the alternate install and run that. The first time I ran it after install it didn't boot up. I had to run in safe graphics mode then edit my xorg.conf file and change the bit depth from 16 to 24. Rebooted and now everything works great.

---

### Post by tman_ubuntu on 2006-10-27
I downloaded the 64bit cd as well and had the exact same problem except using an onboard video card.  I had the Ubuntu RC3 cd laying around and used that to install and worked great.  Once I got it installed it asked if I wanted to do a distribution upgrade.  Answered yes and everything updated to the new release.

I figured it was just the 64-bit version, but it sounds like it is both 32-bit and 64 Ubuntus.

---

