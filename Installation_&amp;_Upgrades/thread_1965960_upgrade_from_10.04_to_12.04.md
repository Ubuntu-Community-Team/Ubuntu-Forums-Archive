---
title: "upgrade from 10.04 to 12.04"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by kevinorourke2008 on 2012-04-26
Hi everybody, I've just followed the instructions on the ubuntu webpage about upgrading to 12.04 but all I'm being offered in update manager is 10.10. Is there any way around this ? I don't want to upgrade to 10.10 then again to 11.!!!! then 12.04. I just want to go straight to 12.04. Help please

p.s. I've already tried update-manager -d.


cheers Kev

---

### Post by techsupport on 2012-04-26
> **kevinorourke2008 said:**
> Hi everybody, I've just followed the instructions on the ubuntu webpage about upgrading to 12.04 but all I'm being offered in update manager is 10.10. Is there any way around this ? I don't want to upgrade to 10.10 then again to 11.!!!! then 12.04. I just want to go straight to 12.04. Help please

p.s. I've already tried update-manager -d.


cheers Kev

AFAIK you can't. A better option would be to do a fresh installation:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

Backup your data first. 

:popcorn:

---

### Post by jadtech on 2012-04-26
ok now that some one has stirred my memory here I believe I have read discussion some where on this board  if you have 10.10 it will be possible to upgrade to 12.04  ..

I cold be wrong on this but I think  the word was not possible from 10.04 forget the reason  I think something like it is only possible to go LTS to LTS upgrade ..

---

### Post by nariub on 2012-04-26
I believe the op said he wanted to go from 10.04 to 12.04.  which is supposed to work.

open update-manager
go to settings at the bottom
   
on the bottom of settings page you will see 
"**Release Upgrade**"
set that to "**Long Term Support Releases Only**"

if it is set to normal releases it offers 10.10.
set to LTS only, and LTS is offered (12.04)

---

### Post by jadtech on 2012-04-26
> **nariub said:**
> I believe the op said he wanted to go from 10.04 to 12.04.  which is supposed to work.

open update-manager
go to settings at the bottom
   
on the bottom of settings page you will see 
"**Release Upgrade**"
set that to "**Long Term Support Releases Only**"

if it is set to normal releases it offers 10.10.
set to LTS only, and LTS is offered (12.04)

thats how  update manager is set by default I never change what I have here and that is how its set .. 

thing is 10.10 is a active LTS that is the option they are given ..

---

### Post by nariub on 2012-04-26
my apologies, but 10.10 is not an LTS.

---

### Post by nariub on 2012-04-26
if the op has already tried 
sudo do-release-upgrade -d 

then it may be that the mirrors have not updated yet.

My 10.04.4 is telling me the same thing.
:~$ do-release-upgrade -c
Checking for a new ubuntu release


My 11.10 box is happy
~$ do-release-upgrade -c
Checking for a new ubuntu release
New release '12.04 LTS' available.
Run 'do-release-upgrade' to upgrade to it.

---

### Post by jadtech on 2012-04-26
directly from Ubuntu.com


Upgrading from Ubuntu 10.04 LTS to Ubuntu 12.04 LTS
To upgrade from 10.04 LTS on a desktop system, upgrade over the network with the following procedure.

Start System/Administration/Software Sources
On the Updates tab, set Show new distribution releases: to Long term support releases only, then press Close.
Press Alt-F2 and type update-manager
Click the Check button to check for new updates. If there are any updates to install, use the Install Updates button to install them, and press Check again after that is complete.
A message will appear informing you of the availability of the new release. Click Upgrade.
Follow the on-screen instructions.


what you are saying to do is correct how ever instrction say to do all update shown  first update is to 10.10 , do all up dates till there are no more then check for upgrades :)

you just cant jump  that far ahead  I guess maybe to many changes all at once I dont know ,,

here is the link 

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS)

---

### Post by mo79 on 2012-04-26
I'm waiting to do the 10.04 to 12.04 jump too, I guess it'll probably take a few days before update manager shows me the upgrade.

---

### Post by Xelort on 2012-04-26
Sorry if it's already said elsewere but, when i click "upgrade" (from my 10.04 to 12.04), there's then a window with a text saying that precise is "still beta, do not install in production machines". 
Is that true, or just some kind of not-yet-updated changelog?
Thanks

---

### Post by jadtech on 2012-04-26
that most likly a good choice, since the server are clogged and updates seem to stall andeven disconnect mid up date not sure if you can just continue were left off  or if it just messes everything up either way I would think there is less chance for corruption not staling out sound like the upgrade from 10.04 could be a good 6 or more hours..

---

### Post by mikewhatever on 2012-04-26
Check out the Release Notes:

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#PrecisePangolin.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure-1.Upgrades](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#PrecisePangolin.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure-1.Upgrades)

