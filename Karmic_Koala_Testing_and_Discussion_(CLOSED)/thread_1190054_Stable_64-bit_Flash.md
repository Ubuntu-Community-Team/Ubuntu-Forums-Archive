---
title: "Stable 64-bit Flash"
date: 2009-06-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DPic on 2009-06-17
IIRC, the Flash 64 bit Alpha almost made it into Intrepid, but was not because it is an alpha. It was already much more stable than using the 32-bit version on 64-bit Ubuntu, and now that [64-bit Flash alpha 2]("http://labs.adobe.com/downloads/flashplayer10.html") is out, i recommend we make an exception, and include it in Karmic.

---

### Post by ronacc on 2009-06-17
I'll second that , I've been using 64bit flash since they released alpha1 and it's been rock solid . much better than the 32bit kluged onto a 64bit install.

---

### Post by robert.rankin.jr on 2009-06-17
AHH, I agree so much. Nothing works when running flash through nspluginwrapper.

---

### Post by zenarcher on 2009-06-17
I'll agree with that, as well.  The 64 bit flash has been working perfectly for me for quite some time, as well.

Cheers,
zenarcher

---

### Post by Swarms on 2009-06-17
Damn I am impressed, it was so frustrating with poor flash support for 64 bit back in the day. I now see no reason why not to run with 64 bit OS. :)

---

### Post by Podex on 2009-06-17
I've been using it since the first alpha came out as well. Much much more stable than the 32-bit+nspluginwrapper option.

Btw, here is the bug report for this: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/326555](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/326555)

---

### Post by DPic on 2009-06-17
> **Podex said:**
> I've been using it since the first alpha came out as well. Much much more stable than the 32-bit+nspluginwrapper option.

Btw, here is the bug report for this: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/326555](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/326555)

Thanks for that link! Here is my understanding of the issue:

We know that 64-bit Flash alplace and alpha 2 (alpha refresh) are more stable than the 32-bit Flash, but that isn't the problem. We would make an exception to include it in Ubuntu, but the current script can olny download Flash from archive.canonical.com which cannot host non-final software for other reasons. My impression was that we need permission from Adobe, but i'm note sure what, "here is no official support from adobe security wise" means, but i think that since this is the only read thing impeding this, we should contact Adobe immediately to work around this.

As far as other possible workarounds go, the old script that didn't take the file from archive.canonical and simply took it straight from Adobe ran into tons of errors so it would be unwise to go back to that method. I was, however, unaware of the link:
[http://packages.debian.org/sid/flashplugin-nonfree](http://packages.debian.org/sid/flashplugin-nonfree)

If the 64-bit package there uses the latest native 64-bit Flash (alpha 2), could we use that with the script?

---

### Post by ELD on 2009-06-17
I +1 to this idea, it would help a lot for gradually moving users to 64bit (over the next million years ;)).

Would be good to work something out with adobe, i can't see a massive problem with it, it gives them more spotlight right?

---

### Post by pferraro on 2009-06-17
While I agree with the proposal, isn't the biggest issue with the 64-bit plugin the lack of full screen hardware acceleration?

---

### Post by ktp on 2009-06-17
> **pferraro said:**
> While I agree with the proposal, isn't the biggest issue with the 64-bit plugin the lack of full screen hardware acceleration?

That's good question...I know in full screen, cpu usage is very high with native 64-bit.  Anyone have 32-bit flash on 64-bit and see how the hardware acceleration is?

---

### Post by Nullack on 2009-06-18
The new 64bit flash plugin does have gpu acceleration when compiz is off and your not on the gpu black list.

---

### Post by rajeev1204 on 2009-06-18
> **DPic said:**
> IIRC, the Flash 64 bit Alpha almost made it into Intrepid, but was not because it is an alpha. It was already much more stable than using the 32-bit version on 64-bit Ubuntu, and now that [64-bit Flash alpha 2]("http://labs.adobe.com/downloads/flashplayer10.html") is out, i recommend we make an exception, and include it in Karmic.


alpha 2? Isnt this old now from february??

---

### Post by Slug71 on 2009-06-18
I back this 110%. nspluginwrapper sucks blue balls.

---

### Post by taavikko on 2009-06-18
flashplugin is the only thing pulling ia32-libs to native 64-bit system.
So to that argument, flashplugin-installer should point to native 64-bit plugin by adobe.

