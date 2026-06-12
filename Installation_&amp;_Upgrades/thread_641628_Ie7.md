---
title: "Ie7"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by twodayslate on 2007-12-15
Hi am am interested in downloading IE7 for my computer. I am running Gutsy (7.10).

I need IE7 for web design. I have IE6 right now with the IE7 beta from IEs4Linux. I was wondering if there was a non beta version out.

I saw a couple threads on this but they all said that I need to have XP run in the background.

---

### Post by achadwick on 2007-12-16
> **twodayslate said:**
> 
I need IE7 for web design. I have IE6 right now with the IE7 beta from IEs4Linux. I was wondering if there was a non beta version out.

I saw a couple threads on this but they all said that I need to have XP run in the background.

I just completed a proof-of-concept  [Gutsy package of ies4linux]("http://ubuntuforums.org/showthread.php?p=3960527#post3960527") over in another thread. It doesn't install the ie7 beta, but it could be made to quite easily. Want the beta made accessible in any future revisions? :)

The ie7 ies4linux beta is *very* beta right now, it seems. As far as I know, it's still a Beta hack due to lack of support for IE7-specific stuff in the guts of WINE rather than in ies4linux: hence the rather ugly trick ies4linux uses of first installing ie6 and then ripping its rendering engine out and dirtily replacing it with ie7's.

---

### Post by twodayslate on 2007-12-17
I have the latest version of IEs4Linux with there version of the beta. IS this different?

---

### Post by achadwick on 2007-12-18
> **twodayslate said:**
> I have the latest version of IEs4Linux with there version of the beta. IS this different?

The package is based on the latest upstream beta tarball, but not on the SVN version. It runs the same code and makes the same hacks,  but it doesn't yet offer you the option of downloading ie7. It probably should... along with ie1, ie3 and all the other easter eggs in ies4linux :)

If the package doesn't ask you anything during installation, type

[INDENT]$ sudo dpkg-reconfigure ies4linux[/INDENT]

and you should get some sort of dialog or menu asking you things. By the way, this package shouldn't interfere with any existing installs of ies4linux from the unpackaged script: it'll install alongside script-installed WINEPREFIXes, though you may of course have difficulty telling the icons apart in the menu!

---

### Post by twodayslate on 2007-12-18
OK, thanks.

---

