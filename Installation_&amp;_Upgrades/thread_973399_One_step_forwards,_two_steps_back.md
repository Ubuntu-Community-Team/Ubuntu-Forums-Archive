---
title: "One step forwards, two steps back"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by SabreWolfy on 2008-11-06
I've been using Ubuntu for many months and I love it. I couldn't possibly go back to using Window$. However, I'm really frustrated with Intrepid at the moment, so I thought I'd see what others have to say.

<rant>
I installed Intrepid fresh onto my Acer Aspire 4710 notebook from the Alternate CD.

[LIST=1]
[*]Bluetooth appears to be unusable. I've found [bug reports]("https://bugs.launchpad.net/bugs/284982"), etc., and that's great, but I can't use bluetooth. ](*,)
[*]Today I tried to print to a PDF document. There were no printers installed by default. I installed CUPS-PDF and spent an hour fighting with it, only to [discover]("http://ubuntuforums.org/showthread.php?t=969002&highlight=cups-pdf+intrepid") that this works differently in [Intrepid]("http://ubuntuforums.org/showthread.php?t=957227&highlight=cups-pdf+intrepid")? In fact, it does not appear to work in Intrepid at all. You have to select "Print to file" to make a PDF. Time wasted. ](*,)
[*]I then tried to connect via my VPN. I had previously exported the VPN client settings from Hardy. They would not import. The entire VPN client seems to be different and I could not find corresponding settings. After trying for ages and not being able to connect, I found a [bug report]("https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/259168") that it's [broken]("http://ubuntuforums.org/showthread.php?t=922362&highlight=intrepid+vpn") in Intrepid. More time wasted. ](*,)
[/LIST]
How is it possible that basic, fundamental, previously-working features are broken in the latest release of a product? I wasted an entire evening fighting with Intrepid. :frown: Is the old saying of "You get what you pay for" true? Pay for an OS and *everything just works*? It's on days like this that I want to throw out all my computers!

On a more serious note though: how can GNU/Linux/Ubuntu/FOSS *ever* hope to be taken seriously when these kinds of issues persist? People rely on their OS to do what they need it to do and they don't have entire evenings to waste because the OS simply *does not work*. Many aspects of Intrepid are great, but do we need to hold thumbs with each new release that retrospective bugs are not introduced? I'm at a loss here, because I'm tired and frustrated and so utterly disbelieving that Intrepid is considered complete enough to release. Don't even get me started on the [ALSA/Shutdown bug]("https://bugs.launchpad.net/bugs/274995") (here, edit and hack away at your ALSA config files in order to shut your machine down). It's on days like this that I think GNU/Linux needs another 10 years before it will be a serious competitor. There is just still way too much which is broken and way too much time gets wasted fixing / sorting / reading / hacking / making it work.

Grrr!
</rant>

Comments, anyone?

---

### Post by the lush on 2008-11-06
I completely agree with you. 8.04 was a great release, in fact every version I have tried going back to 6.06 have been good in comparison to 8.10, so by this rationale, I consider 8.10 to simply be 5 steps back, I cannot even get past the blank screen of death. From other issues listed here (sound, network, shutdown), I am beginning to doubt if it is even worth trying.

---

### Post by SabreWolfy on 2008-11-07
My main desktop is still running Hardy and I'm now considering reinstalling Hardy onto my Intrepid laptop and my Intrepid desktop. I need to use my VPN now, for example, and I "just" can't. Instead, I have to fiddle around downloading updates from other repositories to get it to work.

It seems almost as if we cannot shake the "fiddle to make it work" and "tinker away at a config" approach of earlier versions of Linux. That's all well and good, but *I* don't always have the time. If I want to do X on my machine, I want to do X. I expect it to work. If it doesn't, it means I have to find a few hours to get it to work. Time wasted.

As I mentioned previously, I am a committed supporter and advocate of GNU/Linux/FOSS and Ubuntu in particular. However, I don't know if I can recommend Ubuntu, for example, in good faith to family and friends. How would Aunt Daphne manage if she can't shut her machine down? How would Cousin Pete use bluetooth? They would only manage if I or someone else "technical" could go and "fix" their machines.

