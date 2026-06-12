---
title: "Sub-process gzip returned an error code (1)"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by intrepidus on 2007-06-05
This is what happens when I run apt-get update. Don't worry, I've already highlighted the irony.

```

Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Bizarre Error - File size is not what the server reported 3754411 4911960
W: Duplicate sources.list entry ftp://us.archive.ubuntu.com feisty/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages)
W: You may want to run **apt-get update** to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I've looked around, and no one seems to know what is really causing this, and there has been no released fix. It's a bit frustrating. I just came back to Ubuntu, and I still don't have a workable system (multimedia, etc.) because of this.

The current solution is to change the address from "http" to "ftp." This is not an acceptable solution - it's a hack, and it doesn't work if you don't have ftp access, which many of us don't. I'm extremely frustrated with Ubuntu right now, and I'm hoping someone can help.

This is a fresh installation, and the only changes I've made so far are those explained in the [Enabling Multimedia in Feisty (HOW-TO)]("http://ubuntuforums.org/showthread.php?t=413624") thread.

Reference threads:
[http://ubuntuforums.org/showthread.php?t=397725](http://ubuntuforums.org/showthread.php?t=397725)

Has anyone figured out the actual cause for this problem, and more importantly, the fix?

---

### Post by taurus on 2007-06-05
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the **us.** from all your repos.  Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by intrepidus on 2007-06-05
That appears to have done it. Thank you!

---

### Post by martinrandau on 2007-06-08
I have the same problem. Here is my sources.list

```
# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
```

As you can see there is no **us** to remove. 

Please help! ;)

---

### Post by bigredcherokee on 2007-06-09
Andybody find a fix for this yet? I'm having the same problem.

---

### Post by taurus on 2007-06-09
> **martinrandau said:**
> I have the same problem. Here is my sources.list

```
# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
```

As you can see there is no **us** to remove. 

Please help! ;)

Remove the **gb.** instead.

---

### Post by martinrandau on 2007-06-09
Good thinking! :D

That fixed it.

---

### Post by radiowave911 on 2007-06-09
I tried that.  it worked on one system only, now it does not fix the problem.  My sources.list:

# 
# deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

---

### Post by taurus on 2007-06-10
What happens when you run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by radiowave911 on 2007-06-10
both return no errors, there were some packages upgraded when I ran upgrade.  What is the difference between aptitude and apt-get?  I am still learning my way around Ubuntu, and Linux in general.

Thanks for the help.

By the way, in case I missed posting it earlier, this is on a server install, no GUI.

---

### Post by taurus on 2007-06-10
Here you go.

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by radiowave911 on 2007-06-10
Thank you.  It looks as though there is some rather useful info on that site in general.  I have bookmarked it for further use.

---

### Post by radiowave911 on 2007-06-16
The problem has returned.  apt-get and aptitude both give me the gzip error.  I am not using the country-specific archives, the addresses are all the archive.ubuntu.com addresses.  The Universe repository is the only one that is failing.  Thinking my firewall amy be suspect, i just diod a nuke & pave operation on it - rebuilt from the ground up, no change.

Any suggestions for what to look for/at or try next?

---

### Post by Myiasia on 2008-02-01
Same issue as radiowave911 - Fresh install, did everything this particular topic recommended and it's still failing on the Universe repository. Now, something I *DID* notice is that, despite having edited the package.list file and removed all locale-specific URLs, it's still trying to look in "us.archive.ubuntu.com" for Universe stuff. It's currently running the aptitude upgrade, and I'll try again after it finishes - but this certainly has been a pesky issue.

---

### Post by Myiasia on 2008-02-01
Okay! I've fixed it. What I did was go into the Synaptic Package Manager (under System -> Administration) and selected "Settings -> Repositories" from its menu. I then changed, under the Ubuntu Software tab, the "Download from: " drop-down from "Custom servers" to "Main server" and had it save that. No more errors! :)

---

