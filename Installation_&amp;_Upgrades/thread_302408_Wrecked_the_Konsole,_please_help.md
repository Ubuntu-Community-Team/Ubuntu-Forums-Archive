---
title: "Wrecked the Konsole, please help"
date: 2006-11-18
forum: Installation &amp; Upgrades
---

### Post by aniskasa on 2006-11-18
Problem: Something broke from the Konsole when tried to do [this]("http://www.kde-look.org/content/show.php?content=48303&forummode=2&forumpage=1&forumexplevel=99") (the Installation for Ubuntu/Debian -section)

Something: when changing the scheme in Settings -> Schema -> Transparent, (any transparent schema) the konsole just appears not transparent. In Yakuake I can change the schema to transparent (e.g. Transparent Konsole) and it works for the first tab, but if I open another, it just has a black background.

I tried to reinstall the Konsole with apt-get and compile the Konsole from not-patched (see the link above) source, didn't help.

I just can't figure out what I should and didn't find anything useful with the search.

edit:

Did some more searching and found [this]("https://launchpad.net/distros/ubuntu/+source/scim-qtimm/+bug/52999")

sudo aptitude remove scim-qtimm

and problem solved. Sorry for the idiocy.

---

