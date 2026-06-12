---
title: "Packagekit Help"
date: 2009-07-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Hairy_Palms on 2009-07-09
i want to try packagekit, but no matter what i do the list in gpk-application is totally empty, does anyone know what the problem is?

EDIT 
just mention ive got the version from the PPA

---

### Post by gnomeuser on 2009-07-09
For Karmic please do not use PK from any PPA, it's in the repos in a recent version.

---

### Post by Hairy_Palms on 2009-07-09
right, same problem with the repo version now,was actually using the repo version anyway it turns out as it was a later version, any ideas?

---

### Post by Slug71 on 2009-07-09
Im having issues with PK as well. Having you tried using the search? The search works for me but there is no list for me under the search. I cant seems to update with PK either. I get an internal system error while trying to fetch updates. Ubuntu PK integration really sucks.

---

### Post by Slug71 on 2009-07-09
I also removed the apt backend for PK and installed the smart one and nothing happens in PK now. Smartpm should still be using the apt-deb repos with PK as the frontend??

---

### Post by Hairy_Palms on 2009-07-09
theres nothing when i search either, installing the smart backend didnt work, it just isnt finding any packages, gpk-repo isnt listing anything so the problem seems to be the backend isnt seeing any of ubuntus repositories

---

### Post by rockin_goliath on 2009-07-09
does anyone know if PackageKit will be included in the final version of Karmic? I was wondering because if it is seriously being considered for inclusion, then I will start testing it. If it has already been put off to another release, then I won't bother.

---

### Post by Hairy_Palms on 2009-07-09
after some looking into it i tried to run
> sudo update-packagekit-app-data

which gave me an error about

> Generating mime/codec maps...
bad .desktop file: /usr/share/app-install/desktop/pauker.desktop: ParsingError in file '/usr/share/app-install/desktop/pauker.desktop', [Desktop Entry]-Header missing


deleting pauker.desktop didnt fix anything, the command now finishes silently but packagekit is still empty of any software.

---

### Post by ranch hand on 2009-07-09
Sounds fairly normal for Packagekit to me.

---

### Post by Slug71 on 2009-07-09
> **rockin_goliath said:**
> does anyone know if PackageKit will be included in the final version of Karmic? I was wondering because if it is seriously being considered for inclusion, then I will start testing it. If it has already been put off to another release, then I won't bother.

PK has been dropped for Ubuntu altogether in favour of AppCenter.

---

### Post by Slug71 on 2009-07-09
> **Hairy_Palms said:**
> after some looking into it i tried to run


which gave me an error about



deleting pauker.desktop didnt fix anything, the command now finishes silently but packagekit is still empty of any software.

Time to file some bugs i guess.

> **ranch hand said:**
> Sounds fairly normal for Packagekit to me.

I really think it comes down to PK with Ubuntu because this release seems to work pretty well with Fedora and Foresight.

---

### Post by Slug71 on 2009-07-10
Ive had quite a few 'An internal system error has occured' when trying to update with PK or even trying to use Add/Remove.

Bug has been filed, Bug #393726.


Have also filed a bug for the missing list in the box PK add/remove has with Ubuntu, on the lefthand side under the search box and above the help button. Which really improves the function of PK. 

Bug #397688

---

### Post by Twitch6000 on 2009-07-10
> **Slug71 said:**
> PK has been dropped for Ubuntu altogether in favour of AppCenter.

Uhmm AppCenter is a frontend for PackageKit...Infact on the blog where they discussed this matter they said they will be using packagekit for somethings aswell...

---

### Post by gnomeuser on 2009-07-10
> **Twitch6000 said:**
> Uhmm AppCenter is a frontend for PackageKit...Infact on the blog where they discussed this matter they said they will be using packagekit for somethings aswell...

ergh no mpt has been fairly clear on the matter, going so far as to directly mocking the advantages of PK.

Deeply disappointing and frustrating yes, but that is the Ubuntu way. If it is not invented here, it gets rewritten, just look at what happened with plymouth. Also now being replaced with an Ubuntu specific boot frontend. This behavior is by far what I hate the most about Ubuntu.

So no, you should not expect PackageKit in Karmic or ever. That is as clear as it can be expressed.

---

### Post by Hairy_Palms on 2009-07-10
> ergh no mpt has been fairly clear on the matter, going so far as to directly mocking the advantages of PK.

Deeply disappointing and frustrating yes, but that is the Ubuntu way. If it is not invented here, it gets rewritten, just look at what happened with plymouth. Also now being replaced with an Ubuntu specific boot frontend. This behavior is by far what I hate the most about Ubuntu.

So no, you should not expect PackageKit in Karmic or ever. That is as clear as it can be expressed.

wait, they arent gonna use plymouth ever, i thought it was just not gonna be in karmic? :/ i dont really have any info but i cant see how that makes sense.....

appcenter i can partly understand, simply because add/remove programs functions pretty well already, even if it is dog slow and lacks granularity, but plymouth is out and works, surely improving that would make far more sense.

---

### Post by Hairy_Palms on 2009-07-10
las post I made was offtopic in my own thread lol, but noone knows how to fix my packagekit?

---

### Post by seeker5528 on 2009-07-10
Don't know about the Gnome front end, but KPackageKit seems to be working.

