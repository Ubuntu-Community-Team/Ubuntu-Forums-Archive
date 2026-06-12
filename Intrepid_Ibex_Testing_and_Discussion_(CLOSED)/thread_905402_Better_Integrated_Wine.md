---
title: "Better Integrated Wine"
date: 2008-08-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by MadsRH on 2008-08-30
There's a lot of great ideas on what could be done to get Wine integrated better in Ubuntu, but will anything happen in 8.10?

[https://wiki.ubuntu.com/BetterIntegratedWineSpec](https://wiki.ubuntu.com/BetterIntegratedWineSpec)

I can't find any news about the progress on the feature thread ([http://ubuntuforums.org/showthread.php?t=886980](http://ubuntuforums.org/showthread.php?t=886980)) and I can't find any mailinglists discussing Wine :confused:
[B]
//MadsRH [/B]

---

### Post by olskar on 2008-08-30
Spec says "Not started", looks dead to me

---

### Post by taavikko on 2008-08-30
Sorry for rather boring answer but why?
for almost every program there's an native alternative.

Games must be the main reason to use wine.
For that purpose only, better to have dualboot system, or
somne kind of an console (xbox, psX and so on)

---

### Post by Sand &amp; Mercury on 2008-08-30
I think it'd be against the general idea of using Linux to include Wine by default; People should be directed to Linux for the idea of using Linux, not "a better Windows" if you get my drift. Wine is great but to my mind I think on from an official perspective, it's best left being treated as a nice luxury instead of something that you come to Linux expecting to use. Mac OS has no bundled Windows emulation/compatibility capabilities either and I think that is so for a reason.

---

### Post by Gina on 2008-08-30
> **Sand & Mercury said:**
> I think it'd be against the general idea of using Linux to include Wine by default; People should be directed to Linux for the idea of using Linux, not "a better Windows" if you get my drift. Wine is great but to my mind I think on from an official perspective, it's best left being treated as a nice luxury instead of something that you come to Linux expecting to use. Mac OS has no bundled Windows emulation/compatibility capabilities either and I think that is so for a reason.Yes, I think I would agree with that.

---

### Post by gnomeuser on 2008-08-30
> **Sand & Mercury said:**
> I think it'd be against the general idea of using Linux to include Wine by default; People should be directed to Linux for the idea of using Linux, not "a better Windows" if you get my drift. Wine is great but to my mind I think on from an official perspective, it's best left being treated as a nice luxury instead of something that you come to Linux expecting to use. Mac OS has no bundled Windows emulation/compatibility capabilities either and I think that is so for a reason.

I would agree, if someone wants a good platform for running Windows apps one already exists.. namely Windows. 

Some of the risks in pretending to be Windows compatible is:

A) User disappointment, you promise 100% compliance and that is bound to fail thus turning users off Linux.

B) You risk turning Linux into the gratis Windows instead of letting it shine on it's own merits.

C) By promoting WINE officially you also indirectly push for the Windows API to be the API of choice for cross platform development. An API we have to chase, yet have no control over nor any openness. This is the very method by which IBM' otherwise excellent OS/2 commited suicide.

---

### Post by MadsRH on 2008-08-30
I agree with the posts above. However the idea was never to include Wine by default, but simply to present the user with a "*You need to install Wine to run this application*" dialog when running a exe file or similar.

The purpose is not to pretend to be Windows, but the improve the user experience.

---

### Post by Sophont on 2008-08-30
> **MadsRH said:**
> I agree with the posts above. However the idea was never to include Wine by default, but simply to present the user with a "*You need to install Wine to run this application*" dialog when running a exe file or similar.

The purpose is not to pretend to be Windows, but the improve the user experience.

And this is exactly right.

Yes- don't include it by default.
The purists don't want it and the office worker or granny won't usually need it.

It boils down to:
* Games
* Windows only niche application used by company
* Photoshop

And in all of these cases dual-booting windows is *not* the better alternative if wine is up to the job - and it often is nowadays.

Before I switched to Linux I looked for Linux replacements for all my apps. And that wasn't much of a problem. Except for 1 game that I play (EVE Online). Being able to install IE6 for testing purposes (web apps that I need to verify) is a bonus (thanks to IE4Linux). If I get in the mood to play HL2, Warcraft3, Starcraft or Total War: Rome - they too all work via wine.

Who in his right mind would keep a windows paritions, waste a lot of HDD space and re-boot all the time when s/he doesn't have to?
Dual booting is a silly PITA when there's such an easy alternative.

Don't install wine per default. But of a user starts to start en .exe - pop up a message box, explain that it is a windows application and offer to install wine with the warning that this *might* allow him/her to run this app anyway. In a semi-perfect world (a perfect world would have all apps running on Linux but this is the real one and that day is a few months in the future still :-) ) try to find the name of the program (should be straightforward with an msi) and offer a link to the winehq page for that app.

But telling people it's better to have a dual-booting windows when wine often does the job fine makes no sense to me.

---

### Post by Sand &amp; Mercury on 2008-08-31
> **MadsRH said:**
> I agree with the posts above. However the idea was never to include Wine by default, but simply to present the user with a "*You need to install Wine to run this application*" dialog when running a exe file or similar.

The purpose is not to pretend to be Windows, but the improve the user experience.
Whoops! Yeah, you're right, I misread. Sorry :/

Still, I kind of have the same opinion. That way even if you didn't bundle it you'd still be insinuating that it's needed and that it's going to be a part of the experience.

---

### Post by klange on 2008-08-31
All of the ideas listed in the spec are possible, and they are all really great ways to improve the system. I think they need to be explored and worked on.

---

### Post by Nullack on 2008-08-31
Never going to happen for Intrepid and it would need to gain support for it to become an item for UDS. Personally I think there is more important specs to focus on.

---

