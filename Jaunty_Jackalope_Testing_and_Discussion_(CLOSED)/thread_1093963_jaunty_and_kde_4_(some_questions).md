---
title: "jaunty and kde 4 (some questions)"
date: 2009-03-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by techno-mole on 2009-03-12
I'm not sure if this is the right place to ask this but here goes anyway.

I recently went back to gnome from using kde (from kubuntu hardy to ubuntu intrepid) mainly because I found that gnome was more stable, I know that kde 4 is still being worked on and for the most part looks pretty good and works pretty well.

However I thought I would try out kubuntu intrepid the other day, words kind of failed me, it was bad to say the least, updates didn't install correctly desktop effects refused to work, and installing compiz all but killed the system (I know you can use kwin over compiz, but I like compiz)

so the question is will Jaunty be any better ? I know it uses the 180 nvidia driver (which I assume will fix some issues) it wasn't just the desktop effects, it was little things like the widgets you get with the plasma desktop wouldn't install and the ones that did wouldn't work correctly.

I could go on, but needless to say it was bad (I have a pretty powerful system so I doubt it was hardware issues) so will jaunty be any better ?

I should mention that it was the 64 bit version of kubuntu intrepid I was using, I would like to use kubuntu again, I found it pretty good, although I thought that plasma needed some work, but I don't really want all the hassle I had trying to run intrepid.

my system specs are as follows, in case it might be hardware related.

amd athalon x2 6000+ cpu (running at stock speed of 3.1ghz)
nvidia 9500 gt pci express card (over clocked version, over clocked by asus)
4 gb ddr 2 ram (running @ 800mhz)
500 gb sata 2 hard drive (not used for anything other than ubuntu/kubuntu)
250 gb sata 2 hard drive (only used for playing games on, xp installed)
sound blaster audigy pci card.

64bit ubuntu intrepid runs very well, 64bit kubuntu was well sucky to be honest (and I love ubuntu/kubuntu, I recommend it to anyone who wants to try linux out)

cheers

---

### Post by caryb on 2009-03-12
I have evolved throught the hardy -> Intrepid -> Jaunty KDE4 debacle & I have to say that Jaunty/KDE4 is great, the wireless is fixed & I really don't have any problems anymore. My wife who is studying for her masters was using Intrepid & was having all sorts if greif, I bit the bullet & upgraded her to Jaunty last week & she is very happy with Kubuntu now. I"m holding off doing any upgrades on her laptop till Jaunty is released as she is experiencing no problems.


Cary

---

### Post by nyarnon on 2009-03-12
I quote [http://www.pclinuxos.com/](http://www.pclinuxos.com/)

We decided to use kde3-5-10 as our default desktop as we could not achieve a similar functionality from kde4.

nuf said.

---

### Post by SushiR on 2009-03-12
> **nyarnon said:**
> I quote [http://www.pclinuxos.com/](http://www.pclinuxos.com/)

We decided to use kde3-5-10 as our default desktop as we could not achieve a similar functionality from kde4.

nuf said.Wise words... :-)

---

### Post by ruik on 2009-03-12
How can you take seriously something called "PCLinuxOS"?

:)

---

### Post by nyarnon on 2009-03-12
@ruik

Not so hard at all considering that they decided to go gnome on the next release :-)

---

### Post by caryb on 2009-03-12
I had a look at > [http://www.pclinuxos.com/](http://www.pclinuxos.com/)
 What a blast! I mean the screenshot page is a hoot, they are still using Beryl as there compositor:o Now that's a blast from the past:o


Cary

***Warning contentious comment**** > Not so hard at all considering that they decided to go gnome on the next releaseNow thats a step in the right direction NOT:P

---

### Post by Changturkey on 2009-03-12
> **nyarnon said:**
> @ruik

Not so hard at all considering that they decided to go gnome on the next release :-)

lol wut

---

### Post by kayosiii on 2009-03-13
The only gotcha I can say for the moment is - that nvidia drivers 180.35 does bad things to kde4... there is a ppa with the newer .37 version of the drivers with these or the previous .29 version of the drivers everything runs sweetly. The network plasmoid works great for me the system tray no longer looks broken with nividia drivers.


 With this release there reallly isn't anything I personally used in kde 3.5 that isn't in 4.2 except for the ability to configure mouse gestures. I would be curious to know what other people are still missing.

---

### Post by krazyd on 2009-03-13
> **techno-mole said:**
> 
*snip*

However I thought I would try out kubuntu intrepid the other day, words kind of failed me, it was bad to say the least, updates didn't install correctly desktop effects refused to work, and installing compiz all but killed the system (I know you can use kwin over compiz, but I like compiz)

so the question is will Jaunty be any better ? I know it uses the 180 nvidia driver (which I assume will fix some issues) it wasn't just the desktop effects, it was little things like the widgets you get with the plasma desktop wouldn't install and the ones that did wouldn't work correctly.

I could go on, but needless to say it was bad (I have a pretty powerful system so I doubt it was hardware issues) so will jaunty be any better ?

*snip*

my system specs are as follows, in case it might be hardware related.

