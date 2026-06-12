---
title: "Firefox 3.1 coming soon"
date: 2008-11-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ccw on 2008-11-28
[https://launchpad.net/ubuntu/jaunty/+source/firefox-3.1/3.1~b2+build1+nobinonly-0ubuntu1](https://launchpad.net/ubuntu/jaunty/+source/firefox-3.1/3.1~b2+build1+nobinonly-0ubuntu1)

---

### Post by Slug71 on 2008-11-28
Nice!
I installed it when i installed Jaunty Alpha 1 and it worked really well.

---

### Post by plun on 2008-11-28
xulrunner is a real "pig" to build.... 3rd try within the build machine.

I hope its a default Firefox also....   "hunt down all bugs" and contribute to upstream !

---

### Post by Slug71 on 2008-11-28
plun, Are you using xulrunner 1.9.1?

---

### Post by plun on 2008-11-28
> **Slug71 said:**
> plun, Are you using xulrunner 1.9.1?

Yup from fta:s ppa.... but we need many testers and this is the key issue.
"bang" it in in slangaseks head... sorry.. (with all respect) :oops:


Just a joke to wait for Debian.... better to test it  ourself and contribute
to upstream.

:)

---

### Post by ubulette on 2008-11-28
It has to pass the review in the [NEW]("https://launchpad.net/ubuntu/jaunty/+queue") queue first.

1/ xul src approved in NEW => done
2/ xul debs built => done
3/ xul debs approved in NEW
4/ ff src approved in NEW => done
5/ ff debs built (needs 3)
6/ ff debs approved in NEW (needs 5)

We need 3->5->6, so please be patient until Monday.
In the meantime, my PPA has it, as usual.

---

### Post by Starks on 2008-11-29
> **ubulette said:**
> It has to pass the review in the [NEW]("https://launchpad.net/ubuntu/jaunty/+queue") queue first.

1/ xul src approved in NEW => done
2/ xul debs built => done
3/ xul debs approved in NEW
4/ ff src approved in NEW => done
5/ ff debs built (needs 3)
6/ ff debs approved in NEW (needs 5)

We need 3->5->6, so please be patient until Monday.
In the meantime, my PPA has it, as usual.
Cairo and antialiasing is still broken.

Why?

---

### Post by ubulette on 2008-11-29
> **Starks said:**
> Cairo and antialiasing is still broken.

Why?

