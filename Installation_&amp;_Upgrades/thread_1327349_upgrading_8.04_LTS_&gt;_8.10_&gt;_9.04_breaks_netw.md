---
title: "upgrading 8.04 LTS &gt; 8.10 &gt; 9.04 breaks network manager applet"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by MJWhiteDerm on 2009-11-15
I have a problem which has shown up on two machines.  In both cases, I am upgrading from 8.04 LTS to 8.10 to 9.04 and plan to upgrade to 9.10.  In each case, after the upgrade from 8.04 to 8.10, the network manager applet in the upper right corner of the panel shows that I have no network connection.  I am attaching a screenshot from this computer (one of two affected) so you can see what I'm talking about.  Despite the warning in the applet, I have network access and successfully upgraded each machine to 9.04, hoping the applet would correct in the upgrade.  I have not seen that happen.  Both machines now run 9.04 without any change in the applet.  Email and Firefox have no problems connecting to the internet in each machine.  We have fiber optic to the house, a Cisco router (with which I have different issues) and Cat-5e in the walls, so no wireless is involved.  

This machine is an AMD Athlon 64 X2 Dual core desktop.  The other machine is a Dell Inspiron 1100 laptop -- an old machine.  On the Dell Inspiron, I installed Linux Mint (latest version) in a dual boot, and it has no problems.  

How can I fix the applet before upgrading, or will it go away in the final upgrade to 9.10 for each machine?

Michael

---

### Post by Zoot7 on 2009-11-15
Since you're going to be upgrading 3 times, why not just backup your documents and settings (your /home folder) and do a clean install?
You'll be a lot less likely to experience problems this way. The upgrades are always quite iffey.

---

### Post by MJWhiteDerm on 2009-11-15
That's probably what I will have to do.  It's a hassle, because there are six different users on the system and backing it up is about 120 GB .. a lot of photos.  I have an external 160 GB hard disk, currently blank, for that purpose.

However, Ubuntu's instructions for upgrading from older versions (e.g. LTS such as mine) are to do sequential upgrades, so I wanted the Forum to be aware of a problem.

---

### Post by MJWhiteDerm on 2009-11-15
Also, uninstalling the Applet, then re-installing it, does NOT make the problem go away, which I find interesting.

---

### Post by Zoot7 on 2009-11-15
I had a similar problem with the network manager applet when I upgraded from Hardy to Intrepid (only time I even tried an upgrade), my wireless refused to connect no matter what I did. Although a friend of mine with the same wireless card had no problems (he did a clean install though..). So I went back to Hardy and skipped Intrepid, almost skipped Jaunty too.

Anyway, one thing I'd recommend you check out is using a separate partition for /home. That way you can re-install your OS and keep all your documents and settings. There's a good guide here:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
It's saved me countless hours of configuring applications when I install a new version of Ubuntu.
It's just a case of install the new version of Ubuntu, install all the applications and then re-activate your old /home partition. :)

---

### Post by MJWhiteDerm on 2009-11-15
Alright, now I feel like an idiot.  I have a separate partition for /home already set up ... just didn't occur to me that I could do the alternate install and do it that way.

Thanks.

---

### Post by Zoot7 on 2009-11-15
You're sorted so! ;)

---

### Post by jcoles on 2010-02-14
If the "upgrade" isn't going to keep NetworkManager Applet working, it should at least let us remove the useless thing. 

Make sure you report other wreckage from these updates,
such as Weather Applet, TOR proxy, ...

---

