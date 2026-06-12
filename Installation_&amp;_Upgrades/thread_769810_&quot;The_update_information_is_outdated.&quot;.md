---
title: "&quot;The update information is outdated.&quot;"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by mattnico on 2008-04-26
I am running Ubuntu Hardy Heron.  After a couple of weeks running my system.  I am now getting an orange warning triangle that tells me: > "The update information is outdated.  This may be caused by network problems.  Please update manually by clicking on this icon and then selecting 'Check'."  When I follow these instructions it always tells me that my system is up-to-date.   It also tells me that I haven't updated for 10(+) days even when I performed a check only minutes ago.

Any ideas what could cause this?  I have reinstalled the update manager to no effect.  :-k

Thank you for your help.

---

### Post by mattnico on 2008-04-28
Well now there's another piece of the puzzle.  Today it actually notified me of new updates available (for Skype) but still said that I had last checked for updates 12 days ago.  So the update manager appears to be working, but not updating its log of update checks.  Any ideas how to fix this?

---

### Post by FredB on 2008-04-28
Try to refresh your update database by hand. But first, choose a server which is not overwhelmed, with Synaptic.

Then, type in a console :

sudo aptitude update

Or click on refresh icon in Synaptic.

---

### Post by lolwhites on 2008-05-05
I don't know if this is what made the difference, but when I updated by typing

sudo apt-get update
sudo apt-get upgrade

it sorted itself out.

---

### Post by mattnico on 2008-05-05
I had tried that same thing but it didn't make a difference for me.  Somehow, though, in the past few days it has sorted itself out and everything is hunky-dory again.

---

### Post by DallasMike on 2008-05-14
No joy here with either solution.  Still getting the same error.

---

### Post by lolwhites on 2008-05-15
Have you tried a different repository and/or aptitude instead of apt-get?

---

### Post by sunbird on 2008-05-19
I unchecked the box under software sources for the CD Rom and then refreshed my list and that fixed the problem for me.

---

### Post by Ck.asdf on 2008-08-09
> **lolwhites said:**
> I don't know if this is what made the difference, but when I updated by typing

sudo apt-get update
sudo apt-get upgrade

it sorted itself out.
First, clicking the triangle gives me a pop up telling me
"**Your system is up-to-date**
The package information was last updated 27 days ago."

I ran the two commands (after sudo su), and it displayed the following:


apt-get update
(Note: there was much more than this, but these were the two errors)
```
Err http://download.videolan.org woody/main Packages
  404 Not Found
Err http://hpisi.nerim.net stable/main Packages
  404 Not Found
```

apt-get upgrade
```
root@ck-desktop:/home/ck# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by fjolla on 2008-08-21
I had the same problem up until about 2 minutes ago. I solved it in the following way:

(since I'm running a swedish version, I will translate everything myself, thus some mistakes may occur, but hopefully it will be understandable.)

go to system > administration > software sources

select the second tab (third-hand-software or whatever) and uncheck the boxes which caused the problem, (for me multiverse) in your case it seems to be "http://download.videolan.org woody/main Packages" and "http://hpisi.nerim.net stable/main Packages"

When closing, press reload.
update your system in whatever way you want.

---

### Post by Ck.asdf on 2008-08-21
Okay, I'll try that ... I wonder why those sites are not updating right?

---

### Post by stinger30au on 2008-09-09
my pc has been doing this intermittently now for a few weeks

im going to try changing my repo source to another mirror and try that first

---

### Post by Ck.asdf on 2008-09-09
Yeah, I finally gave up on this ... I just got a laptop, and it's not having that problem.  But I think if I were to disable the sources it's giving me problems with, it would stop giving me that error.

---

### Post by Nirro on 2008-10-31
I have this problem for 28 days now, started with Hardy, continuing in Intrepid.
I have no error when doing manual apt-get update.

I have commented in the bug report, but there is no response yet.

[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/223505](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/223505)

---

### Post by zenthanian on 2009-07-30
I noticed this after I installed FF 3.5 and upgraded to Jaunty from Hardy.  Don't know if its related. Anyone have similar experience?

---

### Post by babygenius55 on 2009-08-10
I've been having this problem for over a week now. I've installed a lot of stuff though, not sure how to tell what it is. I wish there was a way to tell what exactly is not being updated.

---

### Post by krisgesling on 2009-09-23
Hey I've been having this problem but haven't cared so today I fixed it.

So after entering
sudo apt-get update

the errors were in reference to two [ftp://archive.canonical.com](ftp://archive.canonical.com) sources as I'd set all my sources to update over ftp to get around our uni's firewall. So my fix was just to change just those back to http connections.

To edit the update sources just enter
sudo gedit /etc/apt/sources.list

you can then comment out any sources (by entering ## at the start of the line) and rerun sudo apt-get update to see if the error still persists.

It seems like there's a number of different reasons for the problem though so to a degree you just have to find the reason for yours.

cheers
gez

---

### Post by rreese6 on 2009-09-23
[QUOTE=

I ran the two commands (after sudo su), and it displayed the following:


apt-get update
(Note: there was much more than this, but these were the two errors)
```
Err http://download.videolan.org woody/main Packages
  404 Not Found
Err http://hpisi.nerim.net stable/main Packages
  404 Not Found
```
[/QUOTE]

go to /etc/apt/sources.lst and remove those two lines.
It seems that your sources have become corrupted.
you should only run those sources from third parties that are made for the version of your distro. Such as if you are using Hardy Heron (8.04) only use that repository. I can't imagine you are actually running Debian Woody.....

see if that helps.

---

### Post by El_Shrander on 2010-01-26
I've had the same problem for a couple of days, and this:

> **fjolla said:**
> I had the same problem up until about 2 minutes ago. I solved it in the following way:

just fixed it for me. Ty, fjolla! :D

---

### Post by peertje888 on 2010-10-09
Perhaps check your system time / timezone details (i)

---

### Post by Kelvari on 2010-10-21
I was also having the same problem, but found a resolution that seems to work in one of the other threads in the forums via a Google search. [Thread from 2008]("http://ubuntuforums.org/showpost.php?p=5477770&postcount=10") - I followed the instructions in the post, and now it says "last updated less than an hour ago." :)

---

### Post by amjjawad on 2010-11-01
I just got the same problem and I fixed like this this:

1- System > Administration > Synaptic Package Manager
2- From Synaptic, go to Settings > Repositories
3- From the first tap (Ubuntu Software), from **Download From** drop down list, choose: **Other..**
4- Click ***Select Best Server***
5- It will start searching for the best server. Once done, try to close the settings window and go to Synaptic Main Window then click on **Reload**.
6- Synaptic will update its list and after it finishes, that Red Triangle should fade away.
7- To make sure everything is OK, go to System > Administration > Update Manager
8- It should say: **Your System is Up-to-Date **
*The Package Information was last updated less than one hour ago.*


IMHO, I think this should be the first step to fix such issue.

---

