---
title: "Okay, It's A Bug.  Satisfied?"
date: 2010-08-05
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2010-08-05
Somebody ever do anything to make bug reporting straight forward, and I might give it another shot.  For now, forget it.

You knoq what a bug is known as if they don't intend to fix it?  A "design feature".  I think I first heard that phrase about a Microsoft product.  Vista sure had a lot of design features incorporated into it, didn't it?

Anyway, to get to the point, this evident design feature has to to with Ubuntu 10.04 LTS.  You have to have something special mind to run into it.  That is how I found it.

I'm engaged in doing multiple installs of Ubuntu on my laptop.  Some unwanted things happen if the installer makes decisions, so I go into manual mode with the included partitioner to try and get it done my way.

The installer's partitioner does not write al label, but I want one.  Since gparted appears under /System/Preferences, I decide to go into test mode and use that instead.  And that is were I found the.. whatever you want to call it.

Using gparted first, I can also include a partiton label, which I want.  But after some failed efforts at an install (I am doing soe tings differently from the suggested metho), my method uses gparted to reformat, then label the partition.  But almost invariably a reformat as ext3 ends with gparted telling me that the partition now has an unknown type file system on it.  Apparently it screwed up its own reformat effort.  By telling it to now do a second reformat, it will finally come up and show me ext3 as the file system on it.  And then I can apply the label.

Now this gparted does not appear to bet the same as the partitioner that the instaqller calls up.  But if this one messes up on a reformat. what about the one that the installer calls on?  It does not check the reformat or tell me anyrhing before beginning the install process.

So the gparted set up in 10.04 LTS has a formatting problem, and yet it is unclear if the installer's partitioner is running into the same problem or not.

Anyway, it's it.

---

### Post by lemming465 on 2010-08-07
In a scenario this complicated, you might have better luck using command-line tools to browbeat the disk into looking like you want, before starting the installer.  E.g. run *fdisk* and *mke2fs* with the exact options you want.

---

### Post by oldefoxx on 2010-08-08
I'm much closer in my goal at this point, but I will have to consider your suggestions as well.  So thank you for bringing these to my attention,

I worked out a complicated task in my head, but it did not work as expected.  I researched the matter further, which took me to a ferdona site, and their suggestion was exactl like my own.  So what was wrong? 

What was wrong was pretty much key to everything, but it is a reported problem, and nobody is bothering to fix it. In fact, it looks like a bad design choice somewhere up stream.

I worked out a way to use a several step process to deal with it, and that works.  So I am back on track at last.

Not SOLVED, but there is a manual workaround if you know what you are doing.  Why not just post the problem and the workaround?  Because how can I then be sure you really know what you are doing?  Nobody seems to be able to read my posts on any topic, so that is out.

---

