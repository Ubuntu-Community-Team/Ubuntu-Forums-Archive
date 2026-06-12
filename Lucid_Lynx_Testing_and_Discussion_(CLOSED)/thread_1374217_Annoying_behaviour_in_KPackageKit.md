---
title: "Annoying behaviour in KPackageKit"
date: 2010-01-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tomplast on 2010-01-06
Hi.

Maybe it's just me but I find it quite annoying in KPackageKit (under Software Updates) that you can show the changelog for an unlimited (apparently) number of packages. Maybe I'm too lazy to "unselect" the packages to hide the changelogs, but wouldn't it be better if only one (or a couple) of the changelogs could be viewed at the same time.

Has anyone else felt the same as I do about this?

---

### Post by ranch hand on 2010-01-06
If I were you  I would loose kpackagekit.  Install synaptic.

The main reason to do this is that synaptic actually works.

---

### Post by VMC on 2010-01-06
> **ranch hand said:**
> If I were you  I would loose kpackagekit.  Install synaptic.

The main reason to do this is that synaptic actually works.

I was just going to check my Kubuntu. I think at the Kubuntu forums they suggest the same thing. Use Synaptic instead. I don't use either, but I've ran across that before. One would thing the dev's would either fix it or use Synaptic only.

---

### Post by caryb on 2010-01-06
Since they screwed adaptec in V3 I switched to synaptic it's not perfect but is the best package manager available at the moment IMHO


Cary


I hate kpackagekit failing then suggesting you use something else to fix the problem!

---

### Post by xebian on 2010-01-06
> **caryb said:**
> Since they screwed adaptec in V3 I switched to synaptic it's not perfect but is the best package manager available at the moment IMHO


Cary


I hate kpackagekit failing then suggesting you use something else to fix the problem!

kpackagekit is not that bad in lucid.  But never heard of adaptec unless you are talking about HD cards. Can't find it in adept either.  :D  Bored waiting for 4.4 RC1.

---

### Post by caryb on 2010-01-06
Oops adept:redface::oops:

Am building a NAS ATM at work & my mind was elsewhere!

---

### Post by tomplast on 2010-01-07
> **ranch hand said:**
> If I were you  I would loose kpackagekit.  Install synaptic.

The main reason to do this is that synaptic actually works.

What's wrong with KPackageKit? Though I haven't used it for a along time, it seems to do the job very well in Lucid Lynx. Isn't KPackageKit supposed to be something like "Ubuntu Software Center"? Off course it could improve but still it's much more user friendly then Synaptic, so I think replacing KPackageKit would be a big misstake.

---

### Post by m0o on 2010-01-07
KPackageKit is going to receive lots of love in the near future, focusing on being more at par with it's Ubuntu Synaptic counter part, so hang in there.

---

### Post by caryb on 2010-01-07
> **tomplast said:**
> [COLOR="Red"]What's wrong with KPackageKit?[/COLOR] Though I haven't used it for a along time, it seems to do the job very well in Lucid Lynx. Isn't KPackageKit supposed to be something like "Ubuntu Software Center"? Off course it could improve but still it's much more user friendly then Synaptic, so I think replacing KPackageKit would be a big misstake.

It's ok till there is a dependency problem or package failure then it bows out disgracefully. Then it's up to Synaptic or apt to fix the problem.


Cary

---

### Post by VMC on 2010-01-07
> **caryb said:**
> It's ok till there is a dependency problem or package failure then it bows out disgracefully. Then it's up to Synaptic or apt to fix the problem.


Cary
That's why I use aptitude. Great in resolving dependencies. And I'm use to it. Although, I'll use the Ubuntu Store or Synaptic  to find things.

---

### Post by ronacc on 2010-01-07
I find kpackagekit unsatisfactory in it's present state and I quit using aptitude for ANYTHING a couple of releases back after it screwed me royaly a couple of times , synaptic is the way to go.

---

### Post by lykwydchykyn on 2010-01-07
> **tomplast said:**
> What's wrong with KPackageKit?

Here's my abridged list:

