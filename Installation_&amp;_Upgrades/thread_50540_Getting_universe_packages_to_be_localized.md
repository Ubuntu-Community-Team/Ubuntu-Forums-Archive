---
title: "Getting universe packages to be localized"
date: 2005-07-20
forum: Installation &amp; Upgrades
---

### Post by alci on 2005-07-20
Hi all,

I am trying to get a fully (french) localized Hoary install, including universe packages.
I have installed language-pack-fr, language-support-fr, language-pack-update-fr. This works great for main.

But packages from universe won't get translated :
- wxvlc
- multisync
- gtk-gnutella
- gramps (on amd64 only ! on i386, it's translated !?)

All these software is translated when installed on Debian Unstable, so I guess this problem is really related to the way Hoary handles localization... but I can't find the solution to this problem, that makes universe quite less usefull for non english speaking users.

Any hint ?

Thanks
Franck

---

### Post by alci on 2005-07-21
No one on this ?

Have you got for example Firestarter localized, anyone ?

---

### Post by alci on 2005-07-22
Doesn't anyone ahve the same problem ?

# locale

LANG=fr_FR.UTF-8
LC_CTYPE="fr_FR.UTF-8"
LC_NUMERIC="fr_FR.UTF-8"
LC_TIME="fr_FR.UTF-8"
LC_COLLATE="fr_FR.UTF-8"
LC_MONETARY="fr_FR.UTF-8"
LC_MESSAGES="fr_FR.UTF-8"
LC_PAPER="fr_FR.UTF-8"
LC_NAME="fr_FR.UTF-8"
LC_ADDRESS="fr_FR.UTF-8"
LC_TELEPHONE="fr_FR.UTF-8"
LC_MEASUREMENT="fr_FR.UTF-8"
LC_IDENTIFICATION="fr_FR.UTF-8"
LC_ALL=

Gnome is in french, openoffice as well, all app from main it seems,
but firestarter is in english, wxvlc as well,...

I have tried installing localeconf, with no result...

I am sure these apps at least are translated, as they were on Debian sid...

---

### Post by alci on 2005-07-25
Ok, I finally found the cause of all my problems...

I had installed a package called localepurge (from universe) which is supposed to save you disk space by purging unused locales...

It was set to preserve fr_FR, but most software have a fr (not fr_FR) translation. So localepurge was purging fr files, and my packages were in english.

I found the problem by searching in /usr/share/locale/fr/LC_MESSAGES/ for supposedly installed files, that where missing...

That was it !

Franck

---

### Post by eeried on 2005-07-25
Clever of you!

Now I have a question: if you use localpurge do you have to set "fr" files or "fr-FR" files not to be erased? -- sorry I didn't get that.

---

