---
title: "intrepid+ hardy repo for kde3?"
date: 2008-07-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by of_darkness on 2008-07-09
Wat is the best sullution for uppgrading to intrepid later on and still keep kde3 -mainly kicker task-bars?

My ideas are:
use dual repositorys = hardy + intrepid 
use intrepid + 3dparty kde3 repo?
copy my kde3 instaltion to a subdir under let say opt/kde3

Witch is the best sullution untill kde4 is mature enough for my usage (3level horizontal taskbar) ?

---

### Post by ccw on 2008-07-09
> **of_darkness said:**
> Wat is the best sullution for uppgrading to intrepid later on and still keep kde3 -mainly kicker task-bars?

My ideas are:
use dual repositorys = hardy + intrepid 
use intrepid + 3dparty kde3 repo?
copy my kde3 instaltion to a subdir under let say opt/kde3

Witch is the best sullution untill kde4 is mature enough for my usage (3level horizontal taskbar) ?

Stick with Hardy?

---

### Post by of_darkness on 2008-07-10
> **ccw said:**
> Stick with Hardy?
Nah thats not an alternative.. as i want to have the latest of the rest... and kde4 installed besides kde3 as it is now.. but still getting the newer versions of the other stuff..

But i cant use plasma yeat as it donest work whit my usage style..

---

### Post by ccw on 2008-07-10
> **of_darkness said:**
> Nah thats not an alternative.. as i want to have the latest of the rest... and kde4 installed besides kde3 as it is now.. but still getting the newer versions of the other stuff..

But i cant use plasma yeat as it donest work whit my usage style..

Have fun.

---

### Post by of_darkness on 2008-07-11
> **of_darkness said:**
> Wat is the best sullution for uppgrading to intrepid later on and still keep kde3 -mainly kicker task-bars?
*
My ideas are:
use dual repositorys = hardy + intrepid 
use intrepid + 3dparty kde3 repo?
copy my kde3 instaltion to a subdir under let say opt/kde3
*
Witch is the best sullution untill kde4 is mature enough for my usage (3level horizontal taskbar) ?
*
No input? Hey some one must have some input about this?..

---

### Post by psyke83 on 2008-07-11
> **of_darkness said:**
> *
No input? Hey some one must have some input about this?..

You already got the answer. You can't "mix" Hardy and Intrepid repositories. If you want to install KDE3 into /opt, then it will have to be self-compiled anyway.

You're better off sticking with Hardy, enabling all the extra repositories (hardy-proposed and hardy-backports), and using the Kubuntu Members PPA (for KDE 4.1) here: [http://www.kubuntu.org/node/32](http://www.kubuntu.org/node/32)

The purpose of testing Intrepid is to help improve Intrepid, not to support these kinds of custom configurations.

---

### Post by caryb on 2008-07-12
> The purpose of testing Intrepid is to help improve Intrepid, not to support these kinds of custom configurations.=D>

It is almost impossible to disseminate what is a real Intrepid problem & user induced problem with custom installs.   



2c Cary

---

### Post by of_darkness on 2008-07-12
> **psyke83 said:**
> You already got the answer. You can't "mix" Hardy and Intrepid repositories. If you want to install KDE3 into /opt, then it will have to be self-compiled anyway.

You're better off sticking with Hardy, enabling all the extra repositories (hardy-proposed and hardy-backports), and using the Kubuntu Members PPA (for KDE 4.1) here: [http://www.kubuntu.org/node/32](http://www.kubuntu.org/node/32)

The purpose of testing Intrepid is to help improve Intrepid, not to support these kinds of custom configurations.
its not my cracy idea to diss kde3 in future kubuntu.. so at least one should have some viable solution other than going with kde4.. or sticking whit other old stuff that you dont want 2 stick whit..

well as i see it i dont have that mouch of a choise other than mixing..

And i cant be the only one who wants intrepid whit kde3????

---

### Post by of_darkness on 2008-07-12
> **caryb said:**
> =D>

It is almost impossible to disseminate what is a real Intrepid problem & user induced problem with custom installs.   



2c Cary
but dissing kde3 is a problem 4intrepid and the only non sullution is sticking whit hardy or going to a diffrent dist.. cause kde4 whill not be a clone of kde3 in sdeveral years if i understand the dewelopers..

---

### Post by Vorian on 2008-07-12
> **of_darkness said:**
> well as i see it i dont have that mouch of a choise other than mixing..

And i cant be the only one who wants intrepid whit kde3????
Intrepid will not have KDE 3.* and there are no plans of a KDE 3 repository.  If you want to use KDE 3.*, you'll have to do what others have suggested and stick with Hardy.

---

### Post by of_darkness on 2008-07-12
> **Vorian said:**
> Intrepid will not have KDE 3.* and there are no plans of a KDE 3 repository.  If you want to use KDE 3.*, you'll have to do what others have suggested and stick with Hardy.
*
Well sticking whit hardy is not an alternative.. as no one has any better input i gues il ahve to go whit a repo mix of intrepid and hardy and simply lock the kde pakages to hardy version.. witch is a pretty dirty sollution but haey if it works its esier than going of to a another distro that will have kde3 and othervise uppdated packages..

but i cant understand the attitude of sticking to hardy for several years onwards.. ore go to kde4..

---

### Post by Vorian on 2008-07-12
> **of_darkness said:**
> *
Well sticking whit hardy is not an alternative.. as no one has any better input i gues il ahve to go whit a repo mix of intrepid and hardy and simply lock the kde pakages to hardy version.. witch is a pretty dirty sollution but haey if it works its esier than going of to a another distro that will have kde3 and othervise uppdated packages..
The paths would force the entire DE to upgrade.  There will not be .kde3 and .kde4 to keep them all nice and seperate.  

> **of_darkness said:**
> but i cant understand the attitude of sticking to hardy for several years onwards.. ore go to kde4..It's quite simple, all of the development focus is on KDE 4.* and onward.  Kubuntu 8.04 is not a LTS release, and the primary reason is because there is no real reason to support KDE 3.* beyond a 'standard release' time frame.

---

### Post by ffi on 2008-07-12
If feauture-wise kde4.1 beta2 in the ppa for hardy is complete then it will be a big mistake to not include kde3.

I can live with the slowness and the crashes but it quite simply still misses too many features which kde3 does have. KDE4.1 will frustrate many satisfied kde3.5x users....

And other distros, like mandriva and opensuse, will keep kde3 alongside kde4.

---

### Post by of_darkness on 2008-07-12
> **Vorian said:**
> The paths would force the entire DE to upgrade.  There will not be .kde3 and .kde4 to keep them all nice and seperate.  
*
It's quite simple, all of the development focus is on KDE 4.* and onward.  Kubuntu 8.04 is not a LTS release, and the primary reason is because there is no real reason to support KDE 3.* beyond a 'standard release' time frame.

well i well keap the kde4 repo that keaps them in kde4 and when it dosent work well it only one or 2 apps that ive compiled that demanded kde4..

Well cause there is those who feal that kde4 isent redy by far reach? and for them who maybe use both gnome and kde and what to have latest gnome and other apsp and still use kde3.5*

And offering no sullution but to use hardy for the rest of their lives i a betrayal in a form...
*

---

### Post by of_darkness on 2008-07-12
> **ffi said:**
> If feauture-wise kde4.1 beta2 in the ppa for hardy is complete then it will be a big mistake to not include kde3.
*
I can live with the slowness and the crashes but it quite simply still misses too many features which kde3 does have. KDE4.1 will frustrate many satisfied kde3.5x users....
*
And other distros, like mandriva and opensuse, will keep kde3 alongside kde4.

exactly i wouldent care if they offerd some wialble alternative for kde3*..

and the real big no no is the taskbar.. you can only have 4-5programs there.. i have 27 windows listed in my taskbar right now..
*

---

### Post by lewmnik on 2008-07-12
4.1 is already way beyond 3.5.*, you guys just have to bite it and learn to use it :)

