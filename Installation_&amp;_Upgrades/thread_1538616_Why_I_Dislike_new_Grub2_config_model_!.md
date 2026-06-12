---
title: "Why I Dislike new Grub2 config model !"
date: 2010-07-25
forum: Installation &amp; Upgrades
---

### Post by yaubu on 2010-07-25
I just recently installed 10.04 from 9.04.  I like it all in all.

*DISCLAIMER*  what follows is an utter 'poor me _whine fest_'  continue only if you aren't on the edge from constant whining... (I don't do it very often)


I have one issue I'd like to voice about grub2 (grub). I know grub is _not_ ubuntu or Linux.

It seems when very competent developers work on a complicated project for some time, they lose scope of what's intuitive and easy for the user.

I am fairly linux savvy and have used and configured multiple boots regularly.

In terms of grub, it's been fun keeping up with ' grub.conf , menu.lst, or grub.cfg'

I am older and forget things, and rely on linux's legacy of somewhat uniform architecture and configuration structure, and based on 'linux common sense'.

The new grub config, I _do not_ like!
1. if you want to have a dynamic file, why use the one that's in the user's face (grub.cfg), and close to the one we've edited for over a decade?
2. Why bury the user configurable one, outside the boot direcory, into an obscure file called  '40_config' (what the hell is that?)

What bugs me, in a month when I got to tweak by grub.cfg it won't stick, then I'll remember this and I'll go look for the file after not finding it, I'll have to search online again, and relive this experience...

A big universal concept of Linux/associated OS systems (I know grub Is Not linux, but has been closely coupled), is keeping the configurations and output and logs human readable, and let the backend infrastructure handle any complexities.


Am I just whining about 'change'?
Am I on the wrong forum?
Does anybody else care?

---

### Post by radddi on 2010-07-25
I fully agree with you. As far as my own user experience goes, there is no apparent benefit of Grub2 over the original. However, Grub2 is now ridiculously hard and illogical to configure. For example, I tried tinkering with the new settings and after some random crash did a "Fix grub" (or how was this option called?) from Recovery mode. After generating a usable menu.lst, the computer utterly refused to add the new installed Kernels!! :(

So what IS the use of the new Grub2? (no offence to any developers intended.)
:popcorn:

---

### Post by yaubu on 2010-07-25
> **radddi said:**
> I fully agree with you. As far as my own user experience goes, there is no apparent benefit of Grub2 over the original. However, Grub2 is now ridiculously hard and illogical to configure. For example, I tried tinkering with the new settings and after some random crash did a "Fix grub" (or how was this option called?) from Recovery mode. After generating a usable menu.lst, the computer utterly refused to add the new installed Kernels!! :(

So what IS the use of the new Grub2? (no offence to any developers intended.)
:popcorn:

I'm not totally on top of all the new Grub2.

But I know there is a lot of back-end work done.  I'm sure 'under the covers' there was a lot of enhancements and fixes.  Which is great!

But, I think after being in it so deep, they lose sight of the exposed user interface.  That's the point where it has to be sensible, logical, and intuitive, and ease (as possible), for the user.  It seems like they add an interface that makes sense to them, but not to anybody else that has been heavy coding in that environment, I know I've done it...

but, I think it's a _major_ issue that needs to be addressed before it goes on too long...

---

### Post by MAFoElffen on 2010-07-25
Me? I had to convert, stay flexible, adapt, adjust... and stay current.  GNU GRUB and GNU GRUB2 are not Ubuntu, but rather an Open Source that Ubuntu and others are using...

I'm stuck using "both" on my main computer as it's a multi-boot and I have OpenSolaris on it.  OpenSolaris has big "problems"  booting natively from GRUB2, so I have to chainload it's GRUB from GRUB2.

Not saying that there aren't some things to still work out... Like everything else, including how I see myself, it's a work in progress. LOL

Yes things change.  Yes, some things are 'different.' There is new technology.  I think that things needed to adapt to that new technology to take advantage of it.  Where as some of the older systems did have some limitations where it was running into a dead end.  Other improvements seem to be in new hardware support,  error handling and 'recovery.'

Seems like everytime I 'upgrade' one of the 6 OS'es on my machine, I have to learn something new and have to make some changes to get them to 'live' with each other... especially since I do cross-platform apps.  Everytime I upgrade (sometimes even just an update), there is "some" kind of "problem" (change) that I have to work out.  My fiance cringes when I mention that one of my OS'es had an Upgrade!

GRUB and GRUB2 are one of my fairly consistant pieces to my puzzle.  It's okay, but it's something "I" have to keep up with to stay current.

---

### Post by ronnielsen1 on 2010-07-25
> How to revert to grub legacy

A lot of people, myself included, are having difficulty in understanding the 'logic' of grub2, personally I think that for the present grub legacy is a better bet. I am sure that will eventually change but it hasn't yet.

[http://forums.linuxmint.com/viewtopic.php?f=46&t=44056](http://forums.linuxmint.com/viewtopic.php?f=46&t=44056)

I had to go back to Grub! I could edit grub in seconds. Grub 2 seemed overly complex. I think I preferred the KISS method. But it is linux and we're not stuck with it.

---

