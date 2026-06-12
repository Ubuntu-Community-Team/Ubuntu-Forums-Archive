---
title: "From Release Candidate to Final Release (Gutsy)"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by lazyrussian on 2007-10-18
Hey,

If I upgraded to the release candidate a few days ago, do I still need to upgrade to the final release (released this morning). I'm trying to upgrade via the update manager but it's telling me I'm already up to date.

---

### Post by frenchcr on 2007-10-18
> **lazyrussian said:**
> Hey,

If I upgraded to the release candidate a few days ago, do I still need to upgrade to the final release (released this morning). I'm trying to upgrade via the update manager but it's telling me I'm already up to date.

youve got it already

---

### Post by ntwrkguy on 2007-10-18
Honestly, I'm a bit disappointed that there are no updates from RC to final. I had to futz with ALSA (which wasn't difficult at all) to get it to work with my sound upon upgrading, and using full effects with Compiz causes tab malfunctions in Firefox (but hey, at least I have my titlebars back...). Not to mention, I had to disable trackerd from running in a config file because of the intense CPU and memory usage. Are we taking steps forward or are we going backwards?

---

### Post by fingerle on 2007-10-18
We didn't get updates on the release, cause they've been updating the RC like crazy.
  I expect to see more updates as like with all things Linux it's an ongoing process. (We're not limited to "patch Tuesday") LoL
  Compiz still has a lot of growing to do, The backbone is stable enough, but some of the plugins still cause "interesting" problems. As the Compiz team gets those sorted, we'll see the fixes in short order.

  Personally I've found Gutsy to be an improvement over Feisty.  Boots quicker, Everything except my normal collection of non-linux supported hardware works. I have turned off the Compiz eye-candy for the reason stated above, and also killed the indexing and user switching bits as I don't require their use.

  Plain and simple, it's one of the fastest Distros I've tossed at my hardware and so far works like a champ.

That being said I believe Ubuntu is still moving forward.

  Please take note if the problems you've had and the steps you took to correct it. Post it. 
1) If you had the problem someone else will. (Easy to find fix/steps are a wonderful thing)
2) Dev team may be able to easily correct the problem permanently. :)

---

### Post by TeeAhr1 on 2007-10-18
[quote=lazyrussian]Hey,

If I upgraded to the release candidate a few days ago, do I still need to upgrade to the final release (released this morning). I'm trying to upgrade via the update manager but it's telling me I'm already up to date.[/quote]

Same here, I get the message "you are already up to date..." but when I go back into Adept and refresh my sources, I still get the icon for version upgrade.  What's up with that?

-pete

---

### Post by scapalexis888 on 2007-10-18
well, creating an operating system is not an easy task, and the Ubuntu development team is not getting paid a lot for their services. Look at Vista...I am pretty sure their release right now is still just a beta (but they need money to pay their programmers so force everyone to use it). Just wait a while. No need to rush.

---

### Post by TeeAhr1 on 2007-10-18
scapalexis888, I don't know if that was in reply to me or the OP, but I'm in no rush.  I was just wondering if it was a bug  in the process, or maybe the servers are just getting clubbed this morning and I'm not getting through so it's erroring out, or what.

The RC has been totally stable for me.  The sole problem I had was that it shot my fstab to hell and gone (I had a customized fstab, and upgraded from Feisty), so I lost my CD drives for a day, ended up re-editing fstab by hand.  Other than that (and that did kinda suck) it's been smooth sailing for me.

---

### Post by lazyrussian on 2007-10-18
The RC wasn't stable for me.

Had to reinstall XGL drivers + X itself
Had to rebuild ALSA drivers (sound support always seems to be an issue - for every update)

The only problem I still have is with GDM, I'm using gdmlogin instead of gdmgreeter. I posted a bugreport on launchpad and I was told that the fix has already been released - but there hasn't been update for my gdm package yet.

Discussion about the GDM Issue: [http://ubuntuforums.org/showthread.php?t=190310&page=4](http://ubuntuforums.org/showthread.php?t=190310&page=4)
Launchpad Bug Report: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/153426](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/153426)

---

