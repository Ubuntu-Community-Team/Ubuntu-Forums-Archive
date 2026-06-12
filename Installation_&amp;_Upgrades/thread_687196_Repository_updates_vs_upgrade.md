---
title: "Repository updates vs upgrade"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by Lutherian on 2008-02-04
Hi all.
I have a concern about the Ubuntu "herding" approach to releases.
I'm sticking with Ubuntu dapper 6.06 because it's IMHO the best release so far. The later releases have more eye candy but tend to crash my machine(s) - If I bought a new machine these later releases would probably work just fine.

Here's an example: I'd like to install XMMS2 on my system but it's not available in my repository because to quote " In general, once a version of Ubuntu is released, the packages in it are "frozen", and will never be updated except for security or critical bug fixes." XMMS2 is available for Gutsy though.

"So why not just upgrade?"
Well here's my question: I've saved all my .deb files from /var/cache/apt/archives/ to DVD and each time I do an install, I copy these back into the directory so that I do not have to download all my applications from the net again.... BUT it seems to me ( and I could be wrong) that one cannot use the .deb files from 6.06 release for 6.10, 7 etc

So now the Ubuntu landscape does not look so friendly anymore

If one wants new applications they **have** to upgrade and they **have to** re-download packages

[CENTER]Is this statement true?[/CENTER]

"Well, why is this a problem?", you might ask.

Not everyone have high speed internet and re-downloading packages is a royal pain in the butt if it has to be done every 6 month, when it takes 3 months to get the system just the way you like it.
Timeout errors require me to make a wget script BTW.

Also, it seems that debian repository sources cannot be used by Ubuntu. Why on earth would Ubuntu close off their system like that - this is linux, not Apple Mac.

All of this gives me an uneasy feeling - as if I'm a sheep being herded in a certain direction - and that makes me feel uncomfortable, in the same way when I went into an internet cafe in Europe and they told me I must show my ID Document/Passort details before I connect. (I walked out on principle :> ) The feeling of being herded is what made me jump ship from Windows in the first place.
Ubuntu is a wonderful OS, I love it to bits, I'm trying trying to see where it's going to to though.

The only way out I can see is to compile from source, but then what of dependencies and such?
Any advice?

---

### Post by PmDematagoda on 2008-02-04
> If one wants new applications they have to upgrade and they have to re-download packages

Is this statement true?
Not necessarily, you can use newer applications by using different repositories or by manually compiling the required applications, but these **may** cause some problems concerning dependencies which in turn could damage your system, so you are doing that at your own risk

> Here's an example: I'd like to install XMMS2 on my system but it's not available in my repository because to quote " In general, once a version of Ubuntu is released, the packages in it are "frozen", and will never be updated except for security or critical bug fixes." XMMS2 is available for Gutsy though.

The reason that is done is so that the stability of a system can be maintained, if you kept updating software to new versions without a fair deal of testing then you cannot know what breakages could occur since updated software can have different dependencies or different ways of doing things. And the problem is that you cannot properly test every bit of updated since there may be thousands of software version updates in one month and the Ubuntu developers have better things to do than testing new applications everyday.

> Not everyone have high speed internet and re-downloading packages is a royal pain in the butt if it has to be done every 6 month, when it takes 3 months to get the system just the way you like it.
Timeout errors require me to make a wget script BTW.
That is a very unfortunate thing, and that is true, many people who have slow internet connections do find it rather difficult, especially those who only have a limited volume. But Ubuntu and a few others try to compensate for this by offering services such as Ubuntu's Ship It system.

> Also, it seems that debian repository sources cannot be used by Ubuntu. Why on earth would Ubuntu close off their system like that - this is linux, not Apple Mac.
Once again the problem of dependencies and such come into play, but this does not mean that Debian packages will not work on Ubuntu at all.

> Any advice?

Unfortunately the best advice I can offer is to get a Linux distribution, make it work for you and stay with it as much as possible, Ubuntu 8.04(Hardy Heron) may fit your needs well since it gives support for desktops for up to 3 years, you can also consider Ubuntu 6.06 since it's support finishes next year, you could also have a look at other distributions like Debian which also support their releases for quite a long time.

---

### Post by Lutherian on 2008-02-04
Thank you PmDematagoda, for the detailed response. Yes I agree that in mycase sticking with the LTS versions would probably be the best option. In addition, use of CLI type programs are less subject to variations so I'll stick to those. I do not fully understand the technical aspects of dependencies, something I'll have to read up on in the future.

---

### Post by hyperair on 2008-02-04
From what I hear, you were annoyed with the desktop effects not running well on your computer and so you stick with Dapper. However, there are many other improvements which you can enjoy if you just keep the desktop effects off. Why don't you do that?

---

### Post by Lutherian on 2008-02-04
Well hyperair, to tell the truth, I went down that road, turning off effects, but the glitches were more serious than that. Synaptic, Firefox, Nautilus would shut down at random intervals with no apparent reason and the dual boot with windows caused a corruption of the MBR. It wasn't pretty ... especially the second time I re-installed both OSes. However, the fact remains that I would still have to re-install all my applications, download java, reconfig java to be the default java engine (or else certain aspects of Open Office will not work eg. the database), download all the codecs, tweak the Sis Driver on my laptop, on and on and on ....

---

### Post by hyperair on 2008-02-05
Huh, I run Ubuntu Hardy, with Minefield (Firefox nightly build). Both are unstable as hell but I still don't get them crashing at random intervals. As for dual-booting, there's a trick to do with that. You gotta install Windows first then Ubuntu, or Windows will happily screw around with your MBR. I'm not sure about the rest of your issues though.

---

### Post by Lutherian on 2008-02-13
Yup hyperair, you're 100% about installing Windows first and Ubuntu thereafter - I learnt that lesson the hard way lol. I think I've got a clue about what causes program crashes in Ubuntu (Nautilus, firefox etc) 

* Rhythmbox used to crash while adding a large number of file to the library - solution, one of the files (an .acc file) caused the crash - I removed it and it worked thereafter.

* Comix viewer - crashed when I opened a directory, it contain about 1000 odd gifs - solution, I zipped them into chapters (comix can read zip files too), problem fixed.

Ubuntu is very stable, but a large number of files in a given directory can cause a fall.

Other than that, my desktop may have some sort of fault, but I can't compare it with windows, because it crashes randomly anyway in all the year that I've used it.

---

### Post by hyperair on 2008-02-13
If you know that there is a bug, you should try submitting a bug report at launchpad.net.

---

