---
title: "Command to preform updates"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by -gabe-noob- on 2008-05-22
Hey guys I'm using open box and can't figure out how to update my system, it's on kubuntu base. 

I was wondering if I type sudo apt-get update will it preform the same thing as if I updated from the little icon thats usually on the gnome panel and stuff>

---

### Post by LaRoza on 2008-05-22
> **-gabe-noob- said:**
> Hey guys I'm using open box and can't figure out how to update my system, it's on kubuntu base. 

I was wondering if I type sudo apt-get update will it preform the same thing as if I updated from the little icon thats usually on the gnome panel and stuff>

```

sudo apt-get update #update lists
sudo apt-get upgrade #install updates
apt-cache search <terms> #search lists


```

Other useful options are clean and autoclean. man apt-get for more.

Useful aliases (define in .bashrc):

```

alias upgrade='sudo apt-get update && sudo apt-get upgrade && sudo apt-get autoclean'
alias install='sudo aptitude install'
alias search='apt-cache search'

```

Use:

```

~$search build-essential
build-essential - informational list of build-essential packages
dh-buildinfo - Debhelper addon to track package versions used to build a package
sbuild - Tool for building Debian binary packages from Debian sources
devscripts - Scripts to make the life of a Debian Package maintainer easier
~$


```

---

### Post by SunnyRabbiera on 2008-05-22
> **-gabe-noob- said:**
> Hey guys I'm using open box and can't figure out how to update my system, it's on kubuntu base. 

I was wondering if I type sudo apt-get update will it preform the same thing as if I updated from the little icon thats usually on the gnome panel and stuff>

Yup pretty much, also type in apt-get upgrade too if needed as that will install the upgrades you need

---

### Post by -gabe-noob- on 2008-05-22
Thanks guys, anyone know how I can change the color scheme in Openbox?

---

### Post by eriqjaffe on 2008-05-22
> **-gabe-noob- said:**
> Thanks guys, anyone know how I can change the color scheme in Openbox?There are two things that combine for the overall appearance of your windows.

To change the colors of Window Decorations, etc, use obconf, which is in the repos.

To change the appearance of window elements (backgrounds, text, etc), you can use gtk-chtheme, which is also is in the repos.

---

### Post by -gabe-noob- on 2008-05-22
thanks

---

### Post by K.Mandla on 2008-05-22
Moved to Installation and Upgrades.

---

### Post by -gabe-noob- on 2008-05-22
can I install themes into that gtk-chtheme thing you recomended
?

---

### Post by eriqjaffe on 2008-05-23
> **-gabe-noob- said:**
> can I install themes into that gtk-chtheme thing you recomended
?If you extract downloaded themes into /usr/share/themes (you need to be sudo to do that), gtk-chtheme should pick it up automatically.

---

### Post by urukrama on 2008-05-23
> **eriqjaffe said:**
> If you extract downloaded themes into /usr/share/themes (you need to be sudo to do that), gtk-chtheme should pick it up automatically.

Or to ~/.themes/

---

