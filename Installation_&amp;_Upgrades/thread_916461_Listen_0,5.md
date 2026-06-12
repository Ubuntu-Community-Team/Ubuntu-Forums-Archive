---
title: "Listen 0,5"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by SecurityCop on 2008-09-10
I found a much better program for listning to music then Rhythmnbox, and I was following the instructions when this porblem came up.

```
make[4]: *** [install-schemaDATA] Error 1
make[4]: Leaving directory `/home/krystle/libpurple/gconf'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/home/krystle/libpurple/gconf'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/krystle/libpurple'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/krystle/libpurple'
make: *** [install-recursive] Error 1

```

EDIT: Forgot another part. This goes before the other code.

```
 /usr/bin/install -c -m 644 'purple.schemas' '/usr/local/etc/gconf/schemas/purple.schemas'
/usr/bin/install: cannot remove `/usr/local/etc/gconf/schemas/purple.schemas': Permission denied

```

Any ideas on what that means and how to fix it?

---

### Post by Partyboi2 on 2008-09-11
Have you tried installing the deb package from sourceforge? Its alot easier then compiling. [[COLOR=Blue]Here[/COLOR]]("http://sourceforge.net/project/showfiles.php?group_id=161415&package_id=181822&release_id=444676") is the link.

Edit: When you ran make install are you putting sudo infront of it?
so
```
 sudo make install
```

---

### Post by SecurityCop on 2008-09-11
> **Partyboi2 said:**
> Have you tried installing the deb package from sourceforge? Its alot easier then compiling. [[COLOR=Blue]Here[/COLOR]]("http://sourceforge.net/project/showfiles.php?group_id=161415&package_id=181822&release_id=444676") is the link.

Edit: When you ran make install are you putting sudo infront of it?
so
```
 sudo make install
```

Ok so how do you install the deb package? I can't figure out what file I was supposed to target on the other package.

---

### Post by Partyboi2 on 2008-09-11
To install a deb package you can double click on it and install it, or the other way is to open a terminal and cd to where the downloaded deb package is and then install it by
```
sudo dpkg -i packagename
```*Change packagename to actually name
If it tells you that it has missing dependencies then install those packages.

---

### Post by SecurityCop on 2008-09-11
Problem is I don't know what the package nam is.

---

### Post by Junk_head on 2008-09-11
SecurityCop: on the sourceforge page partyboi linked you are looking for a .deb at the end of the filename which would be listen_0.5-beta1-7_i386.deb. Download that to your desktop and double click it and install it, no terminal necessary.

---

### Post by SecurityCop on 2008-09-11
Thanks, and so I did try that, but it said my python-mutagen dependency wasn't acceptable, even though I just installed it and it's the newest version.

---

### Post by Partyboi2 on 2008-09-12
These are some of the packages you will need to install to met the dependencies for listen[FONT=monospace]
[/FONT]```
sudo apt-get install cdbs docbook-xsl docbook-xsl-doc-html docbook2x fdupes libffi-dev libidl-dev libnspr4-dev libnss3-dev liborbit2-dev libxml-namespacesupport-perllibxml-sax-expat-perl libxml-sax-perl orbit2 python-all-dev python-dev python-gnome2-dev python-gobject-dev python-gtk2-dev python-gtk2-doc python-pyorbit-dev texinfo xulrunner-1.9-dev

```

---

### Post by SecurityCop on 2008-09-12
> **Partyboi2 said:**
> These are some of the packages you will need to install to met the dependencies for listen[FONT=monospace]
[/FONT]```
sudo apt-get install cdbs docbook-xsl docbook-xsl-doc-html docbook2x fdupes libffi-dev libidl-dev libnspr4-dev libnss3-dev liborbit2-dev libxml-namespacesupport-perllibxml-sax-expat-perl libxml-sax-perl orbit2 python-all-dev python-dev python-gnome2-dev python-gobject-dev python-gtk2-dev python-gtk2-doc python-pyorbit-dev texinfo xulrunner-1.9-dev

```

I found the dependencies I need already, but the problem is it can't recognise python-mutagen even though it is installed.

---

### Post by Partyboi2 on 2008-09-13
What is the output from the terminal when you try to install it from the terminal
Change directory to where the downloaded listen deb is. If on your Desktop
```
cd ~/Desktop
```
then install
```
sudo dpkg -i package
```
*change package to actually name.

---

### Post by cariboo on 2008-09-13
Listen is also in the repositories. You can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it.

Jim

---

### Post by Partyboi2 on 2008-09-13
> **cariboo907 said:**
> Listen is also in the repositories. You can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it.

Jim
They are using dapper ;),  listen not available from the repo's

---

