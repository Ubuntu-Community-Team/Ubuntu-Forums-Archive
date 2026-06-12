---
title: "About upgrading"
date: 2006-05-31
forum: Installation &amp; Upgrades
---

### Post by Zalbor on 2006-05-31
When I upgraded from Hoary to Breezy, I chose to just reinstall by booting from the DVD (I have /home on a separate partition). After that was done and I had chowned my user's home, I had some problems with GNOME.
I remember that the splash screen wouldn't disappear unless I clicked on it, that CDs wouldn't play and sometimes there was no sound. There were other problems as well, more important than the ones I remember, so I had trouble using it.
I created a new user and started logging in as this one instead and everything worked fine, so the problems were results of the upgrade.

Now I want to upgrade to Dapper, as soon as it's released. I plan to use dist-upgrade this time, but I have two things to ask:
1)Can I download and burn the DVD instead of upgrading directly from the repositories? I suppose it's possible, just making sure.
2)How can I avoid the same (or similar) problems happening this time? Will dist-upgrade take care of them? Is there something I have to do myself to avoid them? Any solution at all?

Thanks in advance.

---

### Post by Fatjoint on 2006-05-31
[QUOTE=Zalbor]
1)Can I download and burn the DVD instead of upgrading directly from the repositories? I suppose it's possible, just making sure.
2)How can I avoid the same (or similar) problems happening this time? Will dist-upgrade take care of them? Is there something I have to do myself to avoid them? Any solution at all?
[/QUOTE]

1) Yes you can.  I have upgraded from DVD before.  You add your DVD drive as one of the repo directories.  I did this for Hoary to Breezy.  I'll try and find the thread on how for you.

2) I don't have any clue how you got yourself into this situation... sorry.  I've never had an issue with upgrading from the repos or directly from DVD, so I'm no help on how to avoid.

---

### Post by Zalbor on 2006-05-31
So maybe it was because I reinstalled instead of upgrading? I hope...

---

### Post by roger6106 on 2006-05-31
[QUOTE=Zalbor]So maybe it was because I reinstalled instead of upgrading? I hope...[/QUOTE]

My guess is that some hidden configuration files in your home folder messed things up. If you installed with a blank home folder you should be fine, but then you'd lose all of your data.

---

### Post by Fatjoint on 2006-05-31
[QUOTE=Zalbor]So maybe it was because I reinstalled instead of upgrading? I hope...[/QUOTE]

That is possible I suppose.  I would think it probably happened because when you reinstalled, you didn't wipe your /root partition by repartitioning or formatting.  Instead, you reinstalled while leaving /root intact and some of your previous files remained.  It probably only replaced those files which are default on install and anything you did that was customized remained to hose everything  up.

Thinking about that possibility makes me believe more and more that's exactly what you did.  

So my advice to you would be to repartition if you do a complete reinstall.  Make sure NOT to repartition your /home, that way everything EXCEPT your /home partition (your data) is refreshed.  If you do a update you shouldn't run into any of these problems.  I haven't run into issue one updating, this aint winblows ya know ;)

---

### Post by Zalbor on 2006-06-02
[QUOTE=Fatjoint]I would think it probably happened because when you reinstalled, you didn't wipe your /root partition by repartitioning or formatting. [/QUOTE]
No. I formatted the partition through the installer, it just reinstalled everything from the beginning.

Dapper has been released now, and still I'm not upgrading... I need to be fairly sure I can prevent that problem this time.

---

### Post by Zalbor on 2006-06-02
Sorry to make a thread especially for myself, but I need some information I've not found elsewhere (so far).

