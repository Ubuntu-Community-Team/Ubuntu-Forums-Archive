---
title: "Whats going on? upgrade woes from 10 to 12.04"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by basilwatson on 2012-04-28
Last night I saw on the Ubuntu front page and from other sources that 12.04 lts was ready to upgrade , so 

information backed up 

do-release-upgrade

and away we go , slow but ,,,,

next morning , installation errors , but please restart machine , which boots into a black screen ,, 

follow sticky on subject, gave up  reinstalled 10 

So I try again 

but this time , update-manager -d and do-release both return ..no distro found 

odd , it was ok last night ? 

has the upgrade been pulled ? servers down ...? 

I tried the upgrade on two different pc , amd and intel an both failed in the same way black screen last night and no disto today ....

anyone know whats going on?

Stephen

---

### Post by jadtech on 2012-04-28
for version 10.04 you have to do all the updates and such  until l the upgrade appears for you if you just re-installed you will have to keep doing  the updates till  the 12.04 release upgrade is avalable to you again ..

this is the info the ubuntu wiki is giving

---

### Post by basilwatson on 2012-04-28
> **jadtech said:**
> for version 10.04 you have to do all the updates and such  until l the upgrade appears for you if you just re-installed you will have to keep doing  the updates till  the 12.04 release upgrade is avalable to you again ..

this is the info the ubuntu wiki is giving


all the updates , or distro upgrades? ( 11.04 10 etc)

at the moment I have downloaded 12.04 ( beta ) and thrown it at the laptop seems to be working ....

just strange that last night  ( Im sure I did all the updates)  was ok today nothing?

oh well

Stephen

---

### Post by jadtech on 2012-04-28
if you are up to beta 

you can use this command in terminal window to complete to the release version 

```
 sudo apt-get update; sudo apt-get upgrade; sudo apt-get dist-upgrade 
``` 

or you can just continue to do updates over time till it updates its self ..

---

### Post by jadtech on 2012-04-28
as far was what  the wiki is saying about upgrading  for 10.044 it  is clear do all updates  though I am thinking short cutting to the next version would be faster  :)

---

### Post by QIII on 2012-04-28
Edit:  Sorry.  Missed the part where you said you had reinstalled 11.10 (I assume that's what you mean by "10").

The LiveCD now gives you the option to upgrade, not just to install.  I think that is on the "Allocate Drive Space" menu.  You could use that method if you can't do it from the terminal.  An LTS to LTS should work fine. 11.10 to 12.04 should work fine.  I'm not sure about an out-of-sequence upgrade from, say, 10.10 or 11.04 directly.

If the Beta doesn't offer that, download and burn the release.  If the Beta does offer it, you may get the Beta.  Just update and upgrade.  That will take you from the Beta to the full release version.


As a general aside:  There is no need to use "apt-get upgrade"  followed by " apt-get dist-upgrade".  Just use "apt-get dist-upgrade".  The latter does everything the former does with the addition of attempting to resolve dependency issues.

---

### Post by plucky on 2012-04-28
> all the updates , or distro upgrades? ( 11.04 10 etc)

No, but you have to be up to date with 10.04.4 before it offers you the Release-Upgrade to 12.04.

Good Luck

---

### Post by QIII on 2012-04-28
> **plucky said:**
> No, but you have to be up to date with 10.04.4 before it offers you the Release-Upgrade to 12.04.

Good Luck

Ah!  I was awakened by grandchildren far too early this morning!  I made the assumption that "reinstalled" also meant updated.

Good catch.

---

### Post by HouTex on 2012-04-28
> **plucky said:**
> No, but you have to be up to date with 10.04.4 before it offers you the Release-Upgrade to 12.04.
 
Good Luck
 
Darn, I just started the update process from 10.4 and it would not let me update directly to 12.4 (like I thought it should). So I'm in the middle of upgrading to 10.10 and I'll eventually get there. Should have read this post first.
 
[edit]  Is there anyway to revert back to version 10.4.4 from 10.10?  If so, I would think it would save time vs. upgrading to 11.4 and then 11.10 and then 12.4.

---

### Post by basilwatson on 2012-04-28
well .........

i DID get 12.04 installed and ,,,,,,it kind of works , but all of the packages used on 10.04 are broken

I was using CAELinux ... 

I changed the sources file and updated ....still broken 

Nuts , but at least the laptop is usable 

Stephen

---

