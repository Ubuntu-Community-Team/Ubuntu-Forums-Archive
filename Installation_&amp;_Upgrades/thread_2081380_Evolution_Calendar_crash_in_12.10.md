---
title: "Evolution Calendar crash in 12.10"
date: 2012-11-06
forum: Installation &amp; Upgrades
---

### Post by unibroker on 2012-11-06
On initial boot I get an error message that the OS has crashed due to Evolution-Calendar having maxed out the CPU (99%).  I don't use it so can I just do a complete removal?  I don't use Thunderbird either if they are related.

---

### Post by Frogs Hair on 2012-11-06
Evolution Calendar shouldn't be installed by default, but I do see an evolution data server package in synaptic which appears to be a dependency.

---

### Post by unibroker on 2012-11-06
> **Frogs Hair said:**
> Evolution Calendar shouldn't be installed by default, but I do see an evolution data server package in synaptic which appears to be a dependency.

I did a clean install of 12.10 last night and didn't directly install it so I don't know how it got on my system.  At any rate I found instructions for removing it but was advised to keep 2 specific evolution files having to do with data server.  I no longer have the date and time in my title bar but I'll take that for an uneventful logon.

---

### Post by Toomuch_ on 2012-11-06
I seem to have a similar issue with Evolution-Calendar... I had it using 99.9% of CPU usage (according to "Top" in the terminal) at ALL times until I decided to remove anything related to evolution, I have no clock on my OS Status bar ever since...

 My hardware is a Thinkpad T500 (Core2 Duo T9400, 2 gigs of ram and radeon HD3650 with open source drivers)

This was a clean install and it seems that the bug only appears on the 64bit version of Ubuntu, as I had tried the 32bit version and did not have this issue.

---

### Post by samjury on 2012-11-06
I get constant 'Sorry Ubuntu has experiencd an internal error' messages. Core i5 ASUS u63jc with 12.10 64bit (8GB RAM).

The culprit appears to be '/usr/lib/evolution-calendar-factory' of package evolution-data-server 3.6.0-ubuntu3 Title: Evolution0calendar-factory crashed with SIGABRT

---

### Post by unibroker on 2012-11-07
No issues on boot up this morning.  Even the mouse didn't freeze which I normally have had to do a hard reset at least once start up.  One other thing, which is a new issue since I erased Evolution, is my screen times out even with the setting on Never.  But again this along with the missing clock and date from the title line are minor compared with what I had going on before.

---

### Post by Toomuch_ on 2012-11-07
My system is finally working properly. Was as easy to fix as uninstalling the "Evolution" packages using synaptic, rebooting and reinstalling afterwards. 

They now work fine and the crash/high CPU usage issue is gone.

Also make sure to verify that the package *indicator-datetime* is reinstalled or your date/time on the title bar will not reappear. If it is missing after uninstalling and reinstalling Evolution packages, simply use this command *sudo apt-get install indicator-datetime*

---

### Post by unibroker on 2012-11-07
> **Toomuch_ said:**
> My system is finally working properly. Was as easy to fix as uninstalling the "Evolution" packages using synaptic, rebooting and reinstalling afterwards. 

They now work fine and the crash/high CPU usage issue is gone.

Also make sure to verify that the package *indicator-datetime* is reinstalled or your date/time on the title bar will not reappear. If it is missing after uninstalling and reinstalling Evolution packages, simply use this command *sudo apt-get install indicator-datetime*

Now this thread is really "Solved"!  I just figured I would have to do without the clock in the title bar.

It makes no sense to me that uninstalling and reinstalling Evolution would do the trick.  It's also interesting that after reinstalling Evolution I was missing the indicator-dateline which was the whole reason I was even going to reinstall.  Care to share your logic?  BTW, you should post this solution to Launchpad.

---

### Post by Toomuch_ on 2012-11-07
> **unibroker said:**
> Now this thread is really "Solved"!  I just figured I would have to do without the clock in the title bar.

It makes no sense to me that uninstalling and reinstalling Evolution would do the trick.  It's also interesting that after reinstalling Evolution I was missing the indicator-dateline which was the whole reason I was even going to reinstall.  Care to share your logic?  BTW, you should post this solution to Launchpad.
The only logical explanation I would have for this particular case is that the packages were probably "broken" during the initial Ubuntu install, maybe corrupted files on the ISO, can't say for sure. 

