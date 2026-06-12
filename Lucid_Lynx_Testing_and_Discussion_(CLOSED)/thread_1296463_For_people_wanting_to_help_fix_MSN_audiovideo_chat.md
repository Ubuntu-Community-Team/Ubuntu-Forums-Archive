---
title: "For people wanting to help fix MSN audio/video chat"
date: 2009-10-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by castrojo on 2009-10-20
Hi everyone,

Unfortunately due to [bugs like this](https://bugs.edge.launchpad.net/ubuntu/+source/telepathy-butterfly/+bug/437828) it's been decided to completely disable A/V over MSN for Karmic (It's mentioned in the release notes).

However, in order to get better data for upstream there is a telepathy ppa here:

[https://launchpad.net/~telepathy/+archive/ppa](https://launchpad.net/~telepathy/+archive/ppa)

If you want to continue helping A/V over MSN you need to install telepathy-butterfly from this PPA! (It will continue to be updated). Filing bugs without running this version of -butterfly will probably NOT be useful so please ensure you're running the latest version! 

If you're looking to help fix these bugs here's the list: [https://bugs.launchpad.net/ubuntu/+source/telepathy-butterfly/](https://bugs.launchpad.net/ubuntu/+source/telepathy-butterfly/)

You can also find people on #telepathy on freenode. Here's the page for how to debug Empathy:

[http://live.gnome.org/Empathy/Debugging](http://live.gnome.org/Empathy/Debugging)

Please note that there's a debugging console now!

---

### Post by castrojo on 2009-10-22
I'm bumping this so it doesn't get lost in the Karmic release thread swamp!

EDIT: whoops, didn't see it was a sticky.

---

### Post by 23meg on 2009-10-22
> **whiprush said:**
> I'm bumping this so it doesn't get lost in the Karmic release thread swamp!

Stuck!

[QUOTE=whiprush]EDIT: whoops, didn't see it was a sticky.[/QUOTE]

You couldn't have, since I made it sticky a few seconds ago.

---

### Post by edin9 on 2009-10-25
This is just an Empathy thing yeah?

---

### Post by Vanishing on 2009-10-25
my empathy video audio with msn works..o.o
whats wrong?

---

### Post by nhasian on 2009-10-25
mine works as well.  I'm just glad they kept empathy and didnt bump it for pidgin.  Hopefully the A/V will be re-enabled for the masses via a system update.

---

### Post by Frank-NL on 2009-10-28
Did anybody else got an ugly big green icon of Empathy in the notification area by upgrading from the mentioned PPA?

---

### Post by nystire on 2009-10-31
Yes, I have the green icon. I much prefer this to the "hidden" one which I get from the official version.

---

### Post by RedVivi on 2009-11-02
Where can we get the last news about A/V with the MSN protocol ? Should I go first to libpurple, then telepathy-butterfly ? BTW, What is the relation between libpurple and Telepaty ? AFAIK, there isn't so much interest to support it.

---

### Post by kenvandine on 2009-11-02
> **RedVivi said:**
> Where can we get the last news about A/V with the MSN protocol ? Should I go first to libpurple, then telepathy-butterfly ? BTW, What is the relation between libpurple and Telepaty ? AFAIK, there isn't so much interest to support it.
Probably the best place to follow for information about telepathy-butterfly would be the telepathy mailing list:

[http://lists.freedesktop.org/mailman/listinfo/telepathy](http://lists.freedesktop.org/mailman/listinfo/telepathy)

libpurple isn't relevant here, telepathy-butterfly provides the MSN interface.  libpurple is used by pidgin and telepathy-haze is a telepathy provider that uses libpurple to support pidgin's protocols.  However currently the development focus for MSN chat features is happening in telepathy-butterfly.

---

### Post by RedVivi on 2009-11-03
> **kenvandine said:**
> Probably the best place to follow for information about telepathy-butterfly would be the telepathy mailing list:

[http://lists.freedesktop.org/mailman/listinfo/telepathy](http://lists.freedesktop.org/mailman/listinfo/telepathy)

libpurple isn't relevant here, telepathy-butterfly provides the MSN interface.  libpurple is used by pidgin and telepathy-haze is a telepathy provider that uses libpurple to support pidgin's protocols.  However currently the development focus for MSN chat features is happening in telepathy-butterfly.

If I understand correctly, telepathy is a library for Empathy, libpurple is another one for pidgin and there isn't any collaboration between the 2 developers team ?

---

### Post by sensory on 2009-11-03
> **Frank-NL said:**
> Did anybody else got an ugly big green icon of Empathy in the notification area by upgrading from the mentioned PPA?

Yep, and I'm desperately trying to get rid of it. I also had to get rid of the version of Empathy it installed because it didn't work well with the indicator applet.

---

### Post by cespinal on 2009-11-08
hey sensory.....did u come with a workaround to get rid of the green ballon?

---

### Post by RedVivi on 2009-11-09
Interesting...people seems more worried about a green icon than MSN A/V :lolflag:.

---

### Post by nystire on 2009-11-09
It's the small things in life... :)

---

### Post by yelo3 on 2009-11-09
The green baloon is really ugly :D

---

### Post by juancarlospaco on 2009-11-19
How Empathy are going?, 
i got the PPA version and dont have A/V or File Transfer on MSN,
*BTW i hate MSN protocol* :)

---

### Post by ernstblaauw on 2009-12-04
> **cespinal said:**
> hey sensory.....did u come with a workaround to get rid of the green ballon?

The indicator-applet support is enabled by some patches applied by Ubuntu. However, the patches are not (yet?) accepted upstream. As the PPA does not apply the Ubuntu patches, there is no support for the indicator-applet in the PPA.

---

### Post by sco on 2009-12-06
if you upgrade the telepathy-butterfly package only, you will not lose the indicator applet support for empathy.

you have to enable the ppa source using  system->administration->software sources (other software) +Add

ppa:telepathy/ppa


do sudo apt-get install telepathy-butterfly


... and don't forget to disable this ppa source to avoid the upgrade of the rest of the empathy packages.

---

### Post by mohxinn on 2009-12-07
OR

after adding the ppa, you can run this in a terminal:

sudo apt-get upgrade


This will only upgrade installed packages and not install new ones.


Hope this helps!


PS: remember to disable ppa as mentioned by sco to prevent updating packages accidently!

---

### Post by zevans on 2009-12-08
Here's a bug for you... I enabled the repo and installed telepathy-butterfly and it hasn't pulled in any sort of IM client. :-)

Shouldn't the PPA version have a dependency on SOME minimum level of empathy, say the Karmic version?

---

### Post by gnomeuser on 2009-12-10
> **zevans said:**
> Here's a bug for you... I enabled the repo and installed telepathy-butterfly and it hasn't pulled in any sort of IM client. :-)

Shouldn't the PPA version have a dependency on SOME minimum level of empathy, say the Karmic version?

No, it doesn't need empathy. The correct way would be:

Optimally:

Have Empathy upstream use PackageKit's DBUS interface to search for and install protocol support on demand (when creating/configuring accounts).

Acceptable:

The empathy package should depend on a suitable subset of functionality such as jabber and msn support.

The optimal approach gives us a lower footprint on the CD (provided naturally that "space saved using on demand installation" > "space consumed by PackageKit", I am confident that if it doesn't already then it will the more applications we bake this into for handling plugins).

---

### Post by geojorg on 2010-01-11
Any news on telepathy butterfly ? Is been a long time since the last release.

---