Some good reading [http://www.groklaw.net/article.php?story=20080710131440951](http://www.groklaw.net/article.php?story=20080710131440951)

---

### Post by of_darkness on 2008-07-12
> **lewmnik said:**
> 4.1 is already way beyond 3.5.*, you guys just have to bite it and learn to use it :)
*
Some good reading [http://www.groklaw.net/article.php?story=20080710131440951](http://www.groklaw.net/article.php?story=20080710131440951)
*

Uhm how is it god for say 30 ore more open windows? and dont say vitual desktops linux old style cause it isent a good way 2 switch fast betwen windows.. so no kde4 is for them who love meningleas plasmoids/gadgets/etc*

i rther youse fullscale applications.. and have them running all the time..

and ive read the post but it youst repting the same propganda that the try to sell to people.. and behind it their saing whe know the best way to youse the desktop and you all have to relearn..

well im 4 one dont want 2 realearn.. in many ways i use the same style as i used in win.xp *and thats the best way 4me..

---

### Post by Nullack on 2008-07-12
Well talking in this thread isnt going to help your cause at all.

You either need to stick with hardy or choose another distro to keep using KDE 3.5.

There isnt much else to say.

---

### Post by of_darkness on 2008-07-12
> **Nullack said:**
> Well talking in this thread isnt going to help your cause at all.
*
You either need to stick with hardy or choose another distro to keep using KDE 3.5.
*
There isnt much else to say.
*
Oh? then you must se into the future or somthing.. cause i think only time will tell.. maybe some one notises it and gives ther experience and what they did to get it working or not working or maybe others speak up when one has spoken..

but hey i can be wrong so.. time vill tell..

anyway im tryoing to compile and if it goes the way put upp an ppa whit kde3*latest svn

---

### Post by Robertjm on 2008-07-20
I would hazard a guess that NOBODY is planning to only include KDE 3.5x in Hardy for the next three years. I'm sure that once its final there will be work to add v4.1 (perhaps 4.2 by then) as an alternative in the same LTS repos. The key there is LTS. Ubuntu drew a fair amount of flack for introducing Firefox v3 Beta version in the LTS so I'm sure KDE 4 won't make its appearance until they determine its "ready for primetime."

Intrepid is still Alpha. Despite that, I installed it yesterday after trying to do a clean install of Hardy TWICE, with it bombing out on me part of the way through both times. By the number of posts by others describing the same problem I'm guessing there's an issue with the 8.04.1 CD.

Yes, I realize its alpha, but it seems to have cured the issues I've had for several months with Hardy, which, ironically, fixed several problems I'd had with Feisty (I had Gutsy on my computer for about two hours only).

But as an Alpha I also realize it is forward thinking for the developers. They have enough problems fixing the issues with future release stuff without having to make sure the older code works with new changes in the works. Last thing they need is bloatware from having to make sure the older stuff works in Intrepid for the Alpha first releases.

Am I running a risk with my data running an Alpha? Perhaps, but I will also back my data up and I ask for help here if I can't find something already posted. However, I do recognize that if I have a custom setup I may not be able to get help since its an out of the ordinary situation which doesn't add to the bigger picture the Ubuntu developers are trying to get fixed between now and October.

I'm in the same boat as you in that I would like to have the ability to install v3.5x to my Intrepid installation today, but after reading the blogs and release info will not since they just released 4.1 RC1 and plan to release the official version by the end of this month.

Good luck with what you decide to do!!

Robert

> **of_darkness said:**
> *
...but i cant understand the attitude of sticking to hardy for several years onwards.. ore go to kde4..

---

### Post by Robertjm on 2008-07-20
After rereading the thread again I see Vorian's post about Kubuntu 8.04 not having LTS status.

This is one of the things about Ubuntu that drives me nuts! You've got Kubuntu and Ubuntu and Xubuntu, etc. Ubuntu 8.04 was released as LTS, but I'd been running it with the KDE desktop since rather than Gnome, which is why I forgot about different statuses depending on the desktop environment. :(

Later,

Robert

---

### Post by kronarq on 2008-08-05
Kubuntu 8.04 was not LTS for this exact reason. KDE 4 had just hit but it wasn't ready for prime time. Hence the Kubuntu 8.04 and Kubuntu 8.04 Kde 4 Remix releases neither being LTS. This was the right decision for them based on the nature of the development taking place outside of Ubuntu. As far as sticking with KDE3 good luck running new distros for several years as most of them are moving to KDE4 as it is the future. For the complaint on multiple panels [http://dot.kde.org/]("http://dot.kde.org/") the latest digest posted references work put into that.

---

### Post by of_darkness on 2008-08-10
> **kronarq said:**
> Kubuntu 8.04 was not LTS for this exact reason. KDE 4 had just hit but it wasn't ready for prime time. Hence the Kubuntu 8.04 and Kubuntu 8.04 Kde 4 Remix releases neither being LTS. This was the right decision for them based on the nature of the development taking place outside of Ubuntu. As far as sticking with KDE3 good luck running new distros for several years as most of them are moving to KDE4 as it is the future. For the complaint on multiple panels [http://dot.kde.org/](http://dot.kde.org/) the latest digest posted references work put into that.


I doo reely hope some one makes an ubuntu kde.3.5* spinnoff distro... 

*start rant*
And plasma panels is not the only bad thing of kde4 in my mind, Amarok 2 -they have realy messed upp what was good in Amarok in the design sence witch is for me the number 1..
And konqueror is also messed upp -in using oxygen anyway..
and colorthems is not the same as in kde3 therfore you cant have the same look in kde4 as in kde3..

and the whole ide that they have puffed fore about oneclick and why they have made dolphin is in my mind cracy..
*end rant*

So my sullution vill be one of the following:
* Do a dirty compile of kde3.5* and put it in /opt or so.. 
*  mixing hardy and intrepid repos and hold all kde packages from uppgrade
*  mixing hardy and intrepid repo and before that remove kde and force version to hardy kde3
*trying out debian
worst case is not to uppgrade.

sullutions not wiable:
*dissing kde3
*opensuse (tried it now and even some smart functions its realy handicaped and some irritating desing ideas)
*mandriva to comersial.

If any one tries out any of the maybe wiable sullutions please let me know of your experiences :) (witch was my point of starting this thred before it went on to be a ranting:/)

---

### Post by Alexia_Death on 2008-08-14
KDE 3 packages should be made available from the repro as built under /usr/opt ie. For me the issue is not plasma. I like it. the issue is that my KDE tools(mainly digikam, that currently is not installable even) that I absolutely need are not stable yet for kde4. And making a user identify and build a whole set of libraries just to use a single application is not nice...

---

### Post by pansz on 2008-08-18
> **Vorian said:**
> Intrepid will not have KDE 3.* and there are no plans of a KDE 3 repository.  If you want to use KDE 3.*, you'll have to do what others have suggested and stick with Hardy.

That is NOT true.

Try run K3b or Amarok in Kubuntu Intrepid Alpha 4, and Choose Help|About KDE, you will see KDE3.5.9 there.

That is to say: KDE 3.5.9 libs still exists in Intrepid, and you should be able to run most KDE 3.5.9 applications inside KDE4.1-based Kubuntu 8.10.

Users don't need an entire KDE3 environment just to run KDE3 apps, they can compile any KDE3 applications and made them run inside Kubuntu 8.10 within KDE4 desktop.

---

### Post by TheMono on 2008-08-19
> **pansz said:**
> That is NOT true.

Try run K3b or Amarok in Kubuntu Intrepid Alpha 4, and Choose Help|About KDE, you will see KDE3.5.9 there.

That is to say: KDE 3.5.9 libs still exists in Intrepid, and you should be able to run most KDE 3.5.9 applications inside KDE4.1-based Kubuntu 8.10.

Users don't need an entire KDE3 environment just to run KDE3 apps, they can compile any KDE3 applications and made them run inside Kubuntu 8.10 within KDE4 desktop.

Er.... You're talkinng about two different things. The post you were saying is untrue meant the KDE3 desktop, Kicker, etc, whereas you mean the KDElibs version 3... The OP was with reference to the former, I believe.

---

### Post by phobos_anomaly on 2008-08-19
sudo aptitude install kde-core brings up kde3 on my intrepid box. Looks like they just added a repo for it.

---

### Post by Jordanwb on 2008-08-19
> **lewmnik said:**
> you guys just have to bite it and learn to use it :)

No thanks, I'm not a masochist (hey I spelt that right). I think I'll stick with KDE 3.5 on my laptop. I tried the Fedora 9 + KDE 4.1 LiveCD and IMHO it was the ugliest thing I ever saw.

---

### Post by of_darkness on 2008-08-19
> **phobos_anomaly said:**
> sudo aptitude install kde-core brings up kde3 on my intrepid box. Looks like they just added a repo for it.

ohh that would inded be nice if the doo..

---

### Post by tsimpson on 2008-08-24
Intrepid will use KDE 4. If we don't provide KDE 2 packages, why should we provide KDE 3 packages? (other than those for packages not yet ported to KDE 4)

---

### Post by of_darkness on 2008-08-25
> **tsimpson said:**
> Intrepid will use KDE 4. If we don't provide KDE 2 packages, why should we provide KDE 3 packages? (other than those for packages not yet ported to KDE 4)

Well cause kde4 is not compleate yeat...
- maybe kde4.3 vill be sufficently working 4 primary desktop..

kde3 is compleate in user way of sence and then there is not any nead 4 kde2 packages.


And kde3 libs is a must for amarok 1* as amarok 2 is a complatly diffrent player just  using the same name.
and probly i vill keap some more apps in kde3* version as i dont like the kde4  pimp style.

---

### Post by RAOF on 2008-08-26
The kde3 libs aren't going away anytime soon.  We still have gtk+1.2 in the archives, and that's been dead for the better part of a decade.

---

### Post by jlacroix on 2008-08-26
I agree with most of the people here, there is no reason to hold onto KDE3. If you feel KDE 4.1 is missing a KDE3 feature or could do something better, then file a wish or bug report with KDE and help them improve it. Otherwise, I'm not going to hold onto the past and refuse to accept great new technologies.

---

### Post by awakatanka on 2008-08-27
What beside kde makes you want to use intrepid? doesn't hardy offer you everything you need? If hardy works for you with kde3 then stick to that. New versions are progress to new stuff and not to stand still because some users can't live with a new version. Its easier to compile the new version to work from source with kde4 then compile kde3 to work from source if you want new versions of software

---

### Post by dawynn on 2008-08-29
Probably just adding fuel to the fire, but...

This offsite page was linked quite a few posts back.  It addresses several myths about KDE 4.  People arguing on both sides of this argument really should read the document carefully.

