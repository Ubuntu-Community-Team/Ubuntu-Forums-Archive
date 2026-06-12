---
title: "How can I directly upgrade from Intrepid to Lucid?"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Maju on 2010-03-23
I'd like to avoid a three step upgrade, which is the only option I get from the interface (i.e. upgrade to 9.04 Jaunty, which in turn will offer upgrade to Karmic and then to Lucid). 

However if one thing is Linux known for is versatility and that you can do almost anything with the terminal... if you know how. 

But I don't know how. 

So how do I do that? ;)

Thanks in advance.

---

### Post by stlsaint on 2010-03-23
Unless something has changed in the last years of ubuntu in this area than from what i know you cannot skip a distro to get to the next outside a fresh install. There are certain ways to achieve a distro you desire if you so choose to without a direct upgrade but they are highly unadviseable and will result in a bonked system. So to answer your question you must either fresh intall or go through the direct upgrade process of each distro.

---

### Post by Maju on 2010-03-28
Alright, thanks. I'm gradually upgrading it already. :/

---

### Post by grandtoubab on 2010-03-28
> **stlsaint said:**
> Unless something has changed in the last years of ubuntu in this area than from what i know you cannot skip a distro to get to the next outside a fresh install. There are certain ways to achieve a distro you desire if you so choose to without a direct upgrade but they are highly unadviseable and will result in a bonked system. So to answer your question you must either fresh intall or go through the direct upgrade process of each distro.

Not right, see the official procedure
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

You can jump from LTS to LTS. 
In Lucid case you should have wait for the final release of Lucid that is 29th april

---

### Post by kansasnoob on 2010-03-28
> **grandtoubab said:**
> Not right, see the official procedure
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

You can jump from LTS to LTS. 
In Lucid case you should have wait for the final release of Lucid that is 29th april

LTS to LTS in this case is Hardy to Lucid, the OP asked about Intrepid to Lucid :)

---

### Post by snowpine on 2010-03-28
Quickest and easiest method:

1. Back up your documents
2. Install Lucid
3. Restore documents from backup

---

### Post by kansasnoob on 2010-03-28
> **Maju said:**
> Alright, thanks. I'm gradually upgrading it already. :/

You're kidding me right?

Intrepid > Jaunty > Karmic > Lucid?

Unless you update each one in between the chances of failure increase like crazy! So you're talking about 3 to 4 hours for each upgrade?

Please tell me this is a joke.

---

### Post by kansasnoob on 2010-03-28
> **snowpine said:**
> quickest and easiest method:

1. Back up your documents
2. Install lucid
3. Restore documents from backup

+1!

---

### Post by Maju on 2010-03-30
> **grandtoubab said:**
> Not right, see the official procedure
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

You can jump from LTS to LTS.

I know but Hardy was becoming too obsolete for some stuff (games in particular), or I had that perception at least, so one happy day I decided to upgrade to Intrepid. But, sincerely, I would have upgraded to the latest stable version directly if that would have been possible.

> In Lucid case you should have wait for the final release of Lucid that is 29th april

Ok, I had the vague impression that it was already released but seems not. Thanks, I'll wait.  

> **snowpine said:**
> Quickest and easiest method:

1. Back up your documents
2. Install Lucid
3. Restore documents from backup

Thought about that but some of my most important "documents" are my browser's bookmarks and, well, I have no idea where they might be stored (Ubuntu's directory organization is kinda crazy and I get totally lost because each program has stuff stored in so many different folders). 

> **kansasnoob said:**
> You're kidding me right?

Intrepid > Jaunty > Karmic > Lucid?

Unless you update each one in between the chances of failure increase like crazy! So you're talking about 3 to 4 hours for each upgrade?

Please tell me this is a joke.

