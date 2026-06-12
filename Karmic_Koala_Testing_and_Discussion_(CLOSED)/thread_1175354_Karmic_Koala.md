---
title: "Karmic Koala"
date: 2009-06-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2009-06-01
Hi,

If I install Karmic Koala side by side windows will it jeopardize the stability of my system.

Thanks,
SK

---

### Post by overdrank on 2009-06-01
Moved to Karmic Koala Testing and Discussion

---

### Post by froggyswamp on 2009-06-01
> **soham_1207 said:**
> Hi,
 If I install Karmic Koala side by side windows will it jeopardize the stability of my system.
 Thanks,
SK
You should not use any alpha software if you care about stability. You can't have both.
So I'd suggest not using Karmic, it can potentially burn your computer and eat your dog, as long as it's not a final release nobody will vouch for it in any way.

---

### Post by Didius Falco on 2009-06-01
I wondered where the heck my dog went...:shock:


Regards,

Didius

---

### Post by meborc on 2009-06-01
> **soham_1207 said:**
> Hi,

If I install Karmic Koala side by side windows will it jeopardize the stability of my system.

Thanks,
SK

just use jaunty 9.04 ... it is great

and koala will net be ready until october

---

### Post by tad1073 on 2009-06-01
I jumped in on testing alpha 1 and it has been very stable for me. Baciclly if boils down to personal choice.

With 9.04, I could not get wireless to work, so, I thought "Might aswell try 9.10." I did and wireless worked flawlessly.

---

### Post by nowin4me on 2009-06-01
> **froggyswamp said:**
> So I'd suggest not using Karmic, it can potentially burn your computer and eat your dog, as long as it's not a final release nobody will vouch for it in any way.

I thought it would eat your kitten not your dog?
Maybe I'm wrong. Either ways it's in the bug reports.
(P.S I think they have a sense of humor so I would worry about it eating your kittens(dogs).)


[SIZE="1"]No kittens or dogs where eaten or harmed in the making of this post[/SIZE]

---

### Post by phenest on 2009-06-01
> **soham_1207 said:**
> Hi,

If I install Karmic Koala side by side windows will it jeopardize the stability of my system.

Thanks,
SK

Let me be the first to read your entire post.

No, despite Karmic being alpha and potentially unstable, it will not affect Windows.

---

### Post by excogitation on 2009-06-01
> **phenest said:**
> Let me be the first to read your entire post.

No, despite Karmic being alpha and potentially unstable, it will not affect Windows.

+1 (unless you delete your windows during the Karmic installation - in which case it wouldn't be in any state anymore)

Edit: hijeyh 200 8)

---

### Post by robert.rankin.jr on 2009-06-01
That's not entirely true. Alpha releases have been known to destroy hardware... they can certainly destroy or alter a partition much more easily, especially during installation.

I wouldn't risk it if you need either system to be guaranteed to work at any given time.

Also, don't be mislead by the fact that Alpha 1 is stable. Based on the fact that the Jaunty Alphas were quite stable, lots of people are getting overconfident. Just be careful... nothing is certain, least of all when it comes to software.

---

### Post by psyke83 on 2009-06-01
> **robert.rankin.jr said:**
> That's not entirely true. Alpha releases have been known to destroy hardware... they can certainly destroy or alter a partition much more easily, especially during installation.

I wouldn't risk it if you need either system to be guaranteed to work at any given time.

Also, don't be mislead by the fact that Alpha 1 is stable. Based on the fact that the Jaunty Alphas were quite stable, lots of people are getting overconfident. Just be careful... nothing is certain, least of all when it comes to software.

Destroying hardware is unlikely (yes, there was the problem with a buggy ethernet driver that was bricking hardware), but what is more likely is a that partitioning bug may cause the Windows partition to become corrupt.

Also, alpha 1 is very early in the cycle. A first-time tester should probably wait until things stabilize somewhat.

---

### Post by phenest on 2009-06-01
> **psyke83 said:**
> ... what is more likely is a that partitioning bug may cause the Windows partition to become corrupt.

+1 This is true, but depends on your current situation. If you need to reduce the space taken by Windows to make room for Karmic, then there is the likelihood of a partitioning error. But if you already have space reserved, then it's unlikely.

---