At least it lets me choose from some groups and displays the relevant packages, and is able to show me the changelogs for the listed packages, seems to be only the most recent change though. The 'All Packages' view seems to have a problem. Have not tried to install anything with it, looks like it should do the job in a stable OS situation, but pretty sparse compared to Synaptic, so I'm a little hesitant during the development cycle. May have to fit it in on some days, after checking in Synaptic to see what shows up as new.

Later, Seeker

---

### Post by Hairy_Palms on 2009-07-11
frontend doesnt seem to matter, after installing kpackagekit(and the half of KDE it pulled in) its empty as well, it seems to be a core packagekit problem, not a frontend issue

---

### Post by Slug71 on 2009-07-11
> **Hairy_Palms said:**
> frontend doesnt seem to matter, after installing kpackagekit(and the half of KDE it pulled in) its empty as well, it seems to be a core packagekit problem, not a frontend issue

Yeh something is definitely up with it. Hopefully there will be a fix for it soon.

---

### Post by golusweet on 2009-07-11
> **gnomeuser said:**
> ergh no mpt has been fairly clear on the matter, going so far as to directly mocking the advantages of PK.

Deeply disappointing and frustrating yes, but that is the Ubuntu way. If it is not invented here, it gets rewritten, just look at what happened with plymouth. Also now being replaced with an Ubuntu specific boot frontend. This behavior is by far what I hate the most about Ubuntu.

So no, you should not expect PackageKit in Karmic or ever. That is as clear as it can be expressed.


I don't really care about packagekit. I would say, Appcentre would make easy for newbies to install and remove software. They won't have to deal with different managers.

plymouth should have been in karmic, I know, They did not choose cause of boot time. Even, 20 secs boot time is also not bad. 

But again, It's okay. I'm looking forward to karmic.

---

### Post by seeker5528 on 2009-07-11
> **Hairy_Palms said:**
> frontend doesnt seem to matter, after installing kpackagekit(and the half of KDE it pulled in) its empty as well, it seems to be a core packagekit problem, not a frontend issue

I didn't do anything to configure any packagekit stuff, it just works for me.

The was an indication earlier in the thread about it not working with the smart backend, which shouldn't get installed by default, but may be worth checking to see if packagekit-backend-apt is installed or if packagekit-backend-smart is installed.

Just installed gnome front end and it works for me too.

I'm not really seeing the point of these for general package management.

The specialized stuff is cool, the codec installer, browser plugin installer, updates, etc... If there was an add/remove software thing that actually showed things in terms of software instead of packages, that might be cool, but when you actually want a more complete package management type of interface, the current offerings are pretty anemic. All the confusion of having every package listed, but none of the additional features you might expect from a package manager these days. Like Synaptic for example has pinning, limited ability to try dealing with broken packages (sometimes it works without having to resort to the command line), a limited ability to force downgrades, ability to view dependencies/dependents, see where the files of installed packages were installed to, etc...

Later, Seeker

---

### Post by Slug71 on 2009-07-12
> **seeker5528 said:**
> I didn't do anything to configure any packagekit stuff, it just works for me.

The was an indication earlier in the thread about it not working with the smart backend, which shouldn't get installed by default, but may be worth checking to see if packagekit-backend-apt is installed or if packagekit-backend-smart is installed.

Just installed gnome front end and it works for me too.

I'm not really seeing the point of these for general package management.

The specialized stuff is cool, the codec installer, browser plugin installer, updates, etc... If there was an add/remove software thing that actually showed things in terms of software instead of packages, that might be cool, but when you actually want a more complete package management type of interface, the current offerings are pretty anemic. All the confusion of having every package listed, but none of the additional features you might expect from a package manager these days. Like Synaptic for example has pinning, limited ability to try dealing with broken packages (sometimes it works without having to resort to the command line), a limited ability to force downgrades, ability to view dependencies/dependents, see where the files of installed packages were installed to, etc...

Later, Seeker

Well thats why its important to have a more standardized package management system in Linux.

Eg. Packagekit's Sources list cannot be edited like Synaptic's because PK isnt distro specific. If however all Distros used the same backend like Smart Package Manager with PK then that could happen. The possibilties for PK would then be endless. Plus you'd only need to know a single set of commands for terminal usage regardless of which Distro you were using.

Thats the main reason i am against AppCenter. The tools needed to make this happen are there. Canonical funds the Smart Package Management system and Mandriva did so before Canonical. 

Most of the flaming PK gets probably wouldnt happen if it worked  properly with Ubuntu either.

---

### Post by ranch hand on 2009-07-12
> **Slug71 said:**
> Well thats why its important to have a more standardized package management system in Linux.

Eg. Packagekit's Sources list cannot be edited like Synaptic's because PK isnt distro specific. If however all Distros used the same backend like Smart Package Manager with PK then that could happen. The possibilties for PK would then be endless. Plus you'd only need to know a single set of commands for terminal usage regardless of which Distro you were using.

Thats the main reason i am against AppCenter. The tools needed to make this happen are there. Canonical funds the Smart Package Management system and Mandriva did so before Canonical. 

Most of the flaming PK gets probably wouldnt happen if it worked  properly with Ubuntu either.
If toads had wings they wouldn't be bumping their butts all the time either.

---

### Post by Hairy_Palms on 2009-07-12
> If toads had wings they wouldn't be bumping their butts all the time either.

I concur

---

