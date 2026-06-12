---
title: "Karmic 9.10 planned features"
date: 2009-05-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tgpraveen on 2009-05-28
first of all to the mods i know  a similar thread exists at [http://ubuntuforums.org/showthread.php?t=459960](http://ubuntuforums.org/showthread.php?t=459960) but this thread is different.while that thread was meant for users to dream of new features to be put in karmic, this thread intends to list those features which will MOST LIKELY be in karmic ie we have some amount of credible proof.

So people who list the features please provide a link to the related announcement preferably by some dev or some other credible reason why you think the feature will be in.

So let me begin by first listing **Mark's announcement **of karmic koala
main features listed there

Desktop

Plymouth, for graphical boot
 new login experience
designer's fingerprints
faster boot
Some more things for server edition

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000536.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000536.html)

**Features which just missed jaunty**

PulseAudio 0.9.15 which brings in many improvements to surround sound and bluetooth audio ie A2DP
Also means new sound controls ie new volume-manager seen in fedora 11
GDM 2.4 (Available through PPA)

- GNOME Power Manager and Device Kit Power (Available through PPA) 
This is also in fedora 11 and looks really cool. [http://blog.fubar.dk/?p=103](http://blog.fubar.dk/?p=103)

Encrypted home directory for all users which is easy to use (confirmed in uds) [http://identi.ca/notice/4652899](http://identi.ca/notice/4652899)

[http://anotherubuntu.blogspot.com/2009/02/what-you-wont-get-in-jaunty.html](http://anotherubuntu.blogspot.com/2009/02/what-you-wont-get-in-jaunty.html)



**Features from UDS**

Appcenter
[http://ubuntuforums.org/showthread.php?t=1170534](http://ubuntuforums.org/showthread.php?t=1170534)

Banshee might replace rhythmbox in karmic, if that doesnt happen then surely in karmic+1

Boot time of around 10 secs [http://ubuntuforums.org/showthread.php?t=1169702](http://ubuntuforums.org/showthread.php?t=1169702)

More improvements to notify-osd
crimsun: notify-osd #karmic: urgencies; timeout extensions; proximity fadeouts; noncomposite; "less-clickable" bubbles #uds
[http://identi.ca/notice/4653086](http://identi.ca/notice/4653086)

Android and ubuntu integration

New contact store with integration with ubuntu-one [http://is.gd/HtE6](http://is.gd/HtE6)

jorge: VT switching and resume are FAST with KMS, nearly instant. Lots of people excited about it at !uds [http://identi.ca/notice/4630220](http://identi.ca/notice/4630220)

**possible features** which are not confirmed in uds

moblin version of ubuntu
LXDE version of ubuntu

**Software upgrades**
while all softwares will be upgraded some deserve special mention like

Openoffice.org 3.1
firefox 3.5 with privacy mode,better performance
gnome 2.28 which brings with it many features like empathy with video chat support in gtalk and geolocation support, epiphany with webkit,
better a2dp and webcam integration in desktop,etc [http://live.gnome.org/RoadMap](http://live.gnome.org/RoadMap)
linux kernel 2.31

**UPDATE 1:** [http://summit.ubuntu.com/media/lifestream.html](http://summit.ubuntu.com/media/lifestream.html)
          pgraner: #uds !uds #ubuntu Kernel Team has decided that Karmic with use 2.6.31
          
          highvoltage: so, ubuntu one will have install options in ubiquity. seems like marketing too me, pidgin/evolution/etc doesn't need this !uds  [http://identi.ca/notice/4686233](http://identi.ca/notice/4686233)

Also it seems that plymouth wont be in karmic atleast to make way for 10s boot, dont know about KMS??

crimsun: #karmic ext4 by default for new installs; dist-upgrade handling ext3 (whether to migrate to ext4- unlikely) is a #uds-foundations task. #uds

---

### Post by olskar on 2009-05-28
Nice initiative!

---

### Post by Swarms on 2009-05-28
Great list, really gonna be a solid release if all this happens.
Especially psyched about Banshee maybe replacing Rhythmbox.

---

### Post by 23meg on 2009-05-28
Note that UDS is still going on, the specification deadline is still ahead, and nothing is set in stone for Karmic at the moment. As long as there's no blueprint about a feature **targeting Karmic, with a "Design" status of "Approved" and a "Delivery" status of "Started"**, and/or a developer/contributor has not publicly announced plans/intentions for working on it for Karmic **in first person** on a mailing list (no third party reportage on external forums, news websites is wholly reliable; actually most of it is full of misinformation), please **suspect all talk of that feature to be hot air**, and do not put it on your list of "promised features" (a wholly flawed concept in our development model anyway) that you are excited about. That will save you and others lots of disappointment and let us avoid lots of unnecessary social friction.

---

### Post by 23meg on 2009-05-28
I've made a small edit to the thread title as per the above :)

---

### Post by tgpraveen on 2009-05-28
@23meg: yes i agree that in oss development it is never complete until its complete and released. but still i have made an attempt to provide reliable liks from devs blog/microblogs etc.

and yes uds is still not complete so expect MORE to come.

---

### Post by Merk42 on 2009-05-28
Darn 23meg, I was hoping I could be the first to say if it has been said by someone, even Mark Shuttleworth himself, to not consider it being part of the release **unless** there is a blueprint.

I searched the blueprints and all I could find with **Approved** and **Started** was EncryptFS and something with KMS, but I'm not sure if that is what tgpraveen was talking about though.

Yes I know it's only two, and I also know it's early (UDS isn't over yet), just saying that as of this writing those are the only two I could find which are officially planned for Karmic.

---

### Post by zekopeko on 2009-05-28
@Merk42 and others

blueprints are gonna be popping up about one week after UDS. it was mentioned several time in different threads.

---

### Post by ghindo on 2009-05-28
> **tgpraveen said:**
> Banshee might replace rhythmbox in karmic, if that doesnt happen then surely in karmic+1[Banshee probably won't replace Rhythmbox]("http://www2.apebox.org/wordpress/linux/105/"), unless Banshee becomes [more accessible to the disabled]("http://bugzilla.gnome.org/show_bug.cgi?id=533030"), and is [able to watch the music library for changes]("http://bugzilla.gnome.org/show_bug.cgi?id=385965").

---

### Post by Swarms on 2009-05-28
I am sure Jorge is going to do everything possible to meet the deadline.

---

### Post by celticbhoy on 2009-05-28
Are you sure Plymouth has been decided upon ?

I have just read this in the latest Linux format magazine :-

LXF : Are you thinking of Plymouth, or something else enitirely?

MS : Well, Plymouth is one option. So, kernel mode settings is the foundational layer, then on top of that you need something that's a framework for what you might draw before X comes up. Plymouth exists, that's great. We've used USplash in Ubuntu and that's great too, we're kinda the first to do that.

So, either USplash on a kernel mode setting framebuffer, or just using Plymouth. And Plymouth is great technology, so I've no objections to embracing that, although I dont think any decision has been taken at that level.

Take what you will from that!

---

### Post by zanox on 2009-05-28
webcam working without workouts??

---

### Post by castrojo on 2009-05-28
> **Swarms said:**
> I am sure Jorge is going to do everything possible to meet the deadline.

Team effort here, it's not just me. The Banshee guys are doing a great job working with directhex etc. on what needs to get done. They are also busy guys so if you know an a11y person who wants to help then that would be great!

Also on the plymouth thing Scott James Remnant told me that they are probably not going to go with it and instead just make boot speed so fast (the announced goal is 10 seconds on a mini9 netbook) that it'll just be a splash for a few seconds and then your desktop.

Some other stuff
- gnome-shell in universe soon so people can bang on it
- android apps running on ubuntu netbook remix
- Firefox 3.5 will be the default browser
- Gwibber by default if it's ready (woo!)

I am going out to dinner now but will try to post later on things I've been observing.

---

### Post by ghindo on 2009-05-28
Thanks for the updates, Jorge!  The gnome-shell news is especially exciting.

---

### Post by Jay_Bee on 2009-05-28
Thanks for the news whiprush!
If I understood correctly from the Gobby documents, the GDM will be started at about 3 seconds into the boot process and booting will start immediately but it will also allow for another os to be selected to boot instead of Ubuntu, while Ubuntu is booting. 
That sentence alone is enough to cause me headache, lol.

---

### Post by mxboy15u on 2009-05-28
Encrypted home directory really needs to be default...especially for the netbook remix.

---

### Post by tgpraveen on 2009-05-29
> **mxboy15u said:**
> Encrypted home directory really needs to be default...especially for the netbook remix.

this is going to be there in karmic

and @everyone
there seems to be some conflictings news coming
Is plymouth dropped indefinetely?
IS KMS still there?
what about new facebrowser gdm?

---

### Post by castrojo on 2009-05-29
> **tgpraveen said:**
> this is going to be there in karmic
Is plymouth dropped indefinetely?
IS KMS still there?
what about new facebrowser gdm?

KMS will be there for sure.
Facebrowser is looking like a no but I need to doublecheck.
Likely no plymouth and just a real fast boot.

---

### Post by tgpraveen on 2009-05-29
oh darn not again!
why dont we never want ubuntu to become good looking.
can understand plymouth being dropped for boot time, but would have liked what mark said that although 10s is good but we would settle for 12 if it is pretty.

but cant understand why the new facebrowser is not there. that would have been a nice addition.

well atleast KMS is there.

@whiprush the gobby document on boot says the target is 15 secs. so what is it actually 10 or 15?

---

### Post by Jay_Bee on 2009-05-29
Looks like the goal is 10 seconds on the testing hardware (dell mini 9 I believe) and 15 seconds should be average on the wide spectrum of hardware.

Just like Jaunty's boot time ranged from 20 to 30 seconds depending on the users hardware.

Please correct me if I misunderstood.

---

### Post by castrojo on 2009-05-29
> **tgpraveen said:**
> oh darn not again!
but cant understand why the new facebrowser is not there. that would have been a nice addition.

This is kind of complicated because we are still using the old gdm and it would make no sense to make it and then drop it for new gdm (which is a rewrite). I am unsure of what the GDM decision was for karmic.

> 
@whiprush the gobby document on boot says the target is 15 secs. so what is it actually 10 or 15?

The target is 10 seconds. Also, I neglected to mention (not on purpose!) that the 10 second goal is for 10.04. So likely more improvements for karmic and then hitting 10 for 10.04. After that it will become an engineering process to ensure that we stay at 10.

---

### Post by castrojo on 2009-05-29
Empathy by default! Upgraded users will keep pidgin and new installs will have it. We'll keep pidgin in main for a while though.

---

### Post by yelo3 on 2009-05-29
Mmm I hope empathy will be at least in feature parity

---

### Post by taavikko on 2009-05-29
> **whiprush said:**
> Empathy by default! Upgraded users will keep pidgin and new installs will have it. We'll keep pidgin in main for a while though.

hooray :)

any link to this?

---

### Post by castrojo on 2009-05-29
Install gobby and find the spec on gobby.ubuntu.com. I don't have time to dig up all the links for everything (I am concentrating on getting the info out quickly). However everything for every session is on gobby.ubuntu.com

---

### Post by Swarms on 2009-05-29
Great! :)

---

### Post by davideotape on 2009-05-29
> **whiprush said:**
> Install gobby and find the spec on gobby.ubuntu.com. I don't have time to dig up all the links for everything (I am concentrating on getting the info out quickly). However everything for every session is on gobby.ubuntu.com

In all fairness the correct document is very hard to find on gobby. I think after UDS the files needs a spring cleaning :D

---

### Post by taavikko on 2009-05-29
> **davideotape said:**
> In all fairness the correct document is very hard to find on gobby. I think after UDS the files needs a spring cleaning :D

Yeah, took a while to find the right one...
desktop-karmic-messaging-and-communication-selection

---

### Post by davideotape on 2009-05-29
> **whiprush said:**
> Empathy by default! Upgraded users will keep pidgin and new installs will have it. We'll keep pidgin in main for a while though.

Does empathy do IRC, cause I can't find it atm. :S

---

### Post by 23meg on 2009-05-29
> **davideotape said:**
> In all fairness the correct document is very hard to find on gobby. I think after UDS the files needs a spring cleaning :D

There will be reports on the wiki after UDS about each session based on the Gobby documents.

---

### Post by 23meg on 2009-05-29
> **taavikko said:**
> hooray :)

any link to this?

The Gobby document name is "desktop-karmic-messaging-and-communication-selection".

---

### Post by taavikko on 2009-05-29
> **23meg said:**
> The Gobby document name is "desktop-karmic-messaging-and-communication-selection".

Thanks for the confirmation and info to others,
I personally found it and posted it on post #28 to davideotape

Those entries could be in general more descriptive, some of them are little bit confusing, atleast to me :)

But "gobby" is a nifty little app.

---

### Post by davideotape on 2009-05-29
It's very handy gobby. Would like folders though, so all the jaunty uds docs and the karmic ones could be separated. Is this feature non-existant or just non-used?

---

### Post by castrojo on 2009-05-29
Gobby is not without it's limitations. We try to name the sessions to make sense but UDS is very dynamic so it ends up being a mess by the end. These notes will be cleaned up and attached to the specs on launchpad, etc. [https://blueprints.launchpad.net/sprints/uds-karmic](https://blueprints.launchpad.net/sprints/uds-karmic)

---

### Post by davideotape on 2009-05-29
I know gobby has limitations, but I think that a naming scheme for all the documents being created needs to be agreed on. Some of the documents start with karmic, yet others to do with this uds do not.

---

### Post by 23meg on 2009-05-29
> **davideotape said:**
> I know gobby has limitations, but I think that a naming scheme for all the documents being created needs to be agreed on. Some of the documents start with karmic, yet others to do with this uds do not.

That has been a gripe of mine as an attendee. Gobby 0.4.92 in Karmic has a folders feature, but it's not protocol-compatible with the old Gobby, and has not exactly stabilized. It's likely that it will be used in the next UDS to organize documents by folder, where each folder contains documents of a single track.

---

### Post by davideotape on 2009-05-29
Good good, sounds good.

---

