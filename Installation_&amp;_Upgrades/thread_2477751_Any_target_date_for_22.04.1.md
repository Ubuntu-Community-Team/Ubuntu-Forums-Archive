---
title: "Any target date for 22.04.1?"
date: 2022-08-05
forum: Installation &amp; Upgrades
---

### Post by xeddog on 2022-08-05
Just curious.  I have 2 machines running 20.04 that I would like to upgrade to 22.04, but I prefer using the "standard" upgrade path instead of going rogue and doing it manually.  I have read that the ".1"  releases are usually about 3 months after initial release, and it has already been that long.

Thanks, 

Wayne

---

### Post by #&amp;thj^% on 2022-08-05
The first point release in the Ubuntu 22.04 LTS series will now arrive on August 11, a week later than originally planned
[https://www.omgubuntu.co.uk/2022/08/first-ubuntu-22-04-point-release-delayed-until-august-11](https://www.omgubuntu.co.uk/2022/08/first-ubuntu-22-04-point-release-delayed-until-august-11)
I'm still chuckling over this "No working Snaps after install — though some will be keen to describe that as a feature, not a flaw &#128540; "

---

### Post by Bashing-om on 2022-08-05
xeddog --
The skinny from the horse's mouth:
[https://lists.ubuntu.com/archives/ubuntu-devel/2022-August/042247.html](https://lists.ubuntu.com/archives/ubuntu-devel/2022-August/042247.html) <<- Ubuntu 22.04.1 delayed until August 11

-these things can happen-

---

### Post by guiverc on 2022-08-05
I'll give a little more

Ubuntu 22.04.1 is scheduled for 11 August 2022 as already stated.  That date refers to the ISO release date though; as existing users of Ubuntu 22.04 LTS are already running 22.04.1 having been doing so for about a week (ISO release is the last step).

However as you want to upgrade from 20.04 LTS, that occurs **after** the release of Ubuntu 22.04.1 LTS where the keyword is 'after'. 

Releases are always a Thursday (look at 4-Aug, or the delayed 11-Aug on a calendar), but the upgrade path from prior-LTS doesn't occur at that time; as that's the ISO release for new installs.

The Ubuntu Release Team usually have their first meeting & discussion about opening the '*upgrade taps*' early the subsequent week, and there tracking document is here

- [https://discourse.ubuntu.com/t/jammy-jellyfish-22-04-1-lts-point-release-status-tracking/29102](https://discourse.ubuntu.com/t/jammy-jellyfish-22-04-1-lts-point-release-status-tracking/29102)

Key items they'll look at is the "***Upgrade Blockers***" which are listed in that document, when they are resolved (*or mitigations are in place*), that's when the change to the metafile(s) are made & existing 20.04 installs are offered the upgrade, and that won't be till ***after*** the release of Ubuntu 22.04.1 LTS; at earliest the subsequent week, maybe even a week or two later.

The status page I gave allows you to monitor it, decide if your boxes will be hit by the *blocker bugs* & thus can risk *release-upgrade* now, or  if you prize stability, wait.

---

### Post by #&amp;thj^% on 2022-08-05
It's back in proposed:
```
apt search ubuntu-release-upgrader
Sorting... Done
Full Text Search... Done
ubuntu-release-upgrader-core/jammy-proposed,jammy-proposed,now 1:22.04.13 all [installed,automatic]
  manage release upgrades

ubuntu-release-upgrader-gtk/jammy-proposed,jammy-proposed,now 1:22.04.13 all [installed,automatic]
  manage release upgrades

```
I can certainly live with no snaps :D
```
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.1 LTS
Release:	22.04
Codename:	jammy

```
Bring on the breakage :P

---

### Post by mIk3_08 on 2022-08-06
> **xeddog said:**
> Just curious.  I have 2 machines running 20.04 that I would like to upgrade to 22.04, but I prefer using the "standard" upgrade path instead of going rogue and doing it manually.  I have read that the ".1"  releases are usually about 3 months after initial release, and it has already been that long. Thanks, 
Wayne
Your 20.04 is still supported until April 2025. That's not a bad thing. But if you are willing to upgrade to 22.04 well, Jammy Jellyfish is the latest release of Linux Ubuntu Operating System. Jammy Jellyfish has a lot of new features that the Focal Fossa don't have. So. Good Luck! Regards and cheers.

---

### Post by Dennis N on 2022-08-06
The upgrade from 20.04 to 22.04 has been offered for maybe a week. The attached notice is from Software Updater.

---

### Post by xeddog on 2022-08-06
Thanks for all the info.  I am in no hurry to upgrade to 22.04 since 20.04 has been rock solid for me, but keeping up-to-date with some of the latest features can't be a bad thing (he says with fingers crossed :P).  Except maybe snaps.  I don't like snaps.  I could change my mind about them if two Windows applications,  Autodesk Fusion 360, and gdmss (a surveillance system monitor), ran as a snap.  Until that happens, I guess I am forced to be dragged along behind the Gates pickup truck, and buy new hardware and eat bugs.  (CENSORED)!


Wayne

---

### Post by poorguy on 2022-08-06
> **1fallen said:**
> 
I can certainly live with no snaps :D

Bring on the breakage :P


I can live without Snaps also however have Ubuntu 22.04 / 22.04.1 installed and haven't had a problem with Snaps.

Yes the first startup of Firefox Snap after a system cold power up or system restart was slower than usual however after that first time Firefox opens as usual and now appears to be fixed with the release of 22.04.1.

The more I learn about Snaps the more I like them.

---

### Post by TheFu on 2022-08-06
I read something yesterday that 22.04.1 was being delayed because some 3rd party snaps weren't starting.  [https://www.phoronix.com/news/Ubuntu-22.04.1-LTS-Delayed](https://www.phoronix.com/news/Ubuntu-22.04.1-LTS-Delayed) They didn't say it, but implied that the Firefox snap was an issue.

---

### Post by bingodingo on 2022-08-06
Looks like .2 is the new .1. 
Hours before the scheduled release a major issue is discovered - that the broken feature is unpopular isn't really here or there.
Previously I've jumped on the first stable releases without major problems; don't do that this time!
Unless you've got issues with the current install or you like using your computers for beta testing, wait for the next point release.

---

### Post by poorguy on 2022-08-06
My 22.04.1 installed through the update manager as an update so I don't know.
Firefox Snap opens a lot faster then before in 22.04 from a cold power up or restart.

```


ubuntu@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:    22.04
Codename:    jammy
ubuntu@ubuntu:~$ 


```

---

### Post by mIk3_08 on 2022-08-07
> **1fallen said:**
> I can certainly live with no snaps :D So, you mean you are not using canonical livepatch client. They are from snaps. What do you think of this livepatch, is this helpful or not, What you think? Regards and cheers.

---

### Post by TheFu on 2022-08-07
Livepatch is scary.  It isn't used enough to be trusted.  It has been around as a paid option in Linux since the 1990s, but there are trade-offs in the required hardware.  We don't get something for nothing. Life doesn't work that way.

Automatic patching is something similar, except it gets used all the time and every few years, something terrible happens, making a system that cannot be booted.  Whether the root cause is the timing of the patching or something the local admin caused is hard to say, but an unbootable system is always bad in my book.  I takes very little effort to manually patch, once a week.  I suppose, doing security only patching once a week for non-technical users would be better than no patching.

---

### Post by mIk3_08 on 2022-08-08
> **TheFu said:**
> Livepatch is scary.  It isn't used enough to be       trusted.  It has been around as a paid option in Linux since the   1990s,     but there are trade-offs in the required hardware.  We don't   get     something for nothing. Life doesn't work that way.
Automatic patching is something similar, except it gets used all the       time and every few years, something terrible happens, making a system       that cannot be booted.  Whether the root cause is the timing of the       patching or something the local admin caused is hard to say, but  an      unbootable system is always bad in my book.  I takes very little   effort     to manually patch, once a week.  I suppose, doing security   only    patching  once a week for non-technical users would be better   than no     patching.
Why you say its scary? I have been using for quite  sometime now. So far      I haven't encountered any scary thing you said with  the use of  this     Livepatch. And also Ubuntu has a free version of  Livepatch for    personal   use and even on the esm (extended security  maintenance).  But   you just   have to limit the use of it.
> **TheFu said:**
> Whether the root cause is the timing of the       patching or something the local admin caused is hard to say, but an       unbootable system is always bad in my book.  I takes very little effort       to manually patch, once a week.  I suppose, doing security only      patching  once a week for non-technical users would be better than no       patching.
I have to test this Livepatch first here in my  system. Maybe I can't      agree with you now because I haven't encountered  any scary things yet      on my system. Maybe I will agree with you with this  manual  patching  so    we can be able to scan and know what exactly the  source  code they   use  that will be patch in our system. This is a good idea   anyway.   Thanks anyway for the idea. Though  the Livepatch explains  the current  applied patch but we  don't  know yet  the  source code  that they use to  patch our system. Hope they  will not do same as MS  Windows freaking  updates. Creating some  unbelievable updates that will  cause to break  your system. Hope NO NO. Yes, I experience this. It  almost break my video card after the MS Windows latest updates was  successful. Its always gives me a headaches. Anyway, I am not using MS Windows now. Glad to have this  Linux Ubuntu now. Regards and  cheers.

---

### Post by TheFu on 2022-08-08
> **mIk3_08 said:**
> Why you say its scary? 

Because I know, technically, how it is performed.  Please explain it for others with technical accuracy.  An understanding of function pointers will be necessary.

---

### Post by #&amp;thj^% on 2022-08-08
> **TheFu said:**
> Because I know, technically, how it is performed.  Please explain it for others with technical accuracy.  An understanding of function pointers will be necessary.
Thanks for your bravery here, and I 100% agree with you.

I've tested and used this since conception, "and my view only"
Absolutely NEVER install Canonical Livepatch unless you buy the **Pro** version. The free version puts you at risk by installing untested patches, YOU ARE THE GUINEA PIG!!! Just run the "canonical-livepatch status" command and you'll see you are a beta tester without any way to opt out.

The "Livepatch" is basically a .ko that acts like most Kernel rootkits by changing stuff in memory while it is running. So ask "yourself", are you sure you would place your trust this??
> 

    Q: Isn't livepatching just a big ole rootkit?

    A: Canonical Livepatches inject kernel modules to replace sections of binary code in the running kernel. This requires the CAP_SYS_MODULE capability. This is required to modprobe any module into the Linux kernel. If you already have that capability (root does, by default, on Ubuntu), then you already have the ability to arbitrarily modify the kernel, with or without Canonical Livepatches.

Source: [https://blog.dustinkirkland.com/2016/10/canonical-livepatch.html](https://blog.dustinkirkland.com/2016/10/canonical-livepatch.html)
Simple solution, just run update and upgrade, your life is now less complicated. ;)

---

### Post by mIk3_08 on 2022-08-09
> **TheFu said:**
> Because I know, technically, how it is performed.   Please explain it for others with technical accuracy.  An understanding  of function pointers will be necessary. Well, I'm not well  versed or expert to this kind of field this is out of my scope all I  know this time is that it doesn't make me inconvenient this time and I  haven't experience any uncomfortable using my Linux Ubuntu Operating System machine. But if you  can explain to me and give me some details or links of it for me to  scan maybe I will believe in you.

> **1fallen said:**
> The "Livepatch" is basically a .ko that acts like most Kernel rootkits  by changing stuff in memory while it is running. So ask "yourself", are  you sure you would place your trust this?? Simple solution, just run update and upgrade, your life is now less complicated. :wink:  I don't think this is very good idea to me. Even if you are very  well  versed in some area because I know you are not expert of all. Are you,  and I already knew the status in my livepatch. I already knew where I  stand for. As long as my system is running well and I can use it anytime  without any hesitation I'm already contented with it. You just don't  know how my Linux Ubuntu Operating System Machine runs well. Why should I  go to upgrade when all I need is already intact. Making silly decisions  makes you dumb. If you can prove to me that my Linux Ubuntu Operating  System Machine will never last long because of livepatch. Then I will  believe in you! Prove it then! I challenge you.

---

### Post by TheFu on 2022-08-09
> **mIk3_08 said:**
>  But if you  can explain to me and give me some details or links of it for me to  scan maybe I will believe in you. 

You shouldn't just trust people when they make big claims.  OTOH, if you don't understand what a function pointer is, it isn't something I'm interested in teaching, especially since hundreds (perhaps many thousands) are involved when livepatch is used.

So, on Saturday morning I patched all my systems. Some need to be rebooted, but I haven't taken the time to reboot them all. It isn't convenient and might not be convenient until the weekend.  For most things that run 24/7/365, that doesn't matter. Most non-core libraries or programs aren't run all the time, so the patches just don't matter, since the new code will be used when it gets run the next time.  I have noticed some video stuttering on 1 system since the patch. I suspect there was a new GPU driver and perhaps a few other based drivers.  The video issues aren't really that important to me. If they were, I'd have already rebooted.

None of this is sufficient for any need to use beta livepatching.  There are so many safer solutions which have been known and used for HA needs in businesses for decades now.  Nobody really cares about long uptimes anymore. We need predictable uptimes - and predictable times for maintenance.  Being predictable is the main aspect here.  I have 4 hours/week of scheduled downtime for my systems, though most weeks it is zero or under 5 minutes.  If I'm already having 2.5 minutes of downtime and the users know that there are 4 hrs scheduled (sometimes something bad happens), I'm vastly exceeding their expectations and building good will.  For things that can never go down, using livepatch is NOT sufficient. There are redundant connection, data replication, redundant power from multiple substations and needs to have systems at least 500 miles apart so natural disasters don't cause downtime in each location concurrently.  This is all very well understood.  All that live patch does is provide a false sense of uptime that proper systems engineering is needed to provide.

But I doubt I can convince anyone of anything, especially if marketing material is what they use to decide, not technical information.  Thank you for testing new features.  I'm sure Canonical appreciates it.

---

### Post by bingodingo on 2022-08-09
Hi mIk3_08, just checking the basics here (no offence intended) you are aware that the only reason for running Livepatch is if you want to be able to avoid a possible need to reboot after updating your os (for high and critical severity kernel           vulnerabilities) because e.g. the system is a server with users who don't want access disrupted? 

You do realise that if you're running a regular desktop system without a need for 24/7 operation (so you're comfortable rebooting or especially if you usually shut down once a day anyway) there is essentially no advantage to Livepatch (only the potential downside that TheFu alludes to)?

Sorry to xeddog for the ongoing hijaking of this thread.

---