### Post by Reiger on 2009-06-01
I doubt that. The partion editor is not exactly Alpha... 
Anyways a corrupt NTFS partition is much like a corrupt E2FS or E3FS partition in that a fs check will be able to find & fix most of those problems for you. Windows will (should, I've seen this happen with Vista) automatically initiate a fs check when it detects that its partitions have been altered by something other than itself.

---

### Post by phenest on 2009-06-01
> **Reiger said:**
> I doubt that. The partion editor is not exactly Alpha... 
Anyways a corrupt NTFS partition is much like a corrupt E2FS or E3FS partition in that a fs check will be able to find & fix most of those problems for you. Windows will (should, I've seen this happen with Vista) automatically initiate a fs check when it detects that its partitions have been altered by something other than itself.

I believe this happened to me once, and it was a final release too. XP didn't like being resized, but it simply did a filesystem check, restarted, and all was well.

So, to summarize to the OP then, I wouldn't worry about it.:D

---

### Post by meborc on 2009-06-01
the problem is not in alpha 1 ... the problem is when the user upgrades it to some daily state... which can break EVERYTHING :)

sure it is unlikely... but don't suggest to new users that alpha 1 is safe

---

### Post by donniezazen on 2009-06-01
Thanks you all,

We have got pretty opposite opinions.

I do not have technical knowledge but i have used Ubuntu for a long time. That makes me curious to see the development of Ubuntu, which is the learning part to me. 

All i was going to do is to make a 10 GB partition and install Karmic in it. Do you guys think that it can destroy the windows partition and may also affect my hardware?

After all its Ubuntu, i am willing to take some risk to enhance my knowledge. I don't mind windows (sorry...the windows partition) being destroyed but i don't want to hurt my pocket by destroying my hardware.

Thanks,
SK.

---

### Post by Slug71 on 2009-06-01
> **soham_1207 said:**
> Thanks you all,

We have got pretty opposite opinions.

I do not have technical knowledge but i have used Ubuntu for a long time. That makes me curious to see the development of Ubuntu, which is the learning part to me. 

All i was going to do is to make a 10 GB partition and install Karmic in it. Do you guys think that it can destroy the windows partition and may also affect my hardware?

After all its Ubuntu, i am willing to take some risk to enhance my knowledge. I don't mind windows (sorry...the windows partition) being destroyed but i don't want to hurt my pocket by destroying my hardware.

Thanks,
SK.

Destroying the Hardware itself is very unlikely. Wiping Windows by installing Karmic is also unlikely but more possible than the Hardware itself. I'd go ahead and install it. 

Just make sure you have a Launchpad account and file/add-to bugs when you come accross them. Contributing that way is a MUST if you choose to use development software.

---

### Post by aamukahvi on 2009-06-01
Virtualization is a very good option if you want to see how things progress without having to worry about things breaking.

---

### Post by donniezazen on 2009-06-01
Virtualization is a good idea but its slow and restricted. I will probably install it in a new partition.

Thanks all,
SK.

---

### Post by seeker5528 on 2009-06-01
> **nowin4me said:**
> I thought it would eat your kitten not your dog?

Well, most people don't notice when the flies and spiders go missing. And in spite of the fact they were warned, when their pet goes missing, out come the torches and pitchforks.

Later, Seeker

---

### Post by crjackson on 2009-06-01
> **nowin4me said:**
> [SIZE="1"]No kittens or dogs where eaten or harmed in the making of this post[/SIZE]

I don't believe you. Can you post your log files to prove it?

---

### Post by donniezazen on 2009-06-01
> **crjackson said:**
> I don't believe you. Can you post your log files to prove it?

> **seeker5528 said:**
> Well, most people don't notice when the flies and spiders go missing. And in spite of the fact they were warned, when their pet goes missing, out come the torches and pitchforks.

Later, Seeker

Can somebody please explain me what are these people talking about? Flies, spiders, dogs, kitten.....

---

### Post by Didius Falco on 2009-06-01
> **soham_1207 said:**
> Can somebody please explain me what are these people talking about? Flies, spiders, dogs, kitten.....

It's all just carried forward from the initial joke about eating your dog.

The main points are, as others have said:

1. Using Alpha software carries no guarantees. You might lose files, you might have to reformat and reinstall everything on your pc. You might even suffer some form of hardware damage - not nearly as likely, but still possible

By using Alpha software, especially Alpha o/s software, you are agreeing to accept these risks.

2. If you do choose to use it, you also undertake a responsibility to help the developers to find and correct bugs.

You'd need to learn the proper way to report and follow up on bugs. A good place to start is here:

[http://ubuntuforums.org/showthread.php?t=1161570](http://ubuntuforums.org/showthread.php?t=1161570)


Regards,

Didius

---

### Post by donniezazen on 2009-06-02
Is it possible to install alternate image using USB drive? Due to some reason i am not able to write the image on a CD, i have tried different computers and different softwares. I used unetbootin to copy image files but the installation is struck at the CD detection step.

Thanks,
SK

---

### Post by meborc on 2009-06-02
> **soham_1207 said:**
> Is it possible to install alternate image using USB drive? Due to some reason i am not able to write the image on a CD, i have tried different computers and different softwares. I used unetbootin to copy image files but the installation is struck at the CD detection step.

Thanks,
SK

it is possible to use ANY iso image and make your usb to "be" the live-cd

use unetbootin program to do it

---

### Post by seeker5528 on 2009-06-03
> **soham_1207 said:**
> Can somebody please explain me what are these people talking about? Flies, spiders, dogs, kitten.....

I doubt anybody would get it unless they just happened to have the same random thought.

The dog thing followed by the kitten thing, just made me think of [the woman who swallowed the fly](http://www.poppyfields.net/poppy/songs/oldwoman.html).

Later, Seeker

---