[http://www.groklaw.net/article.php?story=20080710131440951]("http://www.groklaw.net/article.php?story=20080710131440951")

What *I* got from this document is an honest confession that, for the time being, the KDE folks realize that KDE 4.0 is *not* feature-complete.  KDE 4.1 may not be either.  (If you didn't catch this -- reread myth 2 very carefully)  They indicated in the document that KDE 3.5 was even still seeing bugfixes through August of this year.

As the myth-busting document presents it, KDE 4.0 has been released so that developers can explore and start to use all the new bells and whistles.  At the same time, they freely admit that developers have not discovered all the new features, and very little actually utilizes KDE 4 to its full potential.  So, they are keeping KDE 3.5 alive while things get ported to KDE 4.

Now, whether any particular distribution (Kubuntu, for example) decides to support both platforms, as the KDE people are still doing, remains to the powers that be for the distribution.

That being said, KDE 3.5 is on the way out.  But until KDE 4 truly comes into its own, 3.5 still has an active heartbeat.  In light of this myth-busting document, I personally would vote for keeping both platforms open for now.  But I have no real sway either in the KDE realm or the Ubuntu realm.

As for the snide remark about KDE 2.0: The myth-busting document clearly indicates that KDE 3.5 is still being supported.  KDE 2.0 stopped being supported long ago.  Such irrelevant analogies do not help anyone.

Carry on...

---

### Post by of_darkness on 2008-08-29
> **jlacroix said:**
> I agree with most of the people here, there is no reason to hold onto KDE3. If you feel KDE 4.1 is missing a KDE3 feature or could do something better, then file a wish or bug report with KDE and help them improve it. Otherwise, I'm not going to hold onto the past and refuse to accept great new technologies.

 Until i can get kde4 to look and work like my kde3.5 desktop i wont be satysfied..  like multirow task manger plasmoid is a must as i dont use virtual desktops and have alot of runnings apps (28 diffrent non grouped apps).  and i dont like the redesign of konqueror or amarok.  it is not the tecknology as say.. or some i dont like one click? designs.. i find those realy cracy.. but thats my wiew wich is based upon my usage..   but as kde4 isent feature redy more then basics or hardly even that, as i count multiline task manager as basic feature..   more then that i havent tested kde4 cause i gets o angry over that i dossent work as i vant..  kde4.3 or so whill maybe ready but well to be honest i depends if some apss like kbfx ,domino style and dekorator window design gets ported 2 kde4 and the provide a good backport of kde3 libs to run kde 3.5 apsp like konq and amaraok..

---

### Post by of_darkness on 2008-08-29
> **awakatanka said:**
> What beside kde makes you want to use intrepid? doesn't hardy offer you everything you need? If hardy works for you with kde3 then stick to that. New versions are progress to new stuff and not to stand still because some users can't live with a new version. Its easier to compile the new version to work from source with kde4 then compile kde3 to work from source if you want new versions of software

 newer wersion of many other apps? i use alot of gnome apps and have gnome desktop installed.. and all other app that i might come 2 use some day.. and is always loking to test new media player apps etc..  na not realy as it is alot more then kde3 that gets uppdated..  and it is not only intrepid but the versions comming after that?  and i will probably use amarok 1* the rest of my life or untill some one wriths a beter musicplyer that is as goodloking as amarok and as usable... the only one who is better looking is then winamp or vlc -skins 2 but niether is a real choise..

---

### Post by of_darkness on 2008-08-29
> **dawynn said:**
> Probably just adding fuel to the fire, but...

This offsite page was linked quite a few posts back.  It addresses several myths about KDE 4.  People arguing on both sides of this argument really should read the document carefully.

[http://www.groklaw.net/article.php?story=20080710131440951](http://www.groklaw.net/article.php?story=20080710131440951)

What *I* got from this document is an honest confession that, for the time being, the KDE folks realize that KDE 4.0 is *not* feature-complete.  KDE 4.1 may not be either.  (If you didn't catch this -- reread myth 2 very carefully)  They indicated in the document that KDE 3.5 was even still seeing bugfixes through August of this year.

As the myth-busting document presents it, KDE 4.0 has been released so that developers can explore and start to use all the new bells and whistles.  At the same time, they freely admit that developers have not discovered all the new features, and very little actually utilizes KDE 4 to its full potential.  So, they are keeping KDE 3.5 alive while things get ported to KDE 4.

Now, whether any particular distribution (Kubuntu, for example) decides to support both platforms, as the KDE people are still doing, remains to the powers that be for the distribution.

That being said, KDE 3.5 is on the way out.  But until KDE 4 truly comes into its own, 3.5 still has an active heartbeat.  In light of this myth-busting document, I personally would vote for keeping both platforms open for now.  But I have no real sway either in the KDE realm or the Ubuntu realm.

As for the snide remark about KDE 2.0: The myth-busting document clearly indicates that KDE 3.5 is still being supported.  KDE 2.0 stopped being supported long ago.  Such irrelevant analogies do not help anyone.

Carry on...

  i read it, but it dosent explain or cannot justify the in my mind strange design ideas, and oxygen is realy ugly that makes kde4 not usable untill some makes a more kde3 like style so one can judge the behaviur and funtion..  and in funtion, signle line task manger plasmoid ? it cant contain my apps that are running..  and amarok 2 is like a desing furniture strange and not loking any good -maybe that it is i theory more usable or so but that dosent intrest me if somting dosent loke the wy i vant..  and i have no nead for karamba liks stuff as i newer watch my desktop any way(all windows maximized).  so no i get pissed of because they calme the in my yeas valid criticism of kde4..  well most of it is looks but hey looks are the main thing in my world..

---

### Post by TheMono on 2008-08-29
> **of_darkness said:**
> and oxygen is realy ugly that makes kde4 not usable untill some makes a more kde3 like style so one can judge the behaviur and funtion..  

You do know that the old plastique widget styles etc are still installed by default, right?

It's really very simple. Kubuntu has limited manpower. Kubuntu frames itself as a more cutting edge distribution. Therefore Kubuntu will provide KDE4 and only KDE4. Your alternatives are, other distros which still provide KDE3 (which there are plenty), switching to GNOME / XFCE, or compiling a KDE3 environment yourself - which is no fun, really. I would strongly suggest the former as best fit for what you want. Kubuntu just isn't right for you.

---

### Post by Vorian on 2008-08-29
> **pansz said:**
> That is NOT true.
I was referring to the desktop environment. I apologize for not being as clear as I should have been.

---

### Post by jlacroix on 2008-08-29
I'm really surprised to see so many people refusing to accept new technologies. I'd have expected this out of the Microsoft group, but certainly not Ubuntu folks.

KDE 4.1, in my opinion, is completely ready to take over from KDE 3.5.x. I can only think of a few features missing. Most of the people that complain about missing features just don't know where the features have been moved to. As far as hiding and autohiding the panel, that's coming VERY soon. I read something from Aaron Seigo regarding that and other stuff.

And for the person that wanted to not use KDE 4.1 because there's no way to make it look like Kubuntu, there IS a Kubuntu theme out there for it. You just have to look.

Trust me, when KDE 4.1.1 comes out the first week of September, I urge everyone that hates it to give it another chance.

KDE 4.1 is so well put together I can't even imagine downgrading to KDE 3.5.x. (And I never will).

If Kubuntu does include a KDE3 remix, I'll be EXTREMELY dissapointed in the development team. Just because a few people aren't able to let go of the past, doesn't mean that Kubuntu should be the same way.

---

### Post by of_darkness on 2008-08-29
> **TheMono said:**
> You do know that the old plastique widget styles etc are still installed by default, right?

It's really very simple. Kubuntu has limited manpower. Kubuntu frames itself as a more cutting edge distribution. Therefore Kubuntu will provide KDE4 and only KDE4. Your alternatives are, other distros which still provide KDE3 (which there are plenty), switching to GNOME / XFCE, or compiling a KDE3 environment yourself - which is no fun, really. I would strongly suggest the former as best fit for what you want. Kubuntu just isn't right for you.

  Na newer liked plastik..  well the only alternative would be debian.. tried out open suse 11, and yea some neat trix and functions but rpm system and not having synptic is not a choise.. i nead a .deb distro 64bit version.. and no gento/slackvare style distros either.. to mouch lerning neaded..:P and too old to learn it:P  na gnome is not working rely etiher..   so the chose will be copy my partions to have a indetical test version and live with dependency hell as i will add intrepid repo and not do a dist uppgrade untill kde4 has gotten the req. packages and changes..  and a real reson not to use gnome is klipper and kbfx.  and maybe compile kde3, but the problem is rather packing it correctly..

---

### Post by of_darkness on 2008-08-29
> **jlacroix said:**
> I'm really surprised to see so many people refusing to accept new technologies. I'd have expected this out of the Microsoft group, but certainly not Ubuntu folks.

KDE 4.1, in my opinion, is completely ready to take over from KDE 3.5.x. I can only think of a few features missing. Most of the people that complain about missing features just don't know where the features have been moved to. As far as hiding and autohiding the panel, that's coming VERY soon. I read something from Aaron Seigo regarding that and other stuff.

And for the person that wanted to not use KDE 4.1 because there's no way to make it look like Kubuntu, there IS a Kubuntu theme out there for it. You just have to look.

Trust me, when KDE 4.1.1 comes out the first week of September, I urge everyone that hates it to give it another chance.

KDE 4.1 is so well put together I can't even imagine downgrading to KDE 3.5.x. (And I never will).

If Kubuntu does include a KDE3 remix, I'll be EXTREMELY dissapointed in the development team. Just because a few people aren't able to let go of the past, doesn't mean that Kubuntu should be the same way.

 i often use alpha/beta versions of programs to test,and moastly it is good..  but kde4 is trying to change once desktop behviur as gnome is ,i use primarly the windows style of usage but whit some modifiction  as multiline taskbar/manger and hidden panels whit fast starter icons and some widgets but those are hidden, and i dont use my desktop as windows foks often are using it as fast program starter.  i cant find any better sullution to desktop usage, but i am doing 100thing s at the same time and my comp is running 24/7 so thats why i wont change my behwiur or are intrested in new desktop tecknologys rely.  and yea there are some fancy stuff in kde4 idont deny that.  but i hawe no use of that as i always use maximized windows and no widgets, i rather run full programs for such jobs..  and no multiline taskmanger plasmoid in 4.1 (there is a 3party one on kde look but its still in development and is porly dokumented )  and still its missing kbfx:/ as all the rest of the start menus are ugly and non themable..  but fooks probably havent discoverd the beuty of kbx:/  but kde4 is in essential a new desktop env or a subenverioment of kde..

---

### Post by jlacroix on 2008-08-29
> **of_darkness said:**
> i often use alpha/beta versions of programs to test,and moastly it is good..  but kde4 is trying to change once desktop behviur as gnome is ,i use primarly the windows style of usage but whit some modifiction  as multiline taskbar/manger and hidden panels whit fast starter icons and some widgets but those are hidden, and i dont use my desktop as windows foks often are using it as fast program starter.  i cant find any better sullution to desktop usage, but i am doing 100thing s at the same time and my comp is running 24/7 so thats why i wont change my behwiur or are intrested in new desktop tecknologys rely.  and yea there are some fancy stuff in kde4 idont deny that.  but i hawe no use of that as i always use maximized windows and no widgets, i rather run full programs for such jobs..  and no multiline taskmanger plasmoid in 4.1 (there is a 3party one on kde look but its still in development and is porly dokumented )  and still its missing kbfx:/ as all the rest of the start menus are ugly and non themable..  but fooks probably havent discoverd the beuty of kbx:/  but kde4 is in essential a new desktop env or a subenverioment of kde..

The KDE 4.1 start menu will be theme-able very soon from what I've read. All of the issues you've mentioned, or at least most, have already been addressed and will be fixed.

I can understand your point about KDE3, but I still feel there is no need to hold onto it. 

No offense to anyone in any way, but if you want a desktop that barely changes, use Gnome. (I'm not saying Gnome is bad, though). The lack of change can be a feature to some and a bug to others.

If you choose to stick with KDE, you should expect rapid change. From using Kubuntu, you should always expect it to use the latest KDE.

---

### Post by Asraniel on 2008-08-30
Multiline taskbar will be in intrepedid? i realy don't care about the rest, but i need that one

---

### Post by jlacroix on 2008-08-30
> **Asraniel said:**
> Multiline taskbar will be in intrepedid? i realy don't care about the rest, but i need that one

I'm not sure which KDE update will bring that feature though. It could be 4.1.1, 4.1.2, or 4.2.0. I'm pretty sure its being worked on if I remember right but I could be wrong.

---

### Post by of_darkness on 2008-08-30
> **jlacroix said:**
> The KDE 4.1 start menu will be theme-able very soon from what I've read. All of the issues you've mentioned, or at least most, have already been addressed and will be fixed.

I can understand your point about KDE3, but I still feel there is no need to hold onto it. 

No offense to anyone in any way, but if you want a desktop that barely changes, use Gnome. (I'm not saying Gnome is bad, though). The lack of change can be a feature to some and a bug to others.

If you choose to stick with KDE, you should expect rapid change. From using Kubuntu, you should always expect it to use the latest KDE.

  if it can be made to look and work like kbfx then i would be happy.. (made to usae azeniz  theme, and be configured to be as high as my screen(i have a couple of 100programs instaled and i nead to browse them as i dont know what programs i have) is and work like kbfx)  well ill use kde3 untill kde4 is ready to be made a clone of my desktop, as i newer vant to change it, and that should always be able to do despite the bakground tecknics...  and as i said gnome dosent have klipper.. and it dosent have the widgete style or window dekoration..  otherwise i probaly could have used it.. and using konq as default file manager...   well i dont paticurly nead to use kubuntu,i would be as happy whit ubuntu using kde , as i dont realy like most of the kubuntu changes to kde3.5 at least, but like ubuntu as it uses a good balance of new and working.  but a big distro as ubuntu should be be att least keeping kde3 in repos for post install choise..  But but.. hopfully someone makes a repo for kde3.5..   and i whill try to do an upgrade to intrepid manuly,realy manuly,so that i dosent uppgraed the kdepackges..   btw does someone know if pinned packgess stays pinned in dist uppgrade?

---

### Post by of_darkness on 2008-08-30
> **jlacroix said:**
> I'm not sure which KDE update will bring that feature though. It could be 4.1.1, 4.1.2, or 4.2.0. I'm pretty sure its being worked on if I remember right but I could be wrong.

 Well i have searched planet-kde in Akregator but have not found anyone mentoning work on that.. nor in the dev.plan for Kde4.1 or 4.2...

---

### Post by awakatanka on 2008-08-31
[http://kde-look.org/content/show.php/multirows+task+manager?content=83177](http://kde-look.org/content/show.php/multirows+task+manager?content=83177)

You can add multi-rows task manager if you want. With a little search somethings are already there but you need to search and do it with some compiling.

kde-look also have some themes already and some decorations.

And for konqueror you can change the layout to look like kde3 version very easy
There is now [lancelot]("http://ivan.fomentgroup.org/blog/category/kde/") as choise for another menu and the people at kbfx are working for a kde4 version to > For KDE4 we will use the Raptor-menu Menu engine, the interface nookie has designed this time is really a NextGen, unbeatable and breath taking. so stay tuned for that. so we will fist finish raptor menu engine ([http://www.raptor-menu.org](http://www.raptor-menu.org)) then move on to KBFX for KDE4.

But i don't understand you, you want to try alpha and beta software but complain if you use a new version of kde that lacks some options that are put in later. That is like complaining that the alpha version of the software you are using isn't ready to use.

I think you have 3 options.

1 use debian
2 sick to hardy and use third party repo lines for new stuff our compile them.
3 use intrepid and say by to kde 3, our compile kde3

Because all i see is that you want bleeding edge software to test but i don't see that you need the underling changes that are made in intrepid. ( new hardware support etc )

---

### Post by of_darkness on 2008-08-31
> **awakatanka said:**
> [http://kde-look.org/content/show.php/multirows+task+manager?content=83177](http://kde-look.org/content/show.php/multirows+task+manager?content=83177)

You can add multi-rows task manager if you want. With a little search somethings are already there but you need to search and do it with some compiling.

kde-look also have some themes already and some decorations.

And for konqueror you can change the layout to look like kde3 version very easy
There is now [lancelot]("http://ivan.fomentgroup.org/blog/category/kde/") as choise for another menu and the people at kbfx are working for a kde4 version to 

But i don't understand you, you want to try alpha and beta software but complain if you use a new version of kde that lacks some options that are put in later. That is like complaining that the alpha version of the software you are using isn't ready to use.

 as 4 the kde-look multi-row taskbar the arthur hasent shipped clear instructions howto buld and so as of yeat, im subscribing to coments and updates on it...  hmm well i havent found that option.. but still i havent bean able 2 use 4 long as it so ugly that i cant stand it 2 look at it more than a sec or so.. but well if you say it i supose il have 2 look deper into it..  and lancelot ,well the problem is again the design and the looks of it, the function seams preaty good actualy but as the athour has decleared it is as it is and is not a &quot;camleont&quot; as saya kbx so,,  hmm to me it seams like the kbx is dead as their website is gone from the net.. and if you dont re ont the net you dont exist:P but well hopfully theil comeback..  why? because of distros think its not alpha or beta as they choose kde4 most important *ubuntu:s diss of kde3.5 to intrepid... if it wornot not 4 that i wouldent care and see kde4 as youst somthing else outhere that wouldent affect me..  ------------------------------------------------------------ and no i found even a new hangup, they changed the icon-them stuff so kde3 icons dont work:/ and not kde3 icon schems:/   and i supose there isent a smart sullution to that?...

---

### Post by awakatanka on 2008-08-31
kbfx isn't dead as far as i know, there site has always troubles. one moment it works the other moment there is that page again. Sometimes i see that page for a couple of days and suddenly there page is back and works.

> Hi there,
 sorry about the KBFX site but we have some problems with it ATM that i hope will be resolved very soon.[ Link ]("http://www.kde-look.org/content/show.php?content=24898")

---

### Post by of_darkness on 2008-08-31
> **awakatanka said:**
> kbfx isn't dead as far as i know, there site has always troubles. one moment it works the other moment there is that page again. Sometimes i see that page for a couple of days and suddenly there page is back and works.

[ Link ]("http://www.kde-look.org/content/show.php?content=24898")

  ahh missed it.. just saw that the domain name had expiered.. but thanks 4 the update:)

---

### Post by madscientist159 on 2008-09-14
I happen to be a big KDE3.x fan, and am quite sorry to see KDE3.x go in Intrepid.  Below I will attempt to elaborate exactly why myself and many other users would like to see KDE3.x in Intrepid:

**Desktop Usability:**
KDE4.x does not allow the following operations by simple settings changes (as far as I can tell):
1. Changing desktop, menu, and task tray icon size
2. Removal of the annoying widget control "feet" in the corner of the desktop and taskbar (not sure what to call them)
3. Separate desktop wallpaper for each virtual terminal
4. Changing the taskbar height
5. Hiding the taskbar with one click, and restoring it with another
6. Change the colors of ALL dialogs (no matter what settings I change, the Run dialog, the shutdown dialog, and several others *stay black*.)
7. A centralized **system** control center (not just a **desktop** control center!)
8. Monitoring the contents of each virtual desktop on the taskbar, KDE3.x style.
All in all, KDE4.x feels like the desktop is trying to be the center of attention, instead of the applications that the user is attempting to use.  While I don't mind that as a default setting, the fact that I cannot change this behavior (as elaborated above) is intolerable!  KDE4.x is simply not designed for the Linux power user--in fact, I see many of Microsoft's Vista mistakes being made in the construction of the desktop interface.

**Reasons users don't want to stay with Hardy forever:**
1. Hardy's suspend and resume support is broken on many laptops, even now.
2. Newer devices are not supported under Hardy (obviously, as the kernel is older than the devices are)
3. The Hardy KDE Network Manager is still quite buggy
4. Kubuntu Hardy is not an LTS release!
The newer Intrepid packages will most likely fix these these problems for many users, but they may not want to switch to KDE4.x

KDE4.1 has made many strides towards fixing this list of problems (most notably the "classic" Kicker menu), but I would suggest releasing KDE3.x with Ubuntu at least until KDE4.2 comes out.  It can be an unofficial repository, unsupported, etc. but it should at least be available to the user in packaged form.

I have been using KDE since KDE2, and KDE3 is the most full-featured, mature, configurable Linux desktop environment I have ever had the pleasure to use--even better than Gnome and XFCE4 in my opinion. ;)  Please don't abandon it just yet!  If needed I will try to set up a KDE3 repository myself.

Also, if I have stated something incorrectly in my list above, or if you have an easy fix for any of the annoyances I have mentioned, please let me know ASAP. :)

Tim

---

### Post by 67GTA on 2008-09-14
I switched from Kubuntu 8.04 to Opensuse 11 because of this. They have KDE3 and KDE4 DE on the DVD. They have recently announced that Opensuse 11.1 will still offer KDE3 on the DVD version because so many of their KDE users just aren't happy with the current functionality of KDE4. The idea is that by the next release, KDE4 will be ready to completely replace KDE3. There is a bit of a learning curve if you are used to Kubuntu, but it is the best KDE distro around. Just something to think about.

---

### Post by madscientist159 on 2008-09-14
> **67GTA said:**
> I switched from Kubuntu 8.04 to Opensuse 11 because of this. They have KDE3 and KDE4 DE on the DVD. They have recently announced that Opensuse 11.1 will still offer KDE3 on the DVD version because so many of their KDE users just aren't happy with the current functionality of KDE4. The idea is that by the next release, KDE4 will be ready to completely replace KDE3. There is a bit of a learning curve if you are used to Kubuntu, but it is the best KDE distro around. Just something to think about.

I wonder if there's any way to petition Kubuntu to add KDE3 back to the repositories?  They already have the build scripts, etc. to do so quite easily...

Ironically, I switched from OpenSUSE to Kubuntu Gutsy because of OpenSuse's non-revertible Kicker menu modifications and the lack of Debian-like APT support. :rolleyes:  If Intrepid has no KDE3 support then you may have an OpenSUSE convert...

---

### Post by jlacroix on 2008-09-14
1. Changing desktop, menu, and task tray icon size
The icon size changes with the size of the taskbar. It's always been like that.

2. Removal of the annoying widget control "feet" in the corner of the desktop and taskbar (not sure what to call them)
That's the Plasma Icon if I'm thinking of the same thing you are.

3. Separate desktop wallpaper for each virtual terminal
I'm surprised that's not there, but it's not that big of a deal.

4. Changing the taskbar height
You can already do this.

5. Hiding the taskbar with one click, and restoring it with another
That is coming soon.

6. Change the colors of ALL dialogs (no matter what settings I change, the Run dialog, the shutdown dialog, and several others *stay black*.)
You can do this now by changing the plasma theme as well as the widget colors.

7. A centralized **system** control center (not just a **desktop** control center!)
System Settings already does this. Check the Advanced tab.

8. Monitoring the contents of each virtual desktop on the taskbar, KDE3.x style.
That's not really that big of a deal either.

> All in all, KDE4.x feels like the desktop is trying to be the center of attention, instead of the applications that the user is attempting to use.  While I don't mind that as a default setting, the fact that I cannot change this behavior (as elaborated above) is intolerable!  KDE4.x is simply not designed for the Linux power user--in fact, I see many of Microsoft's Vista mistakes being made in the construction of the desktop interface.

You could've fooled me. KDE4.1 is the ONLY desktop environment I use for anything, and I AM a power user. I simply cannot consider downgrading to KDE3 or GNOME due to how amazing the KDE4.1 desktop is.

1. Hardy's suspend and resume support is broken on many laptops, even now.
Works for me. If it doesn't work for you, what bug # did you file this under?

2. Newer devices are not supported under Hardy (obviously, as the kernel is older than the devices are)
Such as?

3. The Hardy KDE Network Manager is still quite buggy
How so?

4. Kubuntu Hardy is not an LTS release!
That doesn't make any difference at all when it comes to the quality of the release. That's just a label.

> KDE4.1 has made many strides towards fixing this list of problems (most notably the "classic" Kicker menu), but I would suggest releasing KDE3.x with Ubuntu at least until KDE4.2 comes out.  It can be an unofficial repository, unsupported, etc. but it should at least be available to the user in packaged form.

I wouldn't want Intrepid to be stuck in the past and release a KDE3 version. It's time to move on. Those that aren't ready can just stay with their existing distro, expecting Ubuntu to be stuck in the past to please a handful of users is just selfish.
As far as an unofficial repository, there's nothing stopping you from making one if that's what you really want. If that's what you want then I'd suggest getting others together that feel the same way and make it happen.

> If needed I will try to set up a KDE3 repository myself.
Do it. :)

> Also, if I have stated something incorrectly in my list above, or if you have an easy fix for any of the annoyances I have mentioned, please let me know ASAP. :)

If you have any questions about the answers I've posted, let me know, I'd be happy to help you. :)

---

### Post by 67GTA on 2008-09-14
>  	Quote:
 	 	 		 			 				 					Originally Posted by **67GTA** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=5786571#post5786571") 				
 				*I switched from Kubuntu 8.04 to Opensuse 11 because of this. They have KDE3 and KDE4 DE on the DVD. They have recently announced that Opensuse 11.1 will still offer KDE3 on the DVD version because so many of their KDE users just aren't happy with the current functionality of KDE4. The idea is that by the next release, KDE4 will be ready to completely replace KDE3. There is a bit of a learning curve if you are used to Kubuntu, but it is the best KDE distro around. Just something to think about.*
 			 		 	 	 
I wonder if there's any way to petition Kubuntu to add KDE3 back to the repositories? They already have the build scripts, etc. to do so quite easily...

Ironically, I switched from OpenSUSE to Kubuntu Gutsy because of OpenSuse's non-revertible Kicker menu modifications and the lack of Debian-like APT support. :rolleyes:  If Intrepid has no KDE3 support then you may have an OpenSUSE convert...

Probably not at this point. They have a very small dev team. I'm sure they only have the resources to focus on one version. You can run apt in Opensuse, [http://en.opensuse.org/APT](http://en.opensuse.org/APT) but zypper is just as easy: [http://en.opensuse.org/Zypper/Usage](http://en.opensuse.org/Zypper/Usage)

---

### Post by madscientist159 on 2008-09-14
> **jlacroix said:**
> The icon size changes with the size of the taskbar. It's always been like that.OK, but what about the menu and desktop icon sizes?

> **jlacroix said:**
> That's the Plasma Icon if I'm thinking of the same thing you are.How do I get rid of them?

> **jlacroix said:**
> I'm surprised that's not there, but it's not that big of a deal.To me it is!  This feature allows the user to keep track of what virtual desktop he or she is on with just a glance at the screen.  Very handy when working on four different projects at once; it helps to keep related tasks on the same virtual desktops.  Then again, I may be a more organized user than most in this regard. ;)

> **jlacroix said:**
> You can already do this.How?  I couldn't even find the equivalent to the old KDE3 taskbar settings window.  The contextual "configure taskbar" option is stripped down and quite unhelpful.  Another closely related annoyance I'd like to add here is how do I disable like task grouping?  In KDE3 this was a simple matter of bringing up the taskbar or desktop settings window and changing the appropriate option...

> **jlacroix said:**
> That is coming soon.OK, but it is a showstopper for now.  Will this be in Intrepid?

> **jlacroix said:**
> You can do this now by changing the plasma theme as well as the widget colors.So I have to create a whole new theme to change those colors?  Seems a bit odd, but I guess it is OK if there is some kind of theme editor in KDE4.1.  Is there?

> **jlacroix said:**
> 7. System Settings already does this. Check the Advanced tab.The Intrepid Alpha install I have doesn't have the "System Settings" icon anywhere in KDE!

> **jlacroix said:**
> That's not really that big of a deal either.Once again, while multitasking heavily, it saves some time to have the preview rather than having to flip through every single virtual desktop to remember where you put application "x".  On heavily used systems with many large applications running (a common occurrence for me), flipping between virtual desktops can take a while as the system pages the new apps in from swap.

> **jlacroix said:**
> You could've fooled me. KDE4.1 is the ONLY desktop environment I use for anything, and I AM a power user. I simply cannot consider downgrading to KDE3 or GNOME due to how amazing the KDE4.1 desktop is.It is possible that my first impressions are incorrect, but consider that I spent about 30 minutes last night on the Intrepid Alpha system just trying to figure out how to move the Kicker widget from the right side of the taskbar (where it is NOT supposed to be) to the left side.  I walked away frustrated, with the Kicker icon still firmly planted on the right side of the taskbar.  In KDE3 this was a 2-second "hold middle mouse over icon and drag", and the action was simple and intuitive enough that I figured it out within one minute of trying to move the icon, without resorting to a help manual or online forum.  I have many other such stories, but will not post them here.

> **jlacroix said:**
> Works for me. If it doesn't work for you, what bug # did you file this under?Haven't gotten around to filing a bug yet (fighting with KDE4...), but it has to do with the ATI fglrx drivers, so the only thing that can really fix it is a new version of the restricted modules.

> **jlacroix said:**
> Such as?No examples right now, but I have run into this exact problem with Gutsy a couple of months ago with a RAID controller (I would need to look up the chip # again).  The only thing that fixed my problems with that hardware was Hardy's new kernel.

> **jlacroix said:**
> How so?Hmm...crashes about every day, constantly disconnects me from my wireless network, gets stuck in an infinite loop waiting for dhcpd to come up on one of my laptops (this forces the user to "sudo /etc/init.d/dbus restart" every time the laptop is booted).  Using the new Gnome 0.7 nm-applet and underlying 0.7 network manager daemon fixed these problems on both of my laptops.

> **jlacroix said:**
> That doesn't make any difference at all when it comes to the quality of the release. That's just a label. Point taken, sorry about that.

> **jlacroix said:**
> I wouldn't want Intrepid to be stuck in the past and release a KDE3 version. It's time to move on. Those that aren't ready can just stay with their existing distro, expecting Ubuntu to be stuck in the past to please a handful of users is just selfish.
As far as an unofficial repository, there's nothing stopping you from making one if that's what you really want. If that's what you want then I'd suggest getting others together that feel the same way and make it happen.Hey, I didn't say for it to be stuck in the past. :)  My solution was to offer KDE3 just for the Intrepid release, and only to allow KDE4 to mature the last 10% that it has to.  I am eagerly looking to KDE4.2, but KDE4.1 just doesn't have the same flexibility KDE3 had.


> **jlacroix said:**
> Do it. :)I just might...:)

Thank you for taking the time to answer my questions.  If these last issues can be resolved, then the rest of us KDE3 holdouts will probably embrace KDE4.:cool:

EDIT: I have attached a screenshot of the desktop I use every day.  If there is a way to get KDE4 to look like this, I would be happy.  Note the following:
1. The small, unobtrusive taskbar and window borders.
2. The helpful icons in the virtual desktop selectors
3. The clock displaying both the time and the date
4. Tasks not all grouped into one large task button on the taskbar
5. The easily accessible taskbar hiding button

---

### Post by jlacroix on 2008-09-14
> OK, but what about the menu and desktop icon sizes?
Depends on what you mean by "desktop icon sizes". There are plasma icons (which can be resized by the little handle that appears over the icon when the widgets are not locked) or the Folder View Plasmoid icons which can be configured in System Settings > Appearance > Icons. Everything you need should be in that configuration window. (I just looked).

> How do I get rid of them [plasma icons]?
Locking the widgets is the only way I know how, but I haven't looked for this option because it doesn't bother me. If you lock the widgets (rightclick an empty portion of the desktop and select "lock widgets") it gets rid of the one on the task bar and the one on the desktop is so transparent I barely notice it. I know there is a way to kill it but I don't know off the top of my head.

> To me it is! This feature allows the user to keep track of what virtual desktop he or she is on with just a glance at the screen. Very handy when working on four different projects at once; it helps to keep related tasks on the same virtual desktops. Then again, I may be a more organized user than most in this regard.

I have always disabled the preview thing in the pager, and renamed each desktop according to what category of things it will have (Web, IM, Music, etc) and that worked fine for me. However, looking at mine right now it has the preview already if that's what you're talking about. I didn't customize mine in my new install yet.

> How? I couldn't even find the equivalent to the old KDE3 taskbar settings window. The contextual "configure taskbar" option is stripped down and quite unhelpful. Another closely related annoyance I'd like to add here is how do I disable like task grouping? In KDE3 this was a simple matter of bringing up the taskbar or desktop settings window and changing the appropriate option...
First, your widgets have to be unlocked. (Right click the desktop, unlock widgets). Do you see the Plasma icon on the taskbar? Click on that. It brings up a configuration overlay that has handles. You can drag the top handle up and down to resize the taskbar, you can make the taskbar take the whole screen or part of it, and finally you can rearrange the taskbar widgets while in this mode by dragging them with the mouse. When done, click anywhere on the desktop to close the overlay. ALL the KDE3 functionality is here (except hiding the panel) if you know how to do it. I like it a ton better. (The idea is not to have unnecessary menu screens). As far as like task grouping, I've never seen that before in KDE4.

> OK, but it is a showstopper for now. Will this be in Intrepid?
At some point, yes. I believe this feature is tapped for KDE 4.2. I read Aaron's blog about it. Apparently it will have a really good animation if desktop effects are enabled. No offense, but I don't see why this would be a showstopper.

> So I have to create a whole new theme to change those colors? Seems a bit odd, but I guess it is OK if there is some kind of theme editor in KDE4.1. Is there?
You don't have to create a new theme. There are a bunch already a default part of KDE4.1, and the configuration dialogue has a link to KDE-Look where you can one click install any of the ones on that site. Just right click the desktop, hit desktop settings, and on the bottom you can change the theme or install new ones. There's a glass theme (I forgot the name of it) on KDE-Look that you can install through that menu that is pretty sweet. You should check it out.

As far as an editor, I'm pretty sure there is, although I've never had a need to use it, since the plasma themes on the website are really awesome and they all satisfy me.

> The Intrepid Alpha install I have doesn't have the "System Settings" icon anywhere in KDE!
It probably wasn't created for you due to a bug. It's in mine though. Just press ALT+F2 to bring up the run dialogue (which has a sweet process viewer if you haven't already seen it, check it out) when in the run dialogue start typing system settings and you should get an option for it. If not, it may not be installed, although that would be odd. On my menu, System Settings was added to "Favorites" in the kickoff menu.

> Once again, while multitasking heavily, it saves some time to have the preview rather than having to flip through every single virtual desktop to remember where you put application "x". On heavily used systems with many large applications running (a common occurrence for me), flipping between virtual desktops can take a while as the system pages the new apps in from swap.
As I said, I usually just rename each virtual desktop according to the task it will have, (web, IM, music, etc) and then choose to display the name instead. Works for me.

> It is possible that my first impressions are incorrect, but consider that I spent about 30 minutes last night on the Intrepid Alpha system just trying to figure out how to move the Kicker widget from the right side of the taskbar (where it is NOT supposed to be) to the left side. I walked away frustrated, with the Kicker icon still firmly planted on the right side of the taskbar. In KDE3 this was a 2-second "hold middle mouse over icon and drag", and the action was simple and intuitive enough that I figured it out within one minute of trying to move the icon, without resorting to a help manual or online forum. I have many other such stories, but will not post them here.
As I stated, the configuration for the placement of icons is done by clicking on the plasma icon on the right of the taskbar. (It only appears if you have widgets unlocked). I'll post a screenshot if you need me to.

> Hmm...crashes about every day, constantly disconnects me from my wireless network, gets stuck in an infinite loop waiting for dhcpd to come up on one of my laptops (this forces the user to "sudo /etc/init.d/dbus restart" every time the laptop is booted). Using the new Gnome 0.7 nm-applet and underlying 0.7 network manager daemon fixed these problems on both of my laptops.
Sorry I forgot, those problems on Hardy or Intrepid? I never had problems on Hardy, but I've been told that the issues still remain in Intrepid. That's really weird, because on my laptop that has Hardy installed this works wonderfully.

> Hey, I didn't say for it to be stuck in the past. My solution was to offer KDE3 just for the Intrepid release, and only to allow KDE4 to mature the last 10% that it has to. I am eagerly looking to KDE4.2, but KDE4.1 just doesn't have the same flexibility KDE3 had.
The only option then would be to create a PPA or something similar. The source code for KDE3 is available to you, so even if you don't want to build a PPA, you could at least build it for yourself with the build instructions provided.

It just sucks that you aren't having as much fun with KDE4.1 as I am. My usability has increased ten fold. Little things like having a few Folder View widgets on your desktop showing your most used folders (without having to open your file manager every time!) has made things MUCH easier. Although I could complain about things like Konqueror being horrible for web browsing (it always has, so oh well) and Juk not remembering the playlist order (Amarok2 is coming anyway), all the great features to me overshadow the few missing things that KDE4.1 has.

I even [wrote an article]("http://www.linux.com/feature/146323") to publicize the features I think KDE 4.2 needs, and by the time it went to press, several of them were already in Trunk. Again, even though I too feel there are improvements to be made, KDE 4.1 is actually really amazing when you get accustomed to doing things a bit differently.

---

### Post by madscientist159 on 2008-09-14
Thank you for the assistance!  I will look into KDE4.1 again tonight.

I tend to be the opposite of most users--I *like* minimal eye candy, an unobtrusive, minimalist yet feature-rich and powerful desktop environment, context menus with lots of confusing options, **all** the system settings in one place, getting the maximum amount of system information out of each pixel, etc.  So naturally I will balk at the newest trends in desktop design! ;)

If I can get KDE4 to put **me** in the driver's seat, instead of the KDE developers, then I'll be happy.

Thanks again for all your help,

Tim

---

### Post by 67GTA on 2008-09-14
> if i can get kde4 to put **me** in the driver's seat, instead of the kde developers, then i'll be happy.

+1:)

---

### Post by AlanR8 on 2008-09-15
Then KDE 4 had better get its act together.....

---

### Post by of_darkness on 2008-09-15
> **madscientist159 said:**
> I happen to be a big KDE3.x fan, and am quite sorry to see KDE3.x go in Intrepid.  Below I will attempt to elaborate exactly why myself and many other users would like to see KDE3.x in Intrepid:

**Desktop Usability:**
KDE4.x does not allow the following operations by simple settings changes (as far as I can tell):
1. Changing desktop, menu, and task tray icon size
2. Removal of the annoying widget control "feet" in the corner of the desktop and taskbar (not sure what to call them)
3. Separate desktop wallpaper for each virtual terminal
4. Changing the taskbar height
5. Hiding the taskbar with one click, and restoring it with another
6. Change the colors of ALL dialogs (no matter what settings I change, the Run dialog, the shutdown dialog, and several others *stay black*.)
7. A centralized **system** control center (not just a **desktop** control center!)
8. Monitoring the contents of each virtual desktop on the taskbar, KDE3.x style.
All in all, KDE4.x feels like the desktop is trying to be the center of attention, instead of the applications that the user is attempting to use.  While I don't mind that as a default setting, the fact that I cannot change this behavior (as elaborated above) is intolerable!  KDE4.x is simply not designed for the Linux power user--in fact, I see many of Microsoft's Vista mistakes being made in the construction of the desktop interface.

**Reasons users don't want to stay with Hardy forever:**
1. Hardy's suspend and resume support is broken on many laptops, even now.
2. Newer devices are not supported under Hardy (obviously, as the kernel is older than the devices are)
3. The Hardy KDE Network Manager is still quite buggy
4. Kubuntu Hardy is not an LTS release!
The newer Intrepid packages will most likely fix these these problems for many users, but they may not want to switch to KDE4.x

KDE4.1 has made many strides towards fixing this list of problems (most notably the "classic" Kicker menu), but I would suggest releasing KDE3.x with Ubuntu at least until KDE4.2 comes out.  It can be an unofficial repository, unsupported, etc. but it should at least be available to the user in packaged form.

I have been using KDE since KDE2, and KDE3 is the most full-featured, mature, configurable Linux desktop environment I have ever had the pleasure to use--even better than Gnome and XFCE4 in my opinion. ;)  Please don't abandon it just yet!  If needed I will try to set up a KDE3 repository myself.

Also, if I have stated something incorrectly in my list above, or if you have an easy fix for any of the annoyances I have mentioned, please let me know ASAP. :)

