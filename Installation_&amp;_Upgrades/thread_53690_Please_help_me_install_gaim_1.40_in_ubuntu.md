---
title: "Please help me install gaim 1.40 in ubuntu"
date: 2005-08-01
forum: Installation &amp; Upgrades
---

### Post by ekravche on 2005-08-01
I went to this site [http://gaim.sourceforge.net/downloads.php](http://gaim.sourceforge.net/downloads.php), but I'm not sure which package I should download. I'm also not sure how to install the package. Should I remove the older version of gaim that I have installed on my machine?

Thank you in advance.

---

### Post by mingus on 2005-08-01
You can download an rpm version and use alien to convert to a deb; however, users have had very mixed results with this and so *beware*.  Or you can download the source and compile it.  However, the best route is to make a backports request (see that forum) since gaim is a popular application.

---

### Post by ekravche on 2005-08-01
I've tried to compile the source, but I'm not getting anywhere because the make file isn't configured properly for me.

---

### Post by audax321 on 2005-08-02
I'm using Gaim 1.40 from the hoary backports. Just do the following in a console to get it:

1. sudo gedit /etc/apt/sources.list

2. In gedit, add the following at the end:

```

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

3. Then in the console type: sudo apt-get install gaim gaim-data

That should do it. Then you don't need to worry about making anything or uninstalling anything later on if you need to upgrade.

---

### Post by mingus on 2005-08-02
[QUOTE=audax321]I'm using Gaim 1.40 from the hoary backports . . . [/QUOTE]

ekravche - 

audax321 is right . . . I had checked the backports but mis-read the version number.  You definitely want to use this package.

---

