---
title: "Nightmare upgrading from 10.04 LTS to 12.04 LTS"
date: 2014-06-01
forum: Installation &amp; Upgrades
---

### Post by thomas.pppppp on 2014-06-01
Help, please, I'm tearing my hair out!  All I wanted is to upgrade so that I could get Chrome to work because Firefox is sooo slow with Google Docs!

First, everything seemed promising (after figuring out I can't use a CD anymore because the file is now too big, luckily it seems to work fine with a DVD).  I installed 12.04 with the option of keeping my programs and files.

A few things I noticed immediately:  I couldn't find any of the programs I had anymore - Minecraft, Terminal, GIMP, anything really!  Ok, so apparently I have to use the icon at the top and then type in the name and it shows up.  I can live with that, I suppose I can put the ones I often use on the bar on the left-hand side.

Now comes the showstopper:
Previously I had a script that switched my screen to the external monitor using two lines starting with xrandr and the nice thing I found in 12.04 is that the Display settings correctly recognised the external monitor and let me set resolution and which one to use - nice! (or so I thought at the time).  Then I rebooted for the first time and all of a sudden the boot menu shows me a bunch of options I didn't have to go throuigh before:

* Ubuntu, with Linux 3.11.0-15-generic --> if I select this one, I get some text scrolling past the laptop _*and*_ external monitor, then the ubuntu logo and the five progress dots with some message about a /tmp drive, then **both screens go blank and nothing EVER HAPPENS AGAIN**.  The laptop is on, both screens are blank, some hard disk activity from time to time and also the backlight of the external monitor goes on and off, but both screens remain black (I waited 10 minutes).

* Ubuntu, with Linux 3.11.0-15-generic (recovery mode) --> if I select this one, the text scrolls only on the laptop screen, then it goes into a Recovery menu.  I select "resume" and Ubuntu boots fine, but I only have a picture on the laptop screen.  If I go into the Display settings, it only shows the laptop screen, **it doesn't show any external monitor anymore!**

Is there any way I can fix the display settings again, like resetting the settings or something?  Maybe I did something wrong, after the installation, because before the first reboot everything was fine, the problem is, if I put the DVD back in, I only get the option of installing 12.04 alongside the existing 12.04, which seems rather pointless, or to completely wipe out the computer, which would mean I lose all sorts of things (I have backups, but it would be quite a hassle, plus I'd have to re-install things like Minecraft).

PS: I also notice that shut down never really shuts down, and restart doesn't restart (last line on the screen is "* Will now restart", but it never does.

I'm wary of all these constant hassles just to keep a basic working computer and that was a big reason for me to switch from Windows to Linux.  10.04 has served me well for years, but now I'm extremely disappointed - I thought I'd be safe going from one LTS release to the next :-(

---

### Post by TheFu on 2014-06-01
If you'd have asked this question in 2012, more people would be current and able to help.  Most of us LTS users are migrating from 12.04 to 14.04 now.  Support for 10.04 desktop ended over a year ago. Have you noticed that the patches really dropped off  and that no GUI patches have happened recently?

At this point, any new deployment should be with 14.04 unless there is a really, really good reason NOT to do it.  IMHO.

Migrations without a fresh install tend to see major changes in the way that things work. It is easiest to get help within a few months of the LTS release.  For example I vaguely remember that resolveconf was introduced with 12.04 - it was a minor hassle at the time.  With 14.04, upstart changes impacted me ... but I haven't migrated any desktops there yet. Purely servers without any GUI.

The way that I migrate from system to system is outlined here: [http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview](http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview)

Anyway, sorry that I can't really help with the 12.04 issue. **Sometimes searching for the exact model of computer/laptop and "ubuntu 12.04" will lead to previously found solutions.**

---

### Post by oldfred on 2014-06-01
I have an old 4:3 monitor and liked the old gnome2 with top & bottom panels. Tried Unity a bit on test installs and it is a lot better in 14.04 than earlier versions, but I often open the same app and have to click twice to get to correct window. So I install fallback/flashback which is the old menu system, but still Ubuntu not one of the flavors.

They have changed name between 12.04 and 14.04 but basically the same function. 
 [https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback](https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback)
[http://www.omgubuntu.co.uk/2014/04/ubuntu-14-04-classic-gnome-flashback-session](http://www.omgubuntu.co.uk/2014/04/ubuntu-14-04-classic-gnome-flashback-session)
Flashback/fallback in 14.04 Kansasnoob
Installing the package 'gnome-session-flashback' does exactly the same thing as installing the package 'gnome-panel'.
[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)
[http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477](http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477)
[http://ubuntuforums.org/showthread.php?t=2184682&p=12986002#post12986002](http://ubuntuforums.org/showthread.php?t=2184682&p=12986002#post12986002)
[http://ubuntuforums.org/showthread.php?t=2184682&p=12971487#post12971487](http://ubuntuforums.org/showthread.php?t=2184682&p=12971487#post12971487)

      
 12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 
[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

I am still on 12.04 as my main system. 14.04 seems to work well also, but not totally converted yet. But I only have one monitor, so do not know dual monitor issues.
What video card? That may be most of the issue.

---

### Post by thomas.pppppp on 2014-06-01
My computer is an old HP/Compaq laptop with a 4:3 Dell monitor and 512MB memory.  I don't think it's a compatibility issue, because when I first installed Ubuntu 12.04, everything was fine, so I'm thinking that configuring the monitors using the Desktop settings is what screwed up some sort of config.

Re. 14.04:  I noticed 12.04 is already *a lot* slower than 10.04, to the point where it looks like I'll have to install LXDE, so I don't want to go as far as 14.04 - it's even newer, so who knows what issues there are there...

Thanks for the replies, unless someone can send me some command lines around checking/resetting video config, I think I'll have to bite the bullet and do a clean 12.04 install.  Btw., if I start 12.04 from the install DVD, both monitors display a picture just fine.

---

### Post by oldfred on 2014-06-01
the fallback/flashback is lighter than Unity. I cannot run 12.04 with Unity on my 2006 laptop with 1.5GB RAM, but it runs ok with fallback.

But with only 512MB, Lubuntu may be better. 
Full Ubuntu is really intended for newer computers with lots of RAM and decent Video systems.

---

### Post by mörgæs on 2014-06-01
Lubuntu did not have long term support until 14.04, so this is your best candidate.

Why do you expect 14.04 to be slower than 12.04? For Ubuntu it is the other way around and for Lubuntu the two releases are about the same speed.

---

### Post by thomas.pppppp on 2014-06-01
because in general it seems OS versions get slower and slower as more features are added.

I'm now installing LUbuntu 14.04 LTS, since I have to wipe the slate clean anyway.  My heart sank when after a promising start, I got a "kernel panic" (after the initial screen where you choose language, etc.).  Stubbornly I just did the same thing again and now it's into the usual install screens... fingers crossed (but I have to say, I *_should not have to cross fingers_* for crying out loud, I'm installing a fresh version with no baggage...!

...BUT NO!  Now it got stuck on the "Who are you?" screen - was just finishing changing the computer name, but now the cursor is stuck, no mouse pointer anywhere, no reaction to any keys.  Is LUbuntu flaky?  Should I stick to the full Ubuntu? ...again, tried the same thing again and it got past that screen fine and continued all the way.  Next scare:  After telling me it needs a reboot, I pressed the button, it seemed to reboot, showed the Lubuntu logo with 3 of 5 progress dots lit and ejected the DVD drive.  Ok, so I took out the DVD ...and... nothing.  Just stuck with the logo and the three dots (I waited 5 minutes before doing a power button reset).
Next scare: 3 error messages about some b43 drivers missing, but it boots fine now and I have a picture on both screens and internet access, yay!

(PS: I'm tying these posts on my work laptop, which is Windoze (no choice ;-)

---

### Post by oldfred on 2014-06-01
Did you put a space in either the  computer name or user name. That always causes issues.
With Linux never use spaces. Use under_score, or CamelCase or justaname.

---

### Post by TheFu on 2014-06-01
Perhaps the CPU can't handle PAE mode?  Is there an alternate installer?

---

### Post by thomas.pppppp on 2014-06-02
no, didn't have any spaces - maybe the CD/DVD drive is getting flaky, but I'd expect the installer would say so if it has trouble reading the DVD.  Anyway, 3rd time round it worked fine, and everything is still working fine after a couple of reboots, using the buillt-in Display settings to set it to display only on the external monitor (very impressed that that worked!).  So, **everything is working now - LUbuntu 14.04** (apart from the b43 firmware error messages briefly flashing by - I think it has to do with the wireless in the laptop, but I don't use that).

I've even installed a few things already, GIMP, Chromium, Java, and those are all working fine and it's even snappier/faster than 10.04, which is great (although it took a while to get there, e.g. the bug with Chromium where it turns out I had to turn off the ibus!).

The only thing ***[COLOR=#ff0000]not working properly is Minecraft[/COLOR]*** - it used to run fine in 10.04, and even now the installation was easy (thanks to the Minecraft installer that now pulls everything it needs incl. things like lwjgl), and it all starts ok in the starting screen and then until it gets to the game screen (after the Mojang screen), where I *can *see the buttons (start single player, multi player), but the background is all screwed up (mostly white, with a few pixels here and there no slowly moving world in the background) and it's completely stuck.  Maybe it's something with the 3D of the graphics driver?  any thoughts on what could be different in that regard between 10.04 and LUbuntu 14.04?

---

### Post by mörgæs on 2014-06-02
> **TheFu said:**
> Perhaps the CPU can't handle PAE mode?  Is there an alternate installer?

Please don't mention PAE unless original poster does. There's more than enough PAE-fear going on in Ubuntuforums.

Thomas.pppppp, please mark the thread 'solved'.

---

### Post by HR70s on 2014-06-02
I also have 10.04 since it came out. I've not had any issues running google docs. or anything Firefox isn't slow so I'm not sure if you don't have something else going on that's
causing you issues. Yes 10.04 is old by standards but for what I do I see no reason to change.

---

### Post by mörgæs on 2014-06-02
The reason for leaving 10.04 was posted in #2: There are no more security updates.

---

### Post by TheFu on 2014-06-02
> **HR70s said:**
> I also have 10.04 since it came out. I've not had any issues running google docs. or anything Firefox isn't slow so I'm not sure if you don't have something else going on that's
causing you issues. Yes 10.04 is old by standards but for what I do I see no reason to change.

If the system is not connected to any network, then I agree completely.
OTOH, if the 10.04 system is connect to any network, especially the internet, then there are KNOWN attacks to break in and it is just a matter of time or 1 tiny mistake by an end-user to have the system corrupted. 10.04 desktop is like WinXP at this point. Dangerous.

10.04 server is supported for another year - we have 2 systems still running that, happily. We are planning migrations to 12.04 ASAP for one of the machines and going directly to 14.04 for the other one.  These are NOT desktops.

If a system is on a network, it needs to be actively patched to protect against attackers.

I personally think that running a supported [Ubuntu LTS is the best answer today]("http://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release") for these needs.

---

### Post by thomas.pppppp on 2014-06-03
I have marked this as "Solved", however, the real issues have not been solved, only circumvented.  A summary:

1) Upgrade from 10.04 LTS to 12.04 LTS broke my system to the point I had no choice but to do a clean re-install.  In my opinion this isn't really acceptable for what wants to be considered a mainstream OS - things like this are the reason less Ubuntu-savvy people like me dread and avoid upgrades!

2) I "fixed" it with a clean install of LUbuntu 14.04, however, even that had some minor issues like the installer getting stuck, and a major one with Chromium not working (no keyboard input - existing and acknowledged bug, just google "chromium keyboard input lubuntu") - again, I think a major browser not working at all in an LTS version isn't really acceptable for "average" mainstream users who are not going to figure out how to turn off the iBus (Whatever that is).

3) Minecraft is sadly still not working --> I might open a new thread on that; since Java is working fine, and Minecraft starts fine until the screen after the Mojang screen, which is the first one that has a 3D rendered scene, I'm guessing it's related to the graphics driver (Note: other than Ubuntu nothing has changed on my system, I tried it with the same Java and lwjgl as before and with other versions, always same result in 14.04).

---

### Post by TheFu on 2014-06-03
I usually don't respond to things that feel like rants, however, a little more understanding of the way this stuff works may be helpful to future lurkers.

Ubuntu isn't the product of 1 company. It is the output of thousands of developers, most working for no pay, in their free time, for fun. Canonical takes the output from those large groups of "cats" and the better organized things from the Debian team (also not paid people) and builds a relatively solid, cohesive OS they can distribute.  It isn't perfect, but many of us find it significantly better than other alternatives - AT ANY PRICE.

**I love LTS Ubuntu. LOVE IT!**  Not a fan of the intermediate releases, but those serve a critical purpose as well!  Better than holding back everything in an OS for 10 yrs before the next release, IMHO. Also better than completely dropping support for old hardware ... just ask the people that had PowerPC Macs about them (BTW, they run Ubuntu fine). 

Sorry if I've broken any forum rules with these statements. I'm just some guy, currently in Tx, ... not affiliated with Ubuntu / Canonical in **any way**.  I am a LUG organizer and I'm active (in my own way) supporting the introduction of F/LOSS into corporations and governments around the world.

> **thomas.pppppp said:**
> I have marked this as "Solved", however, the real issues have not been solved, only circumvented.  A summary:
At least you **COULD** work around the issue!

> **thomas.pppppp said:**
> 1) Upgrade from 10.04 LTS to 12.04 LTS broke my system to the point I had no choice but to do a clean re-install.  In my opinion this isn't really acceptable for what wants to be considered a mainstream OS - things like this are the reason less Ubuntu-savvy people like me dread and avoid upgrades!

Upgrades for both other mainstream OSes often forces a fresh install - or cannot be performed on the current HW. There are always a few systems that have issues with every OS upgrade. I can assure you that the vast majority of people who upgraded FULL-PATCHED SYSTEMS within 6 months of the initial release date didn't have major issues.  I know that I didn't  --- besides resolvconf stuff. In fact, a few of the GUI programs I needed had stopped working on 10.04 5 months earlier because the specific, independent, development team decided in late 2011 to stop working on 2010 distros.

Have you ever tried to contact the main OS vendor for support?  I have.  It was worthless.  The help here is 1000x more than my company got from them and the hardware maker who shipped that OS on their hardware. It was really frustrating.  Probably similar to what you feel today.

> **thomas.pppppp said:**
> 2) I "fixed" it with a clean install of LUbuntu 14.04, however, even that had some minor issues like the installer getting stuck, and a major one with Chromium not working (no keyboard input - existing and acknowledged bug, just google "chromium keyboard input lubuntu") - again, I think a major browser not working at all in an LTS version isn't really acceptable for "average" mainstream users who are not going to figure out how to turn off the iBus (Whatever that is).

Chromium works for me on the one 14.04 system I've migrated. Can't really comment on the specific issue you are seeing - since I don't use the standard GUI. Again, I suspect it is an exception, not the rule. That doesn't make it any less frustrating to you. I use lxde instead of Unity for the GUI. It is lighter and more like Ubuntu 10.04's GUI.  **sudo apt-get install lxde** will install it in about 3-5 minutes. Then logout, select LXDE from the "gear" prior to login. You might like it more. Doesn't hurt to try it.

> **thomas.pppppp said:**
> 3) Minecraft is sadly still not working --> I might open a new thread on that; since Java is working fine, and Minecraft starts fine until the screen after the Mojang screen, which is the first one that has a 3D rendered scene, I'm guessing it's related to the graphics driver (Note: other than Ubuntu nothing has changed on my system, I tried it with the same Java and lwjgl as before and with other versions, always same result in 14.04).

Yes, you should open a new thread about this.  I've never run Minecraft and generally avoid Java stuff - moreso since Oracle got involved. When you post the new question, if you mention the exact video card and drivers being used, that would be helpful.

Anyway, I hope you will return here again, not just to ask, but to answer questions.  We really value your perspective on this stuff and even the complaints DO help ... if only to let others know about issues.  

I'd also encourage you to find a local LUG where face-to-face help can be acquired.  My metro area has 5 extremely active LUGs, so most should have at least 1 - usually at a University.  One of those meets every Sunday in a laid back, no presentation, way.  We work through issues together, discuss nerdy things (outside Linux) and complain about Distro-X, Y, and Z for using {insert-whatever-new-way}.  Most people only show up a few times annually, which is just fine. They are old friends after a few visits. ;)

---

### Post by thomas.pppppp on 2014-06-03
Dear TheFu,

I feel I owe it to you to respond:

1) **Thank you** for taking the time to respond.

2) Sorry if it came across as a rant, it wasn't meant to.  So, for the record:  ***I actually do love Ubuntu***, because
           - a) anything from Micros**t is indeed worse in terms of: support (I'm amazed how quickly people responded here), reliability, security.
- b) it allows our family to run a modern OS, largely hassle-free, on old hardware to do basic things like browsing, email, a few light games, word processing, homework.

My "closing"-post was intended as a perspective from an average person, not a Linux specialist.  I feel that if Ubuntu wants to be taken seriously, things like this matter: Major browsers *should* work 100%.  Upgrades from one LTS to the next *should *work 100%.  I am not saying it's easy or even achievable, and I'm sure a tremendous amount of unpaid effort has already gone into making it work for 90%+ of cases.   I just wanted to point it out as a reason for the reluctance of an "average" user to upgrade (in response to replies like "why are you still on an unsupported OS?!?").

It seems to me that geeks (and I mean that in a very respectful way) tend to focus on the latest and greatest tech-wizzbangs, frameworks, etc., rather than on the boring bits of making computers "just work".  There may be a solution for all the problems I've had, but users like me are not going to go to LUGs or browse forums or apply patches or config fixes.  I have other hobbies.  What I've done here (e.g. that ibus thing) is already way out of my depth and I have no desire to learn it, I just want a computer that keeps working with no hassle (and fwiw, I'd be willing to pay a small amount for it).

  By and large, Ubuntu does provide that hassle-free computing, but for me the past few days unfortunately seem to confirm the old saying "never touch a running system".  Oh well, with that upgrade done, hopefully I can be another couple of years without "computer maintenance" ;-)

---

### Post by TheFu on 2014-06-03
Appreciate the comments.

There is no such thing as "without computer maintenance" any more than there is "without car maintenance" - oil changes, air filter changes and swapping in a new transmission as necessary from time to time.
I've written an article about Debian/Ubuntu System Maintenance that Lifehacker republished a few years ago. It is  [updated for 2014 here.]("http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs").

All the "average users" that I know do not install OSes. They buy a new PC to get a new OS. Still, that doesn't mean there isn't more work to be done to make things better.

---