I don't understand what you mean. Of course I'm updating them (it's automatic, thank goodness). I've already reached the Jaunty stage (without other trouble than having the computer busy for a whole morning) and I plan to upgrade to Karmic soon (TM).

---

### Post by coffeecat on 2010-03-30
> **Maju said:**
> Thought about that but some of my most important "documents" are my browser's bookmarks and, well, I have no idea where they might be stored

If that's firefox, you do it from within firefox. Bookmarks > Organise bookmarks > Import and Backup > Export html. To import into a fresh firefox, you choose Import html. I've moved bookmarks from Ubuntu > MacOS and Windows firefox (and every whichway) this way.

You don't want to be messing with the bookmarks files themselves.

---

### Post by ravikalsi27 on 2010-03-30
no not now just wait for 25 days.........LUCID lynx well be officially available.......now its just alpha and beta versions.......

---

### Post by dino99 on 2010-03-30
who wants a stable distro never dist-upgrade: always a mess because of hard changes, old settings and configs left behind and else.

make room for a clean fresh install and a dedicated partition for /home.
install with unetbootin or what you want, and you have not later to fight against bad transitions.

---

### Post by cubeist on 2010-03-30
> **Maju said:**
> 
I don't understand what you mean. Of course I'm updating them (it's automatic, thank goodness). I've already reached the Jaunty stage (without other trouble than having the computer busy for a whole morning) and I plan to upgrade to Karmic soon (TM).

Doing four upgrades in a row instead of one fresh install is asking for a world of headaches.  Upgrades are usually about 95% (in my opinion) effective.  This means there are usually a few things you have to do manually.. like configure wireless, or update restricted drivers, or update your software packages/themes, etc. which are not part of the overall upgrade.  These tasks are usually not a big deal, but when you do several upgrades at once, you will be left with a system that will probably need lots of manual intervention to get working perfectly.

I strongly advise a fresh install!

---

### Post by nanog on 2010-03-30
**Wow! The amount of disinformation in this thread is simply incredible.** 

I have never reinstalled ubuntu. Every computer I own or administer is installed once and upgraded. Several boxes have been upgraded sequentially all the way from breezy. As long as you don't install 3rd "junk" debs upgrades are typically flawless. 

If you don't believe me then read this:
[http://ubuntuforums.org/showpost.php?p=8863743&postcount=13](http://ubuntuforums.org/showpost.php?p=8863743&postcount=13)

Since Hardy introduced support for the Dapper-Hardy upgrade Ubuntu has been expressly designed to allow for non-sequential upgrades. Although these upgrades are not officially supported they *should* work. (I skipped jaunty on most of intel boxes due to the driver problem.)

To upgrade from intrepid you just need to change your sources to lucid and comment out or deselect any 3rd party repos or ppas.  Alternatively you can edit /etc/apt/source.list and any list files in /etc/apt/sources.list.d (can't remember if intrepid uses /etc/apt/sources.list.d).

Once you've changed your sources you simply run:

```
sudo apt-get dist-upgrade
```

---

### Post by cubeist on 2010-03-30
> **nanog said:**
>  

To upgrade from intrepid you just need to change your sources to lucid and comment out or deselect any 3rd party repos or ppas.  Alternatively you can edit /etc/apt/source.list and any list files in /etc/apt/sources.list.d (can't remember if intrepid uses /etc/apt/sources.list.d).

Once you've changed your sources you simply run:

```
sudo apt-get dist-upgrade
```

No! Do not do this. This advice will leave *most* systems a complete mess.

To clarify:
Yes, you can skip versions if you are going from one LTS version to another LTS version.

Yes, you can do multiple sequential upgrades in a row.  But, any custom files/libraries/themes/kernels/modules/configurations/programs built from source, etc. will require manual intervention and re-configuration.  However, if you are a user who uses basically a stock Ubuntu system without much customization, then go-ahead and do multiple upgrades.

---

### Post by new_tolinux on 2010-03-30
9.04 to 9.10 was a mess in upgrades. Not only in upgrades, 9.10 just wasn't ready when it first came out als "final".
After having to reinstall my machine with 9.04 I surely suggest you not to upgrade "as soon as you can" when it's april 29th. It may be out of beta-state then, but if it is like with 9.10...... you end up with a lot of non-working hardware, which worked perfectly before.

I didn't try to upgrade that 9.04 laptop again. I did however recently install another system with 9.10 dual-boot to Windows 7. It seems to be better yet, or it's just because the 9.04 machine is about 1.5 years old while this system is only 4 months old yet that the hardware-support for this PC is much better than the 9.10 support for the laptop-hardware.

---

### Post by nhasian on 2010-03-30
i know its about a week late, and your probably already done upgrading... but in the future you could simply backup your /home directory.  thats where all your configuration files are stored.  personally i prefer giving /home its own partition.  makes it easier for me to backup.  

Although I haven't tried it myself I understand that during a fresh install of ubuntu, if you make sure the FORMAT box is not ticked, then it will only wipe the system files and proceed with the installation, leaving your /home folder intact.

> **Maju said:**
> Alright, thanks. I'm gradually upgrading it already. :/

---

### Post by 23meg on 2010-03-30
> **nanog said:**
> 
Since Hardy introduced support for the Dapper-Hardy upgrade Ubuntu has been expressly designed to allow for non-sequential upgrades. Although these upgrades are not officially supported they *should* work.

I have to stress that such upgrades are entirely unsupportable, and are an especially bad idea for upgrading from an EOL release, and/or to an unstable development branch (Lucid). If you perform one, you're on your own: don't file bug reports, don't request support, don't complain about stuff not working; it's highly likely that you'll be wasting your and others' time trying to track down issues that shouldn't be there in a supported install, and possibly do more harm than good in testing.

---

### Post by nanog on 2010-03-31
> No! Do not do this. This advice will leave most systems a complete mess.
This is not correct. (I did this on every intel machine I administer without a single problem.) There is a big difference between unsupported and not possible. 

> But, any custom files/libraries/themes/kernels/modules/configurations/programs built from source, etc. will require manual intervention and re-configuration.
This is not correct. Dpkg will complain if there are dependency errors (regardless of how or to what you upgrade) and the gnu c compiler is designed to be backwards compatible. IMO, if you want to avoid multiple sequential upgrades (or a fresh install) its worth a try. 

> don't file bug reports, don't request support
While I completely agree that this is not an appropriate way to *test*, I like to think that my bug reports have helped make ubuntu better despite the fact that some of them originated from "unsupported" systems.

---

### Post by kansasnoob on 2010-03-31
> **nanog said:**
> This is not correct. (I did this on every intel machine I administer without a single problem.) There is a big difference between unsupported and not possible. 


This is not correct. Dpkg will complain if there are dependency errors (regardless of how or to what you upgrade) and the gnu c compiler is designed to be backwards compatible. IMO, if you want to avoid multiple sequential upgrades (or a fresh install) its worth a try. 


While I completely agree that this is not an appropriate way to *test*, I like to think that my bug reports have helped make ubuntu better despite the fact that some of them originated from "unsupported" systems.

Honestly, you've skipped from Intrepid to Lucid on numerous machines with no problem?

I'd love to see your logs on that.

---

### Post by cubeist on 2010-04-01
> **kansasnoob said:**
> Honestly, you've skipped from Intrepid to Lucid on numerous machines with no problem?

I'd love to see your logs on that.

yeah, me too! I sense a troll a'mist! :) Seriously though nanog, if you have had this much success I can guarantee two things... one, you are the exception to the rule, and two, it is unlikely your streak will continue.

---

### Post by QLee on 2010-04-01
[QUOTE=Maju]I'd like to avoid a three step upgrade, which is the only option I get from the interface (i.e. upgrade to 9.04 Jaunty, which in turn will offer upgrade to Karmic and then to Lucid). [/QUOTE]

Edit: Oops wrong quote, I meant not try the "skip" upgrade. This one would likely work after a long session but probably better  (faster) to backup home and do fresh install. (end edit)

I hope you understood from this thread that that would not be a good thing for you to try.

[QUOTE=Maju]However if one thing is Linux known for is versatility and that you can do almost anything with the terminal... if you know how. 

But I don't know how. [/QUOTE]

And that is the reason for my comment above. A reasonable intelligent, experienced GNU/Linux user can work around or through most if not all of the problems encountered with non-standard upgrade paths. (from myprevious observations and lurking, most of the people commenting here probably could be successful) That, however, does not mean you should try it, by the nature of the question, it seems likely that you don't yet have the skills for it.

[QUOTE=Maju]So how do I do that? ;)[/QUOTE]

In short, please take advice and don't try it

In my opinion it really would be irresponsible to try and help you do that in a help forum situation ...and it would take days and days. Lots of inexperienced users would try copying what was being done (but they wouldn't get it right) and get their systems all mucked up. If you are going to try it get an experienced user to be in person with you and the system.

---

### Post by nanog on 2010-04-01
> yeah, me too! I sense a troll a'mist

Anyone who has run Sid is not afraid of a non-sequential upgrade on debian-based system. If you understand how dpkg works you can do virtually anything to an ubuntu system. On one of my systems I run mixed karmic/testing repos. I also once downgraded a jaunty install back to hardy. Pinning is fun!

If you read my posts you'll note that I upgraded intrepid to karmic (jaunty shipped with a broken intel driver) but I am sure intrepid to lucid would work just fine on a stock system. In fact, I'll prove it.

---

### Post by balloons on 2010-04-01
**DISCLAIMER: If your a newbie, or don't understand what I write below, ignore it. Just click the buttons on update manager when it tells you :p**

This upgrade phobia is very weird to me. I've done all sorts of "bad" things. I've installed ubuntu using a debain netinstall disk, and then changing the sources.list. I've migrated between releases by using an old LTS cd, installing, then bumping the sources.list to what I wanted. Also, before (and after a couple times) jdongs prerelease tool, I grabbed new versions of software and mixed it in the old environment. For jaunty, I used karmic's xorg to get around the intel issues, for karmic I used lucid's openoffice and firefox, etc. You get the idea. None of these things will break your system. It's just packages and configs. And assuming the packages install and remove themselves cleanly, there's no reason you can't change everything about your system and put it all back. You just need to keep a linux base system installed and you can do whatever you please. This may just cause some of these guys to really give me looks, but back in the hoary hedgehog days, I migrated a simplymepis install to debian, and then to ubuntu. That can also work, but requires a bit more care in doing so.

---

### Post by snowpine on 2010-04-01
I agree with the above; the "Debian way" to upgrade is to change your sources.list to the new release and use apt-get. If release upgrades in Ubuntu are not reliable, and users are being told "you shouldn't upgrade; back up your home folder and do a fresh reinstall the new release," then it is a BUG.

---

