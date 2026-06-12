---
title: "Open office 3.x will be included?"
date: 2008-05-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by curtis on 2008-05-20
Open office 3.x will be included?
As I will help out with packaging if need be.

---

### Post by meborc on 2008-05-20
if OOo keeps to its release schedule then yes... the prognosis is that it will be released in september, in that case it will end up in intrepid

to ensure that, please help test the beta builds of OOo... have been running 3.0 for a few weeks now :)

---

### Post by steeleyuk on 2008-05-20
It should be included anyway. Firefox 3 Beta made it in.

---

### Post by tamoneya on 2008-05-20
> **meborc said:**
> if OOo keeps to its release schedule then yes... the prognosis is that it will be released in september, in that case it will end up in intrepid

to ensure that, please help test the beta builds of OOo... have been running 3.0 for a few weeks now :)

Good idea.  I plan on setting up virtual box with 8.10 when the alpha comes out.  First thing I will do is install OOo 3.0

---

### Post by meborc on 2008-05-20
> **tamoneya said:**
> Good idea.  I plan on setting up virtual box with 8.10 when the alpha comes out.  First thing I will do is install OOo 3.0

you can install OOo 3.0 next to 2.4 ... i have them both and i have no problems... 2.4 is opened by default when .odt file is opened... but OOo 3.0 can be launched from /opt/openoffice.org3/program/soffice

so no worries, try it out now ;) just be sure to use 2.4 for any important files

---

### Post by Eclipse. on 2008-05-20
> **steeleyuk said:**
> It should be included anyway. Firefox 3 Beta made it in.

Firefox 3 beta was a huge exception, to give support for firefox 2 for hardy's lifetime would have been very difficult..

OO.o 3 should be finished by intrepid's release.

---

### Post by steeleyuk on 2008-05-21
> Firefox 3 beta was a huge exception, to give support for firefox 2 for hardy's lifetime would have been very difficult..

It wasn't that much of an exception.

Didn't Gutsy initially come with the Release Candidate of The GIMP? OpenOffice should be at that stage even if it is delayed when Intrepid comes out.

---

### Post by Eclipse. on 2008-05-21
> **steeleyuk said:**
> It wasn't that much of an exception.

Didn't Gutsy initially come with the Release Candidate of The GIMP? OpenOffice should be at that stage even if it is delayed when Intrepid comes out.

Gutsy wasnt a LTS release though and the web browser is the most used piece of software in a operating system.RCs are basically the exact same as final releases unless any showstopper bugs pop up.

---

### Post by steeleyuk on 2008-05-21
Its still development software in a release. Not that theres anything wrong with that when you take into consideration that you're going to have to support that software until the end of the support period.

> and the web browser is the most used piece of software in a operating system

You could look at it the other way and say that because its the most used, it also needs to be the most stable and compatible (thinking in terms of addons/plugins).

---

### Post by syxbit on 2008-05-22
> **steeleyuk said:**
> It wasn't that much of an exception.

Didn't Gutsy initially come with the Release Candidate of The GIMP? OpenOffice should be at that stage even if it is delayed when Intrepid comes out.

gutsy STILL has the rc3 version of the GIMP
i'm completely mesmerised that they didn't upgrade it.
oh well, we're all in hardy now anyway :)

---

### Post by ssam on 2008-05-22
> **syxbit said:**
> gutsy STILL has the rc3 version of the GIMP
according to:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gimp&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gimp&searchon=names&subword=1&version=all&release=all)
gimp 2.4.2 got into gutsy-updates.

---

### Post by Gina on 2008-05-22
I'm on GIMP 2.4.5 :)

---

### Post by meborc on 2008-05-23
> **Gina said:**
> I'm on GIMP 2.4.5 :)

and i'm on gimp 2.5 beta... but it doesn't matter cuz i really don't have an artistic side :(

---

### Post by ronacc on 2008-05-23
I checked the OO site and didn't see a 64bit .deb should I force the I386 .deb or dl the sources and build ?

---

### Post by JACooks on 2008-05-23
> **ronacc said:**
> I checked the OO site and didn't see a 64bit .deb should I force the I386 .deb or dl the sources and build ?

