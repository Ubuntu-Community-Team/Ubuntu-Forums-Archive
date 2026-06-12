---
title: "OpenOffice 3.0 is final! Any chance to see it in Ibex?"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by victorche on 2008-10-09
[http://oootranslation.services.openoffice.org/pub/OpenOffice.org/stable/3.0.0/OOo_3.0.0_LinuxIntel_install_en-US.tar.gz](http://oootranslation.services.openoffice.org/pub/OpenOffice.org/stable/3.0.0/OOo_3.0.0_LinuxIntel_install_en-US.tar.gz)

I still have a hope :guitar:

---

### Post by smartboyathome on 2008-10-09
It hasn't been announced on the site though, so it is technically not "final" yet. ;)

---

### Post by victorche on 2008-10-09
> **smartboyathome said:**
> It hasn't been announced on the site though, so it is technically not "final" yet. ;)

Trust my sources ;)
And check the link...

---

### Post by danf_1979 on 2008-10-09
Maybe we could do a poll to know how many openoffice3 testers seems to have/not have problems with 3.0. Maybe calc will change his mind if few people has problems :P.

---

### Post by smartboyathome on 2008-10-09
It most likely won't. I mean, we only got 3 weeks to test it, how are we gonna find all the bugs in that amount of time?

---

### Post by olskar on 2008-10-09
Bugs? There are no bugs ;)

Just kidding, but we should at least get it in backports if not in the mainrepos

---

### Post by smartboyathome on 2008-10-09
> **olskar said:**
> Bugs? There are no bugs ;)

Just kidding, but we should at least get it in backports if not in the mainrepos

Backports yes, definitely put it in backports. That seems to be the right place for this.

---

### Post by nanog on 2008-10-09
Actually many of us have been testing rcs via calc's ppa.

---

### Post by plun on 2008-10-09
I cannot see any problem with including OO-3.0 with Intrepid.

Just build it as fast as possible and roll out for test.

Mandriva 2009 also include it.

[http://www.mandriva.com/enterprise/en/company/press/mandriva-presents-its-latest-release-mandriva-linux-2009](http://www.mandriva.com/enterprise/en/company/press/mandriva-presents-its-latest-release-mandriva-linux-2009)


Just to do it....:)

---

### Post by Sand Lee on 2008-10-09
Yeah, there's no official release on the main page yet. I only see RC4 downloads. It's too bad though, a lot of people are saying that Intrepid gives them little reason to upgrade; OpenOffice 3 would definaltely do the trick ;)

---

### Post by philinux on 2008-10-09
If it fails to make the cut it will most likely come through the backports.

---

### Post by TerpInHotLanta on 2008-10-09
It looks as though OpenOffice is slowly rolling out the stable 3.0.0.

The USA mirror at Utah has some stable versions, but 64-bit and deb's are not yet available; thus, why I don't think they have fully announced OOffice 3.0 yet.

---

### Post by Swarms on 2008-10-09
If Gimp 2.6 could make the cut, hell yeah that they should test with OOo 3.0 for the last days before final. If its only trouble, then just fallback to the old version and we can't be blamed for not trying.

---

### Post by danf_1979 on 2008-10-09
gimp did it :)

```

$ apt-cache policy gimp
gimp:
  Installed: 2.6.0-1ubuntu1
  Candidate: 2.6.0-1ubuntu1
  Version table:
 *** 2.6.0-1ubuntu1 0
        500 http://de.archive.ubuntu.com intrepid/main Packages
        100 /var/lib/dpkg/status

```

---