Tim

i have been testing to add hardy repos on a fresh intrepid install and at the same time commenting out intrpid lines (temporarly)
  and then adding kde3* packages that you want. and the pinning them in synaptick to prevent overvrite when switching back to intrepid.

and it works fine, only trubble is whit the kde4 packages 4 hardy from the separate repo but nothing thats to bad and non real other brekage as i sen yeat that i could entitil to kde3packages...

---

### Post by madscientist159 on 2008-09-16
I am currently working on a KDE3.5 repository specifically for Intrepid.  No guarantee on a completion date, but look for it to come online in the next month or so, barring any unforeseen problems.  I am designing it so that it will be able to coexist with KDE4, so that when KDE4.2 comes along it can be installed without breaking KDE3.

Tim

---

### Post by of_darkness on 2008-09-16
> **madscientist159 said:**
> I am currently working on a KDE3.5 repository specifically for Intrepid.  No guarantee on a completion date, but look for it to come online in the next month or so, barring any unforeseen problems.  I am designing it so that it will be able to coexist with KDE4, so that when KDE4.2 comes along it can be installed without breaking KDE3.

Tim

Ohhh nice:) gl hf:)

---

### Post by TunaBoy on 2008-09-17
madscientist

I am relatively new to Ubuntu (forced from Fedora by change in organization), but as a longtime KDE user, and someone who's moved over to 4.1, I wanted to answer some of your points, as it's not as bad as you might fear.

