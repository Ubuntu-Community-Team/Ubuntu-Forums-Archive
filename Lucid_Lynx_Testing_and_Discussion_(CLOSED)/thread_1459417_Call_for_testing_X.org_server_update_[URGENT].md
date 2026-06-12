---
title: "Call for testing: X.org server update [URGENT]"
date: 2010-04-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Technoviking on 2010-04-21
(From [https://lists.ubuntu.com/archives/ubuntu-devel/2010-April/030673.html](https://lists.ubuntu.com/archives/ubuntu-devel/2010-April/030673.html))

We are looking for people to help test this update. If you want to test the updated packages **be sure to your put your results on the wiki page listed below**.

> Hello fellow developers,

On April 15, a major memory leak was introduced into the X.org server which causes the computer to get slower and slower over some hours, and finally becoming totally sluggish. This is tracked in [https://launchpad.net/bugs/565981](https://launchpad.net/bugs/565981) .

Thanks to the tireless investigations of Robert Hooker and Tormod Volden, this was tracked down to a recently added patch which fixed some crashes intoduced by the GLX 1.4 enablement patches. A first attempt to fixing the memory problem wasn't successful unfortunately, and isn't easy.

The safest solution right now is to roll back all three patches. This will fix both the memory leak and thus the performance problem, as well as avoid the X crashes which were introduced by the GLX 1.4 enabling.  While we had this combination before, we haven't tested it with the current lucid userspace, and thus we need some extensive tests on various hardware to get more data about it.

I set up a wiki page to explain how to install the proposed packages and for adding feedback:

  [https://wiki.ubuntu.com/X/Testing/GEMLeak](https://wiki.ubuntu.com/X/Testing/GEMLeak)

On Friday we will check how much and which kind of feedback we got, and depending on that will decide about the risk of putting it into Lucid final, or doing an early SRU. (We need testing feedback in either case, of course).

Thank you in advance for helping with testing!

Martin

---

### Post by iansyngin on 2010-04-21
The first link above is dead

---

### Post by MacUntu on 2010-04-21
After a reboot it still says "GLX version: 1.4", now what?

---

### Post by Bachstelze on 2010-04-21
> **MacUntu said:**
> After a reboot it still says "GLX version: 1.4", now what?

Are you using a proprietary graphics driver?

> This does not affect cards using proprietary drivers

---

### Post by MacUntu on 2010-04-21
*facepalm*

:D

---

### Post by kansasnoob on 2010-04-21
Please excuse me for being a pain but being visually impaired I can sometimes overlook the obvious :)

First of all I have Intel 82945G/GZ Integrated Graphics so I feel I should get into this. Another reason for this thinking is that I noticed this behavior in a fresh upgrade from Karmic to Lucid about 48 hours ago, but not my "main" Lucid which was (re)installed on 04/01/2010 even though I get this:

```
lance@lance-desktop:~$ glxinfo | grep "GLX version"
GLX version: 1.4

```.

What my blind old self can't see is how to add myself and my machine to "testing" here:

[https://wiki.ubuntu.com/X/Testing/GEMLeak](https://wiki.ubuntu.com/X/Testing/GEMLeak)

:confused:

I will add this info to the bug report after checking the "GLX version" in that "upgraded" version of Lucid.

Also your first link is broken :)

---

### Post by cariboo on 2010-04-21
You need a Launchpad account, once you've logged in, click the **Edit** link in the far left just above the page title.

---

### Post by djchandler on 2010-04-21
The xserver-xorg-video-ati driver has issues of its own. Those who use passive cooling for your GPU, be aware that there are heat issues with that driver. If you are on a laptop, it is bad enough to cause the computer to shut down due to BIOS safety settings. Watching about 5 minutes of flash video is about all it takes for my laptop to shut itself off.

[http://bugs.freedesktop.org/show_bug.cgi?id=27705](http://bugs.freedesktop.org/show_bug.cgi?id=27705)

Here's a thread discussing who is having this issue and who is not affected.

[http://ubuntuforums.org/showthread.php?t=1458089](http://ubuntuforums.org/showthread.php?t=1458089)

---

### Post by kansasnoob on 2010-04-21
> **cariboo907 said:**
> You need a Launchpad account, once you've logged in, click the **Edit** link in the far left just above the page title.

Already have an account:

[https://launchpad.net/~lbsolost](https://launchpad.net/~lbsolost)

Ahhh, maybe I see! When you're blind as a bat (and the Xorg devs disregard you) you end up using fonts that hide things:

[ATTACH]153978[/ATTACH]

See how the tabs to the right cover up some stuff? How can I tell what that says?

It's also impossible to "click on" :(

For now I'm just using the bug report. My comments are too long anyway.

Edit: looking again and I'll be snookered if I can see an Edit link? It's like my fonts + resolution just hide things.

---

### Post by Irihapeti on 2010-04-21
I have to use Vesa driver on two of my machines. I take it that this doesn't affect them?

*Edit: just realised: of course, I can't enable Compiz with Vesa driver, so irrelevant, I think.*

---

### Post by psyke83 on 2010-04-21
> **Irihapeti said:**
> I have to use Vesa driver on two of my machines. I take it that this doesn't affect them?

*Edit: just realised: of course, I can't enable Compiz with Vesa driver, so irrelevant, I think.*

It seems only to apply to KMS configurations (nouveau and intel only support KMS; radeon defaults to KMS, but it can be reverted to UMS/DRI1 with the boot parameter *radeon.modeset=0*).

---

### Post by The Real Dave on 2010-04-21
Ok, going to install the packages now. I've a Geforce4 MX440, which hasn't been tested yet apparently :)

Edit: Hang on a sec, it doesn't effect the Nvidia-96 driver does it? So me testing would be pointless?

---

### Post by psyke83 on 2010-04-21
> **Chauncellor said:**
> I would love to test this, but I can't seem to get compiz to enable itself with Nouveau right now.

[http://ubuntuforums.org/showthread.php?t=1455356](http://ubuntuforums.org/showthread.php?t=1455356)

This topic suggests that the latest kernel does not include the nouveau backport. Is this correct? How could I go about getting it to work? I'd like to ensure this bug report get solved with enough information!

You probably need the [xorg-edgers repository]("https://launchpad.net/%7Exorg-edgers/+archive/ppa") to enable DRI in nouveau. However, by enabling that repository, you are also upgrading to a newer upstream Xserver release which no longer has the GEM memory leak.

I believe an alternative is the [freshgraphics PPA]("https://launchpad.net/%7Efreshgraphics/+archive/ppa"), which only upgrades the Mesa packages - if you use that option, then you may benefit from this Xserver update - as long as the lower GLX version string doesn't break anything.

---

### Post by Yellow Pasque on 2010-04-21
> **kansasnoob said:**
> Edit: looking again and I'll be snookered if I can see an Edit link? It's like my fonts + resolution just hide things.
You need to log in before the edit link shows up... In your screenshot, you're not logged in (and so it says 'Immutable Page').

---

### Post by Captain Smiley Pants on 2010-04-21
I would like to test this patch for my GMA 945, but for whatever reason Xorg defaults on some other driver and not the "intel" one. I just looked around for xorg.conf and found out that there have been changes since Ye Olden Dayes of xorg.conf and it is no more (I'd also LOVE to turn on Compiz, more reason for testing!), how would I go about doing this?

---

### Post by Irihapeti on 2010-04-21
I've got a problem with xserver-xorg on my EeePC 900 which I don't think is related. I've filed a separate bug. I hadn't thought of using Vesa driver so thanks for the tip.

---

### Post by Yellow Pasque on 2010-04-21
> **Chauncellor said:**
> There was just an entry with my same card (Nvidia 8600GT). The entry says it fails. Mr. Anthony Hook, how did you test this?

Note that's he's using the open-source nouveau driver.

---

### Post by psyke83 on 2010-04-21
The proposed update is not working for my radeon card; see comments [#33]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/565981/comments/33") and [#34]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/565981/comments/34").

---

### Post by HankB on 2010-04-22
Couple questions... I've looked at the Wiki and wonder what is a "large number." From a couple runs I get:
```
hbarta@bonsai:~$ grep "object bytes" /sys/kernel/debug/dri/0/gem_objects
44572672 object bytes
hbarta@bonsai:~$ grep "object bytes" /sys/kernel/debug/dri/0/gem_objects
47828992 object bytes
hbarta@bonsai:~$ grep "object bytes" /sys/kernel/debug/dri/0/gem_objects
52973568 object bytes

```
Does the growth of this number indicate the bug?

I see several mentions of Compiz. Is this a problem only when Compiz is used? I'm running on a netbook so I don't enable anything fancy. In fact, the entries on the tab for Appearance => Visual Effects are all grayed out.

---

### Post by forcecore on 2010-04-22
i made my Intel 965 laptop suffer Compiz, HD videos, glxgears some 18-19 hours and everything was fine, memory was around 327mb after stopping glxgears and HD playback. GLX 1.4 should not be removed too because some of 3D apps requires this, i really hope devs can fix this not remove GLX 1.4

---

### Post by psyke83 on 2010-04-22
> **HankB said:**
> Couple questions... I've looked at the Wiki and wonder what is a "large number." From a couple runs I get:
```
hbarta@bonsai:~$ grep "object bytes" /sys/kernel/debug/dri/0/gem_objects
44572672 object bytes
hbarta@bonsai:~$ grep "object bytes" /sys/kernel/debug/dri/0/gem_objects
47828992 object bytes
hbarta@bonsai:~$ grep "object bytes" /sys/kernel/debug/dri/0/gem_objects
52973568 object bytes

```Does the growth of this number indicate the bug?

I see several mentions of Compiz. Is this a problem only when Compiz is used? I'm running on a netbook so I don't enable anything fancy. In fact, the entries on the tab for Appearance => Visual Effects are all grayed out.

It depends on what you're doing on your system. If you are constantly opening new applications and not closing old ones, then the figure would probably rise. If you are closing applications, however, and see no decrease at all, then you are probably suffering from the bug.

See the testcase in the bug and comment #33 onwards in the bug report.

---

### Post by forcecore on 2010-04-22
just note: i discovered that my Gthumb issue is connected with this bug some way, after installing fixed packages then Gthumb is fine too on Virtualbox and desktop pc, laptop is fine with GLX 1.4 and do not need patch.
[http://ubuntuforums.org/showthread.php?t=1458785](http://ubuntuforums.org/showthread.php?t=1458785)

if GLX 1.4 cannot be fixed then looks like best option is to revert to 1.2

---

### Post by chris1379 on 2010-04-24
I'm definitely affected by this bug. After a few minutes of watching a DVD, my 384 MB of RAM and 512 MB of swap were totally used up. The system was unresponsive and all I could do was hit the power button. This is serious! I reverted to GLX version 1.2 and it's OK. It's also more CPU efficient. This is very important on a 700 MHz laptop. It's a Sony PCG-F580K with Neomagic video. This same configuration was used in many laptops including quite a few IBM Thinkpad models. The X-server in Hardy was even less CPU intensive. If Ubuntu developers want to continue advertising that it runs on older hardware, they'll have to do better than this.

---

### Post by psyke83 on 2010-04-24
> **chris1379 said:**
> I'm definitely affected by this bug. After a few minutes of watching a DVD, my 384 MB of RAM and 512 MB of swap were totally used up. The system was unresponsive and all I could do was hit the power button. This is serious! I reverted to GLX version 1.2 and it's OK. It's also more CPU efficient. This is very important on a 700 MHz laptop. It's a Sony PCG-F580K with Neomagic video. This same configuration was used in many laptops including quite a few IBM Thinkpad models. The X-server in Hardy was even less CPU intensive. If Ubuntu developers want to continue advertising that it runs on older hardware, they'll have to do better than this.

Have you updated your system? The patched server was released already, so you shouldn't have issues any longer (though the leak is still present on my system, sadly).

---

### Post by jpeddicord on 2010-04-25
Unsticking; the reverted X server has been pushed out and issues should be resolved.

---

