---
title: "held packages"
date: 2009-12-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by darco on 2009-12-20
Can someone confirm that these packages are still being held back? I have seen these packages for awhile now when I run the update-manager and wondering if its just me or what..thxs

```
 The following packages have been kept back:
  capplets-data compiz-core compiz-gnome compiz-plugins empathy evolution 
  evolution-common evolution-indicator evolution-plugins gdm 
  gnome-control-center libgnome-window-settings1 libgnomekbd4 metacity 
  python-apport python-launchpadlib python-wadllib 

``` 


darco

---

### Post by ranch hand on 2009-12-20
Just ran "sudo apt-get update" and "sudo apt-get upgrade".   Got;
> 
The following packages have been kept back:
  empathy

Your meathod of updating may be different.

---

### Post by bennachie on 2009-12-20
They seem to have disappeared after the most recent update.

---

### Post by darco on 2009-12-20
Then what is the best way to update? I just ran sudo aptitude safe-upgrade and thats what it showed me. I know Ranch Hand isnt a fan of the "update mangler" way. So how should I update?

thxs

---

### Post by hikaricore on 2009-12-20
I always used dist-upgrade on bleeding edge releases myself.
I take a quick look at the packages before proceeding and if it's not going to break anything that i can clearly see I go for it.

Packages that are still held back are as such because they have unmet dependencies usually due to versioning.

---

### Post by ranch hand on 2009-12-20
You can use UM at your own risk.  Read the sticky very carefully before you do it.

I think that the way you are doing it is probably the safest.  I use apt and it lets more stuff through than the " sudo aptitude safe-upgrade" route.

I do not know what, seeing as you use aptitude, what just" upgrade would do.  It is goingto let more through but I don't know if it would be the same as apt.

Synaptic lets through more stuff than apt but is safer than UM.  I like it if I want a particular thing but not the rest as you can mark them one at a time and see what it will do before you hit apply.

If you high light an entry in synaptid and go to Package>Download Changelog you get a bunch of information to help decide if you want to risk it or not.

---

### Post by ranch hand on 2009-12-20
> **hikaricore said:**
> I always used dist-upgrade on bleeding edge releases myself.
I take a quick look at the packages before proceeding and if it's not going to break anything that i can clearly see I go for it.

Packages that are still held back are as such because they have unmet dependencies usually due to versioning.
I do that on one of my 4 installs.  It is exciting.  You stay up to date.  You also get more breakage.

I am using this install, Lounge Lizard, as my production OS.  Anything important is also stored in a separate partition.  But there is on way I am funning a "dist-upgrade" here with out trying it on the other 3 first to see if they break.

After breakage occures, on any of these buggers, it gets a "dist-upgrade" everyday until it;
A>works
B>dies an ugly death

B happened a couple of times last round.

---

### Post by darco on 2009-12-20
This is what I got after running update....

```
sudo apt-get upgrade
[sudo] password for lucid: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  capplets-data compiz-core compiz-gnome compiz-plugins empathy evolution
  evolution-common evolution-indicator evolution-plugins gdm
  gnome-control-center libgnome-window-settings1 libgnomekbd4 metacity
  python-apport python-launchpadlib python-wadllib
The following packages will be upgraded:
  at-spi libatspi1.0-0 python-pyatspi
3 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
Need to get 333kB of archives.
After this operation, 32.8kB disk space will be freed.
 
```

---

### Post by ranch hand on 2009-12-20
Those are the same ones that I got updated.  I do not know why theothers are held back.

Empathy has been for a while.

The thing is that your system is holding them back for some reason.  Probably dependencies are not met.

I would not worry about it too much.  Ride it out.  they will come along some time.

Or you could do a "dist-upgrade" and probably find out in a hurry why they were held back.  If it is your only install of the Lizard (10.04) I would not risk it.

---

### Post by darco on 2009-12-20
ok, I did the dist-upgrade and all is well...empathy still held back.


```
The following packages will be REMOVED:
  evolution-documentation-en libgnomekbdui4 libmetacity0
  python-lazr-restfulclient python-lazr-uri usplash usplash-theme-ubuntu
The following NEW packages will be installed:
  libmetacity-private0 python-lazr.restfulclient python-lazr.uri
The following packages have been kept back:
  empathy
The following packages will be upgraded:
  capplets-data compiz-core compiz-gnome compiz-plugins evolution
  evolution-common evolution-indicator evolution-plugins gdm
  gnome-control-center libgnome-window-settings1 libgnomekbd4 metacity
  python-apport python-launchpadlib python-wadllib
16 upgraded, 3 newly installed, 7 to remove and 1 not upgraded.
Need to get 9,536kB of archives. 
```

thxs

---

### Post by ranch hand on 2009-12-20
You are still up and running I take it.

Everything install without error?

---

### Post by darco on 2009-12-20
Yes, all updated just fine,no issues....I am running the latest kernel .32-9 and running the beta nvida driver...195.22.
I truly am tempting the alpha gods!

---

### Post by ranch hand on 2009-12-20
That is where the FUN is.

---