### Post by canabal on 2008-10-09
I have been using RC3+4 (directly from the site, not calc's ppa) and have had no problems at all.

Sure I am not the power user of it, but still... nothing.

---

### Post by calc on 2008-10-10
> **victorche said:**
> [http://oootranslation.services.openoffice.org/pub/OpenOffice.org/stable/3.0.0/OOo_3.0.0_LinuxIntel_install_en-US.tar.gz](http://oootranslation.services.openoffice.org/pub/OpenOffice.org/stable/3.0.0/OOo_3.0.0_LinuxIntel_install_en-US.tar.gz)

I still have a hope :guitar:

Its still not offically final yet, there will be a meeting on Friday at 3pm Germany time to determine if it is stable enough to release officially on Monday Oct 13. It probably will be deemed to be releasable.

However, it will not be in Intrepid directly at least. It might make it into backports after it has had sufficient time to shake out more bugs. We had to put 2.4.1 into hardy-updates due to the amount of bugs found in 2.4.0 after its release.

---

### Post by plun on 2008-10-10
> **calc said:**
> Its still not offically final yet, there will be a meeting on Friday at 3pm Germany time to determine if it is stable enough to release officially on Monday Oct 13. It probably will be deemed to be releasable.

However, it will not be in Intrepid directly at least. It might make it into backports after it has had sufficient time to shake out more bugs. We had to put 2.4.1 into hardy-updates due to the amount of bugs found in 2.4.0 after its release.

Dear calc

Can you at least build it and put it in your ppa ?

I can see **huge strategic reasons** for rolling out Intrepid with OO-3.0 (despite of any bugs)

Just no bugs in Calc  :D

---

### Post by int on 2008-10-10
all the new linux distro also include oOo3.0. Why Ubuntu not?

Isn't stable/tested enough? 
And about Ubuntu 8.04 LTS (long version, more stable) that include Firefox 3.0 Beta, with lots of bugs(and security bugs)??

I think that Firefox 3.0 was a critical software, but also oOo 3.0 is critical, and is now final.

So, i think that Ubuntu developers can quickly test this, to give the change to go to Ubuntu 8.10 main.

---

### Post by andyrogers2008 on 2008-10-10
Any chance of the release version going into the PPA?

Andy

---

### Post by olskar on 2008-10-10
Since some distros already include this (Mandriva for example) it is going trough massive bugtesting as I write this and if Ubuntu includes it, it would help the bughunting.

Ubuntu has to remember it is not alone and there is a lot of people testing for those three weeks even if it's only three weeks.

---

### Post by hanzomon4 on 2008-10-10
Just do it!!

Ubuntu is more cautious then an old lady with bad hips.

---

### Post by ktp on 2008-10-10
I second this...just do it!!

---

### Post by stinger30au on 2008-10-11
i rekon they shuold go for it and put oo3 in ibex. its not like it is a LTS version, these are the versions of ubuntu where you want to be daring and different and go for broke and add new stuff and get it sorted so it can go in the next lts with the bugs sorted out

---

### Post by JustAboutRealJAR on 2008-10-11
I also would like to see open office 3 included in intrepid

---

### Post by tact on 2008-10-11
> **hanzomon4 said:**
> Just do it!!

Ubuntu is more cautious then an old lady with bad hips.

How short are some memories.....hehehe

Cast your mind back a matter of less than 5 months and the roar of complaints about Ubuntu putting firefox 3 into Hardy.  So many criticising that it was a poor decision etc, too risky, not cautious enough.

Including firefox 3 in Hardy, and whether or not OOo 3 makes it into Intrepid, it will be for good reasons.  So just get on with things - whether OOo 3 is in the standard install or something you have to add on later it really doesn't matter.  Coupla clicks to install (thanks ubuntu devs).  Whats the worry?

---

### Post by Kow on 2008-10-11
And then we have to remember that a great many Ubuntu users don't care if they're using OpenOffice 3.0 or 2.4 because 2.4 gets the job done. What they care about is that the program does what it is supposed to. This is a perfect example of where backports come in. OO 3.0 was, is and will be available to Intrepid users but maybe not as an officially supported package. Ubuntu should not force end-users into being bugtesters. I'm not saying OO 3.0 is loaded with bugs (I don't know yet) but statistically there should be given the amount of code involved. Imagine shipping 3.0 with the intrepid iso's and finding tons of bugs after release. This would be a disaster for all of those with a slower internet connection or none at all. The initial release packages (of any package) do not need to be perfect but they cannot have any major feature-inhibiting bugs.

FYI: OpenOffice binaries are ~300mb.

---

### Post by plun on 2008-10-11
> **Kow said:**
> And then we have to remember that a great many Ubuntu users don't care if they're using OpenOffice 3.0 or 2.4 because 2.4 gets the job done. What they care about is that the program does what it is supposed to. This is a perfect example of where backports come in. OO 3.0 was, is and will be available to Intrepid users but maybe not as an officially supported package. Ubuntu should not force end-users into being bugtesters. I'm not saying OO 3.0 is loaded with bugs (I don't know yet) but statistically there should be given the amount of code involved. Imagine shipping 3.0 with the intrepid iso's and finding tons of bugs after release. This would be a disaster for all of those with a slower internet connection or none at all. The initial release packages (of any package) do not need to be perfect but they cannot have any major feature-inhibiting bugs.

