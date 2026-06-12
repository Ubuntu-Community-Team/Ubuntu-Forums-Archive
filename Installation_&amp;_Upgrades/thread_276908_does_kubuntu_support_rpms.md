---
title: "does kubuntu support rpms?"
date: 2006-10-13
forum: Installation &amp; Upgrades
---

### Post by twidget on 2006-10-13
Hi
im trying to get a Kubuntu based dev computer going for my office.currently im attempting to install blackfin gcc. the problem is that the only packages available seem to be rpms. i took a look in adept and i seem to to have the redhat package manager installed it also has yum which isnt installed. does this mean i can just install the rpms with no worries? alternately theres a package whose extension is .src.rpm. i assume this is the sources file which if i could un-rpm i could just run ./configure and then make right? how do i make it not be an rpm anymore?
thanks

---

### Post by jdusablon on 2006-10-13
There's a package for Debian distros (like Ubuntu) called "alien" for converting RPM to .deb packages. It's quite good at it. You should be able to convert your RPM with almost no effort.

---

### Post by Kateikyoushi on 2006-10-13
You need alien. To install it copy this to the terminal

```
sudo apt-get install alien
```

Then convert your package to .deb.

```
sudo alien -d your_package.rpm
```

If the program is older I would recommend to install from source.

---

### Post by twidget on 2006-10-13
then how come the yum and rpm in adept? actualy i tried alien on msp gcc and it it made the include folder dissapear so thats why im searching for alternatives. i saw that rpm and yum were in my repositories so i thought maybe i was going about things the wrong way.the blackfin people also list cvs as an alternative but as im relatively new to linux 'i've shied away from that so far since i dont realy get how to use it.i figure i'll try alien and if that doesnt seem to work ill give the cvs thing a shot unless anyone has any better suggestions. while im at it if i do actualy get it running is there an easy way to turn the package into a Kubuntu package and add to the repository? i noticed someone did that with avr-gcc and i figure if im already doing the work i might as well save someone else the trouble.

---

### Post by TheWizzard on 2006-10-14
> then how come the yum and rpm in adept?
because linux is free (as in speach). you are free to convert your ubuntu box to rpm-based. 
but please **read**. rpm in adept clearly states: 
> If you want to install Red Hat Packages then please use the alien package. Using rpm directly will bypass the Debian packaging system!
use alien. cvs is for developers.

---