### Post by pixelstuff on 2007-10-18
I had an alright gutsy after the big upgrade two days ago but yesterday some things for kde programs got upgraded and now my compiz is a mess and I cannot get into the Advanced Desktop Effects window. I was hoping for some big final upgrade today to clean and polish and put everthing into order :(:(:(

---

### Post by d_iane1954 on 2007-10-18
> **scapalexis888 said:**
> well, creating an operating system is not an easy task, and the Ubuntu development team is not getting paid a lot for their services. Look at Vista...I am pretty sure their release right now is still just a beta (but they need money to pay their programmers so force everyone to use it). Just wait a while. No need to rush.

quite a statement as i see that  many problems still existed in 7.04 so lets not dwell on those lets all rush out and get a new version with a lot more problems than before then when these problems cant be addressed lets move again to another version with more problems seems to me to be a never ending circle.security is another thing what exactly is security well i guess what it means is how many hours you spend reloading your operating system or looking for a fix for a program that comes within the op system that only partially works or doesnt work at all.examples:evolutionmail,alsa sound mixers,video cards(new)7-zip for files where ya have to do about 8-10 steps to open a file on your desk top,compiz fusion a new and improved combo of beryl and compiz and the list goes on.i guess if you have nothing but time on your hands and dont value the time and effort you put in to making apps work it is a great free system but of coarse if you could have a op system that requires you to reload it once in a blue moon because you were on a site that has a virus or trojan well lets bash that system cause it isnt free lololololl just an opnion from a relatively new user,i sure do know i will be bashed for this but what to hell its all in good taste being i see so much critisism in here of windows.also i know......................................linux isnt for everyone lololololol

---

### Post by Emperor3434 on 2007-10-18
> **d_iane1954 said:**
> quite a statement as i see that  many problems still existed in 7.04 so lets not dwell on those lets all rush out and get a new version with a lot more problems than before then when these problems cant be addressed lets move again to another version with more problems seems to me to be a never ending circle.security is another thing what exactly is security well i guess what it means is how many hours you spend reloading your operating system or looking for a fix for a program that comes within the op system that only partially works or doesnt work at all.examples:evolutionmail,alsa sound mixers,video cards(new)7-zip for files where ya have to do about 8-10 steps to open a file on your desk top,compiz fusion a new and improved combo of beryl and compiz and the list goes on.i guess if you have nothing but time on your hands and dont value the time and effort you put in to making apps work it is a great free system but of coarse if you could have a op system that requires you to reload it once in a blue moon because you were on a site that has a virus or trojan well lets bash that system cause it isnt free lololololl just an opnion from a relatively new user,i sure do know i will be bashed for this but what to hell its all in good taste being i see so much critisism in here of windows.also i know......................................linux isnt for everyone lololololol


Wow...:lolflag:

---

### Post by ubrox on 2007-10-18
I had a stable Gutsy with RC/Final, upgrade from 7.04. It had trouble recognizing nVidia GeForce Go 6100. I had to choose driver manually and then later enable restricted drivers and everything was ok.

However, I liked that my Broadcom wireless is now available on restricted drivers. I had to jump through some hoops top make it work in 7.04.

I like the display config and safe X. However, I am not yet successful in having a good dual monitor configuration. But I confess I tried it only once till now. Soon ...

---

### Post by robeast on 2007-10-18
I've been using Gutsy since the beginning of October and have had significantly less problems than in Feisty, and way less than Dapper. Maybe I just have a solid computer (crappy hardware is often overlooked as the cause of ubuntu problems), but as far as I can tell there has been steady improvement with each new release. Video is flawless with compiz-fusion, and the only problem with sound was the bizarre inverted switch with my Audigy. Stupid bug but easy enough to fix. I even have my Presonus Firebox recording interface operational! ROCK!

Here's the specs for those interested:
AMD Athlon 64 3000+ (32 bit gutsy)
Abit KV8 MAX3 (quality mobo makes all the difference in the long run)
Radeon 9600XT (Abit)
Audigy 1
1.5 gigs ram

---

### Post by thecheatah on 2007-10-18
Why wont anyone answer the question? How do I upgrade from RC to Final? The process says I am already upgraded, but the button in adept wont go away :-(.

Can anyone answer the question for which the post was created?

---

### Post by Mario87 on 2007-10-18
hum..finally, RC=FINAL, inst it?:)

---

### Post by Mario87 on 2007-10-18
hum..finally, RC=FINAL, isnt it?:)

---

### Post by subliminal727 on 2007-10-18
no update here.   maybe they just said it was an RC when it was actually a final version.  that way it spreads out the bandwidth over a few days before the actual release.   or maybe aliens stole our update.  either way...its a conspiracy.

---

### Post by LT1Caprice57L on 2007-10-18
My RC got massive update sessions 3 days in a row.  Sit tight, they're always coming in.

---

### Post by d_iane1954 on 2007-10-18
> **thecheatah said:**
> Why wont anyone answer the question? How do I upgrade from RC to Final? The process says I am already upgraded, but the button in adept wont go away :-(.

Can anyone answer the question for which the post was created?

probably you are having a problem getting an answer is that this release came out in the last 18 hours and it seems few or very few arent having troubles of one type or another just getting a download of the newly released 7.10 without figuring out y it doesnt upgrade.what im figuring here is the servers are so overloaded with people trying to download this new version called gutsy gibbons(because most people dont have enought problems in real life so  they want this new version so they can come home from work and zero stress to fight with it at night)think you get the picture here!!!! and by the way welcome to the ubuntu community!!!!

---

