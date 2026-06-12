---
title: "Disappointed by the last Ubuntu's release."
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by iemand on 2006-11-16
Hi all, 

I've been using ubuntu since the first release of Breezy Badger. I can't remember exactly how long it represents. I think a bit more than a year. When Dapper went out, I upgraded and I've been really glad. Everything worked directly. No problem at all. And since, I've always updated my system when updates were available and I never had a problem.

Last week I saw that a new release is available. I upgraded first using 
```
update-manager -c 
```

I should never had launched this command. When it was complete, my Linux wouldn't boot at all. Even the terminal mode (init 3) didn't work. I could choose a system to launch in grub but only Windows XP was working. On all the others, I had something like the kernel is missing or whatever. 

I then tried a new clean installation. It worked but I noticed there is a lot of small problems. I guess it's only with me because I don't see many other people with the same problem as me. Problems I'm talking about are 
 - application that doesn't start. (right click on a file, open with and select an application, the application doesn't start).
 - unable to save my session. If I change my desktop background, n ext time I restart, the new desktop is back to a dark color.
 - often, gnome doesn't respond anymore. I have to restart X (CTRL + ALT + BACKSPACE).
 - everytime I start listen (a media player) I have a tooltip asking me if I'd like to send a bug report.

...

I'm really disappointed by this version of Ubuntu and I wanted to tell it. Now, as I don't want to reinstall my system again, I'm back on Windows until next release. I hope that these kind of problem will be fixed. 

I regret that I did this upgrade. I'm so disappointed because I had a really cool system on Dapper. Everything was so smooth on it and now, I tried something and praise I won't get an error.

See you

---

### Post by bulldog on 2006-11-16
Well sorry to read you have some bad luck,**but if it comforts you,you aren't alone in this**

If you had read some topic's at this forum you had known the update wasn't a peace of cake for every one.

What I don't understand is,if anyone got a good Ubuntu Dapper install and no probs with it,blindly updates without gathering some info about the new release.

So you shouldn't put all the blame on Ubuntu,you could have read up first,before you install anything.

But you're back on windows and I hope you'll come back some day to Ubuntu.

---

### Post by angkor on 2006-11-16
> **iemand said:**
> I'm really disappointed by this version of Ubuntu and I wanted to tell it. Now, as I don't want to reinstall my system again, I'm back on Windows until next release. I hope that these kind of problem will be fixed. 


I'm sorry you had bad luck with Edgy. I experience none of the problems you mentioned after upgrading from dapper. It impossible to say what could have been wrong with your install since you don't mention any errors.

Why are you back at windows? You can just reinstall Dapper and be a happy camper and try the next release to see if you like it better.

---

### Post by ciscosurfer on 2006-11-16
A fresh install is recommeded.

---

### Post by Henry Rayker on 2006-11-16
I always smash up some data, and do a fresh installation of the next version. That seems to save me from some headaches. If it is good, I move over after configuration is done; resize the partition as I switch. It may sound like a bunch of extra steps, but I've been burned by upgrades from version to version on too many applications (Firefox was a BIG enemy of mine for this).

Additionally, it was well documented, IMO, that Edgy is an experimental, more bleeding edge (read: newer, but potentially less stable) release. That is the purpose of the LTS versions...if you want stability, jump from LTS to LTS, if you want the newest apps, jump from one version to the next.

---

### Post by iemand on 2006-11-16
I never had a problem when I use the update-manager (each time an update is available I receive a tooltip; click on it and two minutes after my system is up2date). 
Why this time should be different? Why this time nothing worked after?  It happen to me to update the kernel using the update manager and it worked fine...

I thought, "I never had a problem doing the updates, so why not updating, I don't risk anything". 

And by the way, I don't blame Ubuntu. Ubuntu is free and no one force me to use it. I actually like the way we can personalize it and its ease of use.

I'm looking forward for a new release soon. I don't want to spend my time installing all my stuff, doing all the changes again and again. 


