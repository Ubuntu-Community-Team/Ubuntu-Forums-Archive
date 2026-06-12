---
title: "upgraded to 12.10 Cannot update software."
date: 2012-11-03
forum: Installation &amp; Upgrades
---

### Post by MickM on 2012-11-03
I upgraded a week ago from 12.04 to 12.10 and all is fine. However, I tried to check for any software updater but I receive the following error.
W:Failed to fetch [http://ppa.launchpad.net/upubuntu-co...source/Sources](http://ppa.launchpad.net/upubuntu-co...source/Sources) 404 Not Found
, W:Failed to fetch [http://ppa.launchpad.net/upubuntu-co...-i386/Packages](http://ppa.launchpad.net/upubuntu-co...-i386/Packages) 404 Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by westie457 on 2012-11-03
That ppa has been removed either temporarily or permanently so the references in your sources list have to be commented out or deleted.

```
gksudo gedit /etc/apt/sources.list
```will open the file. Locate the lines with the troublesome PPA's in and either put a # at the start of each line or delete the lines. Save the file and close it.

Then ```
sudo apt-get update

sudo apt-get upgrade
```

Any problems post back here

Thank you

---

### Post by MickM on 2012-11-03
hi westie457 
I did what you said and this was the result:-

michael@michael-Aspire-one:~$ gksudo gedit /etc/apt/sources.list
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.

(gksudo:20224): Gdk-CRITICAL **: IA__gdk_error_trap_pop: assertion `gdk_error_traps != NULL' failed

(gksudo:20224): Gdk-CRITICAL **: IA__gdk_error_trap_pop: assertion `gdk_error_traps != NULL' failed
michael@michael-Aspire-one:~$ ^C

---

### Post by s9032g@comcast.net on 2012-11-03
That is the problem with posting untried solutions.

Else where in this forum posters mention they they have no been able to get updates for 12.10 for several days. Maybe nothing wrong on your end??

---

### Post by MG&amp;TL on 2012-11-03
Hi Mick-

For some reason, gedit is crashing. Use:

```
sudo nano /etc/apt/sources.list
```

to do the same thing. :)

---

### Post by ibjsb4 on 2012-11-03
Also the two ULR's in your first post are malformed and will never work.

---

### Post by MickM on 2012-11-03
Hi All,
Thanks for all your help. It seems that I will have to wait for the Team to fix this problem.
When I did this :-
sudo nano /etc/apt/sources.list
This was the result:-
  GNU nano 2.2.6          File: /etc/apt/sources.list                           

# deb cdrom:[Lubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric$

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) quantal main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) quantal-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) quantal universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) quantal universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) quantal-updates universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) quantal-updates universe

---

### Post by MickM on 2012-11-08
Since my last comment. I also have lubuntu 12.10 installed on my wife's Dell computer, which was installed 1 day after I did mine and we are able to do Software upgrades on the Dell.
So the problem rests with my installation on my Acer Aspire Notebook.

---

### Post by ibjsb4 on 2012-11-08
Your sources.list is ok.  Those two PPA's that are giving you trouble must be located in sources.list.d

Use the same command and change the last part to read sources.list.d

You can post it if you want, but all you need to do is comment out (#) the two URL's that are in your very first post so they will look like this:

#[http://ppa.launchpad.net/upubuntu-co...source/Sources](http://ppa.launchpad.net/upubuntu-co...source/Sources)
#[http://ppa.launchpad.net/upubuntu-co...-i386/Packages](http://ppa.launchpad.net/upubuntu-co...-i386/Packages)

And that should solve your problem  :)

---

### Post by MickM on 2012-11-13
Hi All
Thanks for all your help, however I could not solve the problem.
Today I again tried the Software Updater and guess what? the software updater worked and I was able to update everything.
It would seem that the Techies fixed the problem for us. Well done Techies.  :P

---

### Post by MickM on 2012-11-13
Problem is now solved.

---

### Post by quentinl on 2012-11-13
sudo apt-get update

---