it's not. fontconfig is.
See [https://bugzilla.mozilla.org/show_bug.cgi?id=458612](https://bugzilla.mozilla.org/show_bug.cgi?id=458612)

---

### Post by plun on 2008-11-29
> **ubulette said:**
> it's not. fontconfig is.
See [https://bugzilla.mozilla.org/show_bug.cgi?id=458612](https://bugzilla.mozilla.org/show_bug.cgi?id=458612)

Just a little question... Is it possible to involve Gnome 2.26 work
and maybe FreeDesktop standards to this ? 

I have no idea who develops/maintain these functions at Gnome...:confused:

---

### Post by plun on 2008-12-01
INFO

> [B]shiretoko aka firefox 3.1 (and xulrunner-1.9.1) preview packages in jaunty/universe
[/B]
on friday, the great fta uploaded xulrunner-1.9.1 and firefox-3.1 to the ubuntu universe archive (jaunty). It took the weekend to get archive admin attention, but now it seems like it will show up on your mirror quite soon (hugs to all involved here).

Similar to what we did for firefox 3.0 in gutsy, we allow you to install this package next to your &#8220;production&#8221; firefox 3.0 install. This is done, by creating a copy of your existing firefox-3.0 profile the first time you start firefox-3.1. So don&#8217;t be scared to test this, just because you fear to bust your profile. Once 3.1 is final we will present you with a choice again where you can decide which profile to use in future.

[B]A few more words on bugs:
If you have pending firefox-3.0 bugs that you feel would be important to get fixed for 3.1, please add the firefox-3.1 target to your bug and state which package version you are using.

From now on we will update the firefox-3.1 and xulrunner-1.9.1 package quite frequently, so if you file bugs, remember to check if they still apply if you receive an update.
[/B]
Also to make bug triaging more easily, I would like to remind everyone that mozilla packages have a normalized bug description format ... which will allow us to swiftly forward your bugs to upstream on your behalf.

Enjoy!

[http://www.asoftsite.org/s9y/archives/154-shiretoko-aka-firefox-3.1-and-xulrunner-1.9.1-preview-packages-in-jauntyuniverse.html](http://www.asoftsite.org/s9y/archives/154-shiretoko-aka-firefox-3.1-and-xulrunner-1.9.1-preview-packages-in-jauntyuniverse.html)


Thanks Ubuntu-Mozilla team,  asac and the great fta...:guitar:

---

### Post by Slug71 on 2008-12-01
Why doesnt FF-3.1 work if i remove 3.0.4?
And xulrunner 1.9.1 doesnt show up in my FF-3.1 Add-Ons.

---

### Post by plun on 2008-12-01
> **Slug71 said:**
> Why doesnt FF-3.1 work if i remove 3.0.4?
And xulrunner 1.9.1 doesnt show up in my FF-3.1 Add-Ons.

Its better to keep both !

From info

> Similar to what we did for firefox 3.0 in gutsy, we allow you to install this package next to your “production” firefox 3.0 install. This is done, by creating a copy of your existing firefox-3.0 profile the first time you start firefox-3.1. So don’t be scared to test this, just because you fear to bust your profile. Once 3.1 is final we will present you with a choice again where you can decide which profile to use in future.

Packagename is firefox-3.1

[http://packages.ubuntu.com/jaunty/firefox-3.1](http://packages.ubuntu.com/jaunty/firefox-3.1)

Also a new GUI entry for Shiretoko  (build name)

---

### Post by Gina on 2008-12-01
You can get it with Synaptic - Search for Firefox 3.1.  Just installed it - now going to try it.

A few mins later...  Seems OK :)

---

### Post by Slug71 on 2008-12-01
> **Gina said:**
> You can get it with Synaptic - Search for Firefox 3.1.  Just installed it - now going to try it.

Yeh ive got it, just wanted to remove 3.0.4.

---

### Post by Gina on 2008-12-01
Using it now - some of my add-ons wont work as yet but otherwise seems alright :)

---

### Post by kernelhaxor on 2008-12-01
> **Gina said:**
> You can get it with Synaptic - Search for Firefox 3.1.  Just installed it - now going to try it.

A few mins later...  Seems OK :)

Great .. I'm gonna get it right now

---

### Post by ccw on 2008-12-02
> **Gina said:**
> Using it now - some of my add-ons wont work as yet but otherwise seems alright :)

Should we bother filing bug reports about broken addons at this point, and ifso should wefile them against firefox or the individual addons?

---

### Post by exploder on 2008-12-02
> Should we bother filing bug reports about broken addons at this point, and ifso should wefile them against firefox or the individual addons?

This is always the case with new versions of Firefox. When 3.1 is officially released by Mozilla people will start to work on updating the add ons. Add ons are independent of Firefox itself.

---

### Post by ccw on 2008-12-03
> **exploder said:**
> This is always the case with new versions of Firefox. When 3.1 is officially released by Mozilla people will start to work on updating the add ons. Add ons are independent of Firefox itself.


I understand why they are broken. I has asking should we bother filing bugs against the add-on debs in the ubuntu repos.

---

### Post by ubulette on 2008-12-03
> **ccw said:**
> I understand why they are broken. I has asking should we bother filing bugs against the add-on debs in the ubuntu repos.

You can if you know for sure that the upstream version works while the ubuntu one doesn't. If the upstream version is broken too, it's better to report the bug upstream, we'll get the fixed version downstream (and then, a bug on lp linking the upstream bug or the release notes is nice to have).

---

### Post by frankleeee on 2008-12-06
If any of you have installed 3.1 and your add ons don't work I found  this link that worked for me it is a easy about:config.
[http://www.jkontherun.com/2008/06/how-to-force-fi.html](http://www.jkontherun.com/2008/06/how-to-force-fi.html)

---

