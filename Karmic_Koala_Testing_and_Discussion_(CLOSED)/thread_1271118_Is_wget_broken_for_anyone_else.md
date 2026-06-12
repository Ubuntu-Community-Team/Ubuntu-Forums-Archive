---
title: "Is wget broken for anyone else?"
date: 2009-09-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2009-09-20
I'm trying to use a shell script that I use to set up my system. For some strange reason, this shell script freezes Konsole, and if I do it in a TTY, it will freeze that too. On my laptop I don't have any problems. 

My script is very simplistic:

```
#!/bin/bash
# init

read -p "Press any key to add the Virtualbox Repository & GPG key..." arg
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -

echo "deb http://download.virtualbox.org/virtualbox/debian intrepid non-free" | sudo tee -a /etc/apt/sources.list

clear

read -p "Press any key to add the PlayonLinux Repository & GPG key..." arg
sudo wget http://deb.playonlinux.com/playonlinux_jaunty.list -O /etc/apt/sources.list.d/playonlinux.list

read -p "Press any key to add the Medibuntu repository & GPG key..." arg
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring;

read -p "Press any key to update the sources..." arg
sudo apt-get update 
```

After I run that script, Konsole will freeze and there isn't anything that can be done to kill the Konsole process. I have to reboot in order to get out of it. I'm assuming this is a bug in wget, or is something else freezing it?

---

### Post by hikaricore on 2009-09-20
Why don't you try the script line by line seeing which one freezes it.
I doubt wget is to blame.

---

### Post by jlacroix on 2009-09-20
> **hikaricore said:**
> Why don't you try the script line by line seeing which one freezes it.
I doubt wget is to blame.

Well, I did copy the first actual line (skipping the "read" line) and it did same thing. :(

This is very weird. Konsole shows up as "disk sleep" now.

---

