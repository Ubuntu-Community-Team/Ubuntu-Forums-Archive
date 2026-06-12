---
title: "[SOLVED] How do I changhe text colour in CLI?"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by PryGuy on 2008-08-19
Good day! I'm just curious how do I change the text colour in command line (NOT the terminal in Gnome/KDE). Just curious...
Thank you!

---

### Post by Loaded.len on 2008-08-19
you mean like in a tty other than 7?

---

### Post by forger on 2008-08-19
1) Not all commands have coloured output, the .bashrc file in Ubuntu has some commented lines, I uncommented some:
```
gedit $HOME/.bashrc
```

The part for the colour, I have it as following:
```

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
#    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

```

edit:
2) You could also use grc: [http://gentoo-wiki.com/TIP_Colored_Command_Output_with_grc](http://gentoo-wiki.com/TIP_Colored_Command_Output_with_grc)

---

### Post by PryGuy on 2008-08-19
Thank you! ;)

---