FYI: OpenOffice binaries are ~300mb.

Well....

The situation now at least within my country is that everyone are looking for alternatives to MS Office, Schools, University's, corporate institutions.

BSA and all "MS fan boys" are desperately trying to spread FUD over this...

Everyone is looking at **OO-3.0**  !!!

So despite of any bugs the road is OO-3.0 in my opinion.

(for private users this is not a challenge)

---

### Post by ajackson on 2008-10-11
I must admit I thought taking risks was part of what the non-LTS versions of Ubuntu were about, after all the lifespan for Ibex is 6 months and there is the stable Hardy to fall back on for those who don't desire bleeding-edge (and if Ibex proves Oo3s stability it should get backported to Hardy).

---

### Post by gnomeuser on 2008-10-11
OOo 3.0 is rather a large piece of kit, the upstream QA is somewhat lacking as well. Though in it's favor we have had a PPA with many active consumers for a while. 

Sadly Ibex will be an amputated shadow of it's promise, the feature list is some what comparable to Fedora 8 (one of the biggest items is NM7 which e.g was in F8 and has matured there). I wish there would have been a bit more risk taking, it is the first release after the LTS, which I personally look upon a bit like the first 2 weeks of a new kernel cycle. We heap up a lot of interesting changes then let them settle down over the next few cycles.

We ended up narrowly missing a few very important releases, Mono 2.0 and OOo 3, that will always happen but together with the rather unadventurous feature set it makes Ibex more conservative than the LTS Hardy release (and for my money more stable than Hardy - I got bitten by a nasty kernel lockup bug on both my machines).

I suspect many people will go and enable PPAs for Banshee, Mono, OOo, PackageKit, all the things Ibex missed so narrowly. The end result will likely be a QA disaster, bugs reported can't be counted on to contain know combinations of software and so on.

---

### Post by MacUntu on 2008-10-11
> **tact said:**
> How short are some memories.....hehehe

Cast your mind back a matter of less than 5 months and the roar of complaints about Ubuntu putting firefox 3 into Hardy.

That was a Firefox BETA, not the final. 

How short are some memories... ;)

---

### Post by IanW on 2008-10-11
OO3 seems to be showing up in the "stable" subdirectory of the mirrors.
UK's "mirrorservice.org" has 32- & 64-bit tarballs in [ftp://ftp.mirrorservice.org/sites/ny1.mirror.openoffice.org/stable/3.0.0/](ftp://ftp.mirrorservice.org/sites/ny1.mirror.openoffice.org/stable/3.0.0/) datestamped 10:10 BST today (GMT+1).

---

### Post by victorche on 2008-10-11
We can put FF 3.0 Beta in a LTS release (Hardy) and we can NOT put such an important package as OO 3.0 Final in a normal release...
So LTS has a BETA browser...
NORMAL release has not a FINAL office suite :confused:
How it is possible that Mandriva 2009.0 was released few days ago and it HAS OO 3.0?
There is almost a month until the release... We are not asking you to code a new office suite. Just to include already released one ;)

