---
title: "Questions about PPA's"
date: 2009-11-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by novafluxx on 2009-11-01
I posted this a while ago, and never got a solid answer...hoping this time it'll be different, since its not as crowded in here!


Is there anywhere I can go to get a list of "official" ppa's? Ones that are provided by Canonical developers? I already know of one for the kernel, but are there any others that are 'official?'

I'm mainly interested in ATI video drivers, the kernel, and boot process enhancements/improvements, but I'd love to just know whats out there.

I've tried searching in launchpad, but I never really get any good results, so I figured I'd ask here!

---

### Post by 23meg on 2009-11-01
> **novafluxx said:**
> 
Is there anywhere I can go to get a list of "official" ppa's? Ones that are provided by Canonical developers? I already know of one for the kernel, but are there any others that are 'official?'

Not right now. You may want to use the [PPA Search]("https://launchpad.net/ubuntu/+ppas").

It's among the plans for the Ubuntu Software Center to provide a system for establishing trust levels for PPAs, so if what you want is to use trusted PPAs (since there are many PPAs maintained by people outside Canonical that are trustworthy), you'll have something like that in the near future.

---

### Post by novafluxx on 2009-11-01
> **23meg said:**
> Not right now. You may want to use the [PPA Search]("https://launchpad.net/ubuntu/+ppas").

It's among the plans for the Ubuntu Software Center to provide a system for establishing trust levels for PPAs, so if what you want is to use trusted PPAs (since there are many PPAs maintained by people outside Canonical that are trustworthy), you'll have something like that in the near future.

That's precisely what I want! I understand there are many other PPA's that are solid and maintained by people outside of Canonical. I use the Pidgin PPA right now actually, because its linked on their website, so I know its not just Jon Q. Public throwing up his builds ;)

This will be an AWESOME feature, I'm all about cutting-edge, thats why I also run Arch.

Thank you 23meg, as always, very helpful!

---

### Post by lovinglinux on 2009-11-01
> **23meg said:**
> Not right now. You may want to use the [PPA Search]("https://launchpad.net/ubuntu/+ppas").

It's among the plans for the Ubuntu Software Center to provide a system for establishing trust levels for PPAs, so if what you want is to use trusted PPAs (since there are many PPAs maintained by people outside Canonical that are trustworthy), you'll have something like that in the near future.

That would be nice.

---

### Post by DougieFresh4U on 2009-11-02
With my 2 Karmic install I have been using the **.32 kernel** along with the **edgers ppa** for use of my **ATI Radeon  HD3200**. Working excellent if I must say so!
Is Lucid going to be using the **.32 kernel**?
I was thinking about starting my Lucid partition with the **.32 kernel**. Don't care to use the **fglrx**

---

### Post by autocrosser on 2009-11-02
I'm sure we'll start with the .32 kernel---not sure what one we'll close with--I bet we stay on the "safe" side this time & just do lots of bug work.......

---

### Post by jppr on 2009-11-02
> **autocrosser said:**
> I'm sure we'll start with the .32 kernel---not sure what one we'll close with--I bet we stay on the "safe" side this time & just do lots of bug work.......

.32 kernel is repos

---

### Post by zika on 2009-11-02
> **lovinglinux said:**
> That would be nice.Since I'm using xorg-edgers also with 2.6.32-999, what is going to happen to my graphics if I upgrade to Lucid at this stage when xorg-edgers does not have Lucid covered? Am I going to degrade my graphics experience or what?

---

### Post by DougieFresh4U on 2009-11-02
> **jppr said:**
> .32 kernel is repos

Find it here [mainline]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")


_**zika**_
I was wondering the same, as I had asked a near same question, but regarding the use of **xorg-edgers ppa**

EDIT- guess I won't know unless/until I try it!

---

### Post by zika on 2009-11-03
> **DougieFresh4U said:**
> Find it here [mainline]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")


_**zika**_
I was wondering the same, as I had asked a near same question, but regarding the use of **xorg-edgers ppa**

EDIT- guess I won't know unless/until I try it!I am daily using 999 a.k.a. "daily" from [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/daily/") but my question was about **ppa : xorg-edgers **and I've got answer from Tormod:[http://www.phoronix.com/forums/showpost.php?p=98220&postcount=78](http://www.phoronix.com/forums/showpost.php?p=98220&postcount=78) so I'm am almost set to embark on LL testing boat ...

---

### Post by novafluxx on 2009-11-03
So it looks as if the "edgers" naming convention is pretty standard amongst the Ubuntu developers PPA's? Should I search for that and see what I get?

---

### Post by Amaranth on 2009-11-03
That's not always true though. We also have team PPA for various packages/package sets like [compiz](https://edge.launchpad.net/~compiz/+archive/ppa). There is one for more stable driver updates for Xorg as well but I can't remember the name... (somewhat ironic)

---

### Post by 23meg on 2009-11-03
[QUOTE=Amaranth]There is one for more stable driver updates for Xorg as well but I can't remember the name... (somewhat ironic)[/QUOTE]

It's ["X Updates"]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates").

---

### Post by DougieFresh4U on 2009-11-06
Any one have the xorg-edgers ppa working with the .32 kernel and not the .32 rc5 kernel?

---

### Post by novafluxx on 2009-11-06
Thanks for the info guys

---