First, I made this thread the other day: [http://ubuntuforums.org/showthread.php?t=185483](http://ubuntuforums.org/showthread.php?t=185483)
Should I fear anything like this happening again?

Also, I want to download and burn a DVD and upgrade from there. The [Dapper Upgrades](https://wiki.ubuntu.com/DapperUpgrades) says I can upgrade from the "Alternative" CD and not from the "Desktop" CD, but it says nothing about the DVD. Is the DVD a combination of the two CDs, like in previous versions?

Also... if the Desktop CD is like a Live CD that can also install, what exactly is the Alternative CD?

Thanks... I'd really appreciate some replies. :)

EDIT: And thanks to the mod who put them both in one thread. ;)

---

### Post by ubuntu_demon on 2006-06-02
[QUOTE=Zalbor]Sorry to make a thread especially for myself, but I need some information I've not found elsewhere (so far).

First, I made this thread the other day: [http://ubuntuforums.org/showthread.php?t=185483](http://ubuntuforums.org/showthread.php?t=185483)
Should I fear anything like this happening again?
[/quote]

I merged your two threads here.

[QUOTE=Zalbor]
Also, I want to download and burn a DVD and upgrade from there. The [Dapper Upgrades](https://wiki.ubuntu.com/DapperUpgrades) says I can upgrade from the "Alternative" CD and not from the "Desktop" CD, but it says nothing about the DVD. Is the DVD a combination of the two CDs, like in previous versions?

Also... if the Desktop CD is like a Live CD that can also install, what exactly is the Alternative CD?

Thanks... I'd really appreciate some replies. :)[/QUOTE]

IMHO it's better to just upgrade from the internet if possible.  Before you actually start the upgrade look here : 
[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)

The desktop CD is a live cd which you have to boot into and then you can install Ubuntu graphically. This is useful for people who are new to Ubuntu and have a lot of memory.

The alternative install cd is just like the install cd in breezy.

AFAIK the dvd is a combination of the install and the desktop cd + a lot of packages.

If you really want to upgrade using a cd without internet I hope you don't have too much software installed from universe because you wouldn't be able to upgrade those. Here's a bit more information : [http://www.ubuntuforums.org/showthread.php?t=179795](http://www.ubuntuforums.org/showthread.php?t=179795)

---

### Post by Zalbor on 2006-06-02
Thanks again... I do have a lot of packages from universe.
Is it not possible to use the DVD for the packages that are on it, and download the rest from the internet? The reason I'm so intent on that is that I don't have the fastest of connections and I want to be sure that the biggest files (all non-universe) will already be safely downloaded.

---

### Post by ubuntu_demon on 2006-06-02
[QUOTE=Zalbor]Thanks again... I do have a lot of packages from universe.
Is it not possible to use the DVD for the packages that are on it, and download the rest from the internet? The reason I'm so intent on that is that I don't have the fastest of connections and I want to be sure that the biggest files (all non-universe) will already be safely downloaded.[/QUOTE]

Yeah that's possible. 

I don't know how much of universe is included on the  dvd but none of universe is included on the cd's.

While running breezy pop the cd/dvd in. aysiu's post here tells you about how to add it to the sources.list :
[http://www.ubuntuforums.org/showpost.php?p=1038288&postcount=4](http://www.ubuntuforums.org/showpost.php?p=1038288&postcount=4)
That post is from this thread : [http://www.ubuntuforums.org/showthread.php?t=179795](http://www.ubuntuforums.org/showthread.php?t=179795)

For more information about apt-cdrom see : $man apt-cdrom or search "the installation and upgrade forum" for apt-cdrom.

After that read this thread :
[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)

And then start upgrading. I wish you luck!

---

### Post by Zalbor on 2006-06-02
Thanks a lot! I'll get around to downloading the DVD then I'll try...

---

### Post by ubuntu_demon on 2006-06-02
[QUOTE=Zalbor]Thanks a lot! I'll get around to downloading the DVD then I'll try...[/QUOTE]
good luck!

---

### Post by ubuntu_demon on 2006-06-02
here are the torrents : 
[http://torrent.ubuntu.com/releases/dapper/release/dvd/](http://torrent.ubuntu.com/releases/dapper/release/dvd/)

---