> Upgrades from Ubuntu 10.04 LTS to 12.04 LTS do not work using the alternate CD or the server CD as a package repository. It is recommended that users running Ubuntu 10.04 LTS wait for the 12.04.1 LTS point release, scheduled for July, before upgrading. (988941)

I think it may be related to your issue.

---

### Post by jadtech on 2012-04-26
> **Xelort said:**
> Sorry if it's already said elsewere but, when i click "upgrade" (from my 10.04 to 12.04), there's then a window with a text saying that precise is "still beta, do not install in production machines". 
Is that true, or just some kind of not-yet-updated changelog?
Thanks

no its no longer beta the release is out as of roughly 12;30 am EST this morning ..

maybe you need to change your server and refresh the cache

---

### Post by jadtech on 2012-04-26
> **mikewhatever said:**
> Check out the Release Notes:

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#PrecisePangolin.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure-1.Upgrades](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#PrecisePangolin.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure-1.Upgrades)



I think it may be related to your issue.

that is why  there  site tells everyone to do the update to 10.10 then the upgrade to 12.04 will come up for them ..

---

### Post by kevinorourke2008 on 2012-04-26
Hi guys, thank you so much for the info I changed my settings to LTS and the upgrade to 10.10 has vanished, but no 12.04 yet maybe patience is the key to this one ? It might take a little while for the upgrade to come through the ether ?

---

### Post by kevinorourke2008 on 2012-04-26
Hi guys, just been researching on the net and it is true the update from 10.04 lts to 12.04 lts is not going to happen until July. when it is actually 12.04.1 lts.
It's my birthday in July so I'm going to wait until then and treat it as a birthday present from Ubuntu.

Cheers everybody.

Kev

---

### Post by mikewhatever on 2012-04-26
> **kevinorourke2008 said:**
> Hi guys, thank you so much for the info I changed my settings to LTS and the upgrade to 10.10 has vanished, but no 12.04 yet maybe patience is the key to this one ? It might take a little while for the upgrade to come through the ether ?

That might be because your local mirror is not yet fully updated, some mirrors are a day or so behind the main one. Out of curiosity, I've just tested the 'update-manager -d' command, and the update manager launched offering to upgrade to 12.04.

---

### Post by jadtech on 2012-04-26
> **mikewhatever said:**
> That might be because your local mirror is not yet fully updated, some mirrors are a day or so behind the main one. Out of curiosity, I've just tested the 'update-manager -d' command, and the update manager launched offering to upgrade to 12.04.

have you  installed any updates today before this popped up for you now ??? 

the dist notes are very clear  for version 10.04 that to upgrade to 12.04 you have to install all updates till you are at version 10.10  then you will see the upgrade notice ..

---

### Post by nariub on 2012-04-26
jadtech, I love you man, but you are wrong and keep pounding on the 10.10 update thing..

please let it go.
you need to make sure you have all the latest updates for your 10.04 so you will be the freshest 10.04 you can be.  then when offered, update to 12.04.

If you confuse someone into updating into 10.10 they will hate you forever..
because then they will be on the gotta do a fresh install or walk it to 11.04 and then 11.10 and then to 12.04.

Let it go, please

---

### Post by jadtech on 2012-04-26
im not pounding it and to say I am wrong is a bit off !!!

this link here 
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS)

directly from ubuntu wiki  page 

Upgrading from Ubuntu 10.04 LTS to Ubuntu 12.04 LTS
It is generally recommended that users of Ubuntu 10.04 LTS wait until the first point release, due in July, before upgrading.

To upgrade from 10.04 LTS on a desktop system before then, upgrade over the network with the following procedure.

Start System/Administration/Software Sources
On the Updates tab, set Show new distribution releases: to Long term support releases only, then press Close.
Press Alt-F2 and type update-manager -d
 **] Click the Check button to check for new updates. If there are any updates to install, use the Install Updates button to install them, and press Check again after that is complete.**
A message will appear informing you of the availability of the new release. Click Upgrade.
Follow the on-screen instructions.

there instructions not mine don't shoot the one passing the direction along it is not an assumption if you update all the updates for 10.04 you will be at the point of 10.10 if you had or have fell behind on updates for 10.04 at some point you need to get the updates first ..

---

### Post by Bucky Ball on 2012-04-26
> **jadtech said:**
> have you  installed any updates today before this popped up for you now ??? 

the dist notes are very clear  for version 10.04 that to upgrade to 12.04 you have to install all updates till you are at version 10.10  then you will see the upgrade notice ..

Don't know where you're getting all this. LTS to LTS has been possible for ages. It is 10.10 that WON'T upgrade to 12.04 LTS. If you go that route you will be upgrading 10.04>10.10>11.04>11.10>12.04. You'll find the same issue with 11.04 > 12.04 LTS. 11.10, of course, doesn't have this problem as 12.04 is the next release.