First, I am unsettled by the gnome-like loss of options, though I've seen some of them come back as I moved from KDE4.0 to 4.1.  I'm hoping the process continues.  

You points, and the ones I can comment on

> Desktop Usability:
KDE4.x does not allow the following operations by simple settings changes (as far as I can tell):
1. Changing desktop, menu, and task tray icon size
It does.  Click on the Ying/Yang symbol on the panel, then bring the mouse to the upper edge of the new bar that appears.  If you bring this up , the height of the panel increases (and this increases icon size).  You can also make the panel take up less than the full bottom of the desktop, and can add a second panel. 

> 2. Removal of the annoying widget control "feet" in the corner of the desktop and taskbar (not sure what to call them)[\QUOTE]
You can make these disappear from the panels (I call them ying/yang symbols), by clicking on them, and choosing to "Lock the Widgets".  I don't know how to get rid of the one at the upper right hand side of the desktop... 
[QUOTE]3. Separate desktop wallpaper for each virtual terminal
I had different wallpaper on each desktop, so I could easily tell them apart.  This isn't available, as far as I can tell.  This really would be a nice thing, as I normally have 9 desktops, and use them each for separate tasks.
> 4. Changing the taskbar height
See item 1.  This is tied to the icon size.  Makes sense, but wasn't the most intuitive thing to figure out.  Now it's what I consider normal, of course.
> 5. Hiding the taskbar with one click, and restoring it with another
Didn't really do this before, but I thought I've done this by mistake.  Sorry I can't help here.
> 6. Change the colors of ALL dialogs (no matter what settings I change, the Run dialog, the shutdown dialog, and several others stay black.)
I'm still coming up to speed on the color system in KDE4, but since I only was able to work around the KDE3 system, it actually is working better for me.  There are lots of color schemes available.  There are also lots that are 'half done'.  
> 7. A centralized system control center (not just a desktop control center!)
I don't understand the distinction.  I think all the knobs I had under the old control center (which wasn't the most obvious thing to find when first starting out in KDE) are there under the "system settings".  They're just in a different place.  Joy.  However, I've put in the time so now it's just dandy.  To be honest, it's only mildly more intuitive to me.  As I'm a dinosaur, this may not mean much.
> 8. Monitoring the contents of each virtual desktop on the taskbar, KDE3.x style.
I'm not sure I understand this either.  I've got a pager, with all my desktops, and I have it set up so I have a cartoon of all the items on each desktop.  I can move items desktop to desktop.  This is exactly like kde3 to me.  Also the task "bar", which I take to be the widget that has a text/graphic list of all running tasks still exists. I can still choose to show all the tasks from all the desktops, only tasks from this desktop, etc.