---

### Post by Swarms on 2008-10-11
I posted it to Brainstorm and it got pretty many votes before it got closed. Funnily enough, apparently it is not an idea.
[http://brainstorm.ubuntu.com/idea/14249/](http://brainstorm.ubuntu.com/idea/14249/)

---

### Post by MALEADt on 2008-10-11
> **victorche said:**
> So LTS has a BETA browser...
NORMAL release has not a FINAL office suite


I don't fully understand this one either. Even if the final releast contains some bugs, they'll get reported and fixed fast enough as OO-3.0 already got included in other distro's (Mandriva). The fact that Mandriva has already released will only speed up this process.

---

### Post by olskar on 2008-10-11
> **victorche said:**
> We can put FF 3.0 Beta in a LTS release (Hardy) and we can NOT put such an important package as OO 3.0 Final in a normal release...
So LTS has a BETA browser...
NORMAL release has not a FINAL office suite :confused:
How it is possible that Mandriva 2009.0 was released few days ago and it HAS OO 3.0?
There is almost a month until the release... We are not asking you to code a new office suite. Just to include already released one ;)

Well, Intrepid includes 2.4.1, that is a final version, just not the latest? ;)

But as I have already stated, I am strongly in favor of including OO.o 3

---

### Post by olskar on 2008-10-11
> **MALEADt said:**
> I don't fully understand this one either. Even if the final releast contains some bugs, they'll get reported and fixed fast enough as OO-3.0 already got included in other distro's (Mandriva). The fact that Mandriva has already released will only speed up this process.

Yeah, exactly what I meant

---

### Post by tact on 2008-10-11
> **MacUntu said:**
> That was a Firefox BETA, not the final. 

How short are some memories... ;)

Which makes the move even more daring etc...  in contrast to the poster I challenged who was saying ubuntu is a "never take risks" distro.  hehe

---

### Post by ajackson on 2008-10-11
To be fair the devs were more or less forced to take Firefox 3 as support for Firefox 2 was being dropped very early on in Hardys LTS period, if FF2 support was around for longer Hardy, IMO, would have shipped with FF2.

---

### Post by int on 2008-10-11
I think that OpenOffice 3.0 is critical software and must be always up to date.

Also FF3.0, Gnome, Kernel..

And this 3 programs have bugs :)


I think that the QA of OpenOffice 3.0 Final is more stable that Kernel and Gnome.

---

### Post by Sef on 2008-10-11
My feeling is that it will be available in the backports.

---

### Post by plun on 2008-10-11
> **olskar said:**
> Well, Intrepid includes 2.4.1, that is a final version, just not the latest? ;)

But as I have already stated, I am strongly in favor of including OO.o 3

Well.. 19 days

[http://www.ubuntu.com/getubuntu/countdown](http://www.ubuntu.com/getubuntu/countdown)

Someone wrote about an "Old Lady" before and maybe her name starts with a D...:)

The reputation of 8.04 was ruined because of too many bugs. (despite of 8.04.1) but I cannot see any reason to not include OO 3.0

---

### Post by evymetal on 2008-10-11
> **int said:**
> I think that OpenOffice 3.0 is critical software and must be always up to date.


I disagree - I see this more like database software or version control - the most important thing is that it's 100% stable and won't lose data, and features come second after that. I think most people who just use software would agree, so I support keeping version 3 to backports.

---

### Post by aldeby on 2008-10-11
I also look forward for having OpenOffice 3.0 available, at least into backports. 

I can understand being cautious with a LTS release, but hey this shouldn't mean being paranoid also with normal releases. Most of people who use linux are keen to glitches and bugs, and for those who are not here they come the LTS releases!

Please devs, be brave when you can!

---

### Post by JGrubbs on 2008-10-11
We have been testing  all the RC's for OOo 3.0 on our Windows and Max boxes at the office, and will be moving to transition the entire company from MS Office to OOo 3.0 starting next week. They stable 3.0 was available on all the mirrors on Friday, they will have the "official" launch party on Monday. I think it makes sense for OOo 3.0 to be included with the final 8.10, which I have already been running as an early upgrade for about a week now.

