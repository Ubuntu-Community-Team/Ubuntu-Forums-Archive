---
title: "FireFox 3.0.3 Really Crashy?"
date: 2008-09-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by [Neurotic] on 2008-09-26
I just really wanted to check that everyone else's experience is similar to mine.

I find Firefox will crash at the drop of a hat.  Generally when I have more than 1 tab open.  In fact, the more tabs, you can practically guarantee it will crash.

Honestly, I can't wait for Google Chrome for Linux, as hopefully we will have a stable browser.

---

### Post by olskar on 2008-09-26
There was only on bugfix that is the difference between 3.0.3 and 3.0.2 I think, find it hard to believe that it is making it crash..or you had similar problems with 3.0.2?

---

### Post by oldsoundguy on 2008-09-26
you don't say if it is crashing while DOING something like running Flash.

Flash 9 is buggy in the first place .. but your choice is to go back to 8 or install the BETA of 10.  I chose the latter and no more problems in FF. (other than typing lagging, but I type very fast at times.)

---

### Post by [Neurotic] on 2008-09-26
I had similar problems with 3.0.2, but this seems worse.

I've disable all my extra add-ons, and that hasn't seemed to have helped at all. (I only had firebug and downloadthemall installed anyway).

I used to be able to open up ~30 tabs.. now I can barely managed to get to 4.

---

### Post by [Neurotic] on 2008-09-26
Generally, it seems pretty random when it crashes.

I have the up to date version of Flash that comes with Ibex installed (10.0.1.218+10.0.0.525ubuntu1).

I would love it if this was just a flash issue, and easily solvable.

---

### Post by Slug71 on 2008-09-26
Not having any issues with FF 3.0.3 here on AMD 64 Intrepid. Using the same version of Flash as you.
Runs a little slow but thats it.

---