Hope this is useful when you or others make the jump.  Actually, I really like it now.  I  just wish I could have the option to have each desktop have it's own wallpaper.  This was actually the reason I moved to and stayed with KDE, as it really improves my ability to get work done as I'm thrashed from task to task.

Tuna

---

### Post by awakatanka on 2008-09-17
If people want plasma follow the system colors then use aya that is the only plasma theme i know of that follows system colors. 

Has anyone got some information on add activty option? 
Zoom out with cashew our use shortcut CTRL- on desktop, click on cashew and if you use add activity it add a second desktop. I can also add a second desktop our more with pager , that activity thing looks the same but can't remove them after i have added it and can't switch to it with pager only zoom out and zoom in will show that second ( our more ) desktops. Does it replace pager desktop later on? our will it be used for other things?

---

### Post by madscientist159 on 2008-09-17
> **TunaBoy said:**
> madscientist

I am relatively new to Ubuntu (forced from Fedora by change in organization), but as a longtime KDE user, and someone who's moved over to 4.1, I wanted to answer some of your points, as it's not as bad as you might fear.

First, I am unsettled by the gnome-like loss of options, though I've seen some of them come back as I moved from KDE4.0 to 4.1.  I'm hoping the process continues.   Me too! :)

> **TunaBoy said:**
> 
Hope this is useful when you or others make the jump.  Actually, I really like it now.  I  just wish I could have the option to have each desktop have it's own wallpaper.  This was actually the reason I moved to and stayed with KDE, as it really improves my ability to get work done as I'm thrashed from task to task.Yes, it does help quite a bit, actually.  I need to completely reinstall Kubuntu alpha 5, as having a corrupt KDE4.1 install is probably not helping at all.