---

### Post by canabal on 2008-10-11
> **plun said:**
> Well.. 19 days

[http://www.ubuntu.com/getubuntu/countdown](http://www.ubuntu.com/getubuntu/countdown)

Someone wrote about an "Old Lady" before and maybe her name starts with a D...:)

The reputation of 8.04 was ruined because of too many bugs. (despite of 8.04.1) but I cannot see any reason to not include OO 3.0

The reputation of hardy was ruined because it was an LTS.  An LTS should not have had firefox 3 beta (the main example) as the default web browser.

intrepid is not an LTS and they are being MORE risky than they were with hardy?  that makes no sense.

OOo is a FINAL version, not a beta, it should be included, full stop.

---

### Post by plun on 2008-10-11
> **canabal said:**
> The reputation of hardy was ruined because it was an LTS.  An LTS should not have had firefox 3 beta (the main example) as the default web browser.

intrepid is not an LTS and they are being MORE risky than they were with hardy?  that makes no sense.

OOo is a FINAL version, not a beta, it should be included, full stop.

8.04.0 was a mess and Firefox 3 was a minor problem, IMHO
Around 150 updates between 8.04.0 > 1

I am rather sure that Sun pushes OO-3.0 and all software includes more or less with bugs.

So therefore it must be tested... now we also have a situation with Fedora 10, OpenSuse 11, Mandriva 2009 is out and all of them includes 00-3.0

Debian will not.... (the old lady)    

I am rather sure that it will not be any problems with OO-3.0 :)

---

### Post by psyke83 on 2008-10-11
> **canabal said:**
> The reputation of hardy was ruined because it was an LTS.  An LTS should not have had firefox 3 beta (the main example) as the default web browser.

intrepid is not an LTS and they are being MORE risky than they were with hardy?  that makes no sense.

OOo is a FINAL version, not a beta, it should be included, full stop.

Give me a break. Hardy shipped with flaws (especially a misconfigured PulseAudio), but it's reputation was *not* ruined because of Firefox 3. It turned out to be a wise decision (especially since the 8.04.1 remaster).

OOo is a complex piece of software. I tested the 3.0 RC debs and noticed that the font rendering hasn't been patched to reflect the new LCD subpixel filtering. Little issues like these also need addressing, and considering that it seems to take a whole day for a single build of OOo to complete, a decision should be made soon.

---

### Post by canabal on 2008-10-11
> **psyke83 said:**
> Give me a break. Hardy shipped with flaws (especially a misconfigured PulseAudio), but it's reputation was *not* ruined because of Firefox 3. It turned out to be a wise decision (especially since the 8.04.1 remaster).

Fine, pulse was the main example, but my point still stands, hardy was not stable enough for an LTS but they are trying to make intrepid stable instead it seems.

---

