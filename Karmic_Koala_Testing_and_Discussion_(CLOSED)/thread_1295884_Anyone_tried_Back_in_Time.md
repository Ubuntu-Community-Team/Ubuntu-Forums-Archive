---
title: "Anyone tried Back in Time?"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rockin_goliath on 2009-10-20
Has anyone tried Back in Time? I just installed it and set it up, and I am *really* impressed by how easy it is to use. It is inspired by Apple's Time Machine and is based on rsync.

[http://backintime.le-web.org/]("http://backintime.le-web.org/")

If we get going early enough and with a little bit of Ubunt integration, perhaps we could have a backup utility installed by default in the Lucid Lynx :)

---

### Post by psyke83 on 2009-10-20
For anyone that's interested, this application is in Karmic already (backintime-gnome/backintime-kde/backintime-kde4, backintime-common) - no need to download from the site or add any extra repositories.

---

### Post by forumache on 2009-10-20
> **psyke83 said:**
> For anyone that's interested, this application is in Karmic already (backintime-gnome/backintime-kde/backintime-kde4, backintime-common) - no need to download from the site or add any extra repositories.

This is what I always do with a new application, starting with best option first.

1st option: is it already in Ubuntu repositories? Great, install it.
2nd option: is there a repository on the developer's site? OK, add the repository and install (I will be notified of updates).
3rd option: is there a link to download the application? Kind of Windows(tm) like, download and install. But I don't like this at all, I should check the site from time to time, it's just a waste of time.

Back-in-Time is included in Ubuntu repositories (at least in Karmic it is) which is great because it is a very good application and the developer is very responsive (I had a question related to the meaning of the second button "Update snapshots" and I received the complete answer in the same day).

---

### Post by TrueTom on 2009-10-20
It's not perfect but it's Ok and I'm using it for some month now.

---

### Post by Joe_Bishop on 2009-10-20
Amateurish unusable stuff for geeks. The only good thing of this kind is opensolaris time slider in nautilus (it uses ZFS). It seems Ext4 has this capability too, but gnome amateurish developers coulnd't implement it.

---

### Post by Nickedynick on 2009-10-20
I'm not disputing the "for geeks" bit (because most of the Linux ecosystem is geek-orientated) but Back in Time seems very usable from my experience! It's fairly easy to set up too. Sure, the interface could do with some tweaking, and it's a simple backend, but it's far from amateurish!

---

### Post by Kobalt on 2009-10-20
> **Joe_Bishop said:**
> Amateurish unusable stuff for geeks. The only good thing of this kind is opensolaris time slider in nautilus (it uses ZFS). It seems Ext4 has this capability too, but gnome amateurish developers coulnd't implement it.

I respectfully disagree, both on the quality of Back in Time and the "amateurish" Gnome Devs. 
I've had an eye and a hand on Back in Time for a while and it has not let me down. It's working quite nicely. Not everyone using Ubuntu is a Dev, or such a skilled user to call Gnome Devs amateurs. We do enjoy from time to time simple solutions that just work.

---

### Post by Joe_Bishop on 2009-10-20
> **Kobalt said:**
> We do enjoy from time to time simple solutions that just work.
back in time is not a "simple solution". Simple solution is Open Solaris time slider.

---

### Post by Seventh Reign on 2009-10-20
I've loved Back in Time for a while, but since there are only 2 applications that I save settings for (Firefox and Thunderbird) I simply save the ~./Mozilla and ~./Mozilla-Thunderbird folders to a backup HDD.  Along with a Text file that has all of my extra repositories and a sudo apt-get install _____ line with every single app I reinstall.  A simple copy and paste and I'm done.  takes about 10 minutes to re install.  Usually an hour for updates and I'm done.

I'd PAY to see Windows do that!

---

### Post by moviemaniac on 2009-10-20
I've been using BIT for over half a year now and I like it. And having migrated to Karmic (fresh install) by using my BIT-backup of my data (entire home directory) I can also report that it works as it should.

---

### Post by TrueTom on 2009-10-20
> **Joe_Bishop said:**
> back in time is not a "simple solution". Simple solution is Open Solaris time slider.

Ext4 doesn't support snapshots therefore it would be hard to get the same quality as in OpenSolaris. Though, it's a cool feature.

---

### Post by Vadi on 2009-10-20
yep, I use it too.

---

### Post by rockin_goliath on 2009-10-20
After Joe_Bishop brought it to my attention, I went and checked out Time Slider on OpenSolaris, and that IS cool. Even in EXT4 does not support file system snapshots, the same effect could probably be accomplished using the same backend that is used in Back in Time. It is a very elegant and simple interface design. 

I always thought what Ubuntu lacked was a really simple, reliable, set-it-and-forget-it backup program, but in the past it did not seem like there were very many options for us to choose from. Given that it is the *lucid* lynx, after all, an integrated backup utility would be an excellent addition to the Ubuntu Desktop, whether is is Back in Time or (something like) Time Slider or whatever. 

It would also be great for people like my dad, who seems to have a technological black thumb.

---

### Post by Nickedynick on 2009-10-20
Time Slider does look cool, but where does it store the data? If it takes up extra space on your normal drive I'd be against it because I'm often juggling about large files and it could very quickly amount to my hard disk being full. If you can set it to store data on an external drive, then presumably that drive would always have to be connected.

I'd much prefer to have a transparent system such as Back in Time that lets me store backups where I like and backup when I like.

Another point I've just thought of - surely it'd be tricky to try and apply backed up data to another machine with Time Slider?

If I'm being ignorant and missing the point then fair enough, but these seem to be important issues to me.

---

### Post by dro0g on 2009-10-28
I just found Back in Time and am very excited to try it out. For those who wonder why someone would want BiT vs. backup to a second device is this fills a totally separate need. 

Backup to a secondary device is to protect against hardware failure, FS corruption, theft of system, etc. 

Snapshotting on the other hand gives you a way to revert back to a version of a file from an arbitrary point in time (for example, you open a doc and make some modifications and save and then say to yourself "oh crap, I meant to save as, I still needed the original version!") Ideally it would be nice if automatic versioning was integrated with the FS (like in VMS) but snapshotting is almost as good. I find a real RCS system is overkill and too slow and cumbersome to use for what I need most of the time.

---

### Post by rockin_goliath on 2009-10-28
> **dro0g said:**
> I just found Back in Time and am very excited to try it out. For those who wonder why someone would want BiT vs. backup to a second device is this fills a totally separate need. 

Backup to a secondary device is to protect against hardware failure, FS corruption, theft of system, etc. 

Snapshotting on the other hand gives you a way to revert back to a version of a file from an arbitrary point in time (for example, you open a doc and make some modifications and save and then say to yourself "oh crap, I meant to save as, I still needed the original version!") Ideally it would be nice if automatic versioning was integrated with the FS (like in VMS) but snapshotting is almost as good. I find a real RCS system is overkill and too slow and cumbersome to use for what I need most of the time.

Ahh, I see where you are coming from, and Back in Time fulfills both of those needs (at least for me) by simply choosing an external hard drive as the backup location. That way I can also have my data backed up in case my laptop gets stolen or busted, and I also have the snapshots in case I do something stupid with my term papers.

---

### Post by whitefort on 2009-10-28
Yep, been using it for a few months now and I'm very happy with it, despite a couple of quirks.

It's how I back up all my Ubuntu machines.  I don't understand the comment that it's for geeks, because I'm no geek (though I'd like to be!) and it's very straightforward to use.

---

