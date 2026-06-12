---
title: "installing a firefox/seamonkey kill/restore script"
date: 2011-09-07
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2011-09-07
if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)

alt + f2
run
```

gnome-terminal

```

then become super user to install the script system wide


(for firefox)

```

sudo su

```

```

cat > /usr/bin/killfirefox << "EOF"
ps -e | grep firefox | sed 's/\(.[0-9]*\).*/\1/' | xargs kill -n 9
firefox &
EOF
chmod 555 /usr/bin/killfirefox
exit

```

and then hit enter to exit root mode.

(for sea monkey)

```

sudo su

```

```

cat > /usr/bin/killseamonkey << "EOF"
ps -e | grep seamonkey | sed 's/\(.[0-9]*\).*/\1/' | xargs kill -n 9
seamonkey &
EOF
chmod 555 /usr/bin/killseamonkey
exit

```

and then hit enter to exit the sea monkey installing script

to use these scripts when firefox / seamonkey is frozen simply

alt + f2

run

```

killfirefox

```

or

```

killseamonkey

```

and a new instance of firefox or seamonkey will load

i find mplayer crashing heavily on my system from electric sheep, so im gonna install a mplayer kill command similar to these....

```

sudo su

```

```

cat > /usr/bin/killmplayer << "EOF"
ps -e | grep mplayer | sed 's/\(.[0-9]*\).*/\1/' | xargs kill -n 9
EOF
chmod 555 /usr/bin/killmplayer
exit

```

command now to kill mplayer

```

killmplayer

```

as you can see just replace the grep name and it will kill whatever process.  change the /usr/bin name to what ever the executable file name will be, and change permissions on the new file to make it so it can run.  to find process names to plug into this command run "ps aux"

---

