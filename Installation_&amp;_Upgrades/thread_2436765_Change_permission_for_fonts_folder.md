---
title: "Change permission for fonts folder"
date: 2020-02-12
forum: Installation &amp; Upgrades
---

### Post by Donnie Love on 2020-02-12
How do I change permission for the fonts folder in Lubuntu 18.04?

---

### Post by CatKiller on 2020-02-13
Don't.

If you want to add a font, and you don't have the ability to put it in /usr/share/fonts, put it in ~/.fonts or ~/.local/share/fonts.

---

### Post by Impavidus on 2020-02-13
It's usually a bad idea to change permissions on files and directories whenever you hit a "permission denied".

There are three standard locations for fonts in Ubuntu.

The first is /usr/share/fonts. These are the system-wide fonts installed by the package manager. Only the root user can write there.

The second is /usr/local/share/fonts. These are the system-wide fonts not installed by the package manager. Ordinary users can't write there, but root and members of the group staff can. So system-wide installation of fonts isn't restricted to the root user only, but certain other users can get that right if the root user adds them to the staff group.

The third is ~/.local/share/fonts. These fonts are available only to the user in whose home directory they are installed.

This system isn't only used for fonts, but for many software packages.

---

