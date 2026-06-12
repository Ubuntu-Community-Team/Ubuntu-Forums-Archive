---
title: "How do you transfere software between PC,s"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by lang0 on 2010-02-24
Hi all just a newbie and I have what some of you may think is a silly question.
How do you transfer software packages between machines. I just upgraded the kernel on one of my computers and it was a 28meg download. I do not want to do that for every machine as I have only limited bandwidth and other people sharing the same internet connection.
If for example I was using windows and wanted to transfer some software I could make a copy of the EXE file and away I go. Any help would be apriceated as it is frustrating if for example you have to reload ubuntu and than download all of the upgrades again that seem very windows to me. Can we not make a copy of all the bits and pieces that are downloaded and reinstall it id need be or move it between machines.:p

---

### Post by nothingspecial on 2010-02-24
For this you can use [[COLOR="Magenta"]aptoncd[/COLOR]]("http://aptoncd.sourceforge.net/")

---

### Post by dvlchd3 on 2010-02-24
In this circumstance, you could install the packages you required, then check

```

/var/cache/apt/archives

```
for the .deb package.  This you could then transfer onto a thumbdrive/cd/etc, and run on the other machine(s).

To just download a package without installing it use:

```

sudo apt-get -d install [PACKAGE_NAME]

```
then check /var/cache/apt/archives for the .deb package.

---

### Post by nothingspecial on 2010-02-24
But installing the deb will download any dependencies.

You could use ```
apt-cache depends --recurse package
``` to list all the dependencies of the package and the dependencies of the dependecies and so on and install them from the base packages up.

But that would be really complicated and you`d probably end up downloading stuff any way.

---

### Post by pmlxuser on 2010-02-24
the best way i hink is the use of files from /var/cache/apt/archives
if you are not in a tendancy of executing apt-get clean that is

if you copy all the files from one machine /var/cache/apt (assuming same version) and paste them in corresponding machines folders and just do a and update you can install all the programs you installed in the original machine..

works if its the same version

---

