---
title: "Trying to upgrade to Karmic"
date: 2009-09-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2009-09-24
When I try and upgrade to karmic I am presented with: Unable to load file '/usr/share/gnome-panel/glade/panel-run-dialog.glade'.

Any ideas so I can safely upgrade?

---

### Post by BAMF1501 on 2009-09-24
Make sure the APT repository is updated:
 [INDENT]sudo apt-get update
[/INDENT] Make sure Update Manager is installed and up to date (which it should be):
 [INDENT]sudo apt-get install update-manager
[/INDENT] Now run the Update Manager from Terminal:
 [INDENT]sudo update-manager -d
[/INDENT] You will see an option “New distribution release ‘9.10&#8242; is available”. Click the Upgrade button to upgrade and follow the prompts to upgrade your distribution.

---

### Post by sports fan Matt on 2009-09-24
I thought I'd see that but to no avail.  I updated my software sources to karmic but no go as well.  
Edit: Im running karmic..Guess I didnt see the new human theme..:lolflag:

---

