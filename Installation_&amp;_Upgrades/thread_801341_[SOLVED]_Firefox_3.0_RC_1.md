---
title: "[SOLVED] Firefox 3.0 RC 1"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by melenor on 2008-05-20
Allright i was wondering when this was going to be included in updates or if there was a script anywhere that would allow for it to be downloaded, or have Firefox 3.0 Beta 5 upgraded to Firefox 3.0 RC 1, because certain Add-Ons i use don't work in Beta 5 but work in RC 1, well they work in Beta 5 but they crash sometimes.
Thank You.

---

### Post by diegops on 2008-05-20
You can use this trick:

[http://blog.rosanegra.org/2008/05/20/how-to-install-firefox-3-rc1-on-ubuntu-hardy/](http://blog.rosanegra.org/2008/05/20/how-to-install-firefox-3-rc1-on-ubuntu-hardy/)

---

### Post by Bubba64 on 2008-05-20
> **melenor said:**
> Allright i was wondering when this was going to be included in updates or if there was a script anywhere that would allow for it to be downloaded, or have Firefox 3.0 Beta 5 upgraded to Firefox 3.0 RC 1, because certain Add-Ons i use don't work in Beta 5 but work in RC 1, well they work in Beta 5 but they crash sometimes.
Thank You.

Have you tried nightly tester tools in Mozilla add ons it will force add ons to work in Beta 5.
[https://addons.mozilla.org/en-US/firefox/search?q=nightly%20tester%20tools](https://addons.mozilla.org/en-US/firefox/search?q=nightly%20tester%20tools)
You can also download FF 3 latest from Mozilla if you want to check it out I downloaded to my desktop and the bookmarks and add ons were there but not the plugins from Beta 5.

---

### Post by corevette on 2008-05-20
Firefox 3 final should be coming out in the next couple coming weeks, and I'm pretty sure it will be included in [Ubuntu Hardy Heron 8.04.1]("https://wiki.ubuntu.com/HardyReleaseSchedule") (July'ish).

---

### Post by melenor on 2008-05-20
All right first, i just realized that i forgot to include the download link to Firefox 3 RC 1, so here it is, [http://www.mozilla.com/en-US/firefox/all-rc.html](http://www.mozilla.com/en-US/firefox/all-rc.html).
I tried that one link and it didn't seem to work. nothing happened and it didn't say anything about updating or upgradeing a program. 
I am kinda impatiant and can't wait for july, especially because the Firefox 3 Final version will come out end of June, meaning that i hope that Ubuntu 8.04.1 includes Firefox 3 Final not Firefox 3 RC 1. I have Nightly Tester Tools installed, even before this, but that doesn't take care of my problem.

---

### Post by melenor on 2008-05-20
Allright i got it to work by going to software resources and adding the online at [http://blog.rosanegra.org/2008/05/20/how-to-install-firefox-3-rc1-on-ubuntu-hardy/](http://blog.rosanegra.org/2008/05/20/how-to-install-firefox-3-rc1-on-ubuntu-hardy/) to a trusted site thing and this allowed me to get Firefox 3 RC 1.
But now i found out that many of my Add Ons that worked before now don't, and will have to find a work around o well.

---

### Post by z0mbie on 2008-05-20
> **melenor said:**
> Allright i got it to work by going to software resources and adding the online at [http://blog.rosanegra.org/2008/05/20/how-to-install-firefox-3-rc1-on-ubuntu-hardy/](http://blog.rosanegra.org/2008/05/20/how-to-install-firefox-3-rc1-on-ubuntu-hardy/) to a trusted site thing and this allowed me to get Firefox 3 RC 1.
But now i found out that many of my Add Ons that worked before now don't, and will have to find a work around o well.

Yeah it's true adding the following to the repos will give you the more upto date Firefox:
```
deb http://ppa.launchpad.net/fta/ubuntu hardy main
```

---

### Post by melenor on 2008-05-20
Allright i made a mistake trying to install firefox 3 RC 1 on unbuntu while on Windows it works great on ubuntu or at least my computer not so. I can no longer download anything and when i try to uninstall firefox 3.0 RC 1 and reinstall Firefox 3.0 Beta 5 i can't because it needs to uninstall xulrunner and to uninstall that i have to uninstall a bunch of stuff, is there a way to downgrade or use a restore point?

---

### Post by tad1073 on 2008-05-20
I am having the same problem.

---

### Post by Technoviking on 2008-05-21
I would suggest waiting for the Ubuntu devs to push out a new package. It will probably be next week after [UDS]("https://wiki.ubuntu.com/UDS-Intrepid") is over.

Mike

---

### Post by domness on 2008-05-21
Aww cheers for the link. I've been looking for this resource.

I tried installing it with the source but it completely failed.

Will try this when I get back home.

---

### Post by Raziel-chan on 2008-05-21
Does anyone know how to update the language packs? They are deemed as incompatible and indeed force-activating them breaks the browser.

The funny thing is that Firefox sees them even after I removed the locale in synaptic. >_>

cya
Raziel-chan

---

### Post by melenor on 2008-05-21
My biggest problem is that it crashes when ever i try to download something.

---

### Post by Raziel-chan on 2008-05-21
I dunno, I can download pretty much anything without any problems. Plus, this version seems to have the file handler system repaired and now it actually remembers my choices.

cya
Raziel-chan

---

### Post by melenor on 2008-05-21
Got everything working had to uninstall the dictonaries because they crashed, thanks everyone.

---

### Post by jonasbh on 2008-05-23
Here is a really good reason to wait for Ubuntu repo to be ready with Firefox. The distros will need to patch this bug:

[http://jasondclinton.livejournal.com/66509.html](http://jasondclinton.livejournal.com/66509.html)

---

### Post by melenor on 2008-05-23
just a side not but will that repo, actually always give you the more up to date one or just right now?

---

### Post by picpak on 2008-05-23
I can download just fine, but the language pack isn't working. My Google in the search bar is Spanish. :???:

---

### Post by melenor on 2008-05-23
The biggest diffculty i had was the langauge packs, uninstall all and just use the default for right now(which everlanguage you downloaded from, or your OS default.) only way, other then that works great.

---

### Post by Exsecrabilus on 2008-05-26
> **melenor said:**
> Allright i made a mistake trying to install firefox 3 RC 1 on unbuntu while on Windows it works great on ubuntu or at least my computer not so. I can no longer download anything and when i try to uninstall firefox 3.0 RC 1 and reinstall Firefox 3.0 Beta 5 i can't because it needs to uninstall xulrunner and to uninstall that i have to uninstall a bunch of stuff, is there a way to downgrade or use a restore point?
Try uninstalling Firefox 3 RC 1 first.

Then remove the APT line of the repository of where you got the RC.

Now RC should no longer be available in Synaptic and I think the only choice available is Firefox 3 Beta 5.

---

### Post by KeithX on 2008-05-27
> **jonasbh said:**
> Here is a really good reason to wait for Ubuntu repo to be ready with Firefox. The distros will need to patch this bug:

[http://jasondclinton.livejournal.com/66509.html](http://jasondclinton.livejournal.com/66509.html)

This issue is now shown as solved in RC2

---

### Post by melenor on 2008-05-27
Firefox 3.0 rc 2 has not been released yet.

---

### Post by Exsecrabilus on 2008-05-27
> **melenor said:**
> Firefox 3.0 rc 2 has not been released yet.
I think he meant Firefox 3 RC 1.....?

---

### Post by war59312 on 2008-05-29
I believe in fact he did mean RC2:

[https://bugzilla.mozilla.org/show_bug.cgi?id=421482](https://bugzilla.mozilla.org/show_bug.cgi?id=421482)

As you can see, its marked as having been fixed in RC2...

But yes not out yet of course, but yeah supposedly this bug is fixed in pre rc 2 builds, check out the nighties...

looks like rc2 will be released soon, if not next week:

[http://quality.mozilla.org/node/1664](http://quality.mozilla.org/node/1664)

seeing as "We hope to have RC2 build candidates on Friday and we will post the Download Link here and in the #testday Channel."

---

### Post by Exsecrabilus on 2008-05-29
> **war59312 said:**
> I believe in fact he did mean RC2:

[https://bugzilla.mozilla.org/show_bug.cgi?id=421482](https://bugzilla.mozilla.org/show_bug.cgi?id=421482)

As you can see, its marked as having been fixed in RC2...

But yes not out yet of course, but yeah supposedly this bug is fixed in pre rc 2 builds, check out the nighties...

looks like rc2 will be released soon, if not next week:

[http://quality.mozilla.org/node/1664](http://quality.mozilla.org/node/1664)

seeing as "We hope to have RC2 build candidates on Friday and we will post the Download Link here and in the #testday Channel."
No, he meant RC 2.

As you said yourself, RC 2 is in development, but not yet released.

---

### Post by stinger30au on 2008-05-29
> **z0mbie said:**
> Yeah it's true adding the following to the repos will give you the more upto date Firefox:
```
deb http://ppa.launchpad.net/fta/ubuntu hardy main
```


who owns these repos???? never heard of them before

---

### Post by fabertawe on 2008-05-30
rc1 is also available from Synaptic package manager if you enable the Hardy proposed repo, then it's authenticated.

---

### Post by melenor on 2008-05-31
Firefox 3.0 RC 2 should come out first week of june they announced, will it be avilable in the repos just as soon?

---

