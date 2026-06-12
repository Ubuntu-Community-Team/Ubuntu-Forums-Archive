---
title: "Dist-Upgrade to 13.04 complete failure"
date: 2013-10-18
forum: Installation &amp; Upgrades
---

### Post by linuxguru43 on 2013-10-18
I'm still here with my windows laptop looking at my broken 13.04 rocket to 13.10 system upgrade. She is frozen. She isn't going anywhere. 

Why don't you warn people to backup their data before recommending a system upgrade? 

Why don't you tell users that there is a slight, however rare, chance that you will bork your system upgrade to the next release?

I use this computer as my production system. I do all my work on this for a living. I'm stuck in the mud. 

I'm going to do a reinstall and wipe the entire parition. I'm going to try to move my work off, and thunderbird mail (somehow?)
into another partition. 

Here is my advice.. Instead of a new release every 9 months. Just focus on the next LTS. 

I'm in the process of rolling back to 12.04 and I am going to stay there indefinitely now until you decide to fix whatever is wrong
with the latest PUSH of ubuntu.

Ubuntu 13.10 upgrades... headache city!

thx):P

---

### Post by craig10x on 2013-10-18
I suspect you didn't do the upgrade using the iso installer...I did TWO UPGRADES that way...both to go from 13.04 to 13.10 while in development and then again today to upgrade again on my 13.10 (to kind of clear out the excess stuff accumulated during all the zillions of updates during development) and they went stellar both times....it is the BEST way to upgrade...
[http://ubuntuforums.org/showthread.php?t=2181643](http://ubuntuforums.org/showthread.php?t=2181643)

---

### Post by linuxguru43 on 2013-10-18
I did it the way the Ubuntu web site sugggested. Maybe you should let people know the risks.

[http://www.ubuntu.com/download/desktop/upgrade](http://www.ubuntu.com/download/desktop/upgrade)

"we recommend you backup your system" should read:

"if you have a working system this release-upgrade may force you to do a bare-metal restoration, so proceed with extreme caution on full-time production systems, and use only if at EOL or if truly necessary..."

It is going to take me several hours now to get this back in business. 

Thank you.

---

### Post by ian-weisser on 2013-10-18
"We recommend you backup your system" seems appropriate advice and wording. 
Ubuntu 13.04 even came with an easy-backup application.
Ubuntu developers repeatedly called for volunteer upgrade testers to catch problems like yours.

I'm sympathetic to your plight - I've lost (backed-up) production systems in the past to various causes.
But I do not see how scarier wording would make a significant difference. Regular backups,, if not automated, are a learned behavior, and scaring millions of users who will have no problem anyway seems counterproductive.

In the event of upgrade failure, you can reinstall from an .iso and it will *try* to preserve your /home data. Like craig10x, I have had success with that on the few occasions I have needed to reinstall.

Your original complaint seems directed to the Ubuntu developers more than the community in general. You are aware that few developers hang out in this forum?

---

### Post by cariboo on 2013-10-18
Moved to Installations & Upgrades, as this has nothing to do with either Saucy or Trusty.

---

### Post by linuxguru43 on 2013-10-19
'Probably only moved it because they didn't want to scare new users. Release-upgrades are dangerous - IMHO. You really should tell people more than - "well, maybe something (oh I don't know) might happen so do MAY want to do a backup"...  It is everytime I do a release-upgrade. I don't have time for this anymore. Closing thread.

---

### Post by craig10x on 2013-10-19
I can't speak for doing software updater method of doing an upgrade (which you used) but all i can tell you is i have done the upgrade option of the live session iso installer TWICE and had the identical great results both times (as i outlined in my thread about it)...and a friend of mine did the same and had the same type of results...so again i say, that method IS very dependable and reliable as far as i can judge from experience...I'm typing this from my newly upgraded 13.10 which i did yesterday...it is ROCK SOLID...

And, as was pointed out...you rant here won't help because developers don't cruise the ubuntu forums...this is just the community here you are addressing...
Good luck to you...

---