### Post by smartboyathome on 2008-10-11
I see Firefox is brought up a lot here. The reason Firefox 3 was included (for those that don't remember) is because Hardy was supported for 3 years, and they couldn't support Firefox 2 for that long. They can, however maintain OO.o 2 for the 1.5 years that Ibex will be around without much loss in stability. After all, there will always be backports.

---

### Post by Jim March on 2008-10-11
I'm running oo3 RC4 with zero problems, and I've been pushing both the writer pretty hard plus testing the optional PDF editing modules with big (BIG) hairy PDFs with nary a hickup.  If anything was gonna choke, that'd be it...

One warning though: I pulled RC4 and tried to load the official .deb installs for the final release and it blew up bigtime - absolutely crashed on every start.  So something is wonky with those .debs and I'm back to RC4.

This is on a fairly standard machine: Intrepid 32 with all updates on a Dell laptop with Intel 965 graphics.  The only weirdness is that I've pulled ALSA and put in OSS4 sound (no PulseAudio) due to an ALSA buggie.  I rather doubt that would make oo3 blow up (esp. when RC4 is rock solid) but I'll note it as my variance from Intrepid standard.

---

### Post by plun on 2008-10-13
> **smartboyathome said:**
> I see Firefox is brought up a lot here. The reason Firefox 3 was included (for those that don't remember) is because Hardy was supported for 3 years, and they couldn't support Firefox 2 for that long. They can, however maintain OO.o 2 for the 1.5 years that Ibex will be around without much loss in stability. After all, there will always be backports.

Yes but newbies stands away from backports and ppas... just a "mystery" for them what it is.

In this case its about giving a potential user a Ubuntu CD and just say "Please test". (or a download URL)

"Howto do" different issues will be only focused against OO 3.0.
  
So roll it out...:)

---

### Post by beameup on 2008-10-13
OOPS!

[http://tech.yahoo.com/blogs/null/106974](http://tech.yahoo.com/blogs/null/106974)

---

### Post by plun on 2008-10-13
> **beameup said:**
> OOPS!

[http://tech.yahoo.com/blogs/null/106974](http://tech.yahoo.com/blogs/null/106974)

Well another OOPS  :)

[http://blogs.zdnet.com/hardware/?p=2704](http://blogs.zdnet.com/hardware/?p=2704)


The major world wide server upload and synch was done last night and it will be officially out today.

---

### Post by linomac on 2008-10-13
Guys it is officially announced at their website

---

### Post by plun on 2008-10-13
> **linomac said:**
> Guys it is officially announced at their website 

Yup testing with Windows  :twisted:](*,)

---

### Post by Oak37 on 2008-10-13
The implementation of custom error bars for graphs was the final nail in the coffin for excel. Now I can do all aspects of my college work without Microsoft, good job OO! \\:D/

It would be great to see this in Intrepid although the PPA way is fine

---

### Post by philinux on 2008-10-13
> **Sef said:**
> My feeling is that it will be available in the backports.

+1 If it fails to make the end of October it will be an upgrade from the Backports.

---

### Post by plun on 2008-10-13
Upgrade request filed.

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/281775](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/281775)

---

### Post by kneewax on 2008-10-13
OO3 offers proper MSOffice07 support.  Not to include it in Intrepid would be a poor error of Judgement.  MS is pushing Office 2007 down users throats at the moment, with OO2 unable to read files created in MS0 we are in danger of loosing the jump on this, it has been hard enough for windoze users I know waiting for  the official OO3 release.

---

### Post by Sef on 2008-10-13
> OO3 offers proper MSOffice07 support. Not to include it in Intrepid would be a poor error of Judgement. MS is pushing Office 2007 down users throats at the moment, with OO2 unable to read files created in MS0 we are in danger of loosing the jump on this, it has been hard enough for windoze users I know waiting for the official OO3 release.

The problem with adding it is what problems are going to occur because of adding OOo3.  Thus it is unlikely to be added this late.

---

### Post by victorche on 2008-10-13
> **Sef said:**
> The problem with adding it is what problems are going to occur because of adding OOo3.  Thus it is unlikely to be added this late.

Let me ask something... Ibex will ship with Gnome 2.24
So how it is possible when it was released a couple of weeks ago?

Ibex has Flash 10 RC. As far as I know there is no official final release of Flash 10 on adobe.com

Hardy was released with Firefox 3.0 RC
How was that possible?

The answer for all those is clear. Those betas (RCs) are included during the development with all the Ubuntu Alpha's and Beta's...

So why the developers are stuck with 2.4.1? They had enough time (6 months for a release, right)... They can include a beta of Gnome, they can include a RC of Flash... And they test it and clean the bugs. And when it goes final, they just include it (no matter if if the Final is before or after the Ubuntu release)...

So now we only hear "Oh, no! It is too late for that!"

Please, someone tell me... Why they do NOT include it when it was in Beta/RC stage?

---

### Post by aaronb on 2008-10-13
> **victorche said:**
> Let me ask something... Ibex will ship with Gnome 2.24
So how it is possible when it was released a couple of weeks ago?

Ibex has Flash 10 RC. As far as I know there is no official final release of Flash 10 on adobe.com

Hardy was released with Firefox 3.0 RC
How was that possible?

The answer for all those is clear. Those betas (RCs) are included during the development with all the Ubuntu Alpha's and Beta's...

So why the developers are stuck with 2.4.1? They had enough time (6 months for a release, right)... They can include a beta of Gnome, they can include a RC of Flash... And they test it and clean the bugs. And when it goes final, they just include it (no matter if if the Final is before or after the Ubuntu release)...

So now we only hear "Oh, no! It is too late for that!"

Please, someone tell me... Why they do NOT include it when it was in Beta/RC stage?

While I'm a supporter of open office 3 being included (And looking at the current state of the website others are too :) ). It may be too late to simply cram it in now with 17 days to go.

I think it would be a lot more constructive on both sides to talk about the pro's and con's of this instead of whining/moaning.

Firefox 3.0 RC was included because Firefox 2.X would quickly become hard to support. So a risk was taken and people experienced a little pain, but by next year people using 8.04.x LTS will be better off with 3.0 than 2.0

Flash 10 RC is probably included as 9 is a pain with its extremely poor video playback performance when full screen. Flash 10 RC seems to work well. [COLOR="Grey"](Flash 10 beta constantly crashed for me).[/COLOR]

Openoffice is a really big package compared to the rest that I noted above so there is potential for issues. [COLOR="Grey"](Including a new version of X at this stage would not be fun).
[/COLOR]

**So where does this leave us?**
1. Could the people who want 3.0 installed list of pro's and con's of doing so.
2. Could the people who do not want 3.0 installed list of pro's and con's of doing so.
3. Could a Ubuntu person state the apparent pro's and/or con's and give a indication of what will happen so this can be laid to rest.

---

### Post by swj on 2008-10-13
OOO 3 is too important not to include...OOO 3 is receiving great reviews everywhere.

We need it. :)