Such examples are very contrary to the idea of Ubuntu and Linux for the people. Ubuntu and other distros seem to me making concerted efforts to be considered as worthy alternatives. Until all these feeble breakdowns in the OS can be ironed out, I don't think they stand a chance with the mainstream user. openSuse 11 and Fedora 9 Live CDs had no idea how to handle the Broadcom driver in my laptop. Without the driver, how could I go onto the internet to find out how to fix it? Again, it can be done by using another machine, etc. A lot of effort to get a wireless device working and more time wasted.

I would like my OS to work for me. With Intrepid, I seem to be working for my OS. I'm tired of doing all the hard "hacking" work simply to get basic functions running :-(

I'm off to use my Hardy machine now, because at least the VPN there works .... :mad:

---

### Post by VastOne on 2008-11-07
I agree completely.  I have two installs with irratating issues and to compound it, I cannot get even a sniff of a response to the questions I have posed which tells me that there is too many issues and not enough solutions or attempts to solve.  I am guessing the the really high level users here have their hands full.  

Do a search on my handle of VastOne to see my issues and lack of responses.

It is frustrating as I have been championing Ubuntu for 2 years now and never thought I would be this frustrated.  And for the life of me I cannot figure out why there was such a need to release code that is so buggy and with so many different issues.  This seems out of whack with the curve we had been on....Maybe someone soon will explain?!?!?

VastOne

---

### Post by SabreWolfy on 2008-11-07
@VastOne:

I couldn't agree with you more -- my sentiments exactly. I really *want* to support Ubuntu, etc., but releases like Intrepid make it really difficult to feel positive about the distro. I'm trying to decide now between sticking with Intrepid, rolling back to Hardy or trying openSuse/Fedora again. I don't really want to have to download half the internet again to install RPM packages of all the software I need though.

I am "happy" though that I am not the only person for whom Intrepid is a disappointment! Of course, there are many people who are delighted with Intrepid because it has solved various issues for them. Hence the subject line of this thread: One step forwards, two steps back. I think the true measure of a release is when it solves many people's issues and does not introduce new ones that break other people's installations.

---

### Post by silkstone on 2008-11-07
If Hardy worked for you, the best idea is probably to go back to it. Hardy seems a very good and stable release, and will be supported for over two years. From what I've seen and read, Intrepid adds little except bugs!

I'm running Hardy on two desktop PCs and a laptop, and everything works. I've always been against the policy of reinventing the wheel every six months, especially when the new wheel turns out square. It would be better if Canonical focused on a good release like Hardy and made it better with updates to both the OS and software. It seems both wasteful and frustrating to start again, and Intrepid is proving that for many people.

---

### Post by SabreWolfy on 2008-11-07
Post #5 [here]("http://ubuntuforums.org/showthread.php?t=964255&highlight=intrepid+vpn") provides a solution to the broken VPN PPTP issue in Intrepid.

