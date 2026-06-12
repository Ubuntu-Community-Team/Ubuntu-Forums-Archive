---
title: "installing offline packages"
date: 2021-07-21
forum: Installation &amp; Upgrades
---

### Post by mintmag on 2021-07-21
Since I like to work off the grid, I prefer to download my packages and install them offline. There are two ways of doing this and I'd like to know which is better and why.

 With Debian: dpkg -i *.deb

Or with apt copy the debs files to the cache and install as you normally world from the terminal.

---

### Post by him610 on 2021-07-21
In *synaptic*, there is an option to only download package files. 
I have never upgraded this way, but I assume you could install the packages whilst you were offline.

---

### Post by Impavidus on 2021-07-22
apt-get also has an option to only download the packages: -d or --download-only

To give a direct answer to the question: I would avoid the dpkg command here. It doesn't properly check the dependencies.

---

### Post by mIk3_08 on 2021-07-22
You can also used this GDebi Package Installer to run your *.deb package you download. It is more convenient, easier and more comfortable to use. This package installer also helps you add some dependencies if needed to your downloaded packages to run. 
I used this package installer for a long time and I haven't experience any difficulties so far. 
If your downloaded package needs more dependencies. You may download it at your own risk and run it. you can also run it directly via terminal if you want. 
Good Luck.

---

### Post by mintmag on 2021-07-22
Guys I'm only interested in these two methods.

---

