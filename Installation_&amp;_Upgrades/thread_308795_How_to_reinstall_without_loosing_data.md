---
title: "How to reinstall without loosing data?"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by shpook on 2006-11-28
Hi

For a number of reasons I need to be able to reinstall  my Ubuntu, however I have alot of data that I wish to keep intact on the same partition. Most of the stuff is currently in /home/ but I can freely move it elsewhere on the partition.

My question is: How can I reinstall Ubuntu without loosing the files?

I would appreciate any help. Thanks.

---

### Post by atoponce on 2006-11-28
Well, as I am sure you are aware, you need to backup your data.  I would recommend everything in /home as well as config files in /etc.  If you have a separate partition, then move everything there.  Otherwise, back it up on an external medium like a USB drive or CDR.


Then reinstall.  Unfortunately, I know no way to keep your data on the partition that you are reinstalling.  It will be wiped clean.  One reinstalled, however, reinstate your data to the new install.

That's the only way I know to do it.

---

### Post by bulldog on 2006-11-28
If you didn't make a separate /home,you have to copy your data to another partition.
Reinstall Ubuntu and copy it back.

You can consider to make a separate /home partition,now you gonna reinstall anyway.

---

### Post by shpook on 2006-11-28
Thanks for replying guys!

I was hoping there's a way to reinstall without having a separate /home or resolving to backups. Perhaps something like creating /mystuff and deleting everything else followed by a fresh install on the same partition without formatting, but was not brave enough to try it without asking first.

---

### Post by matt_risi on 2006-12-13
Not a far fetched request either, Apple can do it.

---

### Post by TimelessRogue on 2006-12-13
Hmmmm ... I've reinstalled upgraded to Dapper and reinstalled twice without losing any data.  Perhaps it was 'cuz when it came time for formatting I chose only the swap partition to reformat and left the others 'as is'.  This was on both my HP laptop and custom-built base-station (with a six drive RAID array) dual booting with Winlose 2k Pro.

BTW, I'm now in the process of upgrading to Edgy ... will post how this all goes ... particularly if there are any problems, insurmountable or otherwise ...

---

### Post by MJN on 2006-12-13
If your data is important enough to you that you don't want to lose it during a reinstall then you ought to take that as a sign that you ought to start thinking about backing it up anyway! Don't wait until you've lost everything to then realise how important backups are. Once you've done the backup, reinstallation will then be a doddle.
 
If you think that sounds like the voice of experience you'd be right - although in my case I thankfully *did* have a full backup of my mail, websites, photos and documents etc along with the same for various members of my family and friends too - thankfully the out-of-the-blue hard disk head crash failed to cause the heartache that it otherwise could have easily done.
 
(As others have said, also use this opportunity to create a seperate partition for /home as if nothing else it makes reinstalls a darn sight easier)
 
Mathew

---

### Post by TimelessRogue on 2006-12-14
Well okay then ... this has to be one of the easiest upgrades I've ever had fun with ... aside from that unpleasant experience a few days ago, that is ... and with no loss of data!

I'm now working with Edgy on my HP Pavilion n5000 laptop after upgrading from the Dapper last evening.  I had previously tried the recommended methods of 'sudo update-manager -c' and 'sudo sh /cdrom/cdromupgrade' from a 'terminal' with a downloaded/burned copy of the 'alternate' i386 iso with results that, while not exactly disastrous 'cuz I didn't lose any data, were somewhat way the other side of satisfactory in that I ended up reinstalling the Dapper both times.  Not a big deal really, just a little aggravating ...

This time, while in the graphical mode of the Dapper and being in something of a curious mood, I loaded the Edgy 'alternate' cd, opened the folder and double-clicked on the 'cdromupgrade' file.  Lo and behold!  It opened on screen and allowed me to do the complete upgrade from Dapper to Edgy on screen and in graphic mode.  Edgy accomplished the entire upgrade, including downloading newer versions of some files over my DSL internet connection. in a matter of just a few hours ... basicly unattended once it got started.  I then used Synaptic to check for updates and that was it.

All is well and everything is functioning ... except for my Linksys wireless, that is.  And because there was no reformatting involved, there was no loss of data ... including my various custom settings (such as fonts, network settings, etc) as well as my Firefox bookmarks!

I ask you:  How much easier could it be?  And yet no one has mentioned managing the update in this manner.  Am I the first?

Anyway ... there you have it:  the story of my 'Edgy Upgrade' ,,,

---