You could wait, according to [http://blogs.sun.com/GullFOSS/entry/openoffice_org_builds_for_linux]("http://blogs.sun.com/GullFOSS/entry/openoffice_org_builds_for_linux") they should have some 64bit builds soon(ish).  Or, there are some instructions in the comments [here]("http://tombuntu.com/index.php/2008/05/08/test-drive-openoffice-3-beta-in-ubuntu/") that talk about how to force the i386 .deb.

---

### Post by ronacc on 2008-05-23
looks like it will still be a bit before the official 64bit builds show up , the link you gave said about M11 and the current is M2 . I think I'll dl the sources and local build , if that don't work I can force the I386 .deb . Thanks

---

### Post by JACooks on 2008-05-23
Closer than you think, the BEA300_m2 is a branch for their beta's.  The m11 referred was their dev tree, which is currently at DEV300_m10 ([release notes, build info at top]("http://development.openoffice.org/releases/3.0.m2_snapshot.html")).  But building from source is always fun, too.

---

### Post by ronacc on 2008-05-24
I took a look at the sources and changed my mind :confused: There dosen't seem to be a master makefile and building dozens of components individualy would require more time than I can give it ( my time not the boxes ) . I'll go ahead and force the i386.deb and then puge and replace it with a 64bit when one shows up.

---

### Post by Sockerdrickan on 2008-05-25
> **meborc said:**
> and i'm on gimp 2.5 beta... but it doesn't matter cuz i really don't have an artistic side :(

You hurt my eyes lol :(

---

### Post by twright on 2008-05-30
> **ronacc said:**
> I took a look at the sources and changed my mind :confused: There dosen't seem to be a master makefile and building dozens of components individualy would require more time than I can give it ( my time not the boxes ) . I'll go ahead and force the i386.deb and then puge and replace it with a 64bit when one shows up.it takes 10 hours to compile (apparently) :)

you can just run the normal windows one under wine

---

### Post by BCurtisWX on 2008-07-06
What are the reason as to why OOo 3.0B2 isn't available in the hardy repos yet?

---

### Post by Amaranth on 2008-07-07
Because it isn't going to happen.

---

### Post by ad_267 on 2008-07-07
> **BCurtisWX said:**
> What are the reason as to why OOo 3.0B2 isn't available in the hardy repos yet?

That's not how things work. Updates only include security and bug fixes.

---

### Post by BCurtisWX on 2008-07-07
> **ad_267 said:**
> That's not how things work. Updates only include security and bug fixes.

whoops... i meant intrepid (hence why its in intrepid discussion). Sorry about that. :(

---

### Post by nanog on 2008-07-07
Wine is actually the recommended method of running bleeding-edge FOSS in ubuntu. (joking)

And BTW OOo3B2 works great in wine on x64! Really snappy and it prints unlike the forced deb build.

---

### Post by caryb on 2008-07-07
I have installed the 32 bit ooo3 on my 64 bit pc & it works fine! interestingly I had to use my Vista partition last week (I feel sooo cheap) when my Kubuntu was in lala land & installed the windows version, it had so many bugs like select save as in calc & it made ooo unresponsive but in Linux it works flawlessly:lolflag:


Cary

---

### Post by DPic on 2008-09-21
so what's the status with including openoffice in intrepid? according to this [https://wiki.ubuntu.com/OOo30Schedule](https://wiki.ubuntu.com/OOo30Schedule) shouldn't it already be there?

---

### Post by amano on 2008-09-21
From what I heard, it is not decided if it will make it at all. It seems that calc isn't happy with its current state. Just having a RC stamp on it doesn't mean that it is at release quality yet.

Thus it is planned to either make it an optional install from the universe repository or to backport it when it is considered ready...

---

### Post by stinger30au on 2008-09-21
at ubuntu brainstorm all the messages i have seen from the devs says oo3 will be included in 8.10

the release date for the final 003 is october 30th

---

### Post by meborc on 2008-09-21
> **stinger30au said:**
> at ubuntu brainstorm all the messages i have seen from the devs says oo3 will be included in 8.10

the release date for the final 003 is october 30th

OOo has never been very "punctual" when it comes to deadlines ;)

---

### Post by andrewabc on 2008-09-21
> **meborc said:**
> OOo has never been very "punctual" when it comes to deadlines ;)