---

### Post by victorche on 2008-10-13
> **aaronb said:**
> ...instead of whining/moaning...

I really don't want to whin/moan ;)

My question was simple. A new release will come (Call it Ubuntu X.YZ)... So someone somewhere should make a choice like:

"Hm, let's see... There is a hard development of the browser X. Beta 2 was released. So we will include this, will clean the bugs as far as we can and until our release the browser will be final, or at least will be at RC2/RC3 stage. We will also watch the development of Gnome, as version 2.8.X will be released in 5 months. So we will include 2.7.X versions, which are in alpha stage now..."

So, during the development of Ibex, we are stuck with OOo 2.4.x

Why?

There was enough time to include OOo 3.0 Beta and RC and it would be tested enough...

---

### Post by aaronb on 2008-10-13
> **victorche said:**
> Why?

Thats a good question, at a guess, it may have been because there was uncertainty at the time of alpha and maybe beta of when open office 3 would be out. (I'm sure someone with more knowledge will correct me :lolflag: )

---

### Post by andrewabc on 2008-10-13
> **aaronb said:**
> Thats a good question, at a guess, it may have been because there was uncertainty at the time of alpha and maybe beta of when open office 3 would be out. (I'm sure someone with more knowledge will correct me :lolflag: )

OOo3 was supposed to be released back in mid september but pushed back each week.
Intrepid did not have the beta or RC installed by default for people to find bugs, so to throw it in now would be a lot of work apparently.

If it is not installed by default, then I hope it is still available in synaptic to easily install.

---

### Post by xebian on 2008-10-13
Leave it in the repo for those who wants it.  Including in the CD is too much.

BTW, you can get the debs direct from OO.  But you may have to wait a while because it's so popular the servers are swamped.:guitar:

---

### Post by caco on 2008-10-14
Well I just just did that got the OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz file from their website.

Uninstall all traces of the previous OpenOffice and used the "sudo dpkg -i *.deb" method to install. Also check the desktop-integration folder for the openoffice.org3.0-debian-menus_3.0-9354_all.deb which installs the menus for me.

If you have not guessed it, I'm using Ubuntu 8.04.1

Oh least I forget do minimise the complaints the devs are only trying to protect us users of the best linux distro available:)

---

### Post by kneewax on 2008-10-14
> **caco said:**
> Ecclesiastes 3


mmmm- "There is a time for everything"  Well for OOo 3 the time is NOW!  :)