amd athalon x2 6000+ cpu (running at stock speed of 3.1ghz)
nvidia 9500 gt pci express card (over clocked version, over clocked by asus)
4 gb ddr 2 ram (running @ 800mhz)
500 gb sata 2 hard drive (not used for anything other than ubuntu/kubuntu)
250 gb sata 2 hard drive (only used for playing games on, xp installed)
sound blaster audigy pci card.The thing to keep in mind here is that any time you are using a proprietary, binary-only driver, you are leaving yourself exposed to undefinable bugs. Whether Gnome, KDE, compiz or kwin trigger those bugs is pretty much just luck. Nvidia are one of the worst offenders, in that they publish no documentation of their hardware, and even replace parts of the X stack within their driver for stuff like redirected direct rendering, which is still being implemented in Mesa.

So really, the fact that enabling compiz all but killed your system is probably not KDE's fault, but almost certainly Nvidia's.  :(

Using the open source radeon driver and KDE 4.2 here is stable and snappy.

---

### Post by nyarnon on 2009-03-13
> **krazyd said:**
> 
So really, the fact that enabling compiz all but killed your system is probably not KDE's fault, but almost certainly Nvidia's.  :(


What is the basis of this conclusion? Sounds much like Microsoft, we don't understand it so theres the problem.

I'm running a 64 bit machine with a NVidia card on a normal Ubuntu desktop, it's stable as steel.

I will not say that that prooves it's not his NVidia driver, but I do ask myself how you can conclude it is not KDE?

---

### Post by asimon on 2009-03-13
> **nyarnon said:**
> What is the basis of this conclusion? Sounds much like Microsoft, we don't understand it so theres the problem.

I'm running a 64 bit machine with a NVidia card on a normal Ubuntu desktop, it's stable as steel.

I will not say that that prooves it's not his NVidia driver, but I do ask myself how you can conclude it is not KDE?

The problems of NVIDIA's propritary drivers with KDE 4 are well known and many problems were already acknowledged by NVIDIA employees - the most dire ones are even fixed in the meantime - it usually gets better with each new driver release.

Probably you don't spend much time on kde mailing lists, on planet kde, the Qt lab blog, or on NVIDIA linux forums. NVIDIA's driver problems with KDE4 are a recurring topic there.

See for example: [http://techbase.kde.org/User:Lemma/KDE4-NVIDIA](http://techbase.kde.org/User:Lemma/KDE4-NVIDIA) or [http://userbase.kde.org/GPU-Performance](http://userbase.kde.org/GPU-Performance) .
That is a little bit outdated, but was easy to find. I am too lazy currently to search the mailing lists or planet archives for more, sorry about that. :-)

The fact that gnome users have much less problems than KDE users with NVIDIA's proprietary drivers is because KDE 4 triggers other code paths in the drivers, code paths which are very buggy and often not optimized because evidently they haven't seen much/any use in the past.

I also know from first hand experience that NVIDIA had very dire problems for quite some time with their drivers on Vista 64 (which makes me also believe the press release from Microsoft that [30% of all Vista crashes occurred in NV driver code](http://www.engadget.com/2008/03/27/nvidia-drivers-responsible-for-nearly-30-of-vista-crashes-in-20/)). A couple of years ago, if someone asked me, I praised NVIDIA's drivers and their stability (especially compared to ATI). These times are gone and my next card will not be from NVIDIA anymore.

So with this in mind it's understandable that people blame NVIDIA, when a desktop crashes or behaves funny - the chance that they are right is greater than zero.  ;-)

---

### Post by nyarnon on 2009-03-13
> **asimon said:**
> 

The fact that gnome users have much less problems than KDE users with NVIDIA's proprietary drivers is because KDE 4 triggers other code paths in the drivers, code paths which are very buggy and often not optimized because evidently they haven't seen much/any use in the past.

So now you are saying *it in fact is* KDE's approach of the NVidia drivers. Please make up your mind.

---

### Post by asimon on 2009-03-13
> **nyarnon said:**
> So now you are saying *it in fact is* KDE's approach of the NVidia drivers. Please make up your mind.

No, the problem is in the driver code. KDE4 uses the api in a correct way and the problems are not there for example with Intel drivers. NVIDIA is even admitting the problems and fixing them.

EDIT:
You can keep work around such problem not indefinitely. Your code would be soon so full of hacks that it becomes unmaintainable. A better approach is to fix the cause of these errors, and this is happening, but in the sad example of NV, this can only be done by NV. It's the curse of proprietary software. It's good that they fix their driver issues and GNOME 3 and a lot of other software (like Firefox) will benefit from it too.

---

### Post by nyarnon on 2009-03-13
Well to be honest I know NVidea drivers have put the Linux community through hell, but I also recognise that they have come a long way since. Just look at the postings in this forum. They do not really stick out compared to others. There's one exception though and thats KDE.

---

### Post by kayosiii on 2009-03-13
Kde4 uses some features of the drivers that nobody else does yet. The kde and nvidia guys communicated and bugs were found to be in the nvidia code. The kde guys decided not work around the problem and let the nvidia guys fix it. That seems to have happened.
With nvidia 80.37 and KDE 4.2. There doesn't seem to be any excessive cpu usage & No visual glitches.

---

### Post by krazyd on 2009-03-13
> **nyarnon said:**
> (...)
They do not really stick out compared to others.
(...)They are the only major graphics card manufacturer (the others being AMD/ATI and Intel) who have not released documentation for their hardware, and who give no support to open source driver development.

---

### Post by techno-mole on 2009-03-14
well i took the plunge and stuck the alpha 6 of jaunty 64bit (kubuntu) and for the most part it seems okay, im not having any major issues, compiz is running, and the system is responsive and not lagging.

Ive had some random crashes for various things (for no reason i can see) but it seems okay for now.

all i need to do is figure out how to get my track ball mouse sorted out, in ubuntu intrepid i created an fdi file and all was well (got the info from here - [https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB) ) but the same file isnt working under kubuntu (jaunty) so i need to either ask some where or try and figure it out.

cheers

---

### Post by nyarnon on 2009-03-14
> **krazyd said:**
> They are the only major graphics card manufacturer (the others being AMD/ATI and Intel) who have not released documentation for their hardware, and who give no support to open source driver development.

Yes we all know. We also know they fix the prices among each other and more of that ****. What has that to do with problems under kde4 that do not exist under gnome?

KDE is just to experimental. When they launched 4 I jump of and went Gnome and up to today I have no real reason to return. I'm not so much with Linus in this as the decision to make that switch was made even before Linus his story turned up. But obvious we share the same opinion. KDE is mismanaged.

---

### Post by asimon on 2009-03-15
> **nyarnon said:**
> KDE is just to experimental.

I agree when it comes to Kubuntu's KDE packages which are everything but rock stable. But I would disagree when with KDE you mean KDE 4.2.1 generally. I for one have no problems with KDE under opensuse or Fedora or selfcompiled under Ubuntu, works like a charm and I get my stuff done (more so then with Gnome).

> **nyarnon said:**
> 
When they launched 4 I jump of and went Gnome and up to today I have no real reason to return. I'm not so much with Linus in this as the decision to make that switch was made even before Linus his story turned up.
Yes, I didn't used KDE 4.0 to 4.1 in production too. But now KDE is good enough for me and I prefer it to Gnome.

> **nyarnon said:**
> 
 But obvious we share the same opinion. KDE is mismanaged.
I don't remember Linus saying such a thing, not even similar. Could you please post a pointer? I remember that he sayed " It may turn out to be the right decision in the end and I will re-try KDE,". Isn't there a difference between "mismanaged" and "right decision"?

---

### Post by nyarnon on 2009-03-15
> **asimon said:**
> I don't remember Linus saying such a thing, not even similar. Could you please post a pointer? I remember that he sayed " It may turn out to be the right decision in the end and I will re-try KDE,". Isn't there a difference between "mismanaged" and "right decision"?

He did not litteraly say mis-managed, he said 'they did it badly' and 'it was a half-baked release' which IMHO accumulates to the same. 

The difference is that you compare apples to eggs. You are comparing the way KDE is managed with a single decision ' starting from scratch'. 

On the primary one I think it is mismanaged on the second one, indeed maybe in future something good comes from it.

My reason not to revert to KDE has a lot to do with that decision making. I think they should have waited at least one more year before releasing it as stable. As long as the same decision-makers row the KDE boat I'm not taking any risk.

I quote Linus from his [COMPUTERWORLD interview]("http://www.computerworld.com/action/article.do?command=viewArticleBasic&taxonomyName=Software&articleId=9126619&taxonomyId=18&pageNumber=5")

>  I used to be a KDE user. I thought KDE 4.0 was such a disaster, I switched to GNOME. I hate the fact that my right button doesn't do what I want it to do. But the whole "break everything" model is painful for users, and they can choose to use something else.

I realize the reason for the 4.0 release, but I think they did it badly. They did so may changes, it was a half-baked release. It may turn out to be the right decision in the end, and I will retry KDE, but I suspect I'm not the only person they lost.

I got the update through Fedora, and there was a mismatch from KDE 3 to KDE 4.0. The desktop was not as functional, and it was just a bad experience for me. I'll revisit it when I reinstall the next machine, which tends to be every six to eight months.

The GNOME people are talking about doing major surgery, so it could also go the other way.

---

### Post by asimon on 2009-03-15
> **nyarnon said:**
> 
As long as the same decision-makers row the KDE boat I'm not taking any risk.
I concur in that some bad decisions have been made. But in all fairness we should grand people the possibility to learn from their failures. We can find bad decision-makers not only in KDE but in Ubuntu or Gnome (whose release process for example allowed the release of a totally broken non-working session management) too.

I try to be very pragmatic about software and use just what works best for me - which of course can change over time. And as they say: never say never ;-)

---

### Post by nyarnon on 2009-03-16
> **asimon said:**
> 
I try to be very pragmatic about software and use just what works best for me - which of course can change over time. And as they say: never say never ;-)

Me too meaning following the principle don't mend if it's not broken. As long as gnome is stable and offers anything I need I see no reason to revert. But I never say never, if gnome would become us unusable as KDE4.0 did the chance is not unequal I might switch again. Users choice.

---

