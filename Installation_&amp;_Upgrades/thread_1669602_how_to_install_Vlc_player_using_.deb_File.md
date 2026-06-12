---
title: "how to install Vlc player using .deb File"
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by ravi.krishan1986 on 2011-01-17
hi all.
i m new to ubuntu.
recently i installed ubuntu 9.10 to my home pc.
i dont have internet connection at home. and need to install vlc player
so i downloaded a .deb from cafe and tried to install it at home.
when i double clicked it.
it shows error.

dependency is not satisfiable.

Please help. how to resolve it.
Thanks.

---

### Post by sanderd17 on 2011-01-18
The power of ubuntu is in the packages. Programs don't have to ship all their code. They may depend on other parts of Ubuntu.

In this case, VLC needs an other part of Ubuntu which you didn't install. Can you do the following to see what's missing:

op a terminal. Press ALT+F2 and type
```

gnome-terminal

```
or search the terminal in the menu.

install the package with dpkg:
```

dpkg -i /path/to/your/vlc/file/vlc/deb

```
with the correct path to your file.

Then dpkg should output which packages you're missing. If that are a lot of packages, I should consider to connect your computer to the internet in some way. Otherwise, you can just download the packages as you have done with vlc and install them.

---

