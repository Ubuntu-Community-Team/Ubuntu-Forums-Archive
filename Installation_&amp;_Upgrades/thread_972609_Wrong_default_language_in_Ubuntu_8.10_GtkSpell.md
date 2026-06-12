---
title: "Wrong default language in Ubuntu 8.10 GtkSpell"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by ilchymis on 2008-11-05
I've just completed a fresh installation of Ubuntu 8.10.  My locale is set to [FONT="Courier New"]en_US.UTF-8[/FONT], and Firefox and OpenOffice are both using the US English dictionaries for their spell check functions, but GtkSpell applications (Gajim, Text Editor, etc.) are defaulting to "English", which is distinct from the "English (United States)" option.  "English", as it turns out, means the Great Britain variety (even though there is a separate "English (United Kingdom)" option), wherein neighbors are neighbours, criticize is criticise, up is down, black is white, etc. ;)

Has anyone else seen this?  How can I make GtkSpell default to US English like my other spell checkers do?  Thanks in advance...

*EDIT: Just realized I posted this in the wrong forum, apologies...*

---

### Post by jointstereotype on 2008-12-26
I too have noticed this. Have you figured it out by any chance?

---

### Post by dutchthomas on 2010-12-22
Anyone still interested in this?  For the sake of google, I'll share my solution.

You can set your default spell checking language using the environmental variable LANG.

I don't use ubuntu so you'll have to refer to [_this guide_]("https://help.ubuntu.com/community/EnvironmentVariables") for help with setting environmental variables.  I guess you could put this in your bash profile.  Anyway, I don't think this is a problem on ubuntu anymore anyway.

In gentoo, you can set the variable in a file in /etc/env.d/* (hint: create your own file)

---