Glad to see someone else misses the multiple desktop wallpapers, and for the exact same reason! ;)

I am still trying to set up the repository--not sure if I should modify the existing Kubuntu packages for a new path or just do a clean build of the upstream KDE3.5.10.  Right now I am leaning towards the latter, as this really is just a stopgap measure until KDE4.2 reintroduces a couple missing features.  Another option would be to build packages that would stomp on the existing KDE4 packages, but would force removal of the conflicting KDE4 packages first.

Here's one more question for those who know more about KDE4.1 than I do: Is there any way to get rid of the rounded window corners that are so prevalent in KDE4 in favor of the squared-off window corners of KDE3.5?  I have always **hated** the rounded "Fisher-Price toy" look of certain desktops (just a personal preference really, except that it also wastes screen space).

Thanks!

EDIT: Looks like these features actually made it to the KDE4.2 feature plan ([http://techbase.kde.org/Schedules/KDE4/4.2_Feature_Plan](http://techbase.kde.org/Schedules/KDE4/4.2_Feature_Plan)), so it is just a matter of getting by until KDE4.2 comes out.

---

### Post by TunaBoy on 2008-09-17
[QUOTE=madscientist159;5808463]Me too! :)
Here's one more question for those who know more about KDE4.1 than I do: Is there any way to get rid of the rounded window corners that are so prevalent in KDE4 in favor of the squared-off window corners of KDE3.5?  I have always **hated** the rounded "Fisher-Price toy" look of certain desktops (just a personal preference really, except that it also wastes screen space).
[\QUOTE]

Moving back to the sharper corners is easy, although I have to admit I really like the rounded corners.  

System Settings -> Appearance -> Windows and pick something retro like "KDE 2", as opposed to "Oxygen".

Got to go, but I'm happy to hear some of these features are going to get back in 4.2.  

Tuna

---

### Post by madscientist159 on 2008-09-17
Thanks for the tip--works great!

Now, how do I bring up something like the old "Configure Panel-->Menus" option of KDE3?  I want to add things like the Run command back to my classic start menu (without resorting to the Menu Editor application--under KDE3.5 this was a simple point and click operation)

BTW the reason I couldn't get into the control center was because the classic start menu is missing that option entirely!  I think I need to file a bug report... :)

EDIT: Another couple of annoyances from the past hour--any fixes are welcome:
1. I want to use the desktop as a "dumping ground" for anything and everything, KDE3.5 style.  Can I do this?  I don't want the icons and files to be treated as widgets or anything stupid like that. :)
2. How can I disable Dolphin?  No offense, but I personally hate Dolphin and would like to use Konqueror instead (and please don't tell me I have to manually remove the dolphin binary and symlink /usr/bin/dolphin to /usr/bin/konqueror)  For that matter, how can I change the application launcher for any file type that I choose?  This was a very powerful feature in KDE3.5, far better than Windows' handling of this task, but in KDE4.1 it is far **worse** than any version of Windows I have ever tried!  Feels like a big step backwards to me...

---

### Post by madscientist159 on 2008-09-21
OK, the repository is now online and loaded up with i386 packages.  Get 'em while they're hot! :)

Add this line to your /etc/apt/sources.list file:
[http://apt.pearsoncomputing.net/](http://apt.pearsoncomputing.net/) intrepid main
and then run apt-get update and apt-get install kde3

You will probably also want to install the gtk-qt-engine package for pretty GTK application support.

WARNING: This will completely remove your KDE4 installation, so be absolutely sure you want to revert to KDE3.5 before you do this.

I have also included a couple of other legacy packages in this repository, such as Glade v2, so look around for them in Synaptic. ;)

AMD64 packages will be added after Intrepid goes to full release, as I only have 3 64-bit systems and they are all used in mission-critical areas.

Let me know what you think!

Tim

---

### Post by TheMono on 2008-09-21
Great work. I've got no interest in using it myself, being a KDE4 lover, but this is what makes free software great - if someone doesn't like something, they can change it and share the results with everyone. Thanks for providing this!

---

### Post by TheMono on 2008-09-21
> **madscientist159 said:**
> 
EDIT: Another couple of annoyances from the past hour--any fixes are welcome:
1. I want to use the desktop as a "dumping ground" for anything and everything, KDE3.5 style.  Can I do this?  I don't want the icons and files to be treated as widgets or anything stupid like that. :)
2. How can I disable Dolphin?  No offense, but I personally hate Dolphin and would like to use Konqueror instead (and please don't tell me I have to manually remove the dolphin binary and symlink /usr/bin/dolphin to /usr/bin/konqueror)  For that matter, how can I change the application launcher for any file type that I choose?  This was a very powerful feature in KDE3.5, far better than Windows' handling of this task, but in KDE4.1 it is far **worse** than any version of Windows I have ever tried!  Feels like a big step backwards to me...

1) Just create a folder view widget, expand it to cover the whole desktop, and set it to showing the desktop folder. Then switch to a plasma theme which has a totally transparent background. The only catch with this, at the moment, is you can't rearrange your icons arbitrarily and have it remember locations.

2) SystemSettings - Advanced - File Associations. Change inode/directory and inode/symlink to associate with Konqueror rather than Dolphin.

