---
title: "Lucid Installer lingering long at 79%"
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by Randymanme on 2011-04-17
I'm presently reinstalling Lucid; I've backed up /home and want to begin again afresh.  I left while it had been installing for about a half hour and came back a half hour after that.  I expected the installer to be done and ready for reboot. 

But, no, it seems to be stuck at 79%.  It's not exactly "stuck" -- the installer switches messages, but it remains at 79%.  When I came back, it said "Scanning cd-rom;" and I wondered, "What for?"  From there it went to "Please wait."  Then "Retrieving file 1 of 4," "retrieving file 2 or 4," and so on.   The installer hung on Retrieving file 4 or 4" for 15 minutes and then went from there to "Retrieving  file 5 of 6."   And all at 79% (nor has the orange-red bar grown any).  After that, "Scanning mirror).  And following that (right now) "Retrieving file 1 of 10."

This is not a problem or complaint, I love Ubuntu and will wait all day if that's how long it'll take; I'm just curious.

---

### Post by Randymanme on 2011-04-17
It's about an hour since my last post.  The installer is still at 79% and is presently "Retrieving file 13 or 28."  What's wrong here?

There is a "skip" option.  If I elect to skip, will that leave a broken systems?

Any assistance here will be appreciated.

Thanks

---

### Post by TheExposedOne on 2011-04-17
is there an error with the cd?
it is also possible that there is an error with your hdd
you could quit the installer, go into windows and run chkdsk or better still run dos and do it, win 98 startup diskette

---

### Post by SecretCode on 2011-04-17
Could also be a slow network. During install, ubuntu fetches updates ... hundreds of megabytes since Lucid came out.

Afaik this is what Skip is there for, and all that happens is you'll have to manually update after the install is completed.

I reckon if it *offers* a Skip option, it's safe to take it!

---

### Post by TheExposedOne on 2011-04-17
yeh there's no harm in skipping

---

### Post by Randymanme on 2011-04-17
Thank you to all who responded.   After six hours and the skip button did not respond to a couple minutes of repeated clicking, I bailed out with a hard reboot.  After deleting the broken system (it wouldn't boot), I started over again.  More of the same.  So I used a 10.10 beta live cd to reinstall it.  So that's what I have now.

But this 10.10  noticeably not a vigorous as either 10.04 or 10.10 upgraded from 10.04.   In ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10687412, I posed the question about which is better 10.10 (10/10/2010) or 10.04.2 (2/18/2011). Yes, I can tell that there is a clear and distinct different.  This one is relatively slow and bloated.

I had previously installed 10.04 with the same dvd (I didn't have a blank cd but I did have a blank dvd, so I burned the live cd to dvd) that froze at 79% today.  And, for the record, it's a similar deal with Linux Mint 10 ME.  I'd burned a live cd of Julia RC, installed it, and then upgraded after the final release.  Later on when I was running out of space and reinstalled using the same RC live cd, I got a different os -- similar but greatly enhanced.

Since I was reinstalling anyway, this morning, I thought I'd upgrade to 10.10 and 11.04 first.  May as well take the scenic route.  For one, Gparted is seems to be supercharged in 10.04.2.  After I upgraded to 10.10 (also by the way) alt-F2 did not give me the 11.04 upgrade option.

I'm going to try upgrading this one to 11.04 now before I try to install 10.04.2 again.  Next to 10.04.2, 10.10 is (for me) unacceptable.

Cheers and thank you very much,

Randall

---

### Post by Randymanme on 2011-04-17
I just read [Installation & Upgrades]("http://ubuntuforums.org/forumdisplay.php?f=333")   	>**Re: 10.10 to 11.04 beta not upgrading and followed **[tordeu]("http://ubuntuforums.org/member.php?u=1256778")'s directions.  This 10.10 is upgrading now.

Thank you Tordeu.

---

### Post by Randymanme on 2011-04-19
Turns out the problem was not with Ubuntu but elsewhere on my end: bandwidth.  I share a 4-bedroom house with four other people and we all have computers -- some of use have two computers.  No televisions or radios or ipods, just computers.  We get all the medibuntu we want with our computers.  Sometimes, depending who all is doing what all, someone may not be able to get online even though the connection(s) and interfaces are up.

Although I'm kind of hazy on how all this computer stuff works, I think one viable  solution might be to just get my own, separate, internet service.  It looks to me like the "retrieving files" thing only happens when there's not enough bandwidth for the  installer (via apt) to get all the files without incident.  So it keeps trying.  

I happened to catch a break in the domination of the bandwidth (I don't know what the correct term is) and the 10.04.2 live cd installed in about 30 minutes, without incident.  But then the bandwidth domination began again and I couldn't update or install any packages that needed to be downloaded from a mirror for another 12 or 13 hours.  After googling, posting, and investigating; doing a process of elimination, and complaining to the main culprit, the person ceased and desisted and now things are back to normal.

Thank you very much for your assistance. 

Cheers, 

Randall;)

---

