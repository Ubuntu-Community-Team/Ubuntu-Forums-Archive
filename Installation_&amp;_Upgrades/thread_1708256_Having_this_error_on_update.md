---
title: "Having this error on update"
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by nklnsk on 2011-03-16
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Im using 10.04.

Connection is fine. Maybe something wrong with server or any of my repository

[IMG]https://picasaweb.google.com/110031831078880863277/Mar16201102[/IMG]

---

### Post by drs305 on 2011-03-16
It looks like the repository you are referencing was a generic one - it includes "user" where normally a name would be included. Please check where you got that ppa address from.

> [http://ppa.launchpad.net/](http://ppa.launchpad.net/)[COLOR="Red"]user/ppa-name[/COLOR]/ubuntu/dists/lucid/main/binary-i386/Packages.gz

In the meantime, you can disable it via Software Sources or Synaptic: Settings > Repositories > Other Software and untick it. Ubuntu Tweak also has the ability to remove ppa's via it's Cleanup function.

---

### Post by nklnsk on 2011-03-16
Thanks for quick reply [[COLOR=#D40000]**drs305**[/COLOR]]("http://ubuntuforums.org/member.php?u=223945"). 

Ok, I untick it, but how can I check where it's from? Its a first time this happening on update.
 Im beginner so... :)

---

### Post by nklnsk on 2011-03-16
Yeah, updated without error.

---

### Post by drs305 on 2011-03-16
It's hard to say who or what added that ppa to your sources.list. If you don't remember manually entering it then some script you ran may have inserted it "for you". It didn't do any damage to your system and your Ubuntu OS doesn't need any ppa's to run properly. They can add software that can add functionality or additional packages but they are not part of the official operating system.

---

### Post by nklnsk on 2011-03-16
Should I delete it or just leave it unticked?

---

### Post by drs305 on 2011-03-16
> **nklnsk said:**
> Should I delete it or just leave it unticked?

You can remove it. If you figure out what it was supposed to be it will probably be easier to add an entirely new entry than to edit the existing one.

---

### Post by nklnsk on 2011-03-16
Thanks man. I'll mark this threat as solved.

---