[http://ubuntuforums.org/showpost.php?p=8199979&postcount=15](http://ubuntuforums.org/showpost.php?p=8199979&postcount=15)

---

### Post by tomplast on 2010-01-07
Is there anyone who have some thoughts on the "issue" I brought up? Or can you guys only complain on how bad KPackageKit is? I may be wrong but KPackageKit is the primary "package installation central" that comes with Kubuntu, so why not try to improve it if we are going to be stuck with it (which ain't a bad thing IMHO)?

---

### Post by ranch hand on 2010-01-07
If you think it will improve I admire you for your glass half full attitude.

It will not happen in the foreseeable future.  It has been used in other distros and there are folks that have talked themselves into thinking it works.  It is, in fact, a terrible pain in the butt.

They may get it to work in a year or two if they work day and night.

---

### Post by ronacc on 2010-01-07
> **tomplast said:**
> Is there anyone who have some thoughts on the "issue" I brought up? Or can you guys only complain on how bad KPackageKit is? I may be wrong but KPackageKit is the primary "package installation central" that comes with Kubuntu, so why not try to improve it if we are going to be stuck with it (which ain't a bad thing IMHO)?

by all means try to help them improve it as ubuntu software center is being improved it may, at sometime become worth using for something , however do not think that you are "stuck with it"  Kubuntu is the  kde "flavor " of Ubuntu and as such is debian based so synaptic works as well in KDE as it does in Gnome as of course does apt itself .

---

### Post by benjamimgois on 2010-01-07
Packagekit was a so promissory project at the beginning, but i really can't understand why is taking so long to make it work.

---

### Post by ranch hand on 2010-01-07
I think that the main developer is better at PR than code.  I have used this dog in Fedora (I forget what version - a couple back).  I hope that they have improved it.

I admit to not really liking rpm distros and Fedora, to me, is not fun to install if you have a lot of other things on your drive.  But packagekit was the deal breaker.

It is another layer on top of your backend and has to be customized to each distros package handling system.  Just seems like a really silly concept to me.

I would not be holding your breath for this one to ever really work better than a lot of alternatives.

The reason a lot of folks support this thing is that they want a unified package handler for Linux.  The problem is that package kit is not that, it just tries to look like it is.

---

### Post by ronacc on 2010-01-08
the goal of a unified package manager for linux is laudable but almost certainly unachievable . While they might find a way to make Rpms and Debs play nice ( alien does a fair job of it) How they could bring portage/emerge into the fold I can't even begin to imagine . But more than that is the fact that linux is is a very big tent and hugely diverse , getting a room full of linux people to agree on anything is worse than herding cats .

---

### Post by Slug71 on 2010-01-08
Has anyone tried using the aptcc backend? Supposedly that work better with Kpackagekit than the python apt backend.

---

### Post by benjamimgois on 2010-01-08
Anyone knows if there's no plans to release Software Center for KDE ? I mean, a QT version ? I would solve the Kpackegekit problem.

---

### Post by Slug71 on 2010-01-08
> **Slug71 said:**
> Has anyone tried using the aptcc backend? Supposedly that work better with Kpackagekit than the python apt backend.

Install packagekit-backend-aptcc.
Go to /etc/PackageKit/PackageKit.conf and change the default backend to 'aptcc'.

---

### Post by Slug71 on 2010-01-08
> **benjamimgois said:**
> Anyone knows if there's no plans to release Software Center for KDE ? I mean, a QT version ? I would solve the Kpackegekit problem.

Possibly for Lucid +1 as packagekit will probably replace apt-daemon as the backend for USC.

---

### Post by seeker5528 on 2010-01-08
> **Slug71 said:**
> Possibly for Lucid +1 as packagekit will probably replace apt-daemon as the backend for USC.

I remember package kit being mentioned after the initial USC announcement when everything was still on the table and everything was still being looked at.

Where did you see anything indicating that possibility since then?   

There is certainly the possibility of using package kit in addition to apt-daemon, but package kit is not designed to allow front ends that deal with complex situations, so I don't really see how it could be used as a replacement for apt-deamon relative to software center features that are being talked about for future releases.

> How does PackageKit handle dependencies?

PackageKit does not do dependency resolution. This problem has already been solved by the backend systems and we don't really want to re-invent the wheel.

**[SIZE="2"]PackageKit does not have the fine-grained API to do everything. For instance, synaptic should still use libapt as can do much more than can be provided by PackageKit[/SIZE]**. 

[http://www.packagekit.org/pk-faq.html](http://www.packagekit.org/pk-faq.html)

Package kit is good for things like the codec installer, command not found, browser plugin installer, etc.... 

If you want an installer the will present the user with a list of software instead of a list of packages and not have to maintain a static list of said software and it's add-ons, I don't think package kit has the features to allow front ends to provide that. 

And what does any of that have to do with having a KDE/QT version of Software Center anyway? :P 

Later, Seeker

---

