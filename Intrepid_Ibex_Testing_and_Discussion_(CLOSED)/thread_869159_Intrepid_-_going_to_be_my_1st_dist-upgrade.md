---
title: "Intrepid - going to be my 1st dist-upgrade"
date: 2008-07-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by BGFG on 2008-07-24
Hi,
before the advanced guys refer me to google and say 'do my own research' I've already started. :)
But i'd still like some feedback on the apt-get dist-upgrade process from people who have used it successfully and unsuccessfully.

My take:
The desktop is upgraded - Gnome 2.24
the kernel
And the filesystem libraries, modules etc...

My main concern is the Filesystem, does distribution upgrade OFTEN break programs(i mean their dependancy on system libraries), or do the developers generally bend over backwards to ensure backwards compatability. I have more questions but like i said i'll wait to see what you guys say and there's always google.

Doesn't google sort of remind you of brainiac ?

---

### Post by Elfy on 2008-07-24
I wouldn't know if it often breaks programs as most which end up here have problems, so there's no real way of knowing who hasn't :)

When it's upgraded the whole thing gets upgraded so programs and their dependencies are done together, logically I guess the only thing not dealt with would be config files in your /home.

I did it once and while I had some problems they were not related to the upgrade itself but something I broke afterwards iirc. 

Personally I don't have much in my /home that isn't easy to recreate so tend to go for a clean install.

Good to have a look at what you might be up against, but you shouldn't be getting any google is your friend stuff

---

### Post by BGFG on 2008-07-24
Thanks,
i too prefer a fresh install, but you know...for the experience....
Besides i'm not too demanding a user, my configuration seems to one of maybe 10 :) that have the -20 kernel working normally....

---

### Post by Elfy on 2008-07-24
I'm one of those with it working too - I guess the best thing is to backup and go for the experience, perhaps get the alternate cd then you can use it do an upgrade and also to do a clean install if it all goes pear shaped.

---

### Post by BGFG on 2008-07-24
Definitely...I can't wait... I'm one of those 'latest' hounds, I'll definitely be on gnome 2.24 before fiesty is out....
Really looking forward to more than just list and icon views.

---

### Post by Elfy on 2008-07-24
> I'll definitely be on gnome 2.24 before fiesty is out....Feisty is supported only until October ! or intrepid - if you're talking about upgrading to intrepid I would wait - I can't get it to go very well at all at the moment.

---

### Post by BGFG on 2008-07-24
Geez, i just realized.. My Brain does this sometimes :) I meant ibex...
LOL. People are probably looking at this thread and wondering WTF is he on about ....LOL

---

### Post by BGFG on 2008-07-24
Geez, i just realized.. My Brain does this sometimes :) I meant ibex...
LOL. People are probably looking at this thread and wondering WTF is he on about ....LOL

---

### Post by arpanaut on 2008-07-24
[SIZE="5"]WTF is he on about ....LOL[/SIZE]

---

### Post by halitech on 2008-07-24
I upgraded from Dapper to Fiesty to Gutsy with no problems anytime but I have a pretty basic machine with no bleeding edge hardware (P4 1.8, 896meg of ram, Nvidia GeForce4 MX 440 AGP video) so didn't expect problems. I did back up just in case.

---

### Post by BGFG on 2008-07-24
And then he double posted.... :) this is what happens when you clog your bandwith with torrents....

I think i'll do Ibex without a backup, by the seat of my pants. It should make for an exciting or very depressing post come 8.10

---

### Post by Elfy on 2008-07-24
Yea - geez

But as you are talking about ibex I really wouldn't do it yet unless you have a machine to run that isn't critical. There are a few things not working all that well at the moment- don't know if you are aware but there is a forum for intrepid

[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

---

### Post by Elfy on 2008-07-24
> And then he double posted....Only one thread though - so you're excused :D


I didn't suss it until you were talking about Gnome 2.24

---

### Post by BGFG on 2008-07-24
Oh no no no, Not now...I meant when the Ibex final comes out :) I'm not THAT eager. Plus, as you said i only have ONE machine, and this was a gift to boot!
So no pre-releases for distributions.. I'll get the Gnome 2.24 final first, and an Ibex dist-upgrade around mid-late october...
And thanks for the forum link...

---

### Post by kansasnoob on 2008-07-24
If you need to ask, you DO NOT want Intrepid yet!

As far as upgrades go my success rate is about 50-50 just upgrading from Gutsy to Hardy, so I imagine the more upgrades necessary the lower the success rate would go. IE: Gutsy to Hardy 50%, Feisty to Gutsy to Hardy 25%, etc, etc.

OTOH, one of my successes was Dapper Kubuntu to Hardy Kubuntu, but Dapper upgrades directly to Hardy ................ that's the beauty of LTS.

But, if you want Intrepid, and you're asking questions here, you won't like Intrepid!

---

### Post by philinux on 2008-07-24
Just check the forum [http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

It's breaking as you would expect for an alpha release.

I'm running it on my second HD. You could try running it in a partition to help with testing.

---

### Post by steveneddy on 2008-07-24
I recommend that you backup your /home folder and totally reinstall.

---

### Post by Joeb454 on 2008-07-24
I deleted the duplicate post, and I've renamed it too :)

Edit: There we go done :) I tried to keep it of similar length too :p

---

### Post by dfreer on 2008-07-24
Totally Off-Topic:

Hmmmm... following the standard naming scheme (**Dapper** Drake, **Edgy** Eft, **Feisty** Fawn, **Hardy** Heron) why wouldn't you call it **Intrepid** Ibex?

---

### Post by BGFG on 2008-07-25
Hey Joeb454 Thanks !
As for the rest of advice, you guys have me thinking really hard now... I still want to try apt-get dist-upgrade for the experience... 
But don't worry too much, i have another 250gig seagate currently housing vista :(
and as soon as i get a dvd burner, (yes, believe it or not, it's 2008 and i have a cdburn/dvdROM LOL) prob a cheap lite-on, and i can burn off enough of my media i'll create a couple of partitions, One for OpenSolaris and one for the next incarnation of Ubuntu..
Hope 8.10 or 9.04 has better webcam support..As things stand that's my only problem. Nothing to fuss about though....

---

### Post by Predator106 on 2008-09-06
> **dfreer said:**
> Totally Off-Topic:

Hmmmm... following the standard naming scheme (**Dapper** Drake, **Edgy** Eft, **Feisty** Fawn, **Hardy** Heron) why wouldn't you call it **Intrepid** Ibex?

Huh? It is called Intrepid Ibex...

---

### Post by dfreer on 2008-09-07
> **Predator106 said:**
> Huh? It is called Intrepid Ibex...

The OP's original title evidently said "Feisty", and then he corrected and said something about "I should've said ibex". 

By the time I got into the thread, the original post had already be corrected to "Intrepid" and so I mistakenly thought the OP and subsequent posters were saying to call the 8.10 release "ibex" instead of "Intrepid" hence my question.

Which isn't what they were talking about at all.

---

### Post by Predator106 on 2008-09-07
Oh okay, sorry.

---

