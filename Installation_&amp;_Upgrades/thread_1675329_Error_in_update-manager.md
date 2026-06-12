---
title: "Error in update-manager"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by jredkai on 2011-01-25
Okay, when opening "Update-manager" I get this error:

 E:Malformed line 47 in source list /etc/apt/sources.list (dist parse)

What I was trying to do was update my Opera web browser, when I tried, Ubuntu told me that I was attempting to download from an unauthenticated source, I checked the software sources list and Opera was in there, so I deleted it and re-added it, I must have done it wrong because after closing out and refreshing "Update-manager"  it gave me the error above and closed. So now I can't update anything. And I do not know the fix for this.
Any help would be appreciated. Thx.

---

### Post by matt_symes on 2011-01-25
Hi

Open a terminal and type

```
cat /etc/apt/sources.list
```

Post the output back here between code tags.

Kind regards

---

### Post by jredkai on 2011-01-25
alright, I'm sorry I do not know what "code tags" are (now's when you shake your head and say "jeez,some people's kids") so I will improvise and just do this:

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates restricted main multiverse universe #Added by software-properties
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main #Third party developers repository
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable
deb-src [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable



Well, that's what I get when I put:" cat /etc/apt/sources.list " into the terminal. Hope this helps, and thx again.

---

### Post by matt_symes on 2011-01-25
Hi

> deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable
deb-src [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable

These are the two problem lines. Press ALT and F2 together and type

```
gksudo gedit /etc/apt/sources.list
```

to open sources.list with root privilages. Scroll down to the bottom and change the two lines so they look like...

> # deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable
# deb-src [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable

Notice the # and <space> in front of them. Save this file and close. I will have a look around for the correct sources for opera for you.

BTW: The code tags is the # button on the toolbar new you type a new message. It makes it much easier to read. 

You can also wrap the text you want in code tags with ```
 Using code tags gives you output that looks like this [/CODE**}** where the last **}** is actually a **]** (i need to fool the parser so i have to use } to demonstrate it to you). 

[CODE] Using code tags gives you output that looks like this 
```

Kind regards

---

### Post by jredkai on 2011-01-25
awesome, after using ```
 gksudo gedit /etc/apt/sources.list 
``` and editing the last two lines, I'm now able to open "update-manager"

Also thx Matt for the: [CODE] yadda yadda yadda [/CODE} 

I now feel like I'm progressing.

---

### Post by matt_symes on 2011-01-25
Hi

> What I was trying to do was update my Opera web browser, when I tried, Ubuntu told me that I was attempting to download from an unauthenticated source, ......

How did you try to update it before ? Can you tell me exactly what you did ? Include links if you were following a web page. Then we can get Opera updated for you.

Kind regards

---

### Post by jredkai on 2011-01-25
No I wasn't following links, I had opened my browser and saw there was an update available so I went to synaptic-manager and all it has is the previous version at the moment so I went to update-manager, refreshed it and saw that there was a new version of opera. So I clicked install and then it told me that I was trying to download from an unauthenticated source. I opened the settings tab in update-manager and looked at all the software sources and saw that opera was in other software as such: [http://deb.opera.com/opera/](http://deb.opera.com/opera/) So since I was getting the error as though opera wasn't in the list, I deleted it, in update-manager, and re-added it to the other software tab, then hit refresh in update-manager then I received the error, and was unable to open update-manager or do anything with it. That's pretty much it.

---

### Post by matt_symes on 2011-01-25
Hi

Right lets fix that opera entry in the sources.list file.

Press ALT and F2 and type

```
gksudo gedit /etc/apt/sources.list
```

change the last two lines

> # deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable
# deb-src [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable

to read

> deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free
deb-src [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free

and save the file. Open a terminal and type (Be careful get this correct. It's a captial letter O below)

```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
```

Enter your password when requested. After that type

```
sudo apt-get update
```

I believe that should fix it for you but if there are errors please post them back.

Kind regards

---

### Post by jredkai on 2011-01-25
Well, did as listed above and this is what I got: ```
 W: Failed to fetch http://deb.opera.com/opera/dists/stable/Release  Unable to find expected entry  non-free/source/Sources in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead. 
``` Unfortunately at this time I have to get to bed, I'm in Thailand and I'm at least 12 hours ahead of you and is now 12:48 a.m. so again thank you for your help and hopefully in the morning we can finally get this resolved. Good night everyone.

---

### Post by matt_symes on 2011-01-25
Hi

No problem. It was my fault. I checked the deb but not the deb-src entry. I assumed it would work for both.

Note to self: don't assume with software. :D

When you wake up comment out this line as you did before by putting a # and a space in front of it.

> deb-src [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free

becomes

> # deb-src [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free

then run

```
sudo apt-get update
```

Sleep well.

Kind regards

---

### Post by jredkai on 2011-01-25
Here is the sources.list file as requested: ```
jared@jared-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates restricted main multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates restricted main multiverse universe #Added by software-properties
deb http://extras.ubuntu.com/ubuntu maverick main #Third party developers repository
deb http://deb.opera.com/opera/ stable non-free
deb-src http://deb.opera.com/opera/ stable non-free

``` And now I will make my exit, btw Matt I had figured you were in the US and didn't know your in the UK, so to correct myself I'm 7 hours ahead :) .....anyway, thx and good night

---

### Post by matt_symes on 2011-01-25
Hi

When you wake up please re-read my last post (the one i posted before this one) as i have edited it with new instructions. 

Please follow those instructions tomorrow.

Kind regards

---

### Post by jredkai on 2011-01-25
> **matt_symes said:**
> Hi

No problem. It was my fault. I checked the deb but not the deb-src entry. I assumed it would work for both.

Note to self: don't assume with software. :D

When you wake up comment out this line as you did before by putting a # and a space in front of it.



becomes



then run

```
sudo apt-get update
```

Sleep well.

Kind regards

Awesome, this did it, thanks very much Matt. So problem solved.

---

### Post by jredkai on 2011-01-25
So now I don't know how to mark this thread SOLVED, so if someone now wants to school me on that simple matter then all be well.

---

### Post by sikander3786 on 2011-01-26
> **jredkai said:**
> So now I don't know how to mark this thread SOLVED, so if someone now wants to school me on that simple matter then all be well.
For marking the Thread Solved, use [COLOR="Red"]**Thread Tools**[/COLOR] near the top of this page.

Happy Ubuntu-ing!

---

### Post by dakkar9999 on 2011-03-22
Thanks Matt, fixed my problem!

---