Let's hope that html5 is soon replacing need for adobes flash ;)
[http://people.mozilla.com/~prouget/demos/DynamicContentInjection/play.xhtml](http://people.mozilla.com/~prouget/demos/DynamicContentInjection/play.xhtml)
NOTE: only for FF-3.5

---

### Post by rajeev1204 on 2009-06-18
> **Nullack said:**
> The new 64bit flash plugin does have gpu acceleration when compiz is off and your not on the gpu black list.


Which new plugin guys? This is old inst it from feb????

---

### Post by SKLP on 2009-06-18
What new alpha 2? If it's the old one from feb it did not have accelerated full screen, unlike the 32-bit plugin. (no I don't use compiz, and atm im on NVIDIA, which I suppose isn't black-listed)

And I don't get why some of you say that the native plugin is any more stable. Last time I compared them(native flash alpha, and nspluginwrapper+32 bit flash), they *BOTH* were unstable. The difference is that with 32-bit flash only nspluginwrapper crashes, and not the whole browser.

I would definately support 64-bit native flash if it had accelerated full screen and also if it was completely stable.

---

### Post by philinux on 2009-06-18
Full screen flash is a joke. Not enough frames per second to make it watchable. I use compiz to zoom in.

---

### Post by izizzle on 2009-06-18
This sounds great. There are tons of threads on these forums packed with users having trouble installing flash on their 64-bit systems. Including it as part of the OS would save alot of us some time & effort.

Great idea! +1

---

### Post by sal_m on 2009-06-18
On my system, the February release dies with an illegal instruction error on some sites.  And when it happens it kills Firefox entirely.  3.5 and 3.1.

If you have access to the flashplayer bug reports on the adobe website, it was bug FP-1026, and it had quite a few me-too reports.

---

### Post by novafluxx on 2009-06-19
I had no issues with the alpha refresh released in late February. I used it in 8.10 and in 9.04 both, and never had any problems. The hardest part was 'installing' it, by just extracting and cp the file to the plugins folder!

---

### Post by pferraro on 2009-06-19
> **novafluxx said:**
> I had no issues with the alpha refresh released in late February. I used it in 8.10 and in 9.04 both, and never had any problems. The hardest part was 'installing' it, by just extracting and cp the file to the plugins folder!

FYI - I found a PPA containing the 64-bit flash installer:
deb [http://ppa.launchpad.net/natros/ppa/ubuntu](http://ppa.launchpad.net/natros/ppa/ubuntu) jaunty main

---

### Post by FuturePilot on 2009-06-19
Where is this new version? [http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html") says it's from February :confused:

---

### Post by plun on 2009-06-20
Someone with "Debian contacts" must probably file an upgrade request to the alpha version....

This is Debians changelog:

[http://packages.debian.org/changelogs/pool/contrib/f/flashplugin-nonfree/flashplugin-nonfree_2.6/changelog](http://packages.debian.org/changelogs/pool/contrib/f/flashplugin-nonfree/flashplugin-nonfree_2.6/changelog)

I dont believe that Ubuntu will upgrade without Debian....;)

---

### Post by DPic on 2009-06-25
> **plun said:**
> Someone with "Debian contacts" must probably file an upgrade request to the alpha version....

This is Debians changelog:

[http://packages.debian.org/changelogs/pool/contrib/f/flashplugin-nonfree/flashplugin-nonfree_2.6/changelog](http://packages.debian.org/changelogs/pool/contrib/f/flashplugin-nonfree/flashplugin-nonfree_2.6/changelog)

I dont believe that Ubuntu will upgrade without Debian....;)

How? Can somebody do this?

---

### Post by zoomy942 on 2009-06-25
you are right, the 32bit one sucks.  how can i install this 64bit one with that linked PPA?  i removed the 32 bit one.

---

### Post by ubuntu27 on 2009-06-26
What new Flash 64-bit? I don't see any new version on the Adobe's site.

---

### Post by rudenko_ruslan on 2009-06-26
> **ubuntu27 said:**
> What new Flash 64-bit? I don't see any new version on the Adobe's site.
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by zoomy942 on 2009-06-26
and to install it?

---

### Post by zika on 2009-06-26
> **zoomy942 said:**
> and to install it?
Just extract libflashplayer.so in /usr/lib/mozilla/plugins/ ... and that is it ... :) (for 64-bit version)

---

### Post by DPic on 2009-06-27
Or, if we find a way to wiggle it into Karmic, you wouldn't have to go throug the trouble =]

---

### Post by taavikko on 2009-06-27
> **DPic said:**
> Or, if we find a way to wiggle it into Karmic, you wouldn't have to go throug the trouble =]

That would be a few lines of code to flashplugin-installer's postinst
file?

checking the architecture of system and then adjusting the version to download and install

Then we could drop ia32 libs entirely... (wine and few others are still dependant of it though)

---

