---
title: "[SOLVED] This is very depressing."
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by bilijoe on 2008-04-28
I just did a quick survey of recently reported bugs in the new release of Ubuntu (8.04), and found that over 300 new bug reports have been filed in the last 24 hours.  It's late now, and I'm completely burned out on all things computer.  I feel like I'm back in the Windows world, and I really can't let word of this leak out to my Windows-using friends.  I have a headache.  I'm going to sleep.  And, tomorrow, I'm rolling my system back to 7.10, before any Windows people stop by and see the mess I'm in.:(

---

### Post by Ub1476 on 2008-04-28
Did you check out the priority of the bugs though (many might be duplicates too).

Does it affect you anyway?

Remember that Linux is open, so every bug is known, this is not the case with Windows;)

---

### Post by FredB on 2008-04-28
And how many bugs will be closed because there related to "dirty" upgrade or bad actions ?

---

### Post by bilijoe on 2008-04-28
To Ub1476, I did look over many of the reports, and after my recent upgrade to 8.04, yes, some of them do affect me.  I now have a plethora of problems, after a seemingly flawless upgrade, and am seriously considering rolling back to 7.10, if only to give myself a clean platform to try from again.  I downloaded the 64-bit version ISO file, so I could install it on my laptop (and finally be rid of Windows all together).  The first download appeared to go without a hitch, but the MD5 didn't check out, and the disk integrity check reported one bad file.  The second attempt, everything went fine, and I appear to have gotten a clean install (this one was not an upgrade, but a new install).  I'm thinking, perhaps some part of the upgrade glitched, as it downloaded, resulting in a really messed up system (can't "sudo", Firestarter won't start, something else fails to start too, but the message goes by so fast during boot that I can't read it, can't access several things from the menus, etc.).  I'm thinking the "safe" way to do an upgrade might be to download the ISO, check the MD5, make the disk, let the disk check itself, and upgrade from the disk.  I don't know if this would result in as thorough an upgrade though.  When the 64-bit version finished installing, it posted a notice saying that, due to space considerations, certain things had to be left out (but could, of course, be added via add/remove and/or synaptic).  Anyway several of those bug reports do relate to problems I am having--several were reported by me, and yes, I do realize that [most] all of Linux's bugs are public, and so it looks like a lot, whereas Microsoft won't admit to having bugs.  My guess is that they don't even maintain a centralized bug database--unless they use FoxPro--too many records for their own database tools to handle!:lolflag:
FredB, I'm sure you're right--many will be closed due to such things, but in the most recent 24 hour period, there have been just over 400 more new bugs reported.  These are not all going to turn out to be non-issues (unless the upgrade engine has a problem:confused:).  It just doesn't seem like a good omen to me, that such a large number of bugs have been reported so soon after a major upgrade.  My system is such a mess, I'm going to have to re-install, from backup, my 7.10 version.  My upgrade appeared to go entirely smoothly, but I now have so many bits and pieces that don't work, that the system is simply unusable (well, by Linux standards anyway.  I know Windows users who, seemingly willingly, put up with this much crap every day--but that's why I switched).  Please don't get me wrong, I'm still a die-hard Ubuntu fan, and will continue trying to convert the entire home computer community to Ubuntu (it is my favorite of all the flavors out there), but I think I'll quit preaching conversion to my Windows-using friends, until this flurry of bug reports settles down.  Their main objection to Linux is that they "have heard it's buggy", and the last thing I want is for them to find out that they [appear to be] right.  We all know it's not, and every new product requires a shake-down cruise and a "running in" period.  I'm just a little disappointed that this release appears to have so many problems.  (Note, I did say "appears to".  I hope you are right, and that a lot--even most--of them boil down to duplicates, installation errors, and a minimal amount of "real" bugs.:D

---

### Post by sgt_debian on 2008-04-28
I don't disagree. Without a 2nd PC already connected to the Net, a lot of users would have no choice but to abandon their Ubuntu installations due lack of drivers or being unable to access to forums/tips/help etc.

---

### Post by FredB on 2008-04-29
And so ? How many people have junky hardware ? Overclocked computers ?

400 bug reports ? I wonder how many will be duplicate of each others. I guess that at least 25% could be duplicate either of known or new bugs.

Clean install are about 50% of the time the answer to buggy installs. Not reading the documentation ? 10 to 20%.

Using old habits no longer useful ? How many % ?

I DON'T SAY that Hardy is perfect. I just say that many people will have problems which are not related to ubuntu software.

Am I a bad person to say this ? I can only speak by my own experience with hardy.

---

### Post by mrbigg75 on 2008-04-29
Well said Fred B.  I believe that most of the newbies, myself included are still using windows principles with the linux os.. It is time for people to do their research, gain the knowledge required, and get out of the Master Microsoft frame of thinking. Linux requires WORK, THOUGHT, KNOWLEDGE, and getting a little dirty at times. 

Use the tools available and things should go well. This forum has done soo much to help me to understand Ubuntu. I think this will work itself out. Good luck to all.

---

### Post by gtdaqua on 2008-04-29
New users should simply wait and get Gutsy. Even when a new version is out, tested and all, you should wait for sometime to see what happens to it. Simply upgrading becausing you hoped it to be shiny, glossy and faster is not the right thing to do. 

One dirty thing about Hardy servers is eventhough faster, Virtualization using VMware is in trouble. You have to change the library paths and apply a certain patch to have your environment alive. This is a shock because, Hardy is an LTS release and it wont 'simply' run the VMWare machines. Tricky tweaks are required. Now, Canonical and VMWare will not rush to our help...it will take sometime for a permanent solution now that we already have workarounds in place. 

Hopefully, VMWare does something about this.

---

### Post by FredB on 2008-04-29
> **gtdaqua said:**
> New users should simply wait and get Gutsy. Even when a new version is out, tested and all, you should wait for sometime to see what happens to it. Simply upgrading becausing you hoped it to be shiny, glossy and faster is not the right thing to do.

Ok, but a lot of people have installed / upgraded to Hardy and have no problems. Being conservative could be a good idea, but too conservative ?!

> One dirty thing about Hardy servers is eventhough faster, Virtualization using VMware is in trouble. You have to change the library paths and apply a certain patch to have your environment alive. This is a shock because, Hardy is an LTS release and it wont 'simply' run the VMWare machines. Tricky tweaks are required. Now, Canonical and VMWare will not rush to our help...it will take sometime for a permanent solution now that we already have workarounds in place. 

Canonical don't have to fix vmware issues. By the way, KVM is a free software virtualization tool which works great. But if you need something that is not available in KVM...

> Hopefully, VMWare does something about this.

of course ! They have to update their code for new linux kernel. Anyway, I remember that any time the kernel is changed, you have to use patches like any-any one to get vmware working again.

---

