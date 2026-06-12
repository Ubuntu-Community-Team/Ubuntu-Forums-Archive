---
title: "Install packages without internet connection"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by athevil on 2010-02-25
Hi all,

I wasnt abel to find the answer for this, or maybe, I'm too newbie to understand this.

Well, my question is, how do i install packages from CD on a system having no internet connection. As, the thing happened with me, I had downloaded some packages for upgrading OpenOffice 3.1.1, and met with some unmatched dependencies problem.

Next, I got error on my panel, showing error(dont remember, wat exactly it was), then i ran '**sudo apt-get autoremove && sudo apt-get -f install**' to remove unwanted packages.

I tried a lot to install openoffice from Ubuntu 9.10 CD, but wasnt able to install it :(
cudnt even find .deb packages, to do it manually.

Seeking help.




and ya, wann kno, procedure to download updates, from archive.ubuntu.org and update it on system, not connected to Internet.

---

### Post by athevil on 2010-02-26
well, i even tried with, by checking 'Installable from CD/DVD' in Synaptic Package Manager -> Repositories.

But, that too, cudnt help me :(

---

### Post by dvlchd3 on 2010-02-26
What version of Ubuntu are you attempting to install Open Office on?  You cannot mix and match different Ubuntu versions of software.  9.10 packages are not necessarily going to work on 8.04, and 8.04 packages are not necessarily going to work on 9.10...

Also, keep in mind, the latest versions of Ubuntu software are typically not on the CD.

---

### Post by athevil on 2010-02-26
im using ubuntu 9.10, 64 bit version.

well, wat am i saying is, Openoffice was ther with my fresh install,but somehow, lost all of its installed files from my system, while updating openoffice packges manually.

Now, all I want, is to install openoffice back,(dont mind even its 3.1.1) from CD.

---

### Post by PRC09 on 2010-02-26
Maybe this link will help.I havent tried it myself but it looks promising.Post back if it works.....


[http://techspalace.blogspot.com/2009/04/offline-update-ubuntu.html](http://techspalace.blogspot.com/2009/04/offline-update-ubuntu.html)

---

### Post by athevil on 2010-02-26
[COLOR=Black]__@PRC09


OKAY, Look.....i think i need to clarify my question bit more

I HAD some package XYZ pre-installed on my system.
I tried to upgrade with some of bug-fixes and met with some unmatched dependencies.
Update manager showed me some error, with unused packges, that no more are useful now.

So I ran '**sudo apt-get autoremove**' to remove those packages, which are of no use, now.

THIS, unfortunately, removed ALL my openoffice-related/dependant packes.

NOW, all I want to do, is to get OpenOffice back in my system, which is ther with me in Karmic Koala CD.

But, how do I install THOSE packages.

Please point me to the right direction, if I am making some noob kinda noise.
[/COLOR]

---

### Post by dvlchd3 on 2010-02-26
Ok, try this.  Insert your CD.  Open your sources file.
```

sudo gedit /etc/apt/sources.list

```

Uncomment (remove the #) from the first line.  It should read something like this:

> 
deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted

Comment everything else since these are all network repositories.  (Just add a '#' in front of every line that doesn't have one)

Save and close the file.

Update your sources
```
sudo apt-get update
```

Install package xyz assuming it exsits on the CD, and all dependencies exist on the CD or are already installed.

```
sudo apt-get install xyz
```

For open office, here are all the packages I have installed on my system (I don't believe I've added any, so these should all be the default)
openoffice.org-thesaurus-en-us
openoffice.org-core
openoffice.org-thesaurus-en-au
openoffice.org-base-core
openoffice.org-hyphenation-en-us
openoffice.org-draw
openoffice.org-calc
openoffice.org-impress
openoffice.org-writer
openoffice.org-math
openoffice.org-style-human
openoffice.org-common
openoffice.org-help-en-us
openoffice.org-hyphenation
openoffice.org-emailmerge
openoffice.org-gnome
openoffice.org-gtk

I can't seem to find a meta package that includes all of these, so you'll probably have to install all of them.  Some probably depend on others, but all should be on the CD.

You can install all of these by:
```

sudo apt-get install openoffice.org-thesaurus-en-us openoffice.org-core openoffice.org-thesaurus-en-au openoffice.org-base-core openoffice.org-hyphenation-en-us openoffice.org-draw openoffice.org-calc openoffice.org-impress openoffice.org-writer openoffice.org-math openoffice.org-style-human openoffice.org-common openoffice.org-help-en-us openoffice.org-hyphenation openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk
```

Does this answer your question?

---

### Post by athevil on 2010-02-27
well, thanx for ur reply...and it was with nice explanations

but, unfortunately, it didnt help me too

```
sudo apt-get install -y openoffice.org-thesaurus-en-us openoffice.org-core openoffice.org-thesaurus-en-au openoffice.org-base-core openoffice.org-hyphenation-en-us openoffice.org-draw openoffice.org-calc openoffice.org-impress openoffice.org-writer openoffice.org-math openoffice.org-style-human openoffice.org-common openoffice.org-help-en-us openoffice.org-hyphenation openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openoffice.org-thesaurus-en-us is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package openoffice.org-thesaurus-en-us has no installation candidate

```


well, how one cud get the list all related packages, for say, openoffice*

---

### Post by gadolinio on 2010-02-27
Don't know if this will be useful to you, but just in case: some packages are meant to be installed only on a 32-bit system, others only for 64-bit, and others are universal. Maybe the packages you have in your CD cannot be installed in your 64-bit ubuntu. Also make sure of the version compatibility. I had that trouble trying to install openoffice 3.something in a version that didn't support it.
Good luck!

---

### Post by athevil on 2010-02-27
@gadolinio

openoffice is already ther on Ubunt 64 bit Karmi Koala 9.10

was working well, too. But, this all happened because of some bug-fixes, i downloaded debs from 'securitu.ubuntu' and...

some error, from update-manager
after a reboot, it all gone



well, im waiting for 10.04 LTS, and if i had to give my opinion to developers, i wud ask them to provide debs instead on CD itself, rather than that Package.gz format(im just making a comment, from the point of a layman, instead)

---

### Post by Hagar Delest on 2010-02-27
If you can download files and put them on a USB stick before installing it on your system, see [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by gadolinio on 2010-02-28
> **athevil said:**
>  (...) i wud ask them to provide debs instead on cd itself, rather than that package.gz format (...)
+1

---

### Post by athevil on 2010-03-05
so here, it goes unanswered :(

---