I'm also not convinced that this is considered an actual "fix" as it is a way around an existing problem. I will wait before posting to Launchpad, or if I do, I will tag it as a temporary "Band-Aid" solution to a problem during initial installation.

Glad it helped you!

---

### Post by VideoRoy on 2012-11-07
I am having the same problem and was about to uninstall / reinstall but once I saw all the dependent packages that were going to be removed I stopped.

I am using the gnome-fallback and a bunch of packages would cripple the system if I remove them.

I had to go to the fallback to begin with due to so many issues with 12.10 on my netbook.

I guess I need to wait a little longer for a fix.

Thanks for the info here though.

---

### Post by VideoRoy on 2012-11-08
Instead of the uninstall, I did just a reinstall through Synaptic and so far so good!  I also had to reinstall the Nautilus package since it was crashing as well.

Very strange because I a reinstall instead of an upgrade to 12.10 but I have a separate /home that I kept in tact.  I am thinking there might have been something left over.

Any way thanks for the idea.  Hopefully this is solved now.

---

### Post by unibroker on 2012-11-09
This morning I was greeted by the same error message on reboot but without the symptoms of a crash.  Might have been a different story had I booted from an off position as I shutdown at the end of every day.  I'm going to compile a kernel from source within the next couple of days to see if that stabilizes my system.

---

### Post by syscrusher on 2012-11-27
I encountered the same popup this morning, during login to an xfce4 session. My system was stable when I logged out of xfce4 yesterday, so I really doubt that the app was corrupted in the installation media, as someone else suggested (maybe on another thread -- there are several on this topic).

Like a previous poster, I was dissuaded from uninstalling "evolution" (even though I use Thunderbird instead) by its dependencies, to wit:

# dpkg --dry-run --purge  evolution evolution-ews  evolution-plugins
dpkg: dependency problems prevent removal of evolution:
 gnome depends on evolution (>= 3.0).

I don't normally login to GNOME, preferring xfce4 (and grateful that in Linux we can have multiple choices!). That being said, I want to keep GNOME on my system for occasional use.

I'm going to try letting Synaptic reinstall the Evolution packages and see if that helps. I'll post the results here.

---

### Post by syscrusher on 2012-11-27
Update: Reinstallation didn't help. It's a segfault of evolution-calendar-factory. I let the system send a crash dump to the developers and will just live with it for now.

---

### Post by VideoRoy on 2012-12-06
I am still having the issue as well.  It crashes every time boot up as soon as I been to do anything.  I have reported multiple times and when I search I have multiple nested launchpad reports but all seem to be dead ends.

I have loaded Ubuntu Gnome Remix 12.10 on another systems and loaded the gnome3 PPAs.  That system never seems to have the issue.  I am considering just loading the gnome3 PPAs on my main system to see if the updated gnome packages help.

Kind of out of ideas here and not sure which launchpad is thread is working on this exactly.

---

### Post by PJSingh5000 on 2012-12-15
I am experiencing this issue in a fresh install of 12.10 x64.

What was your bug report # so I can subscribe to it?

---

### Post by VideoRoy on 2012-12-22
I think this is the bug fix release for the many problems

[Evolution Data Server Crash]("https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/1062068")

But as usual I have a very hard time following the progress in Launchpad.  It is never clear when a patch will be released or really the status unless some nice person describes it in one of the replies.  Clicking on all the links about the patch usually end up in a dead end with no dates.  This has happened on every patch I have ever needed.

Ok, enough on the rant of how hard it is to find information.  It looks like this will be fixed in version 3.6.2 and above of Evolution-data-server package.  Committed for Ubuntu 13.04 unclear when / if it will make 12.10.

---

### Post by VideoRoy on 2012-12-22
Here is a link to the binary package .deb file but there are way too many dependencies to try to fix this manually by removing and installing individual .deb files.

[Evo Data Server 3.6.2]("https://launchpad.net/ubuntu/raring/i386/evolution-data-server/3.6.2-0ubuntu1")

I guess I will wait for an official update or maybe go load the Gnome 3 PPAs to see if they have picked this one up.  That would be going off track with official Ubuntu which I have been avoiding on my main computers and brings many more of the 3.6.x packages that Ubuntu has purposely not updated for good reasons.

---