[And just if you wanna know, what you told me doesn't comfort me. It makes me thing that developers did (this time) a quick and dirty work. I may be wrong :-)]

---

### Post by iemand on 2006-11-16
> **angkor said:**
> I'm sorry you had bad luck with Edgy. I experience none of the problems you mentioned after upgrading from dapper. It impossible to say what could have been wrong with your install since you don't mention any errors.

Why are you back at windows? You can just reinstall Dapper and be a happy camper and try the next release to see if you like it better.

Why am I back at windows? Because I have something to do quickly and I don't have the time reconfiguring a new Dapper installation. I'm not an expert at Linux and it takes me time to do a full installation. (flash, adobe acrobat, gs, LaTeX, java, ...) 

On Dapper I did it step by step when I needed it. Now, I need everything for the moment.

---

### Post by iemand on 2006-11-16
> **ciscosurfer said:**
> A fresh install is recommeded.

That's what I did, but I met lots of problem with Gnome and the graphical interface in general.

---

### Post by iemand on 2006-11-16
> **Henry Rayker said:**
> Additionally, it was well documented, IMO, that Edgy is an experimental, more bleeding edge (read: newer, but potentially less stable) release. That is the purpose of the LTS versions...if you want stability, jump from LTS to LTS, if you want the newest apps, jump from one version to the next.


Well, I didn't know that before. So I'll wait until the next LTS or reinstall Dapper. :-)

---

### Post by Henry Rayker on 2006-11-16
EDIT: Didn't see your response to me until after I posted. I thought your other response was to me.

> **iemand said:**
> [And just if you wanna know, what you told me doesn't comfort me. It makes me thing that developers did (this time) a quick and dirty work. I may be wrong :-)]

Well, the fact of the matter is, they can't put out a super stable version every single release. Breezy was the release before the LTS Dapper. Dapper was a step up in stability (after that initial hiccup, I guess).

The information was out there; no one said, "Come to Edgy! It's more stable than Dapper!!" The general concensus seemed to be, "If you want stability, wait this one out! Only update if you've got little to lose or you don't mind trying to work it out."

There are 3 stages of users, I'd say. Which mirror the three stages of software development I see in Ubuntu.

The first group don't mind breaking their entire system and upgrade to the test versions as soon as they're released. They have the latest and greatest packages. (These are the more alpha users)

The second group is a little more cautious and only upgrades to the "completed" versions. They risk a little bit, but it's okay because they get some newer packages out of it. (Beta users)

The third want stability over everything else. They should jump from LTS version to LTS version (and possibly even wait after each LTS is released to make sure the changes are all ironed out.) (Final release users)

I don't think they "rushed" their code at all. They have a fairly strict release schedule; if they didn't start off fairly unstable in the beginning, there wouldn't be much work to do in the end.

---

### Post by bulldog on 2006-11-16
And there are users who install Edgy next to Dapper,when things go wrong,just fire up Dapper and no worry's :D 

Dapper was my first Ubuntu release and I did the upgrade myself and broke Dapper.

Wise as I am :D ,I reinstalled Dapper and made a different partition for a clean Edgy install.

After some trouble getting all the things to work,I have to say,Edgy runs very well and I don't use Dapper anymore.

Will wait for a month or two,but I think I remove Dapper.

---

### Post by iemand on 2006-11-16
Henry Rayker, I am definitely a member of your third group :-)
This upgrade pissed me off because I spent so much time on it and in the end... nothing. 

I'll be wiser next time. When I'll see an update is available I wont click like a dumb and I won't do upgrade to new releases either.

bulldog, I wish I had time to reinstall everything. But as I am a student, I can't afford spending my time. I have some homework and strict deadlines.

I miss some of my tools now (TeXniCenter, listen...).

---

### Post by earobinson on 2006-11-16
Lots of pepople where, we can only hope to improve next time.

---

### Post by iemand on 2006-11-16
> **earobinson said:**
> Lots of pepople where, we can only hope to improve next time.

So do I :-)
What will be will be :D

---

