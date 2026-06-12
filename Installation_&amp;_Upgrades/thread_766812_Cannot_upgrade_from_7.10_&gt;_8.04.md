---
title: "Cannot upgrade from 7.10 &gt; 8.04"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by ericus on 2008-04-25
I'm having trouble with the update to Hardy Heron. The GUI update-manager freezes, so I tried the alternative CD upgrade. Here's what the log file says:

[http://pastebin.org/31933](http://pastebin.org/31933)

Any ideas?

---

### Post by zvacet on 2008-04-25
Did you checked [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM")? If you didn´´t do it now.If itis correct check cd integrity (you will see that option when you boot CD.If you fin anythin wrong download same iso with torrent and point download to the folder with sxisting iso.Torrent will just check your iso and replace coruppted files with good ones.Check md5sum again,burn at lower possible speed and check disc integrity again.IOf everything is O.K. you should be able to upgrade.Of course your system have to be up-to-date.

---

### Post by Psychoscorpic on 2008-06-12
I am battling too.
Using Alternative CD, since broadband is out of my budget in S.A. at the moment.
Problem is, I'm running the Ultimate Edition of 7.10, and the Upgrade Manager chokes, saying that it cannot resolve problems due to unofficial programs that are installed.

Tried doing it semi-manually via Update Manager (uses Synaptic pointed to the CD) but that chokes on the Human Theme - conflict trying to overwrite existing Human Theme components!

Surely anything currently running should either be turned off by the Manager, or set aside for activation during re-boot?

Please help.

---

### Post by avtolle on 2008-06-12
[http://ultimateedition.info/Ultimate_Edition_1.8/](http://ultimateedition.info/Ultimate_Edition_1.8/) Take a look at that. If you are trying to upgrade to the newest "ultimate", I'd suggest (sorry) that you download the iso for the DVD for 1.8 Ultimate, and do a fresh install from it. Scanning the information there, it looks like this is the best way to go.

---

### Post by Psychoscorpic on 2008-06-14
> **avtolle said:**
> [http://ultimateedition.info/Ultimate_Edition_1.8/](http://ultimateedition.info/Ultimate_Edition_1.8/) Take a look at that. If you are trying to upgrade to the newest "ultimate", I'd suggest (sorry) that you download the iso for the DVD for 1.8 Ultimate, and do a fresh install from it. Scanning the information there, it looks like this is the best way to go.

Thanks, Avtolle.
Much as that hurts - seems to be the general advice everywhere I've looked.
As for getting things back to how they are now after the fresh install, what needs to be backed up besides the home folder?

---

### Post by hoboken on 2008-06-14
When I had 7.10, 8.04 wouldn't even come up in the update manager, so I ignored it and waited. One day... bling! There it was. Now here I am trying to iron out all the bugs in hardy...

---

### Post by avtolle on 2008-06-14
I'm thinking that given the difference between Ultimate 1.8 and earlier releases, I'd only back up the home folder. By "getting things back to how they are now" are you referring to your personal settings, etc., which is what I presumed. There have been substantive changes in many of the applications from 7.1 to 8.04, which causes (as I understand it) some difficulties in just reinstalling the applications from the prior install from a back up drive. I'm keenly aware of the difference, e.g., with Samba from 7.10 to 8.04 as an example. Also, 8.04 (upon which Ultimate 1.8 is based) uses Pulse Audio for its sound handling, rather than Alsa. Given my lack of familiarity with Ultimate, I'll be quiet now, as I may well say something wrong if I go further. 

I will tell you that after an installation of 8.04, there were and continue to be from time to time a large number of updates, and presume at least some of this will also apply to Ultimate. Just FYI.

---

