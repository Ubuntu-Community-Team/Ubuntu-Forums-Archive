---
title: "Synaptic - Removing one lib forces removal of half the OS"
date: 2005-04-23
forum: Installation &amp; Upgrades
---

### Post by bolamix on 2005-04-23
Hi yall,

I've come across a problem for which I can't find a solution, even on this here wonderful board: I tried to install the latest version of Skype, and the dpkg -i command kept asking for various library-upgrades. Each upgrade required the upgrading of something else until finally i realised i was probably going at this the wrong way, when I couldn't upgrade and skype still wouldn't install.
The problem is that now these half-installed packages are "broken" from synaptic's point of view. This has happened to me before, i simply select them for removal with the "broken" custom filter, and apply. But this time, every package I try to remove this way seems to require that half the system be removed as well. Check the following screenshots (i don't know how to get these results from the console):

[IMG]http://membres.lycos.fr/bolamix/images/brokenpackages.jpg[/IMG]
^^ these are the broken packages...

[IMG]http://membres.lycos.fr/bolamix/images/toberemoved.jpg[/IMG] 
... and these are the packages that will be removed along with the broken ones.

My question is: should i get ready to reinstall the whole? Or is there a simpler way out of this? Thanks in advance for any help! ;)

---

### Post by nad on 2005-04-23
Hi,

First, I would reinstall everything, do a complete warty uprade to all the newest packages, then confirm the dependency information as below:

<code>
nad@tetrahead:~$ dpkg --info /tmp/skype_1.1.0.3-1_i386.deb
 new debian package, version 2.0.
 size 5823176 bytes: control archive= 1791 bytes.
      32 bytes,     1 lines      conffiles
     920 bytes,    25 lines      control
    2405 bytes,    36 lines      md5sums
 Package: skype
 Version: 1.1.0.3-1
 Section: alien
 Priority: extra
 Architecture: i386
 Depends: dbus-1 (>= 0.23), libc6 (>= 2.3.2.ds1-4), libgcc1 (>= 1:3.4.1-3), libqt3c102-mt (>= 3:3.3.3), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0) Installed-Size: 7202
 Maintainer: Skype Technologies S.A. <info@skype.net>
 Description: Skype is free Internet telephony that just works
  Skype offers free superior sound quality Internet telephony. In addition, it
  includes:
  .
  * Conference calling - enables simultaneous and seamless voice communication
  between groups of up to five friends, family or colleagues.
  .
  * Global Directory - the user-built global Skype contacts directory with
  numerous search options and an easy add-a-contact tool
  .
  * Customization - My Picture image display
  .
  * Mobility - login into Skype account on more than one PC anywhere in the
  world.
  .
  * Multiple Skype accounts on one PC
  .
</code>

If your system does not meet these dependenies even after an upgrade to all the latest packages you may wish to review the warty backports project for newer packages that have been made compliant with warty.

As you have learned, forcing dependencies is not for the faint of heart, strong or intelligent. You have to be demented or a geek (my apologies to all those demented) to wish to live and try to work in dependency hell.

Dan M

---

### Post by bolamix on 2005-04-23
[QUOTE=nad]First, I would reinstall everything, [/quote]
Shoot. I feared as much :? Ah well, if I must...

[QUOTE=nad]do a complete warty uprade to all the newest packages, then confirm the dependency information as below:

```
nad@tetrahead:~$ dpkg --info /tmp/skype_1.1.0.3-1_i386.deb
```[/quote]Thanks for the --info switch, i didn't know that, makes it a lot more practical.

[QUOTE=nad]If your system does not meet these dependencies even after an upgrade to all the latest packages you may wish to review the warty backports project for newer packages that have been made compliant with warty.

As you have learned, forcing dependencies is not for the faint of heart, strong or intelligent. You have to be demented or a geek (my apologies to all those demented) to wish to live and try to work in dependency hell.

Dan M[/QUOTE]Well I messed with the backports last time I reinstalled Warty (I can't compile dcgui-qt on Hoary, that's the main reason why I haven't switched), which led to another brutal reinstall shortly afterwards :grin: But I might give them another try ;) As for dependency hell, I'll try to steer clear of it (that --info switch should come in handy).

Thanks for the fast reply! Very helpful.

---