I expect RC2 to be out tomorrow. They only had 4 known bugs to fix when they missed RC2 last monday.
Actually it looks like 3 are still not fixed.

---

### Post by meborc on 2008-09-21
well i truly hope OOo3 will make it in... office suit being an important part of an OS - i understand why one would like to make an freeze exception :)

---

### Post by IanW on 2008-09-22
> **stinger30au said:**
> the release date for the final 003 is october 30th

Unfortunately for us, that is also the release date for 8.10 final.
We'll probably have to wait for a backport.

---

### Post by fakewcfrog on 2008-09-22
Ah well, if it doesn't get included I'll use the PPA. After all, it gets swifter updates. :)

---

### Post by andrewabc on 2008-09-22
> **IanW said:**
> Unfortunately for us, that is also the release date for 8.10 final.
We'll probably have to wait for a backport.
The person is mistaken. The release date is around September 30.
Release Candidate 2 was released today. So expect the final version to be out in a week or two.

[http://download.openoffice.org/680/](http://download.openoffice.org/680/)

---

### Post by DPic on 2008-09-22
either way, we made an exception for firefox 3, but we won't for OpenOffice 3? Intrepid isn't even an LTS!

---

### Post by zoomy942 on 2008-09-22
to get the 64bit deb, i go to that stupid bouncer page.

anyone have a direct link to the debs for 64bit ubuntu?

---

### Post by andrewabc on 2008-09-22
> **DPic said:**
> either way, we made an exception for firefox 3, but we won't for OpenOffice 3? Intrepid isn't even an LTS!

I'm confused. They included firefox 3 because it would be impossible to maintain firefox 2 for 3 years.
Maintining openoffice 2.4.x for 18 months wont be as difficult.

And yes I definitely want openoffice 3 in intrepid, but I don't fully expect it since they havn't included any of the 3.0 series yet. But according to a bug at launchpad they are testing to see if it is possible.

---

### Post by lonniehenry on 2008-09-22
see new post in forums under 64 bits about oo3  works today 8/23/08

---

### Post by altonbr on 2008-09-23
Once I have OpenOffice 3.0 (OOo3) installed in Ubuntu 8.04.1 via 'sudo dpkg -i *.deb', how do I run it? No matter what I try, I keep getting 2.4, the version included with Ubuntu.

---

### Post by olskar on 2008-09-23
> **altonbr said:**
> Once I have OpenOffice 3.0 (OOo3) installed in Ubuntu 8.04.1 via 'sudo dpkg -i *.deb', how do I run it? No matter what I try, I keep getting 2.4, the version included with Ubuntu.

Check in /opt

---

### Post by lonniehenry on 2008-09-23
opt/openoffice.org3/program/soffice

---

### Post by olskar on 2008-09-24
Hm,I recently tried latest rc and powerpoint slideshows does not work for me, I can open but when I try to slideshow it all I get is black

---

### Post by xlinuks on 2008-09-24
If you have compiz enabled try disabling it.

---

### Post by olskar on 2008-09-24
> **xlinuks said:**
> If you have compiz enabled try disabling it.

That was my first thought but it didn't help

---

### Post by TerpInHotLanta on 2008-10-01
> **zoomy942 said:**
> to get the 64bit deb, i go to that stupid bouncer page.

anyone have a direct link to the debs for 64bit ubuntu?

Go to the download page: [http://download.openoffice.org/680/](http://download.openoffice.org/680/)
and about a quarter down the page it says 

"If the following Bouncer links do not work then please select one of the mirrors listed at the distribution page and download the binary from the ../contrib/rc/3.0.0rc3/ directory or select the no javascript page."

Just follow the link to the distribution page.

Sorry for the choppy reply-- it's early at work on so few hours of sleep.

Enjoy!

---

### Post by kyleabaker on 2008-10-02
I really hope Open Office 3 makes it into Intrepid. With all of this hype building up about Ubuntu in the news lately they'll need to make sure that they are serving the latest versions of everything...labeled stable of course. ;)

I mean, VLC 0.9.2 made it in and that's just great news for Ubuntu users! Hopefully GIMP 2.6 will make the cut as well. I'm about to install v3 and see how it goes.

---

### Post by stewacide on 2008-10-02
So is it OK to install the RC3 .deb directly from OOo?

---

### Post by smartboyathome on 2008-10-02
> **stewacide said:**
> So is it OK to install the RC3 .deb directly from OOo?

Sure, I'm installing it from there. I would say it is a trusted source and they probably won't slip any bad code into it. ;)

---

### Post by Sef on 2008-10-02
I have OOo 3 installed, but don't have time to check it out.  Sigh.....

---

### Post by JACooks on 2008-10-02
Looks like there will be an RC4, per [http://www.openoffice.org/servlets/ReadMsg?list=releases&msgNo=12683](http://www.openoffice.org/servlets/ReadMsg?list=releases&msgNo=12683).  New expected final release date is Oct. 14th.

---

### Post by Ub1476 on 2008-10-02
I hope they fix the issue that I can't open files (64-bit)..

Always crashes when I choose "open with" or try to open from the new window thingy. Works from the menu though..

---

### Post by zoomy942 on 2008-10-02
i just hope its included in the final Intrepid release

---

### Post by smartboyathome on 2008-10-02
> **zoomy942 said:**
> i just hope its included in the final Intrepid release

I guarentee it won't. The release date for Intrepid is too close to the release date for OpenOffice.org 3 (only just over 2 weeks between the current scheduled OpenOffice.org 3 release and the Intrepid Ibex release, which is not nearly enough time for testing).

---

### Post by zoomy942 on 2008-10-02
> **smartboyathome said:**
> I guarentee it won't. The release date for Intrepid is too close to the release date for OpenOffice.org 3 (only just over 2 weeks between the current scheduled OpenOffice.org 3 release and the Intrepid Ibex release, which is not nearly enough time for testing).


thats a shame.

It would be ince to have it integrate how 2.4 does.  I have tried 3.0 and I like it but i dont know how to remove 2.4

---

### Post by smartboyathome on 2008-10-02
> **zoomy942 said:**
> thats a shame.

It would be ince to have it integrate how 2.4 does.  I have tried 3.0 and I like it but i dont know how to remove 2.4

Open Synaptic and remove everything with OpenOffice.org in its name (not OpenOffice.org3) except openoffice.org-ure (which is a dependancy of OO.o 3).

---

### Post by nanog on 2008-10-02
The  RC2 in the PPA works perfectly for me in 64 bit (on 3 boxes). It is well-integrated into ubuntu (e.g. replaces 2.4).

```

#calcs_open_office_ppa
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main

```

---

### Post by nanog on 2008-10-02
@smartboyathome
At one point removal of the open office meta package resulted in removal of ubuntu-desktop. Has this been changed?

---

### Post by Ub1476 on 2008-10-02
> **nanog said:**
> The  RC2 in the PPA works perfectly for me in 64 bit (on 3 boxes). It is well-integrated into ubuntu (e.g. replaces 2.4).

```

#calcs_open_office_ppa
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main

```

I'll try that on the beta in x minutes/hours. 

Does anypone know when dictionaries (except for english) will be available for ooo3?

---

### Post by zoomy942 on 2008-10-02
> **nanog said:**
> The  RC2 in the PPA works perfectly for me in 64 bit (on 3 boxes). It is well-integrated into ubuntu (e.g. replaces 2.4).

```

#calcs_open_office_ppa
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main

```


whats the difference between using this and just download the deb?

---

### Post by smartboyathome on 2008-10-02
> **nanog said:**
> @smartboyathome
At one point removal of the open office meta package resulted in removal of ubuntu-desktop. Has this been changed?

I guess so, as it didn't remove Ubuntu desktop for me.

---

### Post by zoomy942 on 2008-10-02
the oinly thing i dont like is the integration with Gnome is nice with 2.4.  3.0 doesnt inegrate like it.

---

### Post by danf_1979 on 2008-10-05
Will RC2 be updated to RC3 in calc's PPA?

:)

---

### Post by andrewabc on 2008-10-05
> **danf_1979 said:**
> Will RC2 be updated to RC3 in calc's PPA?

:)

RC4 is probably being released tomorrow, so might as well wait :P

---

