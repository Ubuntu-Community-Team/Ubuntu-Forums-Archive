---
title: "VLC installation issues in Ubuntu 14.04"
date: 2014-04-07
forum: Installation &amp; Upgrades
---

### Post by daggerx on 2014-04-07
Trying to install VLC in 14.04 and I get this.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: vlc-nox (= 2.1.2-2build2) but it is not going to be installed
       Recommends: vlc-plugin-notify (= 2.1.2-2build2) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 2.1.2-2build2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
andrew@andrew-K52F:~$ 

```

Please advise what I need to do to get this right. I get the same error (similar) with ffmpeg. I'll do a separate ffmpeg thread for that. Really need this. Great software and I need it to work in my 14.04. thanks.

---

### Post by monkeybrain20122 on 2014-04-07
Well 14.04 is a beta, so if you really need things to work don't install it. Checkout the Ubuntu+1 threads (beta testers) may be you will get some insights for your problem.

---

### Post by 23dornot23d on 2014-04-07
Go into synaptic package manager and look for - edit - fix broken packages .........

edit - fix broken packages ( top of the screen )

You may have to uninstall vlc ......... or it could be that you just need to update the package manager listings as below.



[B]sudo apt-get update
sudo apt-get install aptitude
sudo aptitude update
sudo aptitude install vlc[/B]

Then post back what its giving as options ....... often answering no 
will bring up another set of alternatives using aptitude ........

but post back the resulting listing before accepting it ..........

---

### Post by alessandro-gobbi on 2014-05-15
It worked for me using:

[B]sudo apt-get update
sudo apt-get install aptitude
sudo aptitude update
sudo aptitude install vlc

[/B]Thank you

---

### Post by monkeybrain20122 on 2014-05-15
> **alessandro-gobbi said:**
> It worked for me using:

[B]sudo apt-get update
sudo apt-get install aptitude
sudo aptitude update
sudo aptitude install vlc

[/B]Thank you

Why aptitude? Anyway look at the date of OP, now that 14.04 is released the repos are sorted out so not surprising that it works. :)

---

### Post by HarryG123 on 2014-06-26
doesn't work for me at all.  latest ubuntu 14.04 lts update really screwed things up -- broke dependencies, deleted vlc...   See [http://askubuntu.com/questions/488443/vlc-broken-after-last-update](http://askubuntu.com/questions/488443/vlc-broken-after-last-update)

would appreciate it if anyone could advise how I can dig myself out of this hole that cannonical dug for me.

-harryg

---

### Post by bapoumba on 2014-06-28
Please first post the outputs of :
```
cat -n /etc/apt/sources.list
ls /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*

```

and the whole outputs to :
```
sudo apt-get update
sudo apt-get upgrade
```

Last two should bring up the same results as you already posted on AU, but we would need a fresh output. Please use code tags to post the outputs : [http://ubuntuforums.org/misc.php?do=bbcode#code](http://ubuntuforums.org/misc.php?do=bbcode#code)

---

