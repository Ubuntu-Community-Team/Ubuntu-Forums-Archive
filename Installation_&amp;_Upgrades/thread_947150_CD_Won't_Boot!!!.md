---
title: "CD Won't Boot!!!"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by warrior_juggalo on 2008-10-14
Hey, I've installed 8.04 on my computer through windows afew months back, LOVING Ubuntu, I would completly switch but i'm what you would consider a "Hardcore gamer".
I have partitoned 250GB from my HDD for Ubuntu and downloaded the Beta for 8.10, Burnt it and it won't boot, It will come up in windows but it won't boot at start up.

I've read afew things on the net about what this problem could be so i'll say write of the bat what it isn't.

It is not that i have downloaded the wrong version, To make 100% sure of that i downloaded the other version and still no dice!!!
It's not that i burnt it too fast.
It's not that i burned the ISO onto a disc and not burnt it as an iso so to speak., Help me, Please, THanks in advance, I'll let you all know how i go.

---

### Post by Partyboi2 on 2008-10-14
Have you checked your bios that boot from cdrom is first?
If you are happy with your current installed version of ubuntu you can move it to its own partition. See [[COLOR=RoyalBlue]here[/COLOR]]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?")

---

### Post by warrior_juggalo on 2008-10-14
Where exactly in the bios is it?

So i can move it even tho it's installed in windows now?

---

### Post by cariboo on 2008-10-14
When your computer boots up you will see amessage something like:

```
press delete to enter setup
```

You have to go to the bios setup menu to set your boot order. Have a look at this link for an explanation of what the bios does:

[http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)

Jim

---

### Post by Partyboi2 on 2008-10-14
>  So i can move it even tho it's installed in windows now? Yes it explains how in the link I provided in my last post.

> Where exactly in the bios is it?
Have a look for boot order, or something along those lines, different bios have slightly different menu layouts

---

### Post by mikecomua on 2008-10-14
Have u md5summed it?

---

### Post by warrior_juggalo on 2008-10-15
Hey, Would i get someone on my aMSN to walk me through migrating it over to a real partition? My msn is [email]warrior_juggalo@hotmail.com[/email], Also do i do the migration on Ubuntu or Windows Vista?

---

### Post by warrior_juggalo on 2008-10-15
Hey, I got my CD to boot, It was the BIOS set up i had to change.

But now when i go to install it comes up some "Getting VBE info block failed"
Next line has something about "failed with -22"

I'm going to attempt to move this Wubi install to a real partition now, I'll let yous all know.

---

