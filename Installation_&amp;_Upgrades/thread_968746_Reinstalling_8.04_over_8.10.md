---
title: "Reinstalling 8.04 over 8.10"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by rgraves on 2008-11-02
Can I go backwards and just reinstall 8.04 over 8.10 using the live CD? Will there be any issues to deal with by doing this?

Too many problems with 8.10. nvidia problems. Open Office 3 problems.
Too much of a headache.

Everything was great and running fine in 8.04. I should have read forums closer before upgrading to 8.10.

---

### Post by Partyboi2 on 2008-11-02
You would have to do a clean install of 8.04, so remember to backup your data before doing a fresh install. Then choose to install to the entire disk and this should wipe your 8.10 installation.

---

### Post by Therion on 2008-11-02
I reverted back from 8.10 to 8.04 myself this weekend and no, there were no issues with re-installing from a "LiveCD".  I installed as usual (Guided: Use Entire Disk) and just let 'er rip.  8.04 is so much snappier and smoother for me...  Felt good having it back.

---

### Post by pansz on 2008-11-03
IMO the best date for install a x.04 version is September, and the best time for install a x.10 version is the next March.

March 2009 might be the time for install the Ubuntu 8.10, not now. ---- just my 2 cents.

---

### Post by rgraves on 2008-11-03
I'm back to 8.04 and couldn't be happier.

Thanx,
bob

---

### Post by N00bB00b on 2008-11-03
> **Therion said:**
> I reverted back from 8.10 to 8.04 myself this weekend and no, there were no issues with re-installing from a "LiveCD".  I installed as usual (Guided: Use Entire Disk) and just let 'er rip.  8.04 is so much snappier and smoother for me...  Felt good having it back.

Did you have to wipe your data, too?

Here's my problem:  X won't start, so I'm concerned that I'm going to have difficulty getting all my data and settings backed up correctly if I have to wipe the entire partition.

---

### Post by Therion on 2008-11-04
> **N00bB00b said:**
> Did you have to wipe your data, too?

Here's my problem:  X won't start, so I'm concerned that I'm going to have difficulty getting all my data and settings backed up correctly if I have to wipe the entire partition.
Ooooooo... I see.  

Well, this is one more reason why I have an external, USB hard drive.  It's where all my data sits.  

I also use it to store the backups of my /, /home and config files after using [QuickStart](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11) to create them.  I'm not sure what to suggest you do.

---

### Post by abn91c on 2008-11-04
go here to install office 3.0
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by N00bB00b on 2008-11-05
Thanks for the help guys.  I'm still thinking of downgrading, but I have managed to get a little closer to making 8.1 operate.  I started looking for help in this thread: 6105565 but then after not getting any replies I started screwing around and got some things working, and began bootstrapping forward.  I have most of 8.1 working now, but I don't think it's enough to justify trying to continue.

The long-story-long story is this:  When doing the upgrade, the installer asks if you want to remove the unused packages.  I (like many others) said "Yes", and then essentially everything "important" got removed.  Once I figured that out and started reinstalling some packages I made some progress.  Now I'm at the point that it's not great, but it is running, I got X/Gnome running, and most of the services running (including sound).

There are multiple recommendations to just boot from an 8.1 live cd and reinstall, which is what I'm probably going to try next if I can't make significant headway in short order.  I can then downgrade to 8.04 if I don't like where things are going in 8.1 with a fresh have-at-it.

Anyway, thanks to everyone for the suggestions.

---

