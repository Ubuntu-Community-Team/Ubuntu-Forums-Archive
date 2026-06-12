---
title: "Upgrading from Hoary to Breezy"
date: 2005-12-04
forum: Installation &amp; Upgrades
---

### Post by MasterC on 2005-12-04
If I were to use terminal to upgrade Hoary to Breezy, would it erase all my files  and installed programs? I wouldn't want to happen, but that is what's holding me back from upgrading. Any advice? Thanks in advance! :)

---

### Post by aysiu on 2005-12-04
It won't.
By the way, are you using Warty? Your subject heading says "Hoary," but this is the Warty support section...

---

### Post by MasterC on 2005-12-04
[QUOTE=aysiu]It won't.
By the way, are you using Warty? Your subject heading says "Hoary," but this is the Warty support section...[/QUOTE]

Oops! You're right- I'm using Warty! 

BTW- Thanks for the info! :cool:

---

### Post by aysiu on 2005-12-04
Be forewarned, though--it may not mess up your files and settings, but it may mess up your xorg.conf. I had some issues with xorg.conf and locale settings when I upgraded from Hoary to Breezy.

---

### Post by MasterC on 2005-12-04
another question- about how long should the upgrade take?

---

### Post by aysiu on 2005-12-04
[QUOTE=MasterC]another question- about how long should the upgrade take?[/QUOTE] Forty minutes on broadband...? Who knows how long on dial-up?

---

### Post by MasterC on 2005-12-04
[QUOTE=aysiu]Forty minutes on broadband...? Who knows how long on dial-up?[/QUOTE]

Ha! You were right! It took 42 minutes!

Now that it's finished, I got two errors:

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

and 

Errors were encountered while processing:
 /var/cache/apt/archives/firefox-gnome-support_1.0.7-0ubuntu20_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

What do those me, and how can I fix them? Thanks for all you help, aysiu!

---

### Post by aysiu on 2005-12-04
If you look back at post #4, I did say I had issues with locale settings after upgrading. Looks as if you did, too. There probably is a fix for that somewhere here [if you poke around a bit.](http://www.google.com/search?hl=en&q=perl%3A+warning%3A+Falling+back+to+the+standard+locale+%28%22C%22%29+site%3Aubuntuforums.org&btnG=Google+Search) I just did a clean reinstall of Breezy.

---

### Post by MasterC on 2005-12-04
sorry it took me so long to respond, but i tried a clean reinstall, and it worked fine. but, i can not connect to the internet at all. and i can't run the terminal as root. arrgh... maybe i'll go back to warty!

---

### Post by aysiu on 2005-12-04
[QUOTE=MasterC]i can not connect to the internet at all. [/quote] Have you tried System > Administration > Networking > Eth0 > Properties > DHCP?

> and i can't run the terminal as root. Go to Applications > System Tools > Applications Menu Editor

Click on System Tools on the left side, and then check the box for Root Terminal on the right side.

---

### Post by MasterC on 2005-12-04
[QUOTE=aysiu]Have you tried System > Administration > Networking > Eth0 > Properties > DHCP?

 Go to Applications > System Tools > Applications Menu Editor

Click on System Tools on the left side, and then check the box for Root Terminal on the right side.[/QUOTE]

okay, i'll go try those! thanks a ton!

edit: i just realized this... i'm using a wireless connection, so instead of Eth0, should I go to Ath0 (i think that stand for Athos, becuase that's what my card is...)

---