### Post by ubulette on 2008-09-26
Please visit [https://wiki.ubuntu.com/MozillaTeam/Bugs](https://wiki.ubuntu.com/MozillaTeam/Bugs)
If this is related to nonfree-flash, there's not much Ubuntu can do.

Note: for backtraces, I've re-introduced the -g/--debug switch recently so on intrepid, the procedure for ff2 also work.

---

### Post by [Neurotic] on 2008-09-26
Thanks for the tip, I'm running under -g now, and will place any bugs that I can find.

---

### Post by nanog on 2008-09-26
> I would love it if this was just a flash issue, and easily solvable.

As if.

---

### Post by oldsoundguy on 2008-09-26
8 tabs open in Gutsy.  No problems.

---

### Post by Kow on 2008-09-26
I'm looking at the 1 change between firefox 3.0.2 and 3.0.3 and the only thing it will do is make firefox run better (or no different at all.)

---

### Post by mwolfe on 2008-09-30
I'm using 3.0.3 with hardy and lately it has been going miserably slow. Gmail is lagging like crazy, yahoo mail even worse, its barely usable. I'm using opera now and things are loading insanely faster.
I know firefox js engine is supposed to be really fast now but something is going on. I have firebug installed but its not enabled afaik for websites.. Perhaps there is a big in there that is slowign things down (gmail doesnt report firebug being on).
Other websites with intensive javascript or flash have been slow also like youtube.

---

### Post by bash on 2008-09-30
Running 8.10 64bit. Firefox crashes quite a few times or just turns grey but it is always related to the flash plugin. If I to open more then 3 or 4 tabs that have something with flash in it, it's bye bye flash player. Got really worse compared to Hardy 64bit.

---

### Post by plun on 2008-09-30
> **'[Neurotic] said:**
> 

I have the up to date version of Flash that comes with Ibex installed (10.0.1.218+10.0.0.525ubuntu1).

I would love it if this was just a flash issue, and easily solvable.

Well... 32 bit runs just fine on Adobes **Release Candidate** version.

EDIT about this RC version, NOT a beta
[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

30 to 35 % CPU playing a Flash video.

Users talks about "betas" for Adobes Flash but its a **RC candidate**. Nothing else.  Ubuntu uses an OLD beta from July

[http://changelogs.ubuntu.com/changelogs/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.0.1.218+10.0.0.525ubuntu1/changelog](http://changelogs.ubuntu.com/changelogs/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.0.1.218+10.0.0.525ubuntu1/changelog)

So I cannot understand why Ubuntu doesnt upgrade Adobe for 32 bit  :confused:


It will be a security hole... its just a matter of time...
[http://secunia.com/advisories/](http://secunia.com/advisories/)


Also Adblock Plus can be something good when visiting crazy commercial websites.

---

### Post by psyke83 on 2008-09-30
> **plun said:**
> So I cannot understand why Ubuntu doesnt upgrade Adobe for 32 bit  :confused:


It will be a security hole... its just a matter of time...
[http://secunia.com/advisories/](http://secunia.com/advisories/)

The flashplugin-nonfree package is architecture-agnostic, so they can't upload just for 32-bit users.

Once the 64-bit issues are resolved, we *will* get an update.

Here's the FFe request: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/257403](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/257403)

---

### Post by kansasnoob on 2008-09-30
Hmmmm, guess I'm lucky, Firefox and the non-free plugin from the repos have been working great for me in the 1386 version of Intrepid.

In fact the only problem I've had with Intrepid in a few days has been with the search feature in synaptic not working after using the "quick search" function. Simply closing and reopening synaptic gets it going again though so it's a minor inconvenience and I'm sure a fix is in the works.

---

### Post by shqip on 2008-09-30
> **'[Neurotic] said:**
> I just really wanted to check that everyone else's experience is similar to mine.

I find Firefox will crash at the drop of a hat.  Generally when I have more than 1 tab open.  In fact, the more tabs, you can practically guarantee it will crash.

Honestly, I can't wait for Google Chrome for Linux, as hopefully we will have a stable browser.
I have not notice any problem with fire fox on machines running Linux OS but I have notice a lot of crashes on machines running windows OS and my take on this is that Microsoft has done something to stop firefox becoming the most popular web browser because a lot of people started using firefox and it is taking over the market and Microsoft and others don't like that.

---

### Post by rbmorse on 2008-09-30
Mine's been good on IA-32 since I uninstaled libflashsupport.

Before that, it was pretty bad.

---

### Post by plun on 2008-09-30
> **psyke83 said:**
> The flashplugin-nonfree package is architecture-agnostic, so they can't upload just for 32-bit users.

Once the 64-bit issues are resolved, we *will* get an update.

Here's the FFe request: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/257403](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/257403)

Well, I am 100% sure that its possible.  

One download "wrapper" for 32 bit, another for 64 bit.

This causes just a mess with "whinings" about Firefox and Flash. 

There are bugs with the nVidia driver and slow scrolling for specific
models and its rather impossible to find correct bugs.

So IMHO it must be much better to ship or directly update 32 bit users
to avoid "whinings".

I can see it myself that the RC version is good...:D 


(Also that Gnash and Swfdec only can handle some basic flash)


If must be a focus on important issues...  instead of "politic"..

---

### Post by psyke83 on 2008-09-30
> **plun said:**
> Well, I am 100% sure that its possible.  

One download "wrapper" for 32 bit, another for 64 bit.

This causes just a mess with "whinings" about Firefox and Flash. 

There are bugs with the nVidia driver and slow scrolling for specific
models and its rather impossible to find correct bugs.

So IMHO it must be much better to ship or directly update 32 bit users
to avoid "whinings".

I can see it myself that the RC version is good...:D 


(Also that Gnash and Swfdec only can handle some basic flash)


If must be a focus on important issues...  instead of "politic"..

Is it really necessary to complicate things by splitting the package? The point of the development release is to iron out such issues, but you have to accept that some issues can take time.

The proper way to fix this is to get nspluginwrapper & ia32-libs updated properly, then roll out the update for everyone. There are some invasive changes necessary to ensure PulseAudio works for 32 bit users and it needs to be done properly. We're just a bit unlucky at the moment because of the beta freeze.

People will always complain no matter what ;).

---

### Post by bash on 2008-09-30
Going to try the flash version supplied in psyke83s archive. Lets see if that solves the insanely frequent crashes. Btw what does libflashsupport actually do? As far as I remember it was there to create "compability" with Pulseaudio. So putting it the other way round: If I uninstall it I'll have no more sound? Or is that assumption wrong.

---

### Post by BwackNinja on 2008-09-30
libflash support is not needed for flash 10

---

### Post by bash on 2008-09-30
Hmm ... I can't seem to get the Flash 10 RC running on Ibex 64bit. Tried psykes ppa but that didn't work. Tried downloading it manually and just linking it with nspluginwrapper. No luck with that either. 

Reverted back to Flash beta and the default nspluginwrapper. Now flash works again but still happy crashy.

---

### Post by ktp on 2008-09-30
> **bash said:**
> Hmm ... I can't seem to get the Flash 10 RC running on Ibex 64bit. Tried psykes ppa but that didn't work. Tried downloading it manually and just linking it with nspluginwrapper. No luck with that either. 

Reverted back to Flash beta and the default nspluginwrapper. Now flash works again but still happy crashy.

Are you running 64-bit?  If you are then there is issue where nspluginwrapper does not support windowless mode correctly.  You can disable windowless mode in the plugin itself by adding following to /etc/adobe/mms.cfg (you will have to create this file)
   WindowlessDisable=true

If you are on 32-bit, you don't need nspluginwrapper so remove it if you have it.

---

### Post by mwolfe on 2008-10-02
Well my problem is gone now. Since I have foxmarks plugin installed and i can get back my bookmarks, I decided to just wipe out the .mozilla directory in my home directory. Then I reinstalled the essential plugins I use and installed flash 9 from the adobe website,
Everything runs great again, very fast, and without the intermittent freezing i was constantly getting before.

---

### Post by bash on 2008-10-02
> **ktp said:**
> Are you running 64-bit?  If you are then there is issue where nspluginwrapper does not support windowless mode correctly.  You can disable windowless mode in the plugin itself by adding following to /etc/adobe/mms.cfg (you will have to create this file)
   WindowlessDisable=true

If you are on 32-bit, you don't need nspluginwrapper so remove it if you have it.

I'm running 64bit. I updated both Flashplugin and nspluginwrapper to the version provided in psykes PPA. But it didn't work for me. Whenever there was a flash applet just nothing showed. I'll try to disable windowless mode and see if that helps.

---

### Post by DavidONE on 2008-10-02
> **'[Neurotic] said:**
> I find Firefox will crash at the drop of a hat.  Generally when I have more than 1 tab open.  In fact, the more tabs, you can practically guarantee it will crash.

It's not Firefox - tens of thousands would be complaining if it were.  I run with dozens of tabs open and it's solid.

Create a new profile (disabling extensions is not enough) by:
```
firefox -profilemanager
```
Run with the new profile for a while.  If no crashes then start adding your extensions, one by one.  Test each one out on a page that you know crashed Firefox previously.

---

### Post by [Neurotic] on 2008-10-06
I just tried the new profile.

No go... open up multiple tabs, and it just goes boom.

I'm going to try upgrading flash manually, see if that makes a difference.

---

### Post by tweston on 2008-10-15
I disabled the Foxmarks add-on and that seems to have solved the problem for me.

---

