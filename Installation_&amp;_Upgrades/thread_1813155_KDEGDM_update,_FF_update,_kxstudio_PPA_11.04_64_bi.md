---
title: "KDE/GDM update, FF update, kxstudio PPA 11.04 64 bitAMD"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by ken78724 on 2011-07-27
Bear with me as there's a series of problems. Look also at Toz's guidance in [http://ubuntuforums.org/showthread.php?t=1789514](http://ubuntuforums.org/showthread.php?t=1789514). I do not understand the two lines in the repositories referred to in No. 4 in this posting and in my last posting to this thread.
  1) a routine 18 MB FireFox internal update fails to open with U able to set a new URL, open "gmail.com" or another http,,, chrome opens but has a similar dysfunction; is like something is frozen. A) Firefox failed to open giving you a chance to set a URL; there's no way to get back to a prior page; b) after the 18 mb internal update, as before all I get is a search screen & no way to page back or page ahead except to shut the page and reopen. I don't know how to describe the hang up.
  2) two days back I did a terminal sudo apt-get install kubuntu-desktop but failed to select kde or gdm [and now cannot do the config which sets kde as my preference. Since doing the sudo kubuntu install, I see a kubuntu page, then a blank dark blue page that slowly opens as the pre-terminal kubuntu install.   
  3) about 20 days back to get my Canon pisma mx420 I did a terminal sudo as recommended by ubuntubuzz.com and gave up as the ppa solely made CUPS contact with my new printer but fails to print; my $5 HP LaserJet bought out of a flea market prints well showing CUPS will deliver 
  4) falkTX's kxstudio ppa appears to have mounted okay but I've not had time to do any video production. I can neither say or not say if the ppa for kxstudio functions or does not function

Please help. Problems one and two are critical. I feel configuration of the kde vs. gdm selection which is supposed to happen before one does a sudo apg-get remove ubuntu-desktop and then sudo apt-get autoremove may be a solution. Do please share light on what must be done. Wow, it takes three-six minutes to post my description once written. Do not get why all this extra time was needed.

If I should report this as a bug, let me know. 

Note, am running 11.04 amd 64bit built to kxstudio, which does not boot with the ubuntu studio icon. oh yes, I have a 4 or 6 gig video card and I believe 4 gig of ram on this PC.

---

### Post by ken78724 on 2011-07-27
Lovinglinux, Toz, & falkTX please look at the respective issues raised in 11091612 - [http://ubuntuforums.org/showthread.php?t=1789514](http://ubuntuforums.org/showthread.php?t=1789514), which I posted @ 4 AM, July 27th

falkTX & Toz
the kxstudio PPA was done 3 weeks back with terminal, where I believe Toz found that I wrongly specified "kernal repositories" instead of "kernel repositories" then I wasn't able to delete two lines where it showed up. I posted a review of the lines in another thread dealing with your ppa. Is my problem because I do not know how to remove the "kernal" influence on the ppa functionality?

lovinglinux
this morning after i've had no url line across the top of Firefox 5.0 making it necessary to put a http in google search and going to the desired http in a round about method. then an auto update showed me there was an 18 MB FF update, which I watched. I rebooted and signed back in only to find there still is no url line across the top of Firefox. I recall a simple correction could be done but not in the past weeks while working on this PC with 11.04 OS. Downloaded 6.0~b3+build2+nobinonly-0ubuntu0.11.04.1~mfn1 (firefox-dbg). Instead 6.0~b3+build2+nobinonly-0ubuntu0.11.04.1~mfn1 (firefox)
is installed.

anyone else having mastered a Canon MX420, please advise how to achieve what ubuntubuzz.org gurus say is feasible. 

If I should move any part of this to launchpad,please advise via email @ koymkg at gmail.com.:popcorn:
Thanks,

---

### Post by ken78724 on 2011-08-02
> **ken78724 said:**
> respective issues raised in 11091612 - [http://ubuntuforums.org/showthread.php?t=1789514](http://ubuntuforums.org/showthread.php?t=1789514)posted July 27th
 now partially solved - see launchpad.net Bug #819095 in Ubuntu Mozilla PPA Bugs: “no url bar exists". Thanks to Toz for explaining how to remove two lines showing "kernal" a misspelling. The removal alleviated a bit of the slowness.   
When >  the kxstudio PPA was done Toz found I wrongly specified "kernal repositories" instead of "kernel repositories"(. first) I wasn't able to delete two lines . Later I applied Toz's solution and did a save. That enhanced >  the ppa functionality  speed. 

I >  had no url bar in Firefox 5.0 making it necessary to put a http in google search. I learned from a FF discussion in Ubuntu One I could click on my PC's "ALT key", click "View" and "Navigate" & "Customize" and then see a URL bar. That response sure made me happy after 20 days of seeking a solution. 

Other bugs exist as I tried to >  Download 6.0~b3+build2+nobinonly-0ubuntu0.11.04.1~mfn1 (firefox-dbg). Instead (I learned ) 6.0~b3+build2+nobinonly-0ubuntu0.11.04.1~mfn1 (firefox)  had been installed. I see no evidence that FF 6.0 or 6.0 Beta 3 has been installed. But, a bug apparently prevented me from saving my first write up of this posting. All that was lost and the forum effort to capture the error and my feedback was lost. 

I'd welcome anyone's guidance who's >  mastered a Canon MX420 ppa driver installation using the ubuntubuzz.org guide or the Ubuntu One. 

Unraveling the remaining parts of this bug means seeing [QUOTE] launchpad Bug #819095. Helping to perfect each of these PPAs could be most helpful to those wanting to enjoy the benefits of the kxstudio ppa; the Install / Upgrade KDE 4.7.0 to Kubuntu via PPA KDE; the Canon printer PPA; and, the higly advanced Firefox 5.0, Firefox 5.0.1, and Firefox 6.0 Beta and Beta 3. 

Thanks to each of you, especially Toz!

---

