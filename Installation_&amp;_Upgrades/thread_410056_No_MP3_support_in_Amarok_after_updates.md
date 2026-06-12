---
title: "No MP3 support in Amarok after updates"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by Old Fart on 2007-04-15
Ever since the last round of updates, every time I start up Amarok  a diolog box pops up and says "Amarok cannot currently play mp3 files" . When I click the button that says "install mp3 support" nothing  happens. 

Everything worked properly before the updates, I have tried to reinstall the libxine-extracodecs but hat didn't help .  I am currently running Kubuntu Edgy on a core2 duo system with a SB Audigy sound card.

---

### Post by vjkeito on 2007-09-16
bump!

this is happening to me too since the latest update to the amarok backport.

i'm on feisty and after the update amarok began crashing compiz-fusion window decorations when I loaded it (amarok)

then out of the blue it stopped playing mp3's.  i get the same error message.  xine now won't play mp3's either

note: other music players not xine engine based work fine with mp3s


HHHHHEEEEEEEELLLLLLPPPPPP

---

### Post by jonsem.phooey on 2008-01-27
The instructions here appear to have worked (I have an old Gutsy install but the exact same problem).

[http://forums.debian.net/viewtopic.php?p=101555&highlight=&sid=197571c9f5f9e2a596d3a43264ac7f80](http://forums.debian.net/viewtopic.php?p=101555&highlight=&sid=197571c9f5f9e2a596d3a43264ac7f80)

Basically, delete the .xine directory from your home directory

then do 

sudo apt-get install libxine1 --reinstall

---

