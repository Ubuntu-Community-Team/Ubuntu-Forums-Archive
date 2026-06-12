---
title: "Why is autopano-sift being used?"
date: 2010-04-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by regomodo on 2010-04-17
I've just discovered something bizarre in the repos. Why is autopano-sift being used? It brings in a heap of deps (mono) and is very old

> The latest version has been released on the 31th of October 2005[Link]("http://user.cs.tu-berlin.de/~nowozin/autopano-sift/#download")

There is autopano-sift-c which works fine with Hugin and is much more up to date. Is this an oversight or is it another one of those stupid licensing+Ubuntu issues? 

I don't want mono on my box.

---

### Post by regomodo on 2010-04-17
So, nobody cares about mono in Ubuntu/Linux? <snip> shame.

---

### Post by emarkay on 2010-04-17
[http://ubuntuforums.org/showthread.php?t=1446596&highlight=mono](http://ubuntuforums.org/showthread.php?t=1446596&highlight=mono)

---

### Post by splicerr on 2010-04-17
Autopano-sift-C doesn't seem to be in the repositories. there's a bug report about that, but no action so far.

[https://bugs.launchpad.net/ubuntu/+source/hugin/+bug/323836](https://bugs.launchpad.net/ubuntu/+source/hugin/+bug/323836)

And yes I care. But it's probably too late now. Most users will have that mono crap installed by default anyway because Ubuntu is still hanging on to that buggy F-Spot photo manager. I think Ubuntu should really try to make 10.10 as Mono free as possible, especially as there are now better alternatives around which don't require Mono.

---

### Post by dagrump on 2010-04-17
I believe there is a sticky somewhere, don't ask me where, I have CRS!! (can't remember stuff), now where was that?
Any way just un-install it and move on. They don't have an issue with it.
I don't have any either, I just remove it for spite!!

BUT, I'm old, grumpy, & sorta set in my ways.

I dual boot to play games, so I'm infected already.
Nothing to see here, move on.

---

### Post by zekopeko on 2010-04-17
> **regomodo said:**
> So, nobody cares about mono in Ubuntu/Linux? ****ing shame.

A huge majority of us aren't paranoid or don't care in what language an app is coded. Second of all Ubuntu and Debian have no problem with Mono. If you would like to use a distribution more aligned with your "purist" views perhaps Fedora would be a better option.

> **splicerr said:**
> Autopano-sift-C doesn't seem to be in the repositories. there's a bug report about that, but no action so far.

[https://bugs.launchpad.net/ubuntu/+source/hugin/+bug/323836](https://bugs.launchpad.net/ubuntu/+source/hugin/+bug/323836)

And yes I care. But it's probably too late now. Most users will have that mono crap installed by default anyway because Ubuntu is still hanging on to that buggy F-Spot photo manager. I think Ubuntu should really try to make 10.10 as Mono free as possible, especially as there are now better alternatives around which don't require Mono.

And what are those better alternatives? Shotwell and Solang? How feature complete are they? Have you actually used them? Do they import user data from F-spot?

Btw I wouldn't be surprised if Banshee replaces Rhythmbox in 10.10. That would be awesome.

Oh and another thing. Please don't call other peoples efforts crap when you in all probability haven't contributed anything valuable to FOSS. And no your "ZOMG!! Mono is a tech with M$ roots" rhetoric doesn't count as a value.

EDIT: You know what is really, really funny? Using the [link ]("http://wiki.panotools.org/Autopano-sift-C")from the bug report we get this: 

> autopano-sift-C is available from the hugin project and can only be used within hugin as an optional installation due to patent issues: the use of the Scale-invariant feature transform algorithm is restricted by US Patent 6,711,293, awarded March 23, 2004 to the University of British Columbia. 

I guess autopano-sift (both C and C# version) should be removed since it has a valid patent and no Community Promise from the University of British Columbia.

---

### Post by splicerr on 2010-04-17
> **zekopeko said:**
> 
And what are those better alternatives? Shotwell and Solang? How feature complete are they? Have you actually used them? Do they import user data from F-spot?


I'm using Shotwell from SVN, and I'm loving it, they are adding features by the week, you should give it a try :P.  I would be surprised if Ubuntu wouldn't follow Fedora and replace F-Spot with Shotwell for 10.10. Btw. There was nothing purist about the decision to remove F-Spot from default install for Fedora 13.

---

### Post by zekopeko on 2010-04-17
> **splicerr said:**
> I'm using Shotwell from SVN, and I'm loving it, they are adding features by the week, you should give it a try :P.  I would be surprised if Ubuntu wouldn't follow Fedora and replace F-Spot with Shotwell for 10.10. Btw. There was nothing purist about the decision to remove F-Spot from default install for Fedora 13.

Actually there is. Fedora (Red Hat that is) doesn't like Mono. It competes with Java and they are heavily invested in Java. And Fedora is a purist FOSS distro.

EDIT:

Don't get me wrong I love the fact that there are alternatives in the photo organizer space (in Gnome). But distros don't function on a purely technical basis. There is a lot of politics involved.

Btw I'll give SVN Shotwell a try. Last time I tried it I liked what I saw.

---

### Post by zekopeko on 2010-04-17
> **regomodo said:**
> **** it, I've just come from Funtoo and I wasn't prepared for this pansy-assed bullshit excuses. 

I'll make my own damn .deb with no autopano-sift. WTF is wrong with you guys (i.e. zekopeko)? I thought it was a Canonical thing but it seems to have filtered down to the community; you just talk.

Whats "Canonical's thing"? Not being paranoid? Presuming innocence before guilty? Being rational? Caring for user experience? Not trying to have a program with known patents packaged in the repos? Crazy me.

---

### Post by regomodo on 2010-04-17
> **zekopeko said:**
> Whats "Canonical's thing"? Not being paranoid? Presuming innocence before guilty? Being rational? Caring for user experience? Not trying to have a program with known patents packaged in the repos? Crazy me.

Go on.... I've heard all this before over the years and yet to see any real substance apart from the occasional stable repo periods.

"Presuming innocence before guilty?" Good one. 3 words: [Miguel de Icaza]("http://www.groklaw.net/article.php?story=20090927151401988")

"Being rational?" Stop it!

"Caring for user experience?" Oh dear God! Enough!

"Not trying to have a program with known patents packaged in the repos?" Canonical is a US company?

---

### Post by cariboo on 2010-04-17
@regomodo

You're a little late to the table, check out [this]("http://ubuntuforums.org/showthread.php?t=1202591&highlight=monolith") thread.

---

### Post by zekopeko on 2010-04-18
> **regomodo said:**
> Go on.... I've heard all this before over the years and yet to see any real substance apart from the occasional stable repo periods.
LOL
> "Presuming innocence before guilty?" Good one. 3 words: [Miguel de Icaza]("http://www.groklaw.net/article.php?story=20090927151401988")
I hope you apply your standards to all FOSS then. Like autopano-sift, a patent encumbered product.
> "Being rational?" Stop it! Stop being rational?
> "Caring for user experience?" Oh dear God! Enough!
You're right. Ubuntu isn't the most popular distro because they care about user experience. They used voodoo magic :lolflag:
> "Not trying to have a program with known patents packaged in the repos?" Canonical is a US company?
Canonical and Ubuntu don't have customers in the US? Really?
And just to preempt you before you continue ranting and FUDing: [http://ubuntuforums.org/showthread.php?t=1200946](http://ubuntuforums.org/showthread.php?t=1200946)
I suggest you install Fedora. They have double standards for projects there. I'm sure you'll fit in perfectly.

---

### Post by regomodo on 2010-04-18
Here's the deb for [autopano-sift-C]("http://www.2shared.com/file/12650679/2666ad7e/autopano-sift-C-251_amd64.html").

Now there's no need for mono with hugin. Hugin has a autopano-sift-c as dependency in it already.

> 
Quote:
"Being rational?" Stop it!
Stop being rational?


No, I don't care what you have to say as I don't see any value in them. You want to pull this thread into a mono flamewar. I just wanted mono off my box. End of.

---

### Post by ranch hand on 2010-04-18
> **regomodo said:**
> Here's the deb for [autopano-sift-C]("http://www.2shared.com/file/12650679/2666ad7e/autopano-sift-C-251_amd64.html").

Now there's no need for mono with hugin. Hugin has a autopano-sift-c as dependency in it already.



No, I don't care what you have to say as I don't see any value in them. You want to pull this thread into a mono flamewar. I just wanted mono off my box. End of.
If what you want is to rant in an offensive, whiny, shrill manner you will find the Community forums more to your liking.

This is a testing and development forum.  We are here to deal with the real world problems of a pre release OS.

Religious philosophy preached to us by fundamentalists (you should look up the word fundament) is really a waste of time and space.

What I am trying to gently say  is troll somewhere else.

---

### Post by zekopeko on 2010-04-18
> **ranch hand said:**
> If what you want is to rant in an offensive, whiny, shrill manner you will find the Community forums more to your liking.

This is a testing and development forum.  We are here to deal with the real world problems of a pre release OS.

Religious philosophy preached to us by fundamentalists (you should look up the word fundament) is really a waste of time and space.

What I am trying to gently say  is troll somewhere else.

^^^ This.

---

### Post by regomodo on 2010-04-18
> **ranch hand said:**
> If what you want is to rant in an offensive, whiny, shrill manner you will find the Community forums more to your liking.

This is a testing and development forum.  We are here to deal with the real world problems of a pre release OS.

Religious philosophy preached to us by fundamentalists (you should look up the word fundament) is really a waste of time and space.

What I am trying to gently say  is troll somewhere else.

Yeah, sorry about that; I'm more accustomed to the CC.  

Yes, I was trolling but only in response to zekopeko's initial, what I hope were, baits. Saying that, I stand by my distrust of Miguel de Icaza and therefore want to keep my distance from him.

Still, I haven't got a reason as to why autopano-sift is preferred over the equally infringing autopano-sift-c.

---

### Post by ranch hand on 2010-04-18
The best place to ask that is probably on one of the IRQs or mailing lists.  There are several for the folks in development and people interested in development.

I will warn you that the best way to be totally ignored is to be combative in your wording in those venues.  The devs are busy folks and have absolutely no time for people they even think are hostile or abusive.

I am not sure where the proper one for your concern is.  I only follow the Lubuntu team mailing list.

I really should subscribe to the ISO-testing mailing list but I get too much to follow now.

---

