---
title: "Problems when updating from Ubuntu 13.04 to 13.10"
date: 2014-04-14
forum: Installation &amp; Upgrades
---

### Post by flavio_ on 2014-04-14
Hi guys, I'm facing some problems when trying to update Ubuntu from 13.04 to 13.10. 

I am using the software update and receiving the following message: 

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/main/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/universe/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Any clue about how to solve that. I bet it's quite simple.

---

### Post by Bashing-om on 2014-04-14
flavio_; Hello.

Release 13.04 is End Of Life, and no longer has support. The repository is turned down and redirected. Thus you are beating on a dead horse. There is no easy solution, but, there is a way to breath just a bit of life back into the situation.
see:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
For the means to perform that End Of Life upgrade .
Check ALL your sources carefully, and then go for it.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by sudodus on 2014-04-14
The natty-backports are old, Natty was the version 11.04 if I remember correctly, and it passed end of life years ago. Unless you know they contain librararies or packages for important programs that you are running, I suggest that you simply remove them. You can use ***Synaptic*** to do that. Install it if it is not available. Look at

Settings -- Repositories

---

### Post by su:bhatta on 2014-04-14
> **flavio_ said:**
> Hi guys, I'm facing some problems when trying to update Ubuntu from 13.04 to 13.10. 

I am using the software update and receiving the following message: 

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/main/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/universe/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Any clue about how to solve that. I bet it's quite simple.

Those are Natty backports.
+1 to BashingOM's suggestion, pay good attention when changing your sources.list.

---

### Post by flavio_ on 2014-04-23
Dear all, thanks for the tips. I may have done something wrong. Nothing working yet. Now, I've been receiving the following message every time I try to upgrade: 

An unresolvable problem occurred whilecalculating the upgrade.
 This can be caused by:
 * Upgrading to a pre-release versionof Ubuntu
 * Running the current pre-releaseversion of Ubuntu
 * Unofficial software packages notprovided by Ubuntu
If none of this applies, then pleasereport this bug using the command 'ubuntu-bugubuntu-release-upgrader-core' in a terminal.

---

### Post by Bashing-om on 2014-04-23
flavio_flavio_; Uuhmmm,

Did you turn down all the PPAs ? ( /etc/apt/sources.list and everyting in the /etc/apt/sources.list.d directory)
Did you change the sources.list file to point to "old-releases ?
Did you follow through on the provided link to page 2 for the expllicit instruction to do so ? 

Else still with problems, show us:
```

cat -n /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list

```

And we will prepare
[INDENT][INDENT]to take  it to the next level
[/INDENT][/INDENT]

---

