---
title: "upgrade ubuntu 12.04 to 13.04"
date: 2013-04-13
forum: Installation &amp; Upgrades
---

### Post by bill23 on 2013-04-13
[FONT=book antiqua][SIZE=3][FONT=verdana][SIZE=2]Hi;
Currently I am running Ubuntu 12.04 LTS. I am contemplating upgrading to 13.04 wh[/SIZE][/FONT][SIZE=3][FONT=verdana][SIZE=2]en its st[/SIZE][/FONT][SIZE=3][FONT=verdana][SIZE=2]able version is released toward the end of this month. [/SIZE][/FONT][SIZE=3][FONT=verdana][SIZE=2]Would I be able to by pass 12.10 and go directly to 13.04 through the Update [/SIZE][/FONT][SIZE=3][FONT=verdana][SIZE=2]Manager or would I need to upgrade to 12.[/SIZE][/FONT][SIZE=3][FONT=verdana][SIZE=2]10 first and then go to 13.04 when it is available (stable version)?
bill23[/SIZE][/FONT]
[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT]

---

### Post by snowpine on 2013-04-13
Safest method is to create a new partition and install 13.04 as a "dual boot." Then you still have stable long term support 12.04 as a fallback while you are getting used to 13.04.

---

### Post by grahammechanical on 2013-04-13
We can use Update Manager to upgrade from one LTS release to another LTS and so bypass the 3 releases in between but when we start off with an interim release (from now on to be called Standard release) with have to go from one to the next. So, you will have to upgrade to 12.10 and then to 13.04. I suggest making sure that your desktop is as default as possible to avoid complications.

Regards.

---

### Post by ahallubuntu on 2013-04-13
I agree with snowpine.  Actually, I can't imagine wanting to upgrade from an LTS version that's supported til 2017 to one that's supported only until January 2014, but I guess some people like upgrading their distro often.

Instead of doing a dual boot, you could (if you have an external hard drive or place to make a big backup) boot a live CD and install "dump" then dump a copy of your 12.04 / partition to one big file, so you could always restore it if something goes wrong with 13.04.  If your / partition uses a lot of disk space that could be a very large backup file, though.

---

### Post by bill23 on 2013-04-13
What you propose is a bit to complicated for me.

---

### Post by bill23 on 2013-04-13
I may stay with what I have for the time being.

---

### Post by ibjsb4 on 2013-04-13
As stated 12o4 (LTS) is supported until 2017.  So your good :)

---

### Post by dmobley88 on 2013-04-19
I know it's a bit late, but I found something where you can upgrade directly from 12.04 LTS to 13.04. 

NOTE: I would NOT reccommend doing this as you have to do alot of work on the os before it will boot up. 

DO THIS AT YOUR OWN RISK. 

open a terminal by pressing: Press ctl-alt-t

enter the commands below

 sudo sed -i 's/quantal/raring/' /etc/apt/sources.list   sudo apt-get update 
 apt-get dist-upgrade

This will take a really REALLY LONG time. It took my computer about 2 hours to complete the upgrade. Good luck

---

### Post by fantab on 2013-04-20
> **snowpine said:**
> Safest method is to create a new partition and install 13.04 as a "dual boot." Then you still have stable long term support 12.04 as a fallback while you are getting used to 13.04.

+1.

I have both 12.04 and 13.04 on their respective partitions. 12.04 is MY stable version and MY back up Ubuntu. 13.04 or next development release is my main Ubuntu. If something breaks I can always fallback on 12.04.
So, CREATE another partition of about 15-20GB and install 13.04 on it.

Good Luck.

---

### Post by Cheesemill on 2013-04-20
> **dmobley88 said:**
> I know it's a bit late, but I found something where you can upgrade directly from 12.04 LTS to 13.04. 

NOTE: I would NOT reccommend doing this as you have to do alot of work on the os before it will boot up. 

DO THIS AT YOUR OWN RISK. 

open a terminal by pressing: Press ctl-alt-t

enter the commands below

 sudo sed -i 's/quantal/raring/' /etc/apt/sources.list   sudo apt-get update 
 apt-get dist-upgrade

This will take a really REALLY LONG time. It took my computer about 2 hours to complete the upgrade. Good luck

That command won't have any effect at all on a 12.04 installation.

It is used for upgrading from 12.10 (quantal) to 13.04 (raring).

---

### Post by kOvaxo on 2013-04-27
[HTML]sudo do-release-upgrade -d[/HTML]

done that my self jumping from 12.10 to 13.04

---

### Post by snowpine on 2013-04-27
> **kOvaxo said:**
> [HTML]sudo do-release-upgrade -d[/HTML]

done that my self jumping from 12.10 to 13.04

Wrong (now that 13.04 has been officially released). More info here: [https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html](https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html)

---

### Post by Alan.Brown on 2013-04-29
I have just upgraded to the "stable" version of 13.04 three days ago.   Disappiontingly, I am having a number of problems with it including not being able to get updates to fix the problems.   

Over the past three years upgrades have worked very well with no problems - but 13.04 is a disaster. [IMHO]

In future I will not upgrade for at least 2 weeks after the so-called "stable" version has been issued to let the initial problems be fixed.

---

### Post by ssloan12 on 2013-05-02
Hi, I always get so excited with the new distribution.  the 12.04 was super stable, yet I always want more.  To be honest, 12.10 totally SUCKED.  Buggy as all heck and had continous problems with updates and catalog mismatches etc.  

I have started with a clean new install.. Right now I am upgrading to 13.04.  By what I've read, its faster more performance etc.  Lets hope so.

I would say, if I could do it over again, going back to 12.04 and being patient would have been a safer move.  However, Safer is not always better.

---

### Post by kbellis on 2013-06-04
> **Alan.Brown said:**
> I have just upgraded to the "stable" version of 13.04 three days ago.   Disappiontingly, I am having a number of problems with it including not being able to get updates to fix the problems.   

Over the past three years upgrades have worked very well with no problems - but 13.04 is a disaster. [IMHO]

In future I will not upgrade for at least 2 weeks after the so-called "stable" version has been issued to let the initial problems be fixed.

Hi Alan, 

How have you made out since writing this post? 
Did you go back to 12.04? 
And what made you want to try 13.04 to begin with? 

I'm contemplating the move to Ubuntu 13.04 primarily to permit running [GIMP 2.8.x]("https://apps.ubuntu.com/cat/applications/gimp/") as Ubuntu 12.04 apparently is unable to update or even install from a fresh get, anything other than GIMP 2.6x... and like you, I've been happily running 12.04 since installing it (last September).

Kind regards,

Kelly

---

### Post by Cheesemill on 2013-06-04
You could always add the Gimp PPA to your 12.04 installation to get the latest version...
```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update
sudo apt-get install gimp
```

---

### Post by kbellis on 2013-06-04
Thanks Cheesemill ! - I'll look into trying that... and learning what PPA means :)

---

### Post by kbellis on 2013-06-04
Follow up: That went quite well! Thanks again for your help!!

Also, this might be worth sharing: [http://handytutorial.com/install-gimp-2-8-4-in-ubuntu-linux-mint-using-ppa/](http://handytutorial.com/install-gimp-2-8-4-in-ubuntu-linux-mint-using-ppa/)

GIMP 2.8.4 looks great!

---

### Post by PeteU18 on 2013-07-11
Thanks Cheesemill,

Just what I was looking for. txs  Pete.

---

