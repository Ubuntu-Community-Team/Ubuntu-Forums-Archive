---
title: "jpilot-syncmal package missing from Ubuntu 7.10 ?"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by onno on 2007-10-25
The jpilot-syncmal package, which is present in the 7.04 repositories, now seems to be missing from 7.10. This makes it hard to sync palmtops with AvantGo through jpilot.

Does anybody know where to find the jpilot-syncmal package for 7.10?

Cheers,
Onno

---

### Post by padlan on 2007-10-26
> **onno said:**
> The jpilot-syncmal package, which is present in the 7.04 repositories, now seems to be missing from 7.10. This makes it hard to sync palmtops with AvantGo through jpilot.

Does anybody know where to find the jpilot-syncmal package for 7.10?

Cheers,
Onno

Man, that is one very good question: I too am frantically looking how to install the syncmal plugin on JPilot after upgrading from Dapper to Gutsy:confused:. I'm sure other jpilot users want it too.

---

### Post by padlan on 2007-10-27
This is all I can find on this so far:

[B][http://packages.ubuntu.com/dapper/otherosfs/jpilot-syncmal](http://packages.ubuntu.com/dapper/otherosfs/jpilot-syncmal)
[http://jasonday.home.att.net/code/syncmal/](http://jasonday.home.att.net/code/syncmal/)[/B]

The question is: if you attempt to install **syncmal** from the web, will you break your system?

I do hope syncmal will be made available in the Repos sometime soon.

---

### Post by onno on 2007-10-29
It appears that it was removed from Debian altogether: [https://answers.launchpad.net/ubuntu/+source/jpilot-syncmal/+question/15671]("https://answers.launchpad.net/ubuntu/+source/jpilot-syncmal/+question/15671") :-(

Anyway, I've installed the Ubuntu Feisty Fawn (7.04) jpilot-syncmal package, and it worked flawlessly. Don't know what it means for the stability of my Ubuntu 7.10 system though...

---

### Post by padlan on 2007-10-30
> **onno said:**
> It appears that it was removed from Debian altogether: [https://answers.launchpad.net/ubuntu/+source/jpilot-syncmal/+question/15671]("https://answers.launchpad.net/ubuntu/+source/jpilot-syncmal/+question/15671") :-(

Anyway, I've installed the Ubuntu Feisty Fawn (7.04) jpilot-syncmal package, and it worked flawlessly. Don't know what it means for the stability of my Ubuntu 7.10 system though...

Hmmm....I still don't get why they removed it. Anyway, thanks for posting this. I'd be curious to see whether your Gutsy remains stable after installing syncmal from Feisty.

---

### Post by padlan on 2007-10-30
HOW TO INSTALL SYNCMAL IN JPILOT ON GUTSY

I did a 'sudo nano /etc/apt/sources.list' to bring up the Gutsy Repos, then scrolled down to 
'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe', then typed 'feisty' in place of 'gutsy' to read: 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe'. Then I saved the new file, opened Synaptic Package Manager, did a 'Reload', then a 'Search&#8221; for syncmal, and installed it.
Then I opened up Jpilot and found Syncmal in the Plugins, synced my Palm Pilot and it worked perfectly.

---

### Post by padlan on 2007-10-30
> **padlan said:**
> HOW TO INSTALL SYNCMAL IN JPILOT ON GUTSY

I did a 'sudo nano /etc/apt/sources.list' to bring up the Gutsy Repos, then scrolled down to 
'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe', then typed 'feisty' in place of 'gutsy' to read: 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe'. Then I saved the new file, opened Synaptic Package Manager, did a 'Reload', then a 'Search&#8221; for syncmal, and installed it.
Then I opened up Jpilot and found Syncmal in the Plugins, synced my Palm Pilot and it worked perfectly.

[I]I must add two very important  things to my post above, namely, first, you need to copy the two appropriate Gutsy universe items, then paste them below (not eliminate the Gutsy ones); and two,  you need to "comment" (i.e. put # in front of the script)- or delete- the Feisty version of these two scripts from the source list or it may destabilize your Gutsy system. So here's what I did after all the above: 
[/I]
sudo nano /etc/apt/sources.list to get into the text editor. Then I found the two lines that mention feisty and I put a # at the begining of both lines. 
Then I hit control-x.  It will ask if you want to save.  Hit "y" and enter.
After that I opened Synaptic and did a Reload.

---

### Post by ederic on 2007-12-27
Syncmal is still not working with JPilot on my Gutsy system. :(

---

