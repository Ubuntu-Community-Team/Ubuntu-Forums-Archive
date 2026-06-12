---
title: "404 Error in Update Manager"
date: 2010-08-15
forum: Installation &amp; Upgrades
---

### Post by VideoAddicted on 2010-08-15
I am running 8.04 (Hardy) and when I try to check for new updates so i can try and upgrade to Lucid, I get the following errors.

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Some index files failed to download, they have been ignored, or old ones used instead.


For some inexplicable reason, my computer is searching for Feisty files and its getting the 404 error when it tries to do it, completely shutting updates (for the past 200 odd days as well).  

I've looked elsewhere on the site for help but all the other relevant ideas haven't worked.  

I tried running the update from aptitude and i tried changing the server i was downloading from which were the only two suggestions that i found for situations that seemed to mirror my own.  

I would would greatly appreciate any help with getting this to work.  Thanks in advance.

---

### Post by howefield on 2010-08-15
Can you post the contents of your sources.list ?

From terminal,

```
sudo /etc/apt/sources.list
```

---

### Post by lykeion on 2010-08-15
If you are trying to upgrade Hardy > Lucid you should check this page:

[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

---

### Post by VideoAddicted on 2010-08-15
```
sudo /etc/apt/sources.list
```

this returns
sudo: /etc/apt/sources.list: command not found

---

### Post by howefield on 2010-08-15
> **VideoAddicted said:**
> sudo: /etc/apt/sources.list: command not found

Apologies, what I meant to type was..

```
cat /etc/apt/sources.list
```

---

### Post by VideoAddicted on 2010-08-15
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse

hope this helps

---

### Post by HeadHunter00 on 2010-08-15
really? *sigh* just use another mirror from software sources.

---

### Post by howefield on 2010-08-15
> **HeadHunter00 said:**
> really? *sigh* just use another mirror from software sources.

Give yourself a break and read the question.

---

### Post by howefield on 2010-08-15
> **VideoAddicted said:**
> hope this helps

Comment out the lines with feisty in them.

Use the terminal command

```
gksudo gedit /etc/apt/sources.list
```

and place a pound sign # in front of the offending lines.

Save and reload your software sources.

---

### Post by robdaemon on 2010-08-15
> **HeadHunter00 said:**
> really? *sigh* just use another mirror from software sources.

really?  You're sooo helpful.

Anyhow, to be more helpful to the OP, the US archive server seems to be having trouble.

In your software sources, you should change your mirror.

I'm switching to [http://mirrors.xmission.com/ubuntu](http://mirrors.xmission.com/ubuntu) for the time being.

You can find Software Sources under Administration in your GNOME menu.  (I'm working on a netbook edition installation right now, so I can't tell you the exact wording in a stock Ubuntu installation.)

---

### Post by HeadHunter00 on 2010-08-15
sorry 4 my ignorance eh. i didnt read the whole post. from wat i can see, your repositories are still at feisty. so, to fix that edit /etc/apt/source.list and then replace all the "feisties" with lucid

---

### Post by VideoAddicted on 2010-08-15
Thanks everyone who posted, your suggestions fixed my problem.  

On a related note, will upgrading from Hardy to Lucid make me lose the data on my hard drive, i've heard this mentioned and I don't want to lose my data because that would be somewhat frustrating...

---

### Post by mörgæs on 2010-08-16
It seems like your machine has a long history of upgrades. If I were you I would back up all my files and do a clean install of 10.04. May I guess that it has been running something like three years?

An update preserves the user files, but it is not the best foundation for a stable system.

---

### Post by howefield on 2010-08-16
> **VideoAddicted said:**
> On a related note, will upgrading from Hardy to Lucid make me lose the data on my hard drive, i've heard this mentioned and I don't want to lose my data because that would be somewhat frustrating...

Your data should be safe enough.

However if you have only one copy of data that is valuable to you, then you're data is an accident just waiting to happen.

Do yourself a favour and get it backed up.

---

### Post by VideoAddicted on 2010-08-17
thanks guys

---

