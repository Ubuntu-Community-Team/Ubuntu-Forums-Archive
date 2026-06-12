---
title: "Problems installing adobe flash player"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by daveyhairbear on 2008-10-25
I'm having probs installing adobe flash...

If I go to the "BBC news" website or "Youface" or whatever, I get an error message and a link to install Flash. Clicking on the link takes me direct ly to the correct page on the Adobe website...

I can download and install ".deb for Ubuntu 8.04" apparently successfully. However, if I subsequently re-visit flash enabled page it still tells me I don't have a flash player installed (Despite it appearing in the package manager!!).

The adobe page also gives the option to download and install "APT for Ubuntu 8.04". However, selecting this option gives an error message that the file cannot be found on the Adobe website!

My question is: How do I go about downloading/installing flash player on Ubuntu 8.04...?

---

### Post by cantormath on 2008-10-25
Howto:
[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron-p4](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron-p4)
scroll down to 
**6.2.4 Adobe Flash Player**

Uninstall the deb you installed and Install this
flashplugin-nonfree

Note:
Some packages like the Adobe Reader are not available in the standard-repositories. The easiest way to make such packages available to your system is to add the medibuntu repository. If you want to add this repository open a terminal ...
 ... import the repository ...
 ```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
``` ... import the gpg-key and update your package-list.
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
 
```

---

### Post by Mark224 on 2008-10-25
I had the same problem.  The plugin f
rom Adobe did not work for me.   flashplugin-nonfree was the solution/

---

