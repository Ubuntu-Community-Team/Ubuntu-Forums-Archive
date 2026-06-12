---
title: "KDE4 broken after todays updates"
date: 2008-05-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by caryb on 2008-05-27
I updated today & I get a lovely dark blue screen & nada! I ctl + alt backspace to go to kde3 but It's missing but I have Gnome in it's place:confused: So I selected Gnome & I get my desktop icons but no taskbar!
I guess one good thing is most apps I use are on the desktop! Since my update to Itrepid I have had a ritual of booting into recovery mode deleting my /home/.kde4/share folder so that I can logon. 

I guess it's missing deps are the problem so I guess I'm in 1/2 Gnomeland for a while:-$


Cary

---

### Post by disturbedite on 2008-05-27
i've got the same problem, but i only have the kde4 de installed.  i'm using a kubuntu 8.04-kde4 live disc right now.

i should be careful what i wish for; i was pretty aggrivated that we didn't have kde 4.1 alpha or beta yet in intrepid, well now we do.  partially that is, i think the reason for the breakage is that only a handful of kde4 packages have been updated to 4.1 beta.  so there is some missing stuff.
before the login window/greeter loads, i get a little window/widget that says:
"No greeter widget plugin loaded.  Check the configuration." so i click the only button, (OK), & i get dumped back to command line login.

i guess we just have to wait for the rest of the packages to be updated to 4.1 beta & hit the repos...

---

### Post by caryb on 2008-05-27
I just had a brain snap & thought I would install the rest of Gnome, but alas if I select gnome or gnome-core it wants to break everywhere:confused:
I guess I'll leave it alone!


Cary

---

### Post by inportb on 2008-05-27
lol, that sounds unfortunate. I had some major X breakage not long ago, and it turned out to be some problem with fglrx :x

---

### Post by disturbedite on 2008-05-28
man, 6 hours later and this problem still hasn't been resolved...

---

### Post by Sicarii on 2008-05-28
"No greeter widget plugin loaded. Check the configuration." so i click the only button, (OK), & i get dumped back to command line login.
Just upgraded to Intrepid today and...whamm..straight into this problem.
There's a dep problem between kidelibs4 and kdelibs5.
'at' fails on upgrade or installation.
'xinit' has a heart attack when kdm is booted up.
So I reinstalled gdm, and kicked into kde4 from there, which made it slightly workable....better than nothing

---

### Post by disturbedite on 2008-05-28
well i definitely knew that it was a dependency problem.  nothing a new update wouldn't fix, afaik.  but i still haven't received those updates!  this is very frustrating, but i guess thats what we get for using a pre-release.
i'm not willing to install gdm just for this though...  (i'm running purely kde4).

---

### Post by utUtu on 2008-05-28
> **disturbedite said:**
> well i definitely knew that it was a dependency problem.  nothing a new update wouldn't fix, afaik.  but i still haven't received those updates!  this is very frustrating, but i guess thats what we get for using a pre-release.
i'm not willing to install gdm just for this though...  (i'm running purely kde4).

Not until Debian is done I suppose.  It's barely functioning right now out of experimental.

---

### Post by meborc on 2008-05-28
> **disturbedite said:**
> well i definitely knew that it was a dependency problem.  nothing a new update wouldn't fix, afaik.  but i still haven't received those updates!  this is very frustrating, but i guess thats what we get for using a pre-release.
i'm not willing to install gdm just for this though...  (i'm running purely kde4).

people who get frustrated over pre-alpha software problems should maybe not use them :lolflag:

i know i know... that you know... and that everybody knows... but still people get frustrated :) that is just so funny

---