---

### Post by of_darkness on 2008-09-22
> **madscientist159 said:**
> OK, the repository is now online and loaded up with i386 packages.  Get 'em while they're hot! :)

Add this line to your /etc/apt/sources.list file:
[http://apt.pearsoncomputing.net/](http://apt.pearsoncomputing.net/) intrepid main
and then run apt-get update and apt-get install kde3

You will probably also want to install the gtk-qt-engine package for pretty GTK application support.

WARNING: This will completely remove your KDE4 installation, so be absolutely sure you want to revert to KDE3.5 before you do this.

I have also included a couple of other legacy packages in this repository, such as Glade v2, so look around for them in Synaptic. ;)

AMD64 packages will be added after Intrepid goes to full release, as I only have 3 64-bit systems and they are all used in mission-critical areas.

Let me know what you think!

Tim

Nice:) shall try it out when you add the 64bit packges:)

is the dependency set to the main repo kde4 packges? and not the ppa for hardy kde4?

---

### Post by madscientist159 on 2008-09-28
OK, the amd64 packages are now built and available.

A couple of caveats and warnings:
1. You may want to install the Ubuntu/Xubuntu/server edition of Intrepid (not Kubuntu) and then install KDE3 on top of that.  Otherwise you will have to drop to a command line and manually remove most of KDE4 before KDE3 will install properly (mainly kdebase-runtime and its dependencies have to go)  In the future I will update the KDE3 metapackage to conflict with the Intrepid kdebase-runtime.
2. The Ubuntu developers DO NOT support these packages, even if the packages themselves say so.  Quite a few of the i386 packages were built with the incorrect maintainer field by accident, so the maintainer will be fixed as the individual packages are rebuilt sometime in the future.
3. This repository may very well eat your cat and cause your computer to go up in smoke.:)  Please back up your system before attempting the "downgrade" to KDE3...

With regards to the KDE4 PPA versus mainline, I have only tested (and conflicted with) mainline.  As far as I know, you can install the KDE4 PPA packages alongside mine without any difficulty.

Let me know if you have any problems!

Tim

---

### Post by beartard on 2008-09-28
> **madscientist159 said:**
> 
A couple of caveats and warnings:
Is there going to be another caveat that people running kde3 under intrepid forfeit the right to post in the testing section unless they're absolutely certain it's not a problem with kde3?  ;)

---

### Post by Vorian on 2008-09-28
> **beartard said:**
> Is there going to be another caveat that people running kde3 under intrepid forfeit the right to post in the testing section unless they're absolutely certain it's not a problem with kde3?  ;) along with any other non-supported applications ;-)

---

### Post by madscientist159 on 2008-09-29
> **Vorian said:**
> along with any other non-supported applications ;-)

Sounds good to me!:)

Any problems with this repository should be reported **here only**.

---

### Post by madscientist159 on 2008-09-29
I have been testing KDE3 on Intrepid for a little while now, and thought I'd share the following advice:
1. Wondering where the restricted driver install utility went?  Do a sudo apt-get install jockey
2. Sick of the ugly interface on your KDE4 apps?  Do a sudo apt-get install kde4-style-qtcurve
3. Can't mount your removable media?  Reboot the computer--some of the Intrepid updates changed the HAL policies around.
3. Problems with your encrypted USB drive?  Can't help you here!:D  (Actually it seems there is a bug of some kind, but I need time to see if it is an Intrepid HAL bug, i.e. in KDE4 as well, or just in KDE3)

---

### Post by dentaku65 on 2008-10-01
A similar tread is present on Kubuntu forum....
[http://kubuntuforums.net/forums/index.php?topic=3096011.0]("http://kubuntuforums.net/forums/index.php?topic=3096011.0")

Maybe Kubuntu users for Intrepid wants the possibility to have kde3 too as wm; me +1
:D

---

### Post by Vorian on 2008-10-01
> **dentaku65 said:**
> A similar tread is present on Kubuntu forum....
[http://kubuntuforums.net/forums/index.php?topic=3096011.0]("http://kubuntuforums.net/forums/index.php?topic=3096011.0")

Maybe Kubuntu users for Intrepid wants the possibility to have kde3 too as wm; me +1
:D
cool, on that note i'll go ahead and close this thread.

for clarifications sake, i'll submit the following:

KDE 3 on Intrepid is not supported by Kubuntu or Ubuntu forums.  dentaku65 provided a link to Kubuntu Forums for users who choose to use KDE 3 in intrepid and would like support.

---

