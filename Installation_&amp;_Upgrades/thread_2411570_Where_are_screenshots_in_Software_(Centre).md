---
title: "Where are screenshots in Software (Centre)?"
date: 2019-01-31
forum: Installation &amp; Upgrades
---

### Post by andremr on 2019-01-31
Hi.

Why I have no screenshot for most software in Software (Centre)?

Using Xubuntu 18.04.1. Even most known software, like Inkscape or Blender. I search or navigate, open the info page and... no screenshot. Only message "no screenshot provided".
I can put a sample screenshot here, but it is in my language (PT-BR).

I used Linux Mint before this Xubuntu install, and had images for almost all software.

It is a bug with my install?

---

### Post by andremr on 2019-02-09
well... anybody knows anything about plz?

---

### Post by #&amp;thj^% on 2019-02-09
Try this:
```
killall gnome-software
```
This kills the software running within the Software Center.

Next, you need to remove the gnome file software location &#8220;~/.local/share/gnome-software.&#8221; Do this by entering the following: 
```

sudo rm -rf ~/.local/share/gnome-software
```

If this seems scary, or you are afraid it will ruin your installation, _you can opt to avoid deletion by moving it to another location._ The Software Center will work fine either way.

---

### Post by andremr on 2019-02-23
I tried. No changes.

I wonder if those screenshots are visible to others, if its just issue with my system.

Take a look (my language is pt-br):
[ATTACH=CONFIG]282628[/ATTACH][ATTACH=CONFIG]282629[/ATTACH][ATTACH=CONFIG]282630[/ATTACH][ATTACH=CONFIG]282631[/ATTACH]

---