### Post by disturbedite on 2008-05-29
> **utUtu said:**
> Not until Debian is done I suppose.  It's barely functioning right now out of experimental.
so is jonathan riddell simply syncing the packages from debian, or is this an ubuntu issue?  (i didn't notice a mention in the changelogs).

---

### Post by utUtu on 2008-05-29
> **disturbedite said:**
> so is jonathan riddell simply syncing the packages from debian, or is this an ubuntu issue?  (i didn't notice a mention in the changelogs).

I have no idea what's going on.  But your guess is as good as mine.  As Mark S. have admitted Ubuntu is **_very much_** dependent on Debian.

When 4.1beta was released, Debian has already packages in experimental, Mandriva, OpenSuse, Windows and Mac OS - yes Windows, are ready.  'Kubuntu packages are in preparation', and looks like has not changed.

So, I have enabled experimental and I'm now enjoying 4.1 beta. :guitar:

---

### Post by 23meg on 2008-05-29
[http://blog.nixternal.com/2008.05.28/hardy-kde-41-beta-packages-soon/](http://blog.nixternal.com/2008.05.28/hardy-kde-41-beta-packages-soon/)

---

### Post by caryb on 2008-05-29
There seems to be a lot of emphasis on 4.1 for Hardy, I would have thought we would have had the chance of "breaking" it 1st:confused:


Cary

---

### Post by utUtu on 2008-05-29
> **23meg said:**
> [http://blog.nixternal.com/2008.05.28/hardy-kde-41-beta-packages-soon/](http://blog.nixternal.com/2008.05.28/hardy-kde-41-beta-packages-soon/)

He forgot all about it.. :guitar:

```
The reason we waited was….well I forgot all about them actually because I was totally busy with something else :)
```

---

### Post by caryb on 2008-05-29
Mind you It's been a few days now & I'm still on KDE3 as KDE4 is still kaput:confused:


Cary

---

### Post by disturbedite on 2008-05-29
> **caryb said:**
> Mind you It's been a few days now & I'm still on KDE3 as KDE4 is still kaput:confused:


Cary
you're lucky.  i've been having to use a kubuntu 8.04-kde4 live disc for the past two or three days!  (its been so long, i don't remember exactly how long its been)!

UPDATE:
i got sick & tired of waiting  so i gave myself (ubuntu:ubuntu when using a live disc) write permission on my HDD & downloaded the 4.0.4 versions of the 4.1 beta 1 (4.0.80) packages & rebooted to command line & downgraded/installed the 4.0.4 packages to get my DE back to a working state.
i will wait till a bunch of the 4.1 beta 1 packages hit the repo before i updated kde again.

---

### Post by disturbedite on 2008-06-02
UPDATE:
nixternal said on his blog (in the comments section of the "Hardy KDE 4.1 Beta Packages Soon" article) that 4.1 beta 1 packages should be done tuesday.  yay!

ANOTHER UPDATE:
don't mix niternal's hardy 4.1b1 packages with the official (jonathan riddell's) 4.1b1 packages for intrepid.  it will likely hose your DE.  it did mine.

---

### Post by xebian on 2008-06-04
> **disturbedite said:**
> UPDATE:
nixternal said on his blog (in the comments section of the "Hardy KDE 4.1 Beta Packages Soon" article) that 4.1 beta 1 packages should be done tuesday.  yay!

ANOTHER UPDATE:
don't mix niternal's hardy 4.1b1 packages with the official (jonathan riddell's) 4.1b1 packages for intrepid.  it will likely hose your DE.  it did mine.

You mean tuesday next week? month?  :)

BTW, is 4.0.5 will be available?  I believe it's to be released June 4,2008.

---

### Post by caryb on 2008-06-04
We are supposed to be testing this before the next release, I wonder how long it is before we have a working KDE4. 

Does anyone know of a distro with a working current KDE4 I can play with while Jonathan gets Kubuntu right:confused:


Cary

---

### Post by utUtu on 2008-06-04
> **caryb said:**
> We are supposed to be testing this before the next release, I wonder how long it is before we have a working KDE4. 

Does anyone know of a distro with a working current KDE4 I can play with while Jonathan gets Kubuntu right:confused:


Cary

Debian Lenny/Sid with Experimental enabled.  I have 4.1 working day after release.  Pretty stable.  :guitar:

---

### Post by disturbedite on 2008-06-04
> **xebian said:**
> You mean tuesday next week? month?  :)

BTW, is 4.0.5 will be available?  I believe it's to be released June 4,2008.
well, since hardy & intrepid are getting 4.1b1 packages, no, i don't think we'll see 4.0.5 in the repos.

---

### Post by disturbedite on 2008-06-04
> **caryb said:**
> We are supposed to be testing this before the next release, I wonder how long it is before we have a working KDE4. 

Does anyone know of a distro with a working current KDE4 I can play with while Jonathan gets Kubuntu right:confused:


Cary
you still have the "No greeter widget plugin loaded" message?
i do too...
currently using a live disc.  (again)

---

### Post by caryb on 2008-06-04
I don't have anything but a blue screen (can go to Windows for that) I have the KDE splash screen then it stops to a blue screen that renders my laptop useless! I cant even ctl + alt backspace back to kill X, at the moment I'm back in KDE3 land. I haven't logged on for a couple of days (am setting up for a local show for this weekend) & I have 135 updates & 22 removals, all KDE4 stuff like Dolphin & kde4-core etc. So I guess I'll have to wait for whatever dependency is missing or broken before I get a chance to see if they have fixed the KDE4 blues in Kubuntu. I am starting to think that Gnome is looking ok :shock:


Cary

---

### Post by disturbedite on 2008-06-05
> **caryb said:**
> I don't have anything but a blue screen (can go to Windows for that) I have the KDE splash screen then it stops to a blue screen that renders my laptop useless! I cant even ctl + alt backspace back to kill X, at the moment I'm back in KDE3 land. I haven't logged on for a couple of days (am setting up for a local show for this weekend) & I have 135 updates & 22 removals, all KDE4 stuff like Dolphin & kde4-core etc. So I guess I'll have to wait for whatever dependency is missing or broken before I get a chance to see if they have fixed the KDE4 blues in Kubuntu. I am starting to think that Gnome is looking ok :shock:


Cary
i get the blue sceen after the kde splash screen too. but then i get a little window that says what i mentioned before. then it dumps me back to command line login.

---

### Post by caryb on 2008-06-05
It's ashame that Kubuntu that does so well on distro watch is so under resourced, It's almost embarrassing the length of time this has been down! I wonder if the Kubuntu devs read the bug reports or forums:confused: I came from Debian because of the pace that *buntu implements new ideas & packages, but on the KDE side of things it is so poor that Debian leaves Kubuntu for dead.


Cary (confused Kubuntu user)

BTW this is not a I'm taking my bat & ball & going home rant but a frank dialog on the state of Kubuntu at the moment.

---

### Post by lewmnik on 2008-06-06
> **caryb said:**
> It's ashame that Kubuntu that does so well on distro watch is so under resourced, It's almost embarrassing the length of time this has been down! I wonder if the Kubuntu devs read the bug reports or forums:confused: I came from Debian because of the pace that *buntu implements new ideas & packages, but on the KDE side of things it is so poor that Debian leaves Kubuntu for dead.


Cary (confused Kubuntu user)

BTW this is not a I'm taking my bat & ball & going home rant but a frank dialog on the state of Kubuntu at the moment.

Devs rarely read the forums, but they do read the bug reports. The problem right now is that KDE 4 is so rapidly changing that bugs are fixed in the next version number rather than in the faulty package.:)

---

### Post by caryb on 2008-06-06
I don't believe this is a KDE issue as other distros have working KDE4 from what I can see we are the only one (Kubuntu) with this problem.


Cary

---

### Post by caryb on 2008-06-07
Well is totally stuffed now don't have any kde or kdm working! am now on Gnome:(


Cary

---

### Post by meborc on 2008-06-08
sometimes when new packages are replacing old ones and there is very rapid development going on, the apt is unable to upgrade your system correctly... that means that person who upgrades II from the beginning may not have the same experience then the one installing from daily or from alpha

again this is a piece of ALPHA operating system (sorry - pre-alpha)... it is NOT MEANT to work 100%... yes, other OSes have it running... so what... the deadline is october

what is your problem? :)

---

### Post by awakatanka on 2008-06-08
If you want a working Kde 4.1 on kubuntu then install hardy and at those lines that are announced here : [http://kubuntu.org/announcements/kde-4.1beta1.php](http://kubuntu.org/announcements/kde-4.1beta1.php)

Don use alpha our beta if you don't want anything to break, because that is what is going to happen in those versions.

---

### Post by caryb on 2008-06-09
I have upgraded but still have the missing widget problem! I dont get an option to what version to select so for now I'm stuck with gnome:confused:


Cary

---

### Post by caryb on 2008-06-09
This is now week 3 with broken deps & no KDE4! I wish they would step back & fix the dep issue before anymore upgrades. I know the caveat this is dev software blah blah, but 3 weeks is a long time in not having a functional O/S.


Cary

---

### Post by meborc on 2008-06-10
> **caryb said:**
> This is now week 3 with broken deps & no KDE4! I wish they would step back & fix the dep issue before anymore upgrades. I know the caveat this is dev software blah blah, but 3 weeks is a long time in not having a functional O/S.


Cary

use hardy :) intrepid is not supposed to be functional... let the devs deal with it... they have done it since 2004... i guess they know what they are doing

---

### Post by caryb on 2008-06-10
I have gone on a different tact & am using Gnome for a while! It's a lot different to KDE! I'm trying to adjust to a system without (or little) system utilities.


Cary

---

### Post by disturbedite on 2008-06-10
> **caryb said:**
> It's ashame that Kubuntu that does so well on distro watch is so under resourced, It's almost embarrassing the length of time this has been down! I wonder if the Kubuntu devs read the bug reports or forums:confused: I came from Debian because of the pace that *buntu implements new ideas & packages, but on the KDE side of things it is so poor that Debian leaves Kubuntu for dead.


Cary (confused Kubuntu user)

BTW this is not a I'm taking my bat & ball & going home rant but a frank dialog on the state of Kubuntu at the moment.
jonathan riddell is the only kubuntu dev. that is right, canonical only hired **1** kubuntu dev. i was/am not mad at jr, just at canonical.

i got fed up with canonical's laughable kde development/attention. i did my research and i have jumped ship to opensuse. i have to say, out of the box, opensuse is a billion times better. it is waaaaaaaay more feature-filled. you can tell that kubuntu only has one dev.
there are a dozen times more packages/programs available for opensuse compared to ubuntu as well.

i am now testing kde 4.1b1+ with opensuse 11.0 rc2. it was pretty easy to install too.
it is light years ahead of kubuntu. i'd highly recommend switching.

that is my two cents.

---

### Post by awakatanka on 2008-06-10
> **disturbedite said:**
> jonathan riddell is the only kubuntu dev. that is right, canonical only hired **1** kubuntu dev. i was/am not mad at jr, just at canonical.

i got fed up with canonical's laughable kde development/attention. i did my research and i have jumped ship to opensuse. i have to say, out of the box, opensuse is a billion times better. it is waaaaaaaay more feature-filled. you can tell that kubuntu only has one dev.
there are a dozen times more packages/programs available for opensuse compared to ubuntu as well.

i am now testing kde 4.1b1+ with opensuse 11.0 rc2. it was pretty easy to install too.
it is light years ahead of kubuntu. i'd highly recommend switching.

that is my two cents.I also think its better but the only thing that is holding me back to switch to opensuse is the rpm update system, i find it to slow, if i update the list it takes ages and installing also. I hear the are working on that in 11.0 but the version i tryed was still t slow in comparison to deb update and installing.

---

### Post by xebian on 2008-06-10
I don't know what to say, but if you are so desperate to check out kde4.1beta1 then get the ppa repos in hardy.

I. Ibex is not ready yet.  Even though the repos are open, devs are just preparing things for the alpha 1 release which is this Thursday.  You are like boys trying to snatch food in the kitchen.  Pls wait at the dining table.  :)

---

### Post by plun on 2008-06-10
Well... I saw this on Ubuntu Planet and an invite from Jonathan, 
I am a "gnomefreak" myself and can also have some opinions...:-#

I really like the way Kubuntu and KDE "just are doing it", without
endless discussions... just great !!

**Kubuntu meeting on Sunday**

[http://www.kdedevelopers.org/node/3511](http://www.kdedevelopers.org/node/3511)


So join up and express your opinions...

---

### Post by caryb on 2008-06-10
I think that the fact we have 1 dev for Kubuntu & having just releasing a LTS version the current version will be deprived! I think at this point I would help Kubuntu (my passion) by working with the Debian guys that way the fixes will eventually make there way back into Kubuntu. 


Cary

---

### Post by 23meg on 2008-06-10
Kubuntu doesn't have one developer; it has one *paid* developer working exclusively on it (meaning it benefits from the work of other paid developers as well). You can work with Kubuntu directly.

---

### Post by caryb on 2008-06-10
I now have a basic working KDE4, I cant do any admin functions or change desktops or resize icons but I'm now off Gnome! Packages like kde core etc will not install because of missing dependencies. :guitar:


Cary

---

### Post by disturbedite on 2008-06-11
@ awakatanka
in 11.0, it has been really sped up. (rpms are now packaged with lzma (iirc) compression which speeds up everything).

@ xebian
please read my whole post. i doubt you did. i explained this was/is a long term problem with canonical's attitude towards kde.

@ 23meg
i already said that in my post. it shows any way...

---

### Post by xebian on 2008-06-12
> **disturbedite said:**
> 
@ xebian
please read my whole post. i doubt you did. i explained this was/is a long term problem with canonical's attitude towards kde.

...

It wasn't meant for you.  Sorry.  I'm with you on the Kubuntu's treatment.  IN fact I was even going to suggest at the very least add Kubuntu to the Other OS Talk section. :)

---

### Post by disturbedite on 2008-06-13
> **xebian said:**
> It wasn't meant for you.  Sorry.  I'm with you on the Kubuntu's treatment.  IN fact I was even going to suggest at the very least add Kubuntu to the Other OS Talk section. :)
ah, ok.  i didn't mean that harshly, even though that is how it might have sounded...
no hard feelings. :)

---

### Post by scokar on 2008-06-19
anyone have KDE4 working "by default" yet ?

---

### Post by xebian on 2008-06-19
Was able to make a fresh cli install of I.Ibex today but kde4 packages are in a very sorry state I think.  A lot of the base/core packages are broken.

Does anyone have a working IIbex kde4 working/useable?

---

### Post by caryb on 2008-06-19
Was supposed to be fixed by Alpha 1 release 13 days ago! But no sign of being fixed. As there is no timeline to when it will be back on track & I assume Hardy is getting all of the resources I guess we could be in for a long wait:(


Cary

---

### Post by Nullack on 2008-06-20
Not sound harsh or anything, but talking honestly its my observation that Kubuntu gets hardly any resources and perhaps a better experience with KDE will be achieved by trying out OpenSuse 11? You could also get into the build service daily KDE builds for testing out the latest in the 4.1 kde tree.

Ive gone back to gnome because I found KDE 4 to be buggy still and I missed aspects of Ubuntu on OpenSuse.

---

### Post by scokar on 2008-06-20
> **Nullack said:**
> Not sound harsh or anything, but talking honestly its my observation that Kubuntu gets hardly any resources and perhaps a better experience with KDE will be achieved by trying out OpenSuse 11? You could also get into the build service daily KDE builds for testing out the latest in the 4.1 kde tree.

Ive gone back to gnome because I found KDE 4 to be buggy still and I missed aspects of Ubuntu on OpenSuse.

no, not harsh at all. 

As I run Kubuntu and am able to sometimes try out development releases, its sometimes fun to help resolve issues.

---

### Post by caryb on 2008-06-20
> As I run Kubuntu 

Is that possible at the moment? Week 3 of KDE4 being broken!



Cary


Cmon Jonathan give 8.4.1 a break for a while! :confused:

---

### Post by scokar on 2008-06-20
> **caryb said:**
> Is that possible at the moment? Week 3 of KDE4 being broken!



Cary


Cmon Jonathan give 8.4.1 a break for a while! :confused:

"as I run the production version of kubuntu" -- multiple machines:)

To the best of my knowledge, ubuntu does not take from debian experimental, so if KDE4 hasn't made it into debian unstable, there is not much Jonathan can do.

---

### Post by awakatanka on 2008-06-22
Funny that hardy has a better 4.1 then ibex and also have a nightly that is a bit better again then the kde 4.1 from hardy.

Ibex is the experimental in alpha, beta it's unstable and live is the stable i thought, and previous version gets backports from those. They know people are waiting for 4.1 to test so at least give them a little working one :P, and 4.1 will be live before ibex so getting it from debian experimental isn't that bad in this case. (if they really don't do that )

But i have fun with the nightly in hardy so it isn't a big deal for me.

---

### Post by caryb on 2008-06-22
Intrepid KDE4 has been broken 4 weeks today, Happy Anniversary:confused:


Cary

---

### Post by xebian on 2008-06-22
> **scokar said:**
> "as I run the production version of kubuntu" -- multiple machines:)

To the best of my knowledge, ubuntu does not take from debian experimental, so if KDE4 hasn't made it into debian unstable, there is not much Jonathan can do.

Where did they get the Hardy KDE4 Remix?  The 4.0.5 at hardy backport?  The 4.1 beta 1 for Hardy?  KDE4 only exist in Debian/experimental.

---

### Post by caryb on 2008-06-23
Bucket loads of KDE4 stuff coming through now! Should fix the problems!


Cary

On a good note I discovered that you can do cups/printer maintenance with a browser with [http://localhost:641](http://localhost:641) :lolflag:

---

### Post by Nullack on 2008-06-24
So technically thats a post bitching adjulation of the wonders that be in the realms of KDE on Ubuntu? I feel it mate.

---

### Post by stokedfish on 2008-06-24
[http://kde.org/announcements/announce-4.1-beta2.php](http://kde.org/announcements/announce-4.1-beta2.php)
[http://kubuntu.org/announcements/kde-4.1beta2.php](http://kubuntu.org/announcements/kde-4.1beta2.php)
[http://dot.kde.org/1214311382/](http://dot.kde.org/1214311382/)

:)

---

### Post by xebian on 2008-06-25
> **stokedfish said:**
> [http://kde.org/announcements/announce-4.1-beta2.php](http://kde.org/announcements/announce-4.1-beta2.php)
[http://kubuntu.org/announcements/kde-4.1beta2.php](http://kubuntu.org/announcements/kde-4.1beta2.php)
[http://dot.kde.org/1214311382/](http://dot.kde.org/1214311382/)

:)

Very poorly done.  Broken packages.

---

### Post by caryb on 2008-06-25
I believe there a lots of new packages to process but I don't think a lot of thought to hierarchy of apps or implications to not getting the order right has happened.


Cary

I could be wrong

---

### Post by tim-bl on 2008-06-25
my problem seems to be that kdm (or gdm) don't show a kde-session to select


anyone able to start kde4 in intrepid or knows how to create such a session?

thanks

---

### Post by tim-bl on 2008-06-26
solved!

turns out i was missing kdebase-workspace
now logged in to a beautiful kde4.1 beta2 on intrepid :-)

---

### Post by scokar on 2008-06-28
a fresh install of kubuntu intrepid alpha 1 lets me into a kde4 session, i'm currently using it now.

---

### Post by caryb on 2008-06-28
I have been replacing any app with -kde4 with the new version i.e. kate-kde4 with kate (both are at 4.0.83 etc) it seems to what is causing me grief.


Cary

---

### Post by scokar on 2008-06-28
> **caryb said:**
> I have been replacing any app with -kde4 with the new version i.e. kate-kde4 with kate (both are at 4.0.83 etc) it seems to what is causing me grief.


Cary


prior to my install of alpha1, i did a:

apt-get install --reinstall kubuntu-desktop

that also gave me a 'working' kde4 session.

---

### Post by awakatanka on 2008-06-28
Is it already workable if i install the alpha with updates?

From what i read it is messing up old and new packages ( with -kde and without )

If it simple installs and updates without messing to much I'm putting it on my test partition.

---

### Post by caryb on 2008-06-28
apt-get install --reinstall kubuntu-desktop seems to replace the old -kde4 packages!


Cary

---

### Post by awakatanka on 2008-06-28
Fresh install doesn't show KDM, it throws me back to CLI with errors that jumping in from ralink firmware when i try to type.

Tips from other in this thread doesn't solve it. Trying to install gdm now to see if that helps me.

---

### Post by awakatanka on 2008-06-29
After some fighting with alpha and gdm/kdm it didn solve my problem. Did a new install and it was the same. This time i did a recovery and did a recovery with X and after that it worked.

---

### Post by caryb on 2008-07-05
In the last 3 days my KDE4 is totaly broken, I will dot point my problems.
1. I get error message "could not start kstartupkde4" (is something like that but am back to Vista as I cant get past this) If I hit the ok button I get asci characters in multi colour & the pc is totaly locked up.
2. When booting up I have a 2 min wait to bring up networking, at this point there is no HDD activity & no keyboard response.
3 The only way to get KDM to activate is to boot to recovery mode & after 5 mins of being frozen (this is after the network freeze) I hit ctl + alt + del & I get the dialog box & I select resume boot & eventually I get the KDM logon.

I thought I would rebuild my pc so I did that as I had a lot of *.kde4 files & this would fix 2 problems. I fixed the .kde4 probs but after I did the updates I'm back to where I was before the rebuild:confused:

Am I the only one with these problems? What do I file this under in a bug report?

Any feedback would be appreciated, Cary

BTW I miss spellcheck in Linux :-(

---

### Post by xebian on 2008-07-05
> **caryb said:**
> In the last 3 days my KDE4 is totaly broken, I will dot point my problems.
1. I get error message "could not start kstartupkde4" (is something like that but am back to Vista as I cant get past this) If I hit the ok button I get asci characters in multi colour & the pc is totaly locked up.
2. When booting up I have a 2 min wait to bring up networking, at this point there is no HDD activity & no keyboard response.
3 The only way to get KDM to activate is to boot to recovery mode & after 5 mins of being frozen (this is after the network freeze) I hit ctl + alt + del & I get the dialog box & I select resume boot & eventually I get the KDM logon.

I thought I would rebuild my pc so I did that as I had a lot of *.kde4 files & this would fix 2 problems. I fixed the .kde4 probs but after I did the updates I'm back to where I was before the rebuild:confused:

Am I the only one with these problems? What do I file this under in a bug report?

Any feedback would be appreciated, Cary

BTW I miss spellcheck in Linux :-(

I have the same issue of pc kinda frozen.  Found out kwin is maxing out cpu for about 5  minutes.  Turned off desktop gui effects, and looks like it helped a lot.

---

### Post by caryb on 2008-07-05
Do you get the error message after loging on? "Could not start kstartupconfig4" ? I googled the error message but it only had something about permissions on file ~/.kde4/shares folder but that does not fix the problem.

Cary

---

### Post by firstc624 on 2008-07-05
> **caryb said:**
> Do you get the error message after loging on? "Could not start kstartupconfig4" ? I googled the error message but it only had something about permissions on file ~/.kde4/shares folder but that does not fix the problem.

Cary

YES, i get that error to caryb.  i just load up into failsafe mode and try to update as much as i can, of course i am currently running intrepid on vmware, as i didn't want to install fully on laptop yet.

but as of yet i do not knwo how to fix it  :-(

---

### Post by Gina on 2008-07-06
> **caryb said:**
> BTW I miss spellcheck in Linux :-(Strange - I have spellcheckers in Firefox and Open Office etc.  Only thing is... I have the EN-GB dictionary installed yet I still get US spellings :confused:

---

### Post by caryb on 2008-07-06
Gina, my ref to spellcheck was the fact I was stuck in Windowz land with no spell check! but the good news is I'm back in Kubuntu:guitar:

My fix was...

I booted to recovery console & executed the following:-

mv /home/myusername/.kde /home/myusename/.kdebac

ln -s /home/myusername/.kde4 /home/myusername/.kde

then ctl +d & selected resume & bingo all is good 

Cary

---

### Post by Gina on 2008-07-06
> **caryb said:**
> Gina, my ref to spellcheck was the fact I was stuck in Windowz land with no spell check! but the good news is I'm back in Kubuntu:guitar:

<...snip...>

CarySorry, I misread your post.

---

