---
title: "Audacious problems. Confused."
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by Roasted on 2007-02-01
I got the repositories from this site.

[http://audacious-media-player.org/Downloads](http://audacious-media-player.org/Downloads)

I'm running edgy, and yes I got the right repositories. I saved my sources.list and did a "sudo apt-get install audacious" but it came back as "could not find packages." Whaaat??

---

### Post by Stochastic on 2007-02-01
after editing sources.list you have to run apt-get update to refresh your package list, then you can apt-get install

---

### Post by Roasted on 2007-02-01
Oh... wow... Thanks man. I should of known that.

---

### Post by Roasted on 2007-02-01
Soooooooooooo how do I fix this then?




jason@jason:~$ sudo apt-get install audacious
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  acroread-escript libotr2 python2.5 python2.5-minimal
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  audacious-plugins libasyncns0 libpulse0 libtagc0
Suggested packages:
  pulseaudio
Recommended packages:
  audacious-plugins-extra
The following NEW packages will be installed:
  audacious audacious-plugins libasyncns0 libpulse0 libtagc0
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 1534kB of archives.
After unpacking 3726kB of additional disk space will be used.
Do you want to continue [Y/n]? 
WARNING: The following packages cannot be authenticated!
  libasyncns0 libpulse0 audacious-plugins audacious
Install these packages without verification [y/N]? 
E: Some packages could not be authenticated
jason@jason:~$

---

### Post by Roasted on 2007-02-03
Just fixed it by installing it via synaptic.

When I marked audacious for installation, it auto-marked this other package for installation too. Think that could of been my problem? Should I of installed that package FIRST via terminal before installing Audacious itself? Is that why I had the broken package?

---

### Post by Theimon on 2007-02-03
Audacious needs its plugins to function properly, that's why Synaptic auto-selected other packages as well. No need to worry. The authentication error is something, in this case, you can ignore as well. The Audacious packages are safe.

---

### Post by Roasted on 2007-02-03
Yeah, just saying though, I wish I knew how to do everything via command line. Sometimes I think it's more fun to use the command line despite it's "blah" personna.

---

