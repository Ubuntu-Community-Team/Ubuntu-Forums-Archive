---
title: "multi terminals"
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2011-11-12
enlightenment's terminal desktop is not correctly built up to pin to a docky dock.

alt + f2

gnome-terminal

run

```

sudo apt-get install konsole eterm lxterminal xfce4-terminal

```

go god mode....
```

sudo su

```

drop this block of code to fix things...

```

cat > /usr/share/applications/eterm.desktop << EOF
[Desktop Entry]
Encoding=UTF-8
Name=eterm
GenericName=Terminal
Comment=Use the command line
TryExec=Eterm
Exec=Eterm
Icon=utilities-terminal
Type=Application
Categories=GTK;Utility;TerminalEmulator;
EOF
exit

```

press enter to exit god mode

some other terminals i have recently found are VERY impressive quake doom half life style terminals....

yakuake is a kde (konsole based) terminal emulator that binds to F12 to make the terminal show up/go away...

guake is a gnome version of yakuake, same for f12, but im sure instead binding to gnome libraries and would be more appropriate to ubuntu....

tilda is probably my favorite of the 3, can adjust terminal size lightweight very xfce appropriate.  by default binds to F1 but you can reassign it to F12.

some more ok terminals are....

sakura, termit, roxterm (though it needs its colors re aranged)

---

