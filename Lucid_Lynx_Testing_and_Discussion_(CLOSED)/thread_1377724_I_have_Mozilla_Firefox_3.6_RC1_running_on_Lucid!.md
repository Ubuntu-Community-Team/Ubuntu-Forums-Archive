---
title: "I have Mozilla Firefox 3.6 RC1 running on Lucid!"
date: 2010-01-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kevpan815 on 2010-01-10
Came through as an Automatic Update Friday Night Chicago Time Zone!

---

### Post by kevpan815 on 2010-01-10
> **kevpan815 said:**
> Came through as an Automatic Update Friday Night Chicago Time Zone!

Forgot 2 mention that this was a Mozilla Automatic Update from 3.6 Beta 5, And NOT a Ubuntu Automatic Update, Just FYI!

---

### Post by kevpan815 on 2010-01-10
> **kevpan815 said:**
> Forgot 2 mention that this was a Mozilla Automatic Update from 3.6 Beta 5, And NOT a Ubuntu Automatic Update, Just FYI!

P.S. If you take a close look at the Build Date: It was compiled on 01/05/2010!

---

### Post by Starks on 2010-01-10
> **kevpan815 said:**
> Came through as an Automatic Update Friday Night Chicago Time Zone!
Why not just use the Ubuntu Mozilla Daily PPA?

---

### Post by kevpan815 on 2010-01-10
> **Starks said:**
> Why not just use the Ubuntu Mozilla Daily PPA?

Don't know what that is, and it sounds dangerous 2 be messing around with nightly builds! I prefer 2 stick with the Mile Stone Builds, especially with my 5 GB Download Limit from U.S. Cellular (my Wireless ISP)! Just FYI!

---

### Post by sliketymo on 2010-01-10
Not really "dangerous".It is the daily created development snapshots of Firefox.I am a big fan of Minefield myself.You may run into an occasional crash,or site rendering problem,but that is to be expected from cutting edge.It's all good.

---

### Post by Merk42 on 2010-01-10
By the time Lucid is released it may even be 3.7 (doubtful)

Even if 3.7 is released after Lucid, [hopefully we won't have to wait until Lucid+1 to use it.](https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-new-firefox-support-model)

---

### Post by kahumba on 2010-01-11
Firefox 3.7 should be released by December 2010 or January 2011.

I know this sounds too late, but haven't you noticed that "every" Firefox release took about 2x time than initially anticipated by Mozilla?
Even the latest version to come (3.6) - Mozilla said it would be out in like 3 months, then they said by October (by Windows 7 release), then before 2010 and then it was again postponed and now.. uhh..

---

### Post by phillw on 2010-01-11
Hi,

If you're 'playing' with the RC, can you keep an eye on this thread --> [http://ubuntuforums.org/showthread.php?t=1347430](http://ubuntuforums.org/showthread.php?t=1347430)  Evidently they're trying to 'nail' what is the most difficult of all - an intermittent bug !!

Me, I'm still on 3.5.7 :)

But 10.04 is very nearly my production environment now (I **know** I shouldn't - And do have my /home safely rsynced so 9.10 can access it if all goes pear shaped)

Phill.

---

### Post by baizon on 2010-01-12
My question is, will Firefox 3.6 will be a part of Ubuntu 10.4? The final release of FF 3.6 should be between Alpha 2 and Alpha 3 so I'm hoping it will be added to the ubuntu repository :)

---

### Post by andrewabc on 2010-01-12
> **baizon said:**
> My question is, will Firefox 3.6 will be a part of Ubuntu 10.4? The final release of FF 3.6 should be between Alpha 2 and Alpha 3 so I'm hoping it will be added to the ubuntu repository :)

Firefox 3.6 should be released by the end of the month, maybe early February.
So it will definitely be part of 10.04.

There is no way they'll ship ff3.5 as default when a new version has been out 2 months before Lucid release.

---

### Post by dino99 on 2010-01-12
hi,

a little question:

 every time i install a new distro with firefox ( now Lucid) on a separate partition, and want to import the bookmarks, passwords and settings, Firefox is not able to find the others firefox installed on others partitions/disks: that's a pain, it's totaly blind :(

So, i reload Karmic and export the settings: only bookmarks are exported  :(

Looking at mozilla docs, they are talking about panels where we can select what we want to export, but i can't see that stuff.

Have you any remarks to help me ?

---

### Post by andrewabc on 2010-01-12
> **dino99 said:**
> hi,

a little question:

 every time i install a new distro with firefox ( now Lucid) on a separate partition, and want to import the bookmarks, passwords and settings, Firefox is not able to find the others firefox installed on others partitions/disks: that's a pain, it's totaly blind :(

So, i reload Karmic and export the settings: only bookmarks are exported  :(

Looking at mozilla docs, they are talking about panels where we can select what we want to export, but i can't see that stuff.

Have you any remarks to help me ?

copy/paste old profile folder into new profile directory. That worked for me with 3.0-3.5. (sorry hard to explain but it should work and is simple).

---

### Post by dino99 on 2010-01-12
> **andrewabc said:**
> copy/paste old profile folder into new profile directory. That worked for me with 3.0-3.5. (sorry hard to explain but it should work and is simple).

thanks,

of course it's the easiest way but i don't desperate to find an automated solution. Seem i fill a bug report for so bad design  :P

---

### Post by phillw on 2010-01-12
> **dino99 said:**
> hi,

a little question:

 every time i install a new distro with firefox ( now Lucid) on a separate partition, and want to import the bookmarks, passwords and settings, Firefox is not able to find the others firefox installed on others partitions/disks: that's a pain, it's totaly blind :(

So, i reload Karmic and export the settings: only bookmarks are exported  :(

Looking at mozilla docs, they are talking about panels where we can select what we want to export, but i can't see that stuff.

Have you any remarks to help me ?

bookmarks can be exported / imported via Bookmarks --> Organise Bookmarks.
For Passwords, get hold of a nifty little add-on called Password Exporter.

I must admit to doing it the way previously mentioned. Although I take it to the extreme - I use rsync to take my entire /home directory over with me (keeps all my settings, pidgin passwords etc). But you could just ```
rsync -aS /old_home/.mozilla/. /new_home/.mozilla/. 
``` If that's all you wanted.

That simple method does rely on you having the same UID and login name on both the old installation and the new one - If they're different you can change that, but I don't recall how !

That's about as automated as I've gotten it :D

Regards,

Phill.

---

### Post by gabo.cr on 2010-01-12
> rsync -aS /old_home/.mozilla/. /new_home/.mozilla/.

Thank you for that, I like it.

---

### Post by seeker5528 on 2010-01-13
Personally I prefer [febe](https://addons.mozilla.org/en-US/firefox/addon/2109) for backing up/syncing my bookmarks.

If you have merged bookmarks from multiple sources or for some other reason end up with duplicates you may also find [bookmarkdd](http://bookmarkdd.mozdev.org/) useful for the half of the duplicate handling that isn't built into Firefox.

Later, Seeker

---

