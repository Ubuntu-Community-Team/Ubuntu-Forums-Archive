---
title: "Settings missing after upgrade to 20.04"
date: 2020-04-24
forum: Installation &amp; Upgrades
---

### Post by raikoss on 2020-04-24
Hello! 

Today I upgraded from Ubuntu 18.04 LTS to 20.04 LTS (no clean install), and it seemed to be pretty painless. Though, I am now missing the settings app and icon, gnome-control-center. After trying to apt get install gnome-control-center, I get an error with the following output: [https://pastebin.com/NGaCYNr9](https://pastebin.com/NGaCYNr9) 

Things I've already tried:
- sudo apt upgrade
- sudo apt update
- sudo apt install -f
- Restarting

To no avail. 

Can anyone help me? Much appreciated!

---

### Post by dino99 on 2020-04-24
Before dist-upgrading, have you disabled external sources (like ppa or private) and downgraded them to genuine versions ? (if necessary)
Be sure that > cat /etc/apt/sources.list only list Focal entries; if not use gedit to clean that file, then re-update.

Start cleaning the system via
> sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

then>  sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by raikoss on 2020-04-24
Yes, it seems all external sources are commented out, and all non-commented out are related to focal. 

I ran all commands, autoremove seemed to remove some packages but the others didn't output anything or stated no changes. Same error when trying to install it still

---

### Post by Claus7 on 2020-04-24
Hello,

from the messages you are getting, have you installed the packages: libsnmp35 and sane-utils? I have both of them installed in a 20.04 box. It seems in your case that these packages are not installed.

Regards!

---

### Post by raikoss on 2020-04-24
I tried to install sane-utils, and when trying to install the dependencies it wanted libsnmp35 as well. Tried that package, which down the line wanted the libsensors-config package, though a lot of packages would be deleted if I installed it, see pastebin: [https://pastebin.com/Ux3yqfVk](https://pastebin.com/Ux3yqfVk) I would guess removing a lot of these packages would probably break my system, as there's a lot of gnome packages there, though I'm not very experienced in Linux/Ubuntu yet. 

Thanks for the responses so far, appreciate it :)

---

### Post by Claus7 on 2020-04-25
Hello,

most of the packages, if not all, from pastebin, are necessary ones for the system to work. I would advice you to check what is going on from synaptic package manager and set aside the terminal for the time being. You might find out some broken packages or something that has caused this situation. Indeed the packages mentioned should not be removed, unless it is possible after that to re-install them anew, yet I would be very careful if I was in your shoes.

Regards!

---

### Post by mörgæs on 2020-04-25
Have you considered a clean install?

---

### Post by raikoss on 2020-04-27
It seems a clean install is looking most safe right now. Looked through synaptic a bit, though I don't think my issues are very solvable in this state. 

Thanks for the help, I'll do a clean install :)

---

### Post by mörgæs on 2020-04-27
Good, if it works then please mark the thread solved.

---

