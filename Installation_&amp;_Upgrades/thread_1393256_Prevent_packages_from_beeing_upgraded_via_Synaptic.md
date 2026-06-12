---
title: "Prevent packages from beeing upgraded via Synaptic/Aptitude Lock doesn't work"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by bbruecker on 2010-01-29
Hi,

As described in the title. I need to prevent a certain package (libportaudio2) from beeing ugraded.

[LIST=1]
[*]I manually installed an older version of package via **dpkg -i xxx**
[*]I started the synaptic gui, selected the package and choose "**lock**" (maybe transl. might be different because I use German version.
[*]After that I opened a console and made an upgdate (apt-get update ) and after that I wanted to install something via (**apt-get install blah**). libportaudio2 was in the list of packages to update! Also every **apt-get upgrade** brings me the libportaudio2 to the candidates for upgrades. 
[/LIST]
Result is that I'm not able to run an upgrade via sudo apt-get without loosing my old version.

After that I tryed to lock the package via **aptitude** with hold option. But that doesn't work either.

What is wrong?
Benjamin

---

### Post by ajgreeny on 2010-01-29
You can easily pin the package to the version you haveat the moment:-

To pin a package version add these lines to  /etc/apt/preferences: you may need to make this file yourself, as it is not available by default, with ```
gksudo gedit /etc/apt/preferences
```
Package: name                
Pin: version (number from repos)    
Pin-Priority: 1001

---

### Post by bbruecker on 2010-01-30
Hi ajgreeny, Good advice! Thx!

---

