---
title: "fortune"
date: 2011-08-05
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2011-08-05
if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)

i like to see a fortune when i open a new terminal...  slackware style...

```

sudo apt-get install fortune

```

```
cat >> $HOME/.bashrc << "EOF"
/usr/games/fortune
EOF

```

Sign here without admitting guilt.
mkultra [ ~ ]$ :P

you will need to install the fortune package and cookies package from the repository in synaptic.

[IMG]http://img828.imageshack.us/img828/9350/terminals.jpg[/IMG]

---

### Post by andrew.46 on 2011-08-05
I had at least 10 minutes of laughing by using the -o option with fortune, but be warned:

```

     -o    Choose only from potentially offensive aphorisms.  Please, please,
           please request a potentially offensive fortune if and only if you
           believe, deep down in your heart, that you are willing to be
           offended.  (And that if you are, you'll just quit using -o rather
           than give us grief about it, okay?)

```

Have fun :).

---

