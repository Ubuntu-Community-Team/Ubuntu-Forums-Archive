---
title: "Which version of Intrepid Ibex for EeePC?"
date: 2008-10-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by yeehi on 2008-10-01
I heard that Intrepid Ibex is being written with EeePCs in mind, so I would like to try out installing the beta. (One of the benefits of using Ibex might be longer battery life, iiuc.)

1) I am not sure which download to use, as the processor is not an AMD or Pentium. Could you please let me know which link to use?

2)How stable is Ibex at the moment?

3)I read there is some flavour of Ubuntu that is specifically for EeePCs. Is this true? Are many people working on it?

Thank you for your help.

---

### Post by shifty_powers on 2008-10-01
erm, the eeepc is an intel is it not? either way, it uses an x86 instruction set, so it makes no difference...

i'm using kubuntu 8.10 and loving it myslef....

---

### Post by shifty_powers on 2008-10-01
[http://event.asus.com/eeepc/microsites/en/index.htm](http://event.asus.com/eeepc/microsites/en/index.htm)

indeed, they all use an intel processor and chipset...

---

### Post by yeehi on 2008-10-01
Thanks, shifty_powers!

I now see clearly that it is the chipset, rather than the processor, that is the concern.

---

### Post by shifty_powers on 2008-10-01
just download the livecd and you'll find out...

and it is an intel chipset so ti should be fine...

---

### Post by t0p on 2008-10-01
> **yeehi said:**
> Thanks, shifty_powers!

I now see clearly that it is the chipset, rather than the processor, that is the concern.

Why is there any concern?  I'm running ubuntu 8.04.1 on my eeepc, and everything works fine.  It was necessary to do a bit of tweaking (basically the stuff described [here]("http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly") - especially running the RiceeeyTweak script... which seems to have been replaced on the wiki with a new [Niceee script]("http://wiki.eeeuser.com/niceeepc")).  Even the webcam and wireless are working okay.  So I can't see any reason for you to be concerned about the "chipset" (whatever you mean by that!)

---

### Post by yeehi on 2008-10-02
Hi,t0p.

You probably know what a [chipset]("http://en.wikipedia.org/wiki/Chipset") is better than I do - a group of integrated circuits, or chips, that are designed to work together, and are usually marketed as a single product.

I read on the Internet that somebody had been getting shorter battery life using Hardy Heron than Windows. One of the main reasons for getting an EeePC was the long battery life.

btw, I just noticed that there is a warning for people using Intrepid Ibex -  they should not be used on Intel ethernet hardware supported by the e1000e driver (Intel GigE).

---

### Post by yaknowwat on 2008-10-02
The e1000e fix may of come out yesterday I can't say if its going to be ready for the beta though.

[http://lkml.org/lkml/2008/10/1/368](http://lkml.org/lkml/2008/10/1/368)

---

### Post by yeehi on 2008-10-02
What about the EeePC specific version of Ubuntu? Is anybody familiar with that?

---

### Post by yaknowwat on 2008-10-02
> **yeehi said:**
> What about the EeePC specific version of Ubuntu? Is anybody familiar with that?

It was designed specifically with the Eee PC in mind so its good choice.

---

### Post by bornagainpenguin on 2008-10-02
> **yeehi said:**
> I read on the Internet that somebody had been getting shorter battery life using Hardy Heron than Windows. One of the main reasons for getting an EeePC was the long battery life.

That might have been me, [here](http://ubuntuforums.org/showthread.php?t=909237).  If you see the last post you'll see I managed to fix that with the eee-control package byy Marx over at the eeeuser.com forums.

--bornagainpenguin

---

### Post by CapnChkn on 2008-10-15
Hello!  I've been having trouble with all the versions of Xandros, Xubuntu, UbuntuEee, Mandriva, Jose Cuervo, well anything but Windows!  I did get the whole thing working with Niceeepc somehow's and somewhere's, and when I tried to backup that configuration, it wrote to the SS drive and filled it up.

First impression of the new Beta, nothing worked.  I tried running Niceeepc for S&G and it fooled up my FN and Numberpad emulations.

I'm trying to find the list of commands I ran in terminal to get where I was before, the search led me here.

---

### Post by Johnsie on 2008-10-15
Intrepid comes with alot of eeepc kernel modules, previous versions of Ubuntu don't. I've found 8.10 (intrepid) to be alot more functional with the eeepc than 8.4(hardy).

There is still a lot of work needing done for full compatibility though. Things like vga out are essential for many eeepc users

---

