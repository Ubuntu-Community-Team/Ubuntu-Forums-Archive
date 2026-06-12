---
title: "Need to backup xfce4-panel config?"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by SnickerSnack on 2010-12-31
I'm thinking of using a GIT repo to get version 4.7 of xfce4-panel, but I need to know if I need to backup any config files before removing version 4.6 through apt.  I have several panel buttons that I don't want input again (could easily take 30+ minutes of clicking).

I do realize that 4.7 will become stable on Jan 16, but that doesn't mean it will be available through apt.  If someone knows for sure whether it will be, or how I can find out, I'd like to know about it.

Thanks.

---

### Post by lithopsian on 2010-12-31
New versions can take a long time to appear in the main stable repository.  And by a long time I mean perhaps never!  Almost certainly you will be able to find a PPA if this is a significant release supported on your distro.

The settings on earlier versions were in ~/.config/xfce4.  That would be the most important thing to backup.

---

### Post by azertyh on 2010-12-31
hello,
i see all my launchers/buttons in ~/.config/xfce4/panel.
but i'm not sure that you can restore your buttons after backed up these files.

---

### Post by SnickerSnack on 2011-01-02
The information is stored there, but it doesn't appear to be read from there.  Changes made there aren't reflected in the panel after a restart, the files are just over-written with the old settings.

Thanks though.

---

