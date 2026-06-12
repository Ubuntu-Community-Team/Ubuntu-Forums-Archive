---
title: "Moonlight 1.0 Beta"
date: 2008-12-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Starks on 2008-12-03
[http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

This needs to hit the repos and Ubufox ASAP.

I'm not sure if the Microsoft Media Pack would be a Restricted Extra or not...

---

### Post by mick222 on 2008-12-03
I don't think it will be in the repos a lot of people are against it and think microsoft will not fully cooperate with novell .
 I just installed it tried to watch cartch= up on itv uk doesn't seem to work still says install silverlight. How do i get the microsoft media pack.

---

### Post by RAOF on 2008-12-03
> **mick222 said:**
> I don't think it will be in the repos a lot of people are against it...
Oh, it absolutely will.  It's been somewhat delayed by the Mono 2.0 transition, but you can watch the progress (such as it is) [here](http://wiki.debian.org/Teams/DebianMonoGroup/Moonlight).

Leave the world of the forums and you find that there really aren't that many people against it; they're just vocal here.  In particular, it seems that no-one in a position of responsibility in the Ubuntu developer community seems especially concerned about it (Mono in general - moonlight hasn't really come up in particular).

> **mick222 said:**
> ...I just installed it tried to watch cartch= up on itv uk doesn't seem to work still says install silverlight. How do i get the microsoft media pack.

That requires Silverlight 2 support; Moonlight only supports 1.0 at this point.

---

### Post by directhex on 2008-12-03
> **Starks said:**
> This needs to hit the repos and Ubufox ASAP.

```
jms@destiny:~$ head -1 Projects/pkg-mono/moon/trunk/debian/changelog 
moon (1.0~beta1-1) UNRELEASED; urgency=low
```

I've been delayed by being at a conference, and crappy hotel wifi having a transfer limit (which is rather easy to exceed when you need to set up a pbuilder)

> I'm not sure if the Microsoft Media Pack would be a Restricted Extra or not...

It doesn't need to be. Packages will be built against libavcodec (as already found in the repos), which should cover *most* situations. In the event that it doesn't, then the MMP will automatically be offered by the plugin. No need for MMP to ever live outside Microsoft.com - and indeed, the license on it requires that it only be obtained from there

---

### Post by mick222 on 2008-12-03
thanks for correcting me raof. I tried the test sites from the mono site and they all ask for silverlight to be installed what do i need to enable these sites.

---

### Post by plun on 2008-12-03
This site is a good working test

[http://videoshow.vertigo.com/](http://videoshow.vertigo.com/)

- FF 3.04 install OK   FF3.1 must be "forced".

- Codecs install OK

- Still gives EULA (empty)

- Seems to be recognition error for many sites

[http://silverlight.net/Showcase/](http://silverlight.net/Showcase/) 

- HD content sites broken....

This one is a important test for a mainstream user: 
[http://www.nbcolympics.com/video/](http://www.nbcolympics.com/video/)

(Browser agent switcher must also be used for above)

---

### Post by directhex on 2008-12-03
> **plun said:**
> - Still gives EULA (empty)

On the plugin, or on the Microsoft Media Pack?

> - Seems to be recognition error for many sites

Yes, that's true - there are two scenarios:
[list]
[*]The site is using SL2.0 - this will cause the "install Silverlight" button (as moon is 1.0-only right now). Unavoidable for now.
[*]The site uses an ancient version of Silverlight.js with known browser detection bugs on FF3. Generally, that's the site author's fault - mail them and tell them to use the latest Silverlight.js from [http://code.msdn.microsoft.com/silverlightjs/](http://code.msdn.microsoft.com/silverlightjs/) (Silverlight.js is Free Software). This can be worked around using Greasemonkey and this script: [http://anonsvn.mono-project.com/viewvc/trunk/moon/data/silverlight-ff3-quirks.user.js](http://anonsvn.mono-project.com/viewvc/trunk/moon/data/silverlight-ff3-quirks.user.js)
[/list]

> - HD content sites broken....

Broken how? Any examples? Not related to the 1.0-only thing?

---

### Post by plun on 2008-12-03
> **directhex said:**
> On the plugin, or on the Microsoft Media Pack?



Yes, that's true - there are two scenarios:
[list]
[*]The site is using SL2.0 - this will cause the "install Silverlight" button (as moon is 1.0-only right now). Unavoidable for now.
[*]The site uses an ancient version of Silverlight.js with known browser detection bugs on FF3. Generally, that's the site author's fault - mail them and tell them to use the latest Silverlight.js from [http://code.msdn.microsoft.com/silverlightjs/](http://code.msdn.microsoft.com/silverlightjs/) (Silverlight.js is Free Software). This can be worked around using Greasemonkey and this script: [http://anonsvn.mono-project.com/viewvc/trunk/moon/data/silverlight-ff3-quirks.user.js](http://anonsvn.mono-project.com/viewvc/trunk/moon/data/silverlight-ff3-quirks.user.js)
[/list]

Broken how? Any examples? Not related to the 1.0-only thing?


1. MMP pack with EULA at Vertigos video show [http://videoshow.vertigo.com/](http://videoshow.vertigo.com/)


2.  Going to test some more and compare with a compiled version against an unstripped FFmpeg.

HD content seems nevertheless to be broken after a quick test...

(also forced it to FF3.1 with a brutal hack)

Testing...;)

---

### Post by directhex on 2008-12-03
```
jms@destiny:/tmp$ dpkg -l \*moon\*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                     Version                  Description
+++-========================-========================-================================================================
ii  libmoon0                 1.0~beta1-1              Free Software clone of Silverlight 1.0 - runtime library
un  moonlight                <none>                   (no description available)
ii  moonlight-plugin-core    1.0~beta1-1              Free Software clone of Silverlight 1.0 - plugin core components
ii  moonlight-plugin-mozilla 1.0~beta1-1              Free Software clone of Silverlight 1.0 - Xulrunner 1.9 plugin

```

Tested & working fine. Will get it double-checked, and submitted to Debian NEW, tonight

---

### Post by plun on 2008-12-03
> **directhex said:**
> 

Tested & working fine. Will get it double-checked, and submitted to Debian NEW, tonight

Ok... nice and thanks  ;)

Also remove "the barrier" against FF 3.1...  we suppose to test FF3.1.

max version and security certificates are "messed" up...

---

### Post by directhex on 2008-12-03
> **plun said:**
> Ok... nice and thanks  ;)

Also remove "the barrier" against FF 3.1...  we suppose to test FF3.1.

max version and security certificates are "messed" up...

Which barrier? Packages don't have the same restrictions that .xpi files have (though there ARE a few tweaks I'm making right now for 3.1 support)

---

### Post by directhex on 2008-12-03
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1b2) Gecko/20081126 Ubuntu/8.10 (intrepid) Shiretoko/3.1b2

Works fine, one minor dependency to tweak

---

### Post by plun on 2008-12-03
> **directhex said:**
> Which barrier? Packages don't have the same restrictions that .xpi files have (though there ARE a few tweaks I'm making right now for 3.1 support)

Ok....just so we can test and not fall down in the discussions black hole.

---

### Post by plun on 2009-01-20
**Watching the Obama Official Inauguration on Linux with Moonlight.**

[http://tirania.org/blog/archive/2009/Jan-20.html](http://tirania.org/blog/archive/2009/Jan-20.html)


Obamas site:
[http://www.pic2009.org/page/content/live](http://www.pic2009.org/page/content/live)

---

### Post by plun on 2009-02-12
***Moonlight 1.0 goes live***

[http://tirania.org/blog/archive/2009/Feb-11.html](http://tirania.org/blog/archive/2009/Feb-11.html)


MS blog
[http://www.hanselman.com/blog/Moonlight10ReleaseOpenSourceSilverlight10ImplementationOnLinux.aspx](http://www.hanselman.com/blog/Moonlight10ReleaseOpenSourceSilverlight10ImplementationOnLinux.aspx)


Download
[http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

---

