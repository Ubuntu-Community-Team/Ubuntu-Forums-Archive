---
title: "Gnome 2.24"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by mhh91 on 2008-09-24
the official website says it's available

and when will it be available through the repos??

---

### Post by mikewhatever on 2008-09-24
Never on Hardy :). It will come bundled with Intrepid, when it's released in October.

---

### Post by mhh91 on 2008-09-24
is intrepid ibex safe to upgrade to now?

and how do i know whether my ethernet card is e1000 or not???

---

### Post by Natsuko640 on 2008-09-24
> **mhh91 said:**
> is intrepid ibex safe to upgrade to now?


If I'm right, Intrepid is still in Alpha. You can upgrade if you want, but it's full of bugs and unstable.

---

### Post by perlluver on 2008-09-24
Intrepid is at Alpha 6 right now, I would advise waiting, unless you really can't wait, as for your Ethernet card, you can find out by running lspci in a terminal.  Applications>Accessories>Terminal.

---

### Post by mhh91 on 2008-09-24
i ran lspci and this is what i got
> 00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)

will that work with intrepid or not?

---

### Post by cariboo on 2008-09-24
Yes you nic will work in Intrepid. Gnome 2.24 just showed up in the Intrepid repo's this morning. I would suggest when you do install Intrepid to do a clean install, as a lot of things have changed, and you don't want to use your old configuration files as things may not work as expected. That being said, I have been running Intrepid since it became available in the repo's and aside from a few problems with installation, I find it is really stable.

Jim

---

### Post by mhh91 on 2008-09-25
clean install means that i have to remove my current system,which i can't do because i don't have CD's atm,what are the risks if i did an upgrade?

---

### Post by phoenix49 on 2008-09-25
There's no need to remove the whole system, its enough to remove gnome configuration files from your home folder, or more easier way, is to create a new user and login there after you've upgraded everything

---

### Post by mhh91 on 2008-09-25
one last question,what's the size of the upgrade?

and is there a lot of upgrades to be installed once i log in?,like the 200+ upgrades that i find once i install hardy

---

### Post by phoenix49 on 2008-09-25
Actually, if you are running Hardy now, then there will be a lot of packages to download and upgrade. So it may take 200 or even more packages. Also, these packages will be the latest ones, so no updates should be after that.

---

### Post by perlluver on 2008-09-25
I had 505 updates, when updating from the Alpha 4 disc, of Intrepid, so I would guess there would be more for Hardy.

---

### Post by mikewhatever on 2008-09-25
> **mhh91 said:**
> one last question,what's the size of the upgrade?

and is there a lot of upgrades to be installed once i log in?,like the 200+ upgrades that i find once i install hardy

Upgrading from Hardy to Intrepid means most of the packages will get upgraded to a newer version. Hardy has about 2000 of them installed by default, so you should expect quite a few hundred of megabytes.
After the upgrade, you should also expect lots of updates, because Intrepid is currently in its development stage. I'd say several tens of megabytes every day should be a good estimation.
That said, you are greatly discouraged to upgrade until the final release is out in October, unless you know how to fix things and like tasting unstable software. It will almost certainly break, so be sure to have a good backup strategy.

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-September/000487.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-September/000487.html)
[http://www.ubuntu.com/testing/intrepid/alpha6](http://www.ubuntu.com/testing/intrepid/alpha6)

---

### Post by Elfy on 2008-09-25
Another thing to bear in mind is what graphics card you use. Older nvidia are a problem at the moment.

---

### Post by russlar on 2008-09-25
How about installing Gnome 2.24 on Hardy _not_ using the repo's (i.e. downloading a .deb package directly from Gnome)? Any advice on how to do this without completely hosing yourself?

---

### Post by mhh91 on 2008-09-26
my graphics card is nVidia GeForce 6200,is that an old card?

---

### Post by Elfy on 2008-09-26
Not that I know of - the driver should be ok - but whether you have other problems is quite another matter.

---

### Post by mhh91 on 2008-09-26
well,i don't have any CD's at the moment,and i think i'll just wait for the beta version to come out,i think it'll be more stable

---

### Post by Sef on 2008-09-26
> How about installing Gnome 2.24 on Hardy _not_ using the repo's (i.e. downloading a .deb package directly from Gnome)? Any advice on how to do this without completely hosing yourself?

Read what the [Gnome]("http://gnome.org") site says.   **Back up **your data.  There is always a risk of hosing your system.

---

