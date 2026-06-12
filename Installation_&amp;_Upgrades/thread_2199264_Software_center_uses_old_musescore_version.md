---
title: "Software center uses old musescore version"
date: 2014-01-13
forum: Installation &amp; Upgrades
---

### Post by MaZaMo on 2014-01-13
I installed musescore from the software center in Ubuntu, but when I type ```
musescore -v
``` in terminal it shows that it's version 1.2, and the current version from the website is 1.3. The reason this is so important to me is because all the soundfonts for musescore are updated for the newer version and don't work on 1.2, and I depend on those soundfonts to write music. So I need the newer version.

I then uninstalled musescore and tried downloading it from the website, but that doesn't work because when you go to the download page ([http://musescore.org/en/download](http://musescore.org/en/download)) and open it in the software center it goes back to that same older version already in the software center! I really need the newer version! I don't want to have to go back to windows!

---

### Post by deadflowr on 2014-01-13
Go down the linked page you have and click on the [mscore-stable PPA]("https://launchpad.net/~mscore-ubuntu/+archive/mscore-stable") in the part for Ubuntu Backports.
Then follow the direction to add the ppa.

The software center only contains the version that is available in Ubuntu's default repository system.
Adding the ppa will allow you to install a newer version, as well as keep it up to date.

---

### Post by MaZaMo on 2014-01-13
Ok I added the PPA, but now how do I install musescore? Just from the software center again?

---

### Post by MaZaMo on 2014-01-13
It worked! I ran *musescore -v* again and it says version 1.3. Thank you!

---

### Post by deadflowr on 2014-01-13
I've found when you add the ppa for something, **IF **you have the Ubuntu version already installed, running the update manager will upgrade the version to the one in the ppa[B].
[/B]
Otherwise if you don't have the package already installed, then installing it will bring in the ppa package.

---