I have installed the updated network manager, etc. mentioned in the above post, but this has not solved the problem. There appear to be two or three (!) separate bugs relating to PPTP VPN in Intrepid! :-( The second relates to [CHAP]("https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/283376") passwords in the wrong format and the third relates to the fact that [MPPE]("https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/282624") settings are not sticky. A search on LaunchPad for MPPE reveals [9 bugs]("https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=mppe&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=")!  I'm just irritated that I can't import the VPN settings I exported from Hardy.

Maybe the best approach is to be six months (one release) behind, and to upgrade to the "current" version when the "next" one is released. That way, you can be pretty sure it's (more) stable.

I guess it's pointless complaining here and taking no action. Bugs have been reported. Fixes will be issued, in time. But, it's time to take action now.

Goodbye Intrepid.

Hello Hardy, my old friend.

---

### Post by ke3ju on 2008-12-04
Here I am trying to talk large corps into dumping Windows for Unbuntu, and they go and put out a release where VPN doesn't even work.

Nice work...

Cheers,
Ed

---

### Post by SabreWolfy on 2009-01-22
> **SabreWolfy said:**
> 
...
<snip>
...

[LIST=1]
[*]Bluetooth appears to be unusable. I've found [bug reports]("https://bugs.launchpad.net/bugs/284982"), etc., and that's great, but I can't use bluetooth. ](*,)
[/LIST]


[COLOR="Blue"]**Update:** It appears that the Acer Aspire 4710 laptop ... does *not have* built-in bluetooth! :shock: This despite one of the buttons on the front of the machine which has a bluetooth logo on it! :confused: Available on "certain models" only I presume, but "designed" (?) to "trick" unsuspecting customers who see the machine in-store? Sigh.[/COLOR]

I've completed a fresh install of Intrepid (with a saved /home from Hardy) onto the laptop and so far it's actually working pretty well. The printing issue mentioned in my first post is not actually an issue really, as it is still possible to print to PDF. It was just the time-wasting aspect that initially frustrated me.

I still have no idea how to set up VPN in Intrepid. The client is completely different to the Hardy one and the settings file from Hardy cannot be imported. Any detailed walk-thru's on setting up VPN in Intrepid? I don't know what to enter for most of the fields -- the "Apply" button remains greyed out. Setting up VPN in Hardy was easy!

---

### Post by uberdonkey5 on 2009-01-31
despite another thread complaining that people rant, I would say without any reservation DO NOT INSTALL INTREPID

Hardy worked perfectly for me (given a few hardware tweaks) on my dell laptop, Then I installed intrepid, and this is what happened..

1. boot time went from 23secs to about 2 min 20 secs (this is WITHOUT the splash screen)
2. repositories didn't work
3. microphone doesn't work (pulse audio problem)
4. modem doesn't work anymore
5. I lost skype, cinelerra, and vlc
6. totem and mplayer take about 15 seconds before starting playing a video
7. the stupid shut down button! (now seperate from log off)

I am currently typing from Xandros in my eeepc, whilst backing up ALL my files for a complete reinstall.

Intrepid is at best the 'windows vista' of ubuntu. Indeed I'd go as far to say it is actually the 'windows 98' of ubuntu. Makes me worry about whats gonna happen in Jaunty, though its difficult to perceive that my computer is gonna be less operable than it currently is.

Hardy was pretty efficient and good, but if these issues aren't solved by Jaunty I fear that ubuntu will fade away. People will use hardy till unsupported.. avid linux users will change to another distro, and newbies will return to windows.

---

### Post by Eck on 2009-01-31
I think most of the Intrepid difficulties, bugs, whatever, are caused by what needed to be done to release it in the normal 6 month release cycle.

Don't forget that Debian has been in a mostly frozen state for months and months now.  It happens every time a new release of Debian Stable is imminent.  Since Ubuntu takes an image of Debian Sid and freezes it, then adds what it takes to meet goals from experimental and 3rd party, the base Ubuntu for Intrepid naturally became more of a mix-match than it normally would be.  I'm sure the bug-squashing was as thorough as ever but there's only so much that can be done with a mixed bag of fresh upstream and experimental stuff and older Debian Sid stuff.  Normally Sid stuff isn't old, but for this release it was old because of the freeze.

Hardy Heron has been fixed up nicely, just having another point release to 8.04.2.  That's the one I'd use, perhaps mixing in the backports to get the most popular new upgraded things. But at least the base system has been stabilized.

For newer software (yeah, old at this point but newer than Hardy Heron) one could install Debian Lenny.  Don't think other distros (Fedora, OpenSUSE) aren't having the same sorts of problems with some of the newer bleeding edge software.  They are.  Debian Lenny is a way to keep full access to favorite software but avoiding some of the pitfalls of the instability of the cutting edge stuff most distros are using these days.  Once it hits stable and goes a couple of months until testing gets security support, an upgrade to testing will bring in non-buggy versions of all the latest goodies.  Just at a slower pace.

---

### Post by SabreWolfy on 2009-04-24
For what it's worth, I found a solution to PPTP VPN in Jaunty (and presumably Intrepid too). Link [here]("http://ubuntuforums.org/showthread.php?t=1136020").

---

