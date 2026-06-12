---
title: "Kaffeine"
date: 2005-04-30
forum: Installation &amp; Upgrades
---

### Post by iammike on 2005-04-30
Pretty simple, I tried this through the GUI and through apt-get on the command line.  It installs Kaffeine with no errors, it also installs the Mozilla plug-in with no errors but it's not added to my drop down list and if I run a locate or try to find files through the GUI, it doesn't find anything on the hard drive with the name kaffeine.

I have the same exact problem trying to install k3b.

---

### Post by emuman on 2005-04-30
Control the package content with kpackage. Search for the package kaffeine and look at the file list. Is "/usr/bin/kaffeine" misssing? If yes, uninstall kaffeine ("apt-get remove kaffeine") and install it with dpkg:

dpkg -i /var/cache/apt/archives/kaffeine_0.6-0ubuntu4_i386.deb

---

### Post by iammike on 2005-04-30
[QUOTE=emuman]Control the package content with kpackage. Search for the package kaffeine and look at the file list. Is "/usr/bin/kaffeine" misssing? If yes, uninstall kaffeine ("apt-get remove kaffeine") and install it with dpkg:

dpkg -i /var/cache/apt/archives/kaffeine_0.6-0ubuntu4_i386.deb[/QUOTE]
 Tried the above with the same exact results.

The /usr/bin/kaffeine directory does not exist and a locate or search ran on the computer still finds nothing for kaffeine.

As far as apt is concerned, it installs just fine.

---

### Post by rajaiskandarshah on 2005-05-01
Create a launcher on the desktop for Kaffeine:

1. Right click on your Desktop, then select "Create Launcher"

2. In the Create Launcher window, enter a Name (e.g. Kaffeine) , the Command line "/usr/bin/kaffeine", and select an Icon.

You may also want to download and extract the essential codecs for Linux x86 from [http://www.mplayerhq.hu/homepage/index.html](http://www.mplayerhq.hu/homepage/index.html) to a /usr/lib/win32/ directory.

Can't live without the Kaffeine....

---

### Post by iammike on 2005-05-01
[QUOTE=rajaiskandarshah]Create a launcher on the desktop for Kaffeine:

1. Right click on your Desktop, then select "Create Launcher"

2. In the Create Launcher window, enter a Name (e.g. Kaffeine) , the Command line "/usr/bin/kaffeine", and select an Icon.

You may also want to download and extract the essential codecs for Linux x86 from [http://www.mplayerhq.hu/homepage/index.html](http://www.mplayerhq.hu/homepage/index.html) to a /usr/lib/win32/ directory.

Can't live without the Kaffeine....[/QUOTE]
 Yes, but the problem is that it isn't at /usr/bin/kaffeine, it isn't anywhere.  That's the weirdest part.  It installs without error yet none of the files are anywhere on the hard drive.

---

### Post by emuman on 2005-05-01
Please post the output of

dpkg --contents /var/cache/apt/archives/kaffeine_0.6-0ubuntu4_i386.deb

and

dpkg --info /var/cache/apt/archives/kaffeine_0.6-0ubuntu4_i386.deb

---

