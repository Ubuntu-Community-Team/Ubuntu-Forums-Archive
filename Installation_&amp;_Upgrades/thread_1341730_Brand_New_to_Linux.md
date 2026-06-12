---
title: "Brand New to Linux"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by robertmarchiselli on 2009-11-30
I'll start this post by stating I've never used Linux in my life.  Second I'll state that all I'm looking for is the most simple, brief instructions on doing what I'm looking to do, and/or any extra advice or tips. Basically I've never used Linux before and I got bored with running the Windows 7 Beta and didn't plan on using it until it expired for me in April. What I'm looking to do is find the most efficient way to get back to playing World of Warcraft and having Ventrilo working how it did on Windows. I've looked around and noticed I'll at least need Wine, the World of Warcraft files, and the Ventrilo files. 

Right now I am running a completely updated copy of Ubuntu 9.1 which I have spent all day upgrading to from the Ubuntu 8.1 Live CD I order back in March or so. My steps for such were to upgrade 8.1 fully, then upgrade to 9.0.4 fully, and then I upgraded to 9.1. So, yes, all I have right now is a fresh install.

I've tried installing Wine through the "Ubuntu Software Center", however I am clearly missing multiple dependencies. In addition, I'm missing many dependencies OF dependencies.


Basically if someone can provide me some brief explanation as to how to acquire everything I need to run World of Warcraft: Wrath of the Lich King and the latest Ventrilo Client, that would be really awesome.


If not, at least a list of all dependencies I need would be awesome.



Thanks,
Robert

---

### Post by earthpigg on 2009-11-30
well, to be brutally honest...

an OS 'upgrade' from ubuntu X to ubuntu X+3 is no more reliable than an 'upgrade' from Windows 98 to Windows Vista Ultimate (ie: horrible idea).

download ubuntu 9.10 and do a *fresh* install of that.

and then, we will go from there.

you can use your current ubuntu install to burn the 9.10 .iso onto a CD-R at the lowest speed possible (thus helping ensure reliability of the CD itself).

---

### Post by earthpigg on 2009-11-30
and if your primary goal is to play Wow and vent?

well, those are both windows programs.... any reason you aren't just using what you have until it expires in april, and hoping you come across an install CD of any version of windows in the mean-time? (xp, vista, 7)

Microsoft Windows is the best Operating System to run non-free and immoral software intended to run on Microsoft Windows.

---

### Post by robertmarchiselli on 2009-11-30
I... ugh.


I wanted a OS change. It's just a personal preference. Is it really going to be horrible running World of Warcraft in Wine? Also, /facepalm regarding the upgrade from 8.1 to 9.1! FML

---

### Post by earthpigg on 2009-11-30
WoW and Vent run fine in WINE. eventually.

eventually.

...WINE is ok for folks willing to invest themselves into Linux. Like me, and some others.

but as a replacement for the MS Windows Video Game Platform? 

no. MS Windows is for people that want to use MS Windows and MS Windows software, and are willing to pay the price (both in terms of personal freedoms and dollars).

this is my personal opinion. ask 500 people, and you will get 500 vastly different opinions.





The Best Video Game Console Platform that Exists is Microsoft Windows.

(though i think it kind of sucks for anything and everything else. again, my personal and fallible opinion.)

---

### Post by robertmarchiselli on 2009-11-30
I'd still like to attempt to try Linux. I'm open to -new- things.

So...

What dependencies do I need? >_<

---

