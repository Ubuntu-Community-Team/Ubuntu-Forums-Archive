---
title: "ubuntu python hello world installed system wide"
date: 2012-02-15
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2012-02-15
i guess my university teaches python....  i know bash skillz

activate your terminal in god mode....

alt + f2

gksu gnome-terminal

run

then drop this block of code

```

cat > /usr/bin/helloworld << EOF
#!/usr/bin/python
print "Hello, World!"
EOF
chmod 755 /usr/bin/helloworld
exit

```

press enter to exit root mode.

now 

alt + f2

gnome-terminal

run

then type hello and hit tab to load world, then press enter.

echo $PATH shows /usr/bin is in the user path therefore we dont need a ./ to run it.  its marked as executable (via chmod 755 filename command)

man cat will print the manual for cat, and i use cat to encapsulate my system modifications.

i could write these as files that you download and ./filename to run modifications....

```

cat > $HOME/sudc <<EOF
#!/bin/bash
gksu date
echo "is the time and date loaded with gksu, and now im going to ping myself 5 times"
ping -c 5 localhost
EOF
chmod 755 $HOME/sudc

```

then ./sudc will ask you to do super user and then checks the date and pings localhost 5 times.

most scripting languages require escaping after commands, bash probably requires ; signs at the end of every command.

```

#!/bin/bash
gksu date;
echo "is the time and date loaded with gksu, and now im going to ping myself 5 times";
ping -c 5 localhost;

```

in other words also works....

---

