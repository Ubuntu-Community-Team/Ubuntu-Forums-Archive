---
title: "Big problems with a fresh install"
date: 2012-09-15
forum: Installation &amp; Upgrades
---

### Post by Shie6meepo on 2012-09-15
I just went ahead and did a completely new install of 12.04 last night after idiotically and automatically saying yes to one of those "partial upgrade" prompts in the software center or upgrade manager. Long story short, it ruined my system as predictable and I didn't want to go through and reinstall all the missing vital packages, so I just threw the whole broken system out.

The next morning (it decided to take a number of hours to install the new OS and I fell asleep), I re-started and attempted to load some software that I'd had before. Seconds, later, it seemed I'd been transported back to last night with a useless system. First, the universe repository was not loaded and errored out if I attempted to add it. Then, package manager started throwing up a million error and many of my system programs won't open. Here's what the terminal says when I attempt to update:

[CENTER][http://imageshack.us/a/img411/7154/screenshotfrom201209150.png](http://imageshack.us/a/img411/7154/screenshotfrom201209150.png)

[LEFT]And here's what happens when I try to start Update Manager:

[CENTER][http://imageshack.us/a/img337/7154/screenshotfrom201209150.png](http://imageshack.us/a/img337/7154/screenshotfrom201209150.png)

[LEFT]I'm using the 64-bit install on an HP Pavilion dm1-4010us with an AMD E2 processor.



**Any ideas?**
[/LEFT]
[/CENTER]
[/LEFT]
[/CENTER]

---

### Post by Bucky Ball on 2012-09-15
For future reference: Please attach screenshots or make thumbnail size rather than pasting large files in the body of the post. ;)

Files can be attached by editing the post as per normal then click 'Go Advanced' and attach with the paperclip icon.

---

### Post by kaytrance on 2012-09-15
It appears that the US mirror was down. Add some mirrors, [here's the guide]("http://askubuntu.com/questions/37753/how-can-i-get-apt-to-use-a-mirror-close-to-me-or-choose-a-faster-mirror").

---

### Post by Shie6meepo on 2012-09-15
> **kaytrance said:**
> It appears that the US mirror was down. Add some mirrors, [here's the guide]("http://askubuntu.com/questions/37753/how-can-i-get-apt-to-use-a-mirror-close-to-me-or-choose-a-faster-mirror").

I'll try it and report back ASAP.

---

### Post by Shie6meepo on 2012-09-15
EDIT: Never mind on that front.

---

### Post by Shie6meepo on 2012-09-15
Unless I did something wrong with it, editing the mirrors didn't work. I re-started and got all the same errors.

EDIT: Is the mirror issue an issue with sources far away and therefore should it solve itself within a few days (hours), or is it something within my system?

---

### Post by kaytrance on 2012-09-15
> **ssrock64 said:**
> Unless I did something wrong with it, editing the mirrors didn't work. I re-started and got all the same errors.
In your first screenshot you can see some lines like /var/lib/apt/lists...
So, make this:
```
sudo mv /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en ~/Desktop/pkg.crap
sudo apt-get update

```

Correct the path in the first line if I am misspelled something there. There seems to be some problems in fetched packages, that may be not fully downloaded.

---

### Post by Shie6meepo on 2012-09-15
> **kaytrance said:**
> In your first screenshot you can see some lines like /var/lib/apt/lists...
So, make this:
```
sudo mv /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en ~/Desktop/pkg.crap
sudo apt-get update

```Correct the path in the first line if I am misspelled something there. There seems to be some problems in fetched packages, that may be not fully downloaded.

It tells me the location doesn't exist. I triple-checked the spelling.

---

### Post by kaytrance on 2012-09-15
> It tells me the location doesn't exist. I triple-checked the spelling.
ok, lets try it another way - while typing the path, press the first letter (or 2) and press TAB - this should autocomplete the path. Well you know how does TAB works :)
So, in your first screen I can see there are 3 lines that have paths that starts with "/var/...". try to "mv" them all, one by one.

---

### Post by Shie6meepo on 2012-09-15
I've tried pointing it that way to files that most definitely exist, and it keeps handing back the same error message. Also, is the "FAILED" at the end of the last package listed here telling of the issue at all?

[CENTER][http://imageshack.us/a/img211/6900/screenshotfrom201209151.png](http://imageshack.us/a/img211/6900/screenshotfrom201209151.png)
[/CENTER]

---

### Post by Bucky Ball on 2012-09-15
Open a terminal and paste this in:

```
nano /etc/apt/sources.list
```Post the result back here, please.

---

### Post by Shie6meepo on 2012-09-15
```
deb mirror://mirrors.ubuntu.com/mirrors.txt precise main restricted universe multiverse
deb mirror://mirrors.ubuntu.com/mirrors.txt precise-updates main restricted universe multiverse
deb mirror://mirrors.ubuntu.com/mirrors.txt precise-backports main restricted universe multiverse
deb mirror://mirrors.ubuntu.com/mirrors.txt precise-security main restricted universe multiverse

# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

^G Get Help              ^O WriteOut              ^R Read File             ^Y Prev Page             ^K Cut Text              ^C Cur Pos
^X Exit                  ^J Justify               ^W Where Is              ^V Next Page             ^U UnCut Text            ^T To Spell

```

---

### Post by Bucky Ball on 2012-09-15
Make the last section look like this:

```

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
# deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

```The simplest way to do this is to open update manager, click settings in the bottom left corner then 'Other Software' tab, then disable the repos in question. See how that goes.

PS: While you're in settings make sure the CD is not enabled as a repository ... another tip; find out if your ISP runs free mirrors. In Australia most ISPs have some free mirrors and you can usually find one with Ubuntu. If you can, you will be able to set the server/mirror to that in the Settings gui and be certain you have got that bit right.

---

### Post by Shie6meepo on 2012-09-15
> **Bucky Ball said:**
> Make the last section look like this:

```

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
# deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

```The simplest way to do this is to open update manager, click settings in the bottom left corner then 'Other Software' tab, then disable the repos in question. See how that goes.

PS: While you're in settings make sure the CD is not enabled as a repository ... another tip; find out if your ISP runs free mirrors. In Australia most ISPs have some free mirrors and you can usually find one with Ubuntu. If you can, you will be able to set the server/mirror to that in the Settings gui and be certain you have got that bit right.
I'm not quite sure what you mean by "the last section". The last section I see it the partner repositories, and there's too many multiverse-referencing sections to know which one to edit. I cannot edit it through update manager because it closes upon error.

EDIT: That's my bad for not having the full code posted before. Should I just comment every multiverse phrase?

---

### Post by Bucky Ball on 2012-09-15
Okay then. Open a terminal and:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```... to save a copy in case you screw up. Then:

```
sudo nano /etc/apt/sources.list
```Scroll to the last bunch of entries that look like this, without the hash to start:

```
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
## team, and may not be under a free licence. Please satisfy yourself as  to  ## your rights to use the software. Also, please note that software  in  
## multiverse WILL NOT receive any review or updates from the Ubuntu ## security team. 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
```Put hashes in front of the last three entries, like so:

```
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
## team, and may not be under a free licence. Please satisfy yourself as to  ## your rights to use the software. Also, please note that software in  
## multiverse WILL NOT receive any review or updates from the Ubuntu ## security team. 
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse 
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
```Control+X, Y to save and quit. Then:

```
sudo apt-get update
```

What now?

---

### Post by Shie6meepo on 2012-09-15
The internal errors now all seem gone, but all of the IP-related errors are still there.

---

### Post by Bucky Ball on 2012-09-15
The first ones, top of the list:

```
deb mirror://mirrors.ubuntu.com/mirrors.txt precise main restricted universe multiverse 
deb mirror://mirrors.ubuntu.com/mirrors.txt precise-updates main restricted universe multiverse 
deb mirror://mirrors.ubuntu.com/mirrors.txt precise-backports main restricted universe multiverse 
deb mirror://mirrors.ubuntu.com/mirrors.txt precise-security main restricted universe multiverse
```Try hashing them out, too. If this works, bring the last ones back in again. 

The reason I'm saying this is because the only AMD64s are hashed out already and the first entries at the top are out there with no heading and the 'mirrors.txt' looks odd. 

Incidentally, if you need to get back to the beginning, you can put the original file back with:

```
sudo cp /etc/apt/sources.list.bak /etc/apt/sources.list
```

---

### Post by Shie6meepo on 2012-09-15
When I revert it that way, I gain back one internal error with the Translation package. Do you think it's better at this point that I just do another fresh install?

EDIT: And when I do, should I re-do the whole ISO with a brand-new download from the Ubuntu site, or should the current boot files be acceptable?

---

### Post by Bucky Ball on 2012-09-16
Yes, agreed. Torrent the download if you can. Safest, quickest way. md5um checked on way. 

A clean install is best. Upgrades can sometimes go sideways. There could be an easy fix for this and I just don't know it, but if you have nothing to lose I'd go the clean install anyhow. (And back up anything you don't want to lose, naturally, just in case). ;)

* If you have the space and want to keep fiddling with this install/plaything, you could do a clean install on another partition. You can use the existing /swap (and /home partition if there is one).

---

### Post by admelfo on 2012-10-11
> **Bucky Ball said:**
> 
A clean install is best. Upgrades can sometimes go sideways. There could be an easy fix for this and I just don't know it, but if you have nothing to lose I'd go the clean install anyhow. 

Yup. Was happily running 10.04 since it was released on a eeePC with the least issues I've ever had. Got the message that 12.04 LTS was out, and clicked "update" -- lots of hang-ups and error messages, but it seemed to get through it. Then, my home wifi was all screwed up (connected, but wouldn't load web pages), scanned the forums, tried to go back to an earlier version of Network Manager, somehow screwed up Update Manager in the process -- long story short, last night, I just did a total re-install of 10.04 from flash drive, and everything's back the way it was before. Fortunately, didn't have anything really important saved on the netbook, which I mainly use for convenience around the house and on the road.

Still love Ubie. Just wish I had more time to devote to it on a consistent basis, so I wouldn't feel like I was flying blind every time I run into sys probs.

---