---

### Post by swj on 2008-10-14
Anyone know if there is a ooo 3 tango or human icon theme yet?

The default ooo 3 icons are ugly... ;)

---

### Post by Half-Left on 2008-10-14
> **swj said:**
> Anyone know if there is a ooo 3 tango or human icon theme yet?

The default ooo 3 icons are ugly... ;)

Yep, they've got to spend their resources now on making look part of the desktop, the default OO.o3 doesn't.

---

### Post by linomac on 2008-10-14
the openoffice.org site has only 32 bit debs
where are 64 bit debs or how i can convert these to 64 bit?
thanks

---

### Post by cendant on 2008-10-19
I installed them on 64-bit system by 

sudo dpkg -i --force-all *.deb

Oh, and you need 32-bit libraries. They can be installed easily if you get Flash

sudo aptitude install flashplugin-nonfree

---

### Post by glococo on 2008-10-21
Im using Openoffice 3 in production enviroment. Is the only competitive office software to M$.

Why not in Intrepid ???? I cant understand.
How Firefox b5 could be in hardy and OOo3 Final not in Intrepid ?

Please.. make a poll !

Thanks a lot !

---

### Post by zba78 on 2008-10-21
From the little I&#8217;ve used of OOo 3 final it seems to run fine. 

It&#8217;s a shame it wasn&#8217;t included by default but I guess as long as it&#8217;s available &#8216;somewhere&#8217; in the repositories then that&#8217;s ok.

---

### Post by Sef on 2008-10-21
This site has a [OOo 64-bit deb]("ftp://ftp.spnet.net/openoffice/stable/3.0.0/").

---

### Post by bash on 2008-10-21
Why don't you use the OpenOffice 3 from the repo provided by [[COLOR="Sienna"]**calc**[/COLOR]](http://ubuntuforums.org/member.php?u=13344). It includes OOo 3 final plus all the Ubuntu integration for both 32 and 64bit systems.

```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

---

### Post by zoomy942 on 2008-10-21
> **bash said:**
> Why don't you use the OpenOffice 3 from the repo provided by [[COLOR="Sienna"]**calc**[/COLOR]](http://ubuntuforums.org/member.php?u=13344). It includes OOo 3 final plus all the Ubuntu integration for both 32 and 64bit systems.

```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```


so, on my tablet pc which has recenntly been reinstalled - would running my update manager with these courses simply install openoffice 3?  or will it install and remove 2.4?  or will it simply update 2.4?

---

### Post by danf_1979 on 2008-10-21
The only thing I've noticed is that it is slow? Sometimes it needs several seconds to open up just some small documents (~700kB MS formats).

---

### Post by olskar on 2008-10-21
> **danf_1979 said:**
> The only thing I've noticed is that it is slow? Sometimes it needs several seconds to open up just some small documents (~700kB MS formats).

On my computer it is a lot faster then the old version

---

### Post by zoomy942 on 2008-10-21
the reason i asked about the upgrade is becasue with other debs i had used, you had to manually setup shortcuts and such.

with this, woulkd it just upgrade my 2.4 and place icons where they go and remove 2.4?

---

### Post by shane19174 on 2008-10-21
> the reason i asked about the upgrade is becasue with other debs i had used, you had to manually setup shortcuts and such.

with this, woulkd it just upgrade my 2.4 and place icons where they go and remove 2.4? 

Yes, calc's repositories will do exactly what you want. No manual setup or other such fiddling around.

I did this the other day, and everything works great.

Shane

---