### Post by lidex on 2009-11-30
You may find this of assistance:
[https://help.ubuntu.com/community/WorldofWarcraft]("https://help.ubuntu.com/community/WorldofWarcraft")
and this:
[https://help.ubuntu.com/community/Wine]("https://help.ubuntu.com/community/Wine")

---

### Post by robertmarchiselli on 2009-11-30
> **lidex said:**
> You may find this of assistance:
[https://help.ubuntu.com/community/WorldofWarcraft]("https://help.ubuntu.com/community/WorldofWarcraft")

Thank you very much! Skimming over that, it seems to be what I need. I'll check it out!


Also, might be a bit of a dumb question, but I currently only have blank DVD's available to me. They are rather large I'd say (3.7gigs, up to x16 write speed) and I'm not sure if they would work. Below I attached a pic of my settings for burning with my drive. I can burn at either x16, x12, x8, or x4. 

Would I fail attempting to write the ISO at any of these speeds to my DVD disk? I already did the hash check as suggested in the burning guide and that's good to go.

The main question here is (yeah, I'm terrible at making a point):

If I *could* succeed at burning the ISO through Ubuntu to this DVD disk, what speed would I write it at, and what are the actual chances of it working 100%?


Again, thanks!

---

### Post by jrrader on 2009-11-30
DVD could work.  I think my first install was from a DVD (because I didn't have CDs at the time).  Burn slow, x4.

---

### Post by Grenage on 2009-11-30
> If I *could* succeed at burning the ISO through Ubuntu to this DVD disk, what speed would I write it at, and what are the actual chances of it working 100%?

I burn all my disks at maximum speed, and I have never had a problem; some people do, but they are in the minority.  People that *do* need to write at a low speed either have bad disks and/or a bad writer.

Just burn it at default speed.

---

### Post by scorp123 on 2009-11-30
> **robertmarchiselli said:**
>  /facepalm regarding the upgrade from 8.1 to 9.1! FML No idea what the guy is talking about. My wife's PC was last installed in 2006 ... And I've been doing upgrades ever since. Ubuntu 6.06 => 6.10 => 7.04 => 7.10 => 8.04 => 8.10 => 9.04 => 9.10

If you read the instructions and avoid hard-to-upgrade packages from obscure third-party repositories it will "just work".

---

### Post by robertmarchiselli on 2009-11-30
Alright, I started it at x16 which was what the option was set to right when I popped the disk in. I only have one extra disk after this, so wish me luck! >_<

And yeah, if can't tell, I'm clueless when it comes to much anything regarding hardware.

---

### Post by robertmarchiselli on 2009-11-30
> **scorp123 said:**
> No idea what the guy is talking about. My wife's PC was last installed in 2006 ... And I've been doing upgrades ever since. Ubuntu 6.06 => 6.10 => 7.04 => 7.10 => 8.04 => 8.10 => 9.04 => 9.10

If you read the instructions and avoid hard-to-upgrade packages from obscure third-party repositories it will "just work".


This might be comical or I might sound stupid, but I'm inclined to believe you because you have more forum "beans".

I'm going to burn this CD anyways, but I'm missing a lot of dependencies still...? 


-__-





robert@robert-desktop:~$ glxinfo | grep rendering
direct rendering: Yes
robert@robert-desktop:~$ sudo apt-get install wine1.2
[sudo] password for robert: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine1.2: Depends: libmpg123-0 (>= 1.6.2) but it is not installable
           Depends: libopenal1 but it is not installable
           Recommends: ttf-mscorefonts-installer but it is not going to be installed
E: Broken packages
robert@robert-desktop:~$ 



^ there's a big chunk of goodness.

---

### Post by lidex on 2009-11-30
run this command in a terminal:
```
sudo dpkg --configure -a
```

Make sure you have multiverse repository enabled in "System>Administration>Software Sources". I would just check off all the boxes on the "Ubuntu Software" tab.

Now run these commands, one line at a time:
```
sudo apt-get update
sudo apt-get upgrade
```

Try again or use synaptic to install the version in your repositories.

---

### Post by scorp123 on 2009-11-30
> **robertmarchiselli said:**
>  but I'm missing a lot of dependencies still...?  Depends on how you upgraded. Since you're new I will assume that you used the "Update Manager" GUI?

That one has one hell of a nasty habit: It **disables** all third-party repositories **without re-enabling** them after the upgrade.

What this means for you is this:

Your repositories are stored in these locations:
**/etc/apt/sources.list**  .... a file
**/etc/apt/sources.list.d/**  ... a directory, possibly containing other ***blablabla-something.list*** files 

What you could do is to check these locations for disabled repositories.

Let's open **/etc/apt/sources.list** ... that's the main list. Please type this into a terminal (*Applications > Accessories > Terminal* ...):
```
gksudo gedit /etc/apt/sources.list
``` ... when it asks for a password -- that's your own password.

This is what my file looks like -- your's may look similar, depending on what continent you live you will probably have different Ubuntu mirror servers listed:
```

[B]deb http://ch.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://ch.archive.ubuntu.com/ubuntu/ karmic main restricted[/B]

## Major bug fix updates produced after the final release of the
## distribution.
[B]deb http://ch.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://ch.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
[/B]
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
[B]deb http://ch.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://ch.archive.ubuntu.com/ubuntu/ karmic universe
deb http://ch.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://ch.archive.ubuntu.com/ubuntu/ karmic-updates universe
[/B]
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
[B]deb http://ch.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://ch.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
[/B]
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
[B]deb http://ch.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
[/B]
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
[B]deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
[/B]
```

Please make sure that there is no comment sign **#** in front of any line that says "**deb** *bla bla bla something*" ... If there is a comment sign **#** in front of such a line it would mean that the line is disabled .... Taaddaaaaa. That's how you get dependency problems.

B Please make sure that each and every "deb" line says something about **karmic** .... and not anything about other Ubuntu releases. Mixing repositories from different Ubuntu releases is a BAD IDEA ... don't do it.

So ... you've cleared the main list. You will have to repeat this step for each file underneath this location **/etc/apt/sources.list.d/**
```
gksudo gedit /etc/apt/sources.list.d/whatever-the-name.list
gksudo gedit /etc/apt/sources.list.d/maybe-some-other.list
```

Those would be third-party repositories. There is a slight chance that those might still be pointing to older Ubuntu releases. So maybe you had e.g. the Medibuntu repositories active (e.g. to get more and better multimedia codecs Ubuntu can't ship with for licensing reasons? --- and please note: **this is just an example!**), so maybe your "**medibuntu.list**" (**again: just an example!!**) file now looks like this:
```

**[COLOR="Red"]##[/COLOR]** deb http://packages.medibuntu.org/ **[COLOR="Red"]jaunty[/COLOR]** free non-free
**[COLOR="Red"]##[/COLOR]** deb-src http://packages.medibuntu.org/ **[COLOR="Red"]jaunty[/COLOR]** free non-free
```

I highlighted the problematic stuff in **[COLOR="Red"]red.[/COLOR]**

So we have two problems up there: The repository is disabled. And it's still pointing to "*jaunty*" ... and not to "*karmic*" as it should.

So that's something you will have to look out for. Disabled lists + repo *.list files pointing to the wrong distributions. **It's easy to fix.** But I honestly wish the stupid Update Manager did that itself.

Last step:

Once you have all the *.list files corrected and are 100% sure that all is OK now, have "apt" update its list so it knows again where to get what package from:
```
sudo apt-get update
```


Last but not least ... You said you wanted WINE. I myself have found odd bugs in the WINE release that is in the Karmic repositories. Instead I use an inofficial version that's newer than what's officially available. Detailed instructions on how to get that version are here:

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

You can simply open the "Software Sources" manager (***System > Administration > Software Sources*** ...) and then add this string as new repository:  **ppa:ubuntu-wine/ppa**

Voila ... from here onwards your system will know where to get the newest WINE version from.

---

### Post by robertmarchiselli on 2009-11-30
Holy crap. Alright, I did all that. However, I've opted to try to latest Wine version for now. I'm actually, somehow, at the WoW: WotLK patch screen right now. O_O

I skipped the whole confusing part and just right-clicked the .exe installer on my desktop. It had an option called "Start in Wine" or something rather, so I did.

20mb out of 6.5gigs to go!

Yay! Thanks guys.




On another note, regarding Ventrilo, I came across Mangler ([http://www.mangler.org/](http://www.mangler.org/)), a Linux-based client that can connect to Ventrilo 3+ servers. 


Can anyone verify that this will work on Ubuntu 9.1 for me? :)

---

### Post by lidex on 2009-11-30
> **scorp123 said:**
> Depends on how you upgraded. Since you're new I will assume that you used the "Update Manager" GUI?

That one has one hell of a nasty habit: It **disables** all third-party repositories **without re-enabling** them after the upgrade...*snip*...

As they say on the "Family Feud" -- Good Answer!

---

