---
title: "Firefox 3.5 by default"
date: 2009-05-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phrostbyte on 2009-05-02
Firefox 3.5 should be made the default web browser early on in the development process so there is ample time to check for bugs.

---

### Post by Slug71 on 2009-05-02
My guess is that it will be default by Alpha 1 or 2. At least i hope it would be.

---

### Post by linux6994 on 2009-05-02
I know it very early for the 3.5, the Add-ons aren't available yet. By Alpha1 all should be better.

---

### Post by Nullack on 2009-05-02
Adblock plus and downthemall works fine for me, I dont need other add ons.

---

### Post by BwackNinja on 2009-05-02
You can disable version checking, most plugins work anyway.

---

### Post by medjam8 on 2009-05-03
How do you mean making Firefox 3.5 the default? Is there a way to update the Mozilla Firefox for Ubuntu to version 3.5. Or do you just have to follow these steps:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)
Because the colors from your Ubuntu theme don't work and Firefox starts using different ones and they..... well ... I hate them!

---

### Post by jmmL on 2009-05-03
firefox-3.5 is available in the karmic repos. I've just installed in a virtual machine, and it was as easy as```
sudo apt-get install firefox-3.5
```
There's also the mozilla-daily PPA which has more recent builds, as well as builds of firefox-3.6 aka minefield aka firefox.next.

---

### Post by Slug71 on 2009-05-03
> **medjam8 said:**
> How do you mean making Firefox 3.5 the default? Is there a way to update the Mozilla Firefox for Ubuntu to version 3.5. Or do you just have to follow these steps:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)
Because the colors from your Ubuntu theme don't work and Firefox starts using different ones and they..... well ... I hate them!

Meaning that Firefox 3.5 is the Browser in Karmic and not 3.x.x.

---

### Post by Seventh Reign on 2009-05-03
I say install both the Beta and the Stable Firefox together by default.  3.5 needs ALOT of work yet.  I've been using it for a few days and there's no way I could use it all the time.  Its nowhere near where 3.0 was when it was in Beta.

---

### Post by Darkshade on 2009-05-03
> **BwackNinja said:**
> You can disable version checking, most plugins work anyway.

I did that once and my AIO Sidebar (supposed to be on the left side of the Firefox window) ended on the 2nd screen :D  I wouldn't recommend it for everyone, though people in this section of the ubuntuforums are usually masochists and might enjoy it :lolflag:

---

### Post by jmmL on 2009-05-03
I'm finding 3.5 to be extremely stable at the moment. In fact, the whole trunk is so stable I'm using minefield as my day-to-day browser. The only thing that crashes it at the moment is forcing foxmarks, so I've just switched to weave instead.

---

### Post by artir on 2009-05-03
A small rant on firefox.next (Firefox 3.6): They blatantly forget linux:
[https://wiki.mozilla.org/Firefox/Namoroka](https://wiki.mozilla.org/Firefox/Namoroka)
They set as a goal
> System Integration
    Integrate with the look and feel of the host operating system, including data-level interactions with existing system services such as dictionaries. 
and they set this objectives:
>     * OSX Dictionary integration
    * OSX Services & AppleScript integration
    * OSX Keychain integration
    * Windows Aero Glass
    * Windows Aero Peek
    * Windows 7 
Where is notify-osd,  gnome-keyring-manager, etc?

---

### Post by olskar on 2009-05-03
> **artir said:**
> A small rant on firefox.next (Firefox 3.6): They blatantly forget linux:
[https://wiki.mozilla.org/Firefox/Namoroka](https://wiki.mozilla.org/Firefox/Namoroka)
They set as a goal

and they set this objectives:

Where is notify-osd,  gnome-keyring-manager, etc?

Your feedback and comments are welcomed on the discussion page.
[https://wiki.mozilla.org/Talk:Firefox/Namoroka](https://wiki.mozilla.org/Talk:Firefox/Namoroka)

:)

---

### Post by Toe on 2009-05-03
Is anybody else running into this issue with today's Firefox 3.5 updates?
```
Could not find compatible GRE between version 1.9.1b4pre and 1.9.1b4pre.
```

---

### Post by simon_wrafter on 2009-05-03
> **Toe said:**
> Is anybody else running into this issue with today's Firefox 3.5 updates?
```
Could not find compatible GRE between version 1.9.1b4pre and 1.9.1b4pre.
```

Here's a bug report and a fix I found. [371361]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/371361")

---

### Post by Toe on 2009-05-03
thank you :)

---

### Post by Neon Lights on 2009-05-04
> **Seventh Reign said:**
> I say install both the Beta and the Stable Firefox together by default.  3.5 needs ALOT of work yet.  I've been using it for a few days and there's no way I could use it all the time.  Its nowhere near where 3.0 was when it was in Beta.
How so? I've been running it since Beta 2 as my primary browser, the ONLY problem I've had is that Flash is very buggy with it.

---

### Post by caryb on 2009-05-04
I guess the viability of getting 3.5 as default would depend on the status of the release date as of October for Karmic & where 3.5 is at this time.


2c Cary

---

### Post by Slug71 on 2009-05-04
I could be wrong but last i heard was that FF-3.5 Final is due June/July 09.

---

### Post by iaskedalice09 on 2009-07-12
I agree with this.

phrostbite, I also love your avatar. I would make one that says &#1488;&#1502;&#1514; (truth) or &#1495;&#1505;&#1491; (kindness), but I doubt they'd fit into a 100x100 icon. Hmm...

---

### Post by Merk42 on 2009-07-12
> **artir said:**
> A small rant on firefox.next (Firefox 3.6): They blatantly forget linux:
[https://wiki.mozilla.org/Firefox/Namoroka](https://wiki.mozilla.org/Firefox/Namoroka)
They set as a goal

and they set this objectives:

Where is notify-osd,  gnome-keyring-manager, etc?

Considering how 3.5 is handled in Jaunty, can you blame them?

Which brings up a point, I know this thread is about 3.5 for default in Karmic, but what are the preparations for 3.6 in Karmic?
I'm very annoyed at the hoops I have to jump through to get a satisfactory 3.5 install on Jaunty.  Hopefully if 3.6 comes out **after** Karmic it will be a much smoother upgrade experience.

---

### Post by ghindo on 2009-07-12
I don't believe we will see Fx 3.6 for another year or so, so I wouldn't worry too much about the upgrade path just yet.

---

### Post by novafluxx on 2009-07-12
> **ghindo said:**
> I don't believe we will see Fx 3.6 for another year or so, so I wouldn't worry too much about the upgrade path just yet.

We'll see 3.5.x long before we see 3.6. Probably won't see FF 3.6 before 10.04

---

### Post by descendent87 on 2009-07-12
but back on subject, when will we see FF3.5 as default?

---

### Post by bekind2thenoob on 2009-07-12
> **artir said:**
> Where is notify-osd,  gnome-keyring-manager, etc?

For notify OSD integration you want the FirefoxNotify add-on

> **descendent87 said:**
> but back on subject, when will we see FF3.5 as default?

Karmic

---

### Post by descendent87 on 2009-07-12
yes I am using karmic, but when? Fedora 11 has had it for ages. What is taking ubuntu so long to update it?

---

### Post by MacUntu on 2009-07-12
Install the package firefox-3.5 - what's the big deal? Karmic is in its alpha stage so I don't understand the urge.

---

### Post by 23meg on 2009-07-12
> **artir]Where is notify-osd, gnome-keyring-manager, etc?[/QUOTE]

The majority of the work needed for keyring manager code [has been in for some time]("http://blog.mozilla.com/dolske/2007/05/28/followup-password-manager-changes-coming-in-ff3-alpha-5/"), and it's "patches welcome" for the rest. Same for notifications, probably.

Nobody depends on a few words on a wiki page to go in and implement those said:**
> This is a DRAFT document.

> **Merk42]Considering how 3.5 is handled in Jaunty, can you blame them?[/QUOTE]

Where do I start...

[list]
[*] Mozilla let us use their otherwise restricted branding by default through a trademark agreement, in exchange for a guarantee of preserving their product quality. The fact that you see a Firefox logo in the default Ubuntu installation means that the Ubuntu Mozilla Team is dedicated to preserving that quality said:**
>  The fact that you don't and won't see official Firefox branding for 3.5 in Jaunty has to do with this too (as well as our own branding policy): we only have enough workforce to maintain 3.5 as a preview / testing package in Universe. The kind of work that would be required to maintain 3.5, along with all its dependencies, which affect not just Firefox but many other applications as well in Jaunty, while satisfying Mozilla's quality requirement as well, would be huge, and even if other concerns such as not changing default top level UI elements through stable release updates were sorted out somehow, it would be completely unrealistic to assume we could undertake it.

[*] The wiki page was drafted in March, when neither Jaunty, nor Firefox 3.5 was final.
[/list]

[QUOTE=descendent87;7605532]yes I am using karmic, but when? Fedora 11 has had it for ages. What is taking ubuntu so long to update it?

This:

[https://wiki.ubuntu.com/MozillaTeam/Specs/Karmic/Firefox35Transition](https://wiki.ubuntu.com/MozillaTeam/Specs/Karmic/Firefox35Transition)

---

### Post by Slug71 on 2009-07-13
> **descendent87 said:**
> but back on subject, when will we see FF3.5 as default?

Pretty soon im guessing seeing as it was released June 30th.

---

### Post by andrewabc on 2009-07-13
> **Slug71 said:**
> Pretty soon im guessing seeing as it was released June 30th.

It better be before alpha 3 in less than two weeks.

---

### Post by novafluxx on 2009-07-14
> **andrewabc said:**
> It better be before alpha 3 in less than two weeks.

Remember, the Alpha releases are just snapshots of the repos, with the installed added on, all you're really testing with the Alpha's are the installer, and initial experience. All the packages at this point are dynamic, and whats in Alpha 3, might be changed/updated 2 days later.

---

### Post by Merk42 on 2009-07-14
Sorry about my comment 23meg, it was more sarcastic than serious.

So am I to understand the advantage you mentioned in the other thread about shared libraries is actually a disadvantage to getting a branded up to date version of Firefox?

---

### Post by andrewabc on 2009-07-14
> **novafluxx said:**
> Remember, the Alpha releases are just snapshots of the repos, with the installed added on, all you're really testing with the Alpha's are the installer, and initial experience. All the packages at this point are dynamic, and whats in Alpha 3, might be changed/updated 2 days later.

I know that. I meant if it wasn't included in alpha 3 you'd end up with lots of people complaining about why it isn't default. And also with it included with alpha 3 a lot more testing can be done.

Many people usually just download the alphas to test out.

---

### Post by 23meg on 2009-07-14
> **Merk42 said:**
> Sorry about my comment 23meg, it was more sarcastic than serious.

No worries, but overuse of sarcasm can be quite detrimental to maintaining a healthy discourse.

> **Merk42 said:**
> So am I to understand the advantage you mentioned in the other thread about shared libraries is actually a disadvantage to getting a branded up to date version of Firefox?

..as a stable release update, yes, since it introduces updated dependencies.

---

### Post by 23meg on 2009-07-14
Something else to note: [the Firefox 3.5 transition spec]("https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-firefox-3.5") is targeting the beta.

---

### Post by Merk42 on 2009-07-14
> **23meg said:**
> No worries, but overuse of sarcasm can be quite detrimental to maintaining a healthy discourse.



..as a stable release update, yes, since it introduces updated dependencies.

I apologize;
You accept;
We agree on something;


I'm pretty sure Hell just froze over...

---

### Post by Slug71 on 2009-07-14
> **23meg said:**
> Something else to note: [the Firefox 3.5 transition spec]("https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-firefox-3.5") is targeting the beta.

Beta?? This must mean it has a Freeze Exception? Why cant it be in before that?

---

### Post by 23meg on 2009-07-15
> **Slug71 said:**
> Beta?? This must mean it has a Freeze Exception?

It can get a standing freeze exception, as was the case during the 3.0 transition.

> **Slug71 said:**
> Why cant it be in before that?

It can; the fact that it's *targeting* the beta doesn't mean it will definitely happen at the beta stage. Nevertheless, if you read the spec, you'll note that there's a lot to do. I think we'll switch to 3.5 as default some time after Alpha 3, and the transition will be completed shortly before the beta release. This is purely my estimation based on the progress of the Mozilla Team's transition PPA ([https://edge.launchpad.net/~mozillateam/+archive/ffox35](https://edge.launchpad.net/~mozillateam/+archive/ffox35)), and cursory IRC impressions, though; don't hold me up to it. You may want to check with the Mozilla team if you want more details.

---

