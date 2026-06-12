---
title: "xulrunner-1.9.1 being heldback?"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by JCoster on 2010-03-27
Hey guys.
Just a quick one today...  Is anyone else having xulrunner-1.9.1 being held back?  I know packages being held back is normal but I ask because I was having trouble with Eclipse during the alpha stages of Lucid and only got around it by install xulrunner-1.9.3 from the Mozilla daily PPA.  If I remove 1.9.3 and the PPA from my software sources (which I hate being there because it means I have to update Firefox daily) will the new version of xulrunner be available to me?

On a similar note, is everyone else getting a bunch of Eclipse updates held back too?

Cheers guys,
JC

---

### Post by JCoster on 2010-03-31
Bump!

---

### Post by JCoster on 2010-04-02
One more try..  bump!

(sorry- I even hate myself for doing it..)

---

### Post by mc4man on 2010-04-02
xulrunner-1.9.1 is available as is xulrunner-1.9.2 ( there actually was an update today to xulrunner-1.9.1 - previous was back in feb I believe.

Both versions can be installed at the same time, some apps still use xulrunner-1.9.1, some sources need to be built off of the 1.9.1 -dev headers.

If you're going to run into issues it would be any apps that depend of the ppa version you installed - if that version needs to go...

---

### Post by JCoster on 2010-04-02
Thanks for replying.  I've alpha tested since Jaunty so I'm used to packages being held back all the time, I just think it's more than coincidental that on this machine both Eclipse and XULRunner are being heldback since they're the only things i've had to fiddle with to get working!  

```

jcoster@jcoster-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  couchdb-bin eclipse-jdt eclipse-pde eclipse-platform eclipse-plugin-cvs
  eclipse-rcp gir1.0-clutter-1.0 gir1.0-clutter-gtk-0.10 gir1.0-gtk-2.0
  libarchive1 libequinox-osgi-java libnb-apisupport1-java libnb-ide12-java
  libnb-java3-java linux-generic linux-headers-generic linux-image-generic
  netbeans ntfs-3g parted system-config-printer-common udisks update-notifier
  update-notifier-common xulrunner-1.9.1 xulrunner-1.9.1-gnome-support yelp

```

Does everyone else have all of that?

---

### Post by mc4man on 2010-04-02
> Does everyone else have all of that?
I would suspect only those that have 'fiddled' around with things like you did.
If you spend some time in synaptic possibly you can find a way to move forward, otherwise your lucid install is somewhat dead in the water.

For instance - the first package you listed - couchdb-bin - it depends on xulrunner-1.9.2 ( not 1.9.1 or 1.9.3

ect. ect.

---

### Post by JCoster on 2010-04-02
Ok- I've removed the mozilla-daily PPA and have manually install xulrunner-1.9.2.

couchdb has now updated but still stuck with Eclipse being heldback...  will keep you posted.

Cheers for your help,
JC

---

### Post by JCoster on 2010-04-02
Ok xulrunner-1.9.1 has been updated by removing gnome-shell and libgjs0 (as libgjs0 depended on a version of the -dev headers of a version < the new one)...

Half way there!

---

### Post by mc4man on 2010-04-02
The eclipse is probably related to some java or jre libs - netbeans probably is in with that

sounds like you'll get the last roadblock or 2 removed

---

### Post by JCoster on 2010-04-02
Ok so I ran update-manager and it updated me to the latest kernel and Eclipse so problem solved!

Thanks for all your input!
Cheers,
JC

---