Incidentally, my 10.04 update manager has been showing the option to upgrade to 12.04 for some time ...

---

### Post by jadtech on 2012-04-26
im not pounding it and to say I am wrong is a bit off !!!

this link here 
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS)

directly from ubuntu wiki  page 

Upgrading from Ubuntu 10.04 LTS to Ubuntu 12.04 LTS
 **It is generally recommended that users of Ubuntu 10.04 LTS wait until the first point release, due in July, before upgrading **.

To upgrade from 10.04 LTS on a desktop system before then, upgrade over the network with the following procedure.

Start System/Administration/Software Sources
On the Updates tab, set Show new distribution releases: to Long term support releases only, then press Close.
Press Alt-F2 and type update-manager -d
 **] Click the Check button to check for new updates. If there are any updates to install, use the Install Updates button to install them, and press Check again after that is complete.**
A message will appear informing you of the availability of the new release. Click Upgrade.
Follow the on-screen instructions.

there instructions not mine don't shoot the one passing the direction along it is not an assumption if you update all the updates for 10.04 you will be at the point of 10.10 if you had or have fell behind on updates for 10.04 at some point you need to get the updates first ..

i belieeve what it is saying is update all the way to 10.10 or wait till july :)

---

### Post by jadtech on 2012-04-26
> **Bucky Ball said:**
> Don't know where you're getting all this. LTS to LTS has been possible for ages. It is 10.10 that WON'T upgrade to 12.04 LTS. If you go that route you will be upgrading 10.04>10.10>11.04>11.10>12.04. You'll find the same issue with 11.04 > 12.04 LTS. 11.10, of course, doesn't have this problem as 12.04 is the next release.

Incidentally, my 10.04 update manager has been showing the option to upgrade to 12.04 for some time ...

it was in some post here on the forum about upgrading older ubuntu version to 12.04 i cant remember which one but some one was upgrading  from version 8 something one version at a time and  it was discussed that they can jump from 10.10 to 12.04  no problem . I think that was the advice given at the time .. 

the ubuntu wiki is some what making the same point ..


I believe

---

### Post by nariub on 2012-04-26
> **jadtech said:**
> im not pounding it and to say I am wrong is a bit off !!!

this link here 
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS)

directly from ubuntu wiki  page 

Upgrading from Ubuntu 10.04 LTS to Ubuntu 12.04 LTS
It is generally recommended that users of Ubuntu 10.04 LTS wait until the first point release, due in July, before upgrading.

To upgrade from 10.04 LTS on a desktop system before then, upgrade over the network with the following procedure.

Start System/Administration/Software Sources
On the Updates tab, set Show new distribution releases: to Long term support releases only, then press Close.
Press Alt-F2 and type update-manager -d
 **] Click the Check button to check for new updates. If there are any updates to install, use the Install Updates button to install them, and press Check again after that is complete.**
A message will appear informing you of the availability of the new release. Click Upgrade.
Follow the on-screen instructions.

there instructions not mine don't shoot the one passing the direction along it is not an assumption if you update all the updates for 10.04 you will be at the point of 10.10 if you had or have fell behind on updates for 10.04 at some point you need to get the updates first ..


You are confusing updates and upgrades and release upgrades
updates is pulling the new updates for your release
upgrade in the context above could be better stated as "install updates"
release upgrade is a different button on the top of the screen

---

### Post by hno3 on 2012-04-27
Bucky Ball and nariub are correct.

Here is the proof:-
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=216716&stc=1&d=1335552839[/IMG]
This a screenshot of my 10.04 LTS desktop. I have the option to 

Just to clarify...

One can only jump from one upgrade to the immediate next upgrade. The only exceptions that are allowed are for one Long term support version to other long term support version. So 10.04 LTS to 12.04 LTS is possible.

However, 10.10 is not an LTS and therefore user cannot jump from 10.10 to 12.04 LTS directly without going through 11.04 and 11.10..

So if a person having 10.04 LTS is looking for 12.04 upgrade, then please DON'T upgrade to 10.10 otherwise you definitely would have to go through both the 11.04 and 11.10.

I'd suggest to wait till July for "first point release". I am waiting for the same.

---

### Post by nariub on 2012-04-30
I did up a 10.04 laptop to 12.04 over the weekend.

other than the fact it blew up the gnome graphics and I could not read several dialog boxes during the install it went kinda nice..  I havent had a chance to beat on that laptop much but I have taken two 11.10's and one 10.04 to 12.04  
And I still have 2 11.10s and a 10.04 to upgrade..




(when the graphics blew up in 10.04, I kept clicking the lower right hand check box as that is where OK usually resides)

---

