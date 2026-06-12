---
title: "Oneric -&gt; Precise upgrade hanging on openjdk file download failure"
date: 2014-05-07
forum: Installation &amp; Upgrades
---

### Post by ergeorge on 2014-05-07
Well, not exactly hanging - it just keeps trying to download the same file over and over.

uname -ra
Linux adelie3 3.0.0-30-generic #47-Ubuntu SMP Wed Jan 2 23:16:29 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

I'm trying to upgrade my workstation using the command line do-release-upgrade command.  It appears to start properly and downloads on the order of about 1400 files if I recall correctly.  Then it gets to this:

Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main openjdk-6-jre-headless amd64 6b31-1.13.3-1ubuntu1~0.12.04.2 [32.8 MB]

(this is on the 3rd restart, so the counter is at 1)

It tries to download this file over and over - the progress line shows it getting to "32.7/32.8 MB 99%" and then it appears to start over again??

Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main openjdk-6-jre-headless amd64 6b31-1.13.3-1ubuntu1~0.12.04.2 [32.8 MB]                                                                                                                                          
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main openjdk-6-jre-headless amd64 6b31-1.13.3-1ubuntu1~0.12.04.2 [32.8 MB]                                                                                                                                          
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main openjdk-6-jre-headless amd64 6b31-1.13.3-1ubuntu1~0.12.04.2 [32.8 MB]                                                                                                                                          
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main openjdk-6-jre-headless amd64 6b31-1.13.3-1ubuntu1~0.12.04.2 [32.8 MB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main  openjdk-6-jre-headless amd64 6b31-1.13.3-1ubuntu1~0.12.04.2 [32.8  MB]                                                                                                                                           
Get:6 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main  openjdk-6-jre-headless amd64 6b31-1.13.3-1ubuntu1~0.12.04.2 [32.8 MB]

The above is just while I've been typing this.

Any suggestions?

---

### Post by Bashing-om on 2014-05-07
ergeorge; Hi ! Welcome to the forum.

oneiric is End-Of-Life and as such no longer enjoys support. the software repository has been turned down ad redirected.
Did you change your sources.list to point to old_releases ?
This guide for the howto:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
The guide is old, but remains valid.

[INDENT][INDENT]Hope This Helps
[/INDENT][/INDENT]

---

### Post by ergeorge on 2014-05-07
Thanks for the reply - yes, I'm aware about the EOL issue, which is why I'm attempting this.

It looks like the upgrade process had already modified my /etc/apt/sources.list file - all of the repositories are for precise

I added the "old-releases" repositories anyway, as described in your link.  I then tried to install update-manager-core update-manager

as described in the link, but this tried to install a large number of packages from precise, which seemed like a bad idea given that my precise install hasn't actually started yet - so I cancelled that.

I then tried to do the upgrade uperation again:  sudo do-release-upgrade

  Lots of activity, but now it fails with this:

[I]Error during update 

A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 

W:Failed to fetch 
[http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release) 
Unable to find expected entry 'multiversea/binary-amd64/Packages' in 
Release file (Wrong sources.list entry or malformed file) 
, E:Some index files failed to download. They have been ignored, or 
old ones used instead. 


Restoring original system state

Aborting[/I]

Have I FUBARed things by not having those "old-releases" repositories in the when I first attempted this?  This operations is starting to look like a long shot.

---

### Post by Bashing-om on 2014-05-07
ergeorge; Hey,

There is hope yet !

You are advised of an action to take:
> 
Release file (Wrong sources.list entry or malformed file)

Take a look and correct your "/etc/apt/sources.list" file and/OR the files in the 3rd party directory "/etc/apt/sources.list.d".
If you want confirmation, post the outputs - between code tags, please - of terminal commands:
```

cat /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
Once you are sure the source index files are good, test:
```

sudo apt-get update
sudo apt-get upgrade

```
Depending on those outputs,  to insure the upgrade process completes;  will require a few other terminal commands.
I am hesitate to make the further advisement until the state of the package manager and installed software is known - the update/upgrade process outputs.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by ergeorge on 2014-05-08
Thanks for the help - I really appreciate it.

But I've thought about this some more  and realized that I'd have to do this 4 more times to really get current, each step with potential for kludging up or breaking things and lots of downloads over a relatively slow connection.  I think I'll be better off just starting from scratch with a fresh install of Tahr, despite the pain of all the custom config and such.

---

### Post by Bashing-om on 2014-05-08
ergeorge; Hey,

I happen to agree, a clean install is the better choice.

I too am in this same situation of doing a "clean" install for 14.04(s).
I too am in the process of crossing my T's and dotting my I's in preparation of what I need/intend to back up, wipe my drives, repartition - not using my system like I did, and will behoove me to simplify -, install 14.04(s) and copy all my data and .configs back into place.
When all done

[INDENT][INDENT]a much better operating system
[/INDENT][/INDENT]

---

### Post by ergeorge on 2014-05-08
I'm going to try to preserve the filesystem where half a TB of data & such lives - will save hours compared to bringing it back across the network.  But I do have it backed up in case things don't work out.

---

