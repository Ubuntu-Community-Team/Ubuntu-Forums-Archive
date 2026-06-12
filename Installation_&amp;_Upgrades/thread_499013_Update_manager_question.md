---
title: "Update manager question"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by Gooorn on 2007-07-12
Hello.

I'm sorry if this is reposted Q but I didn't find it so far. Well, I'm having 1 Ubuntu Server machine and 5 Ubuntu Desktop laptops in my consulting company and I want to know is there a way to set this configuration like this:

1. All updates (using Update Manager) are coming only to the Ubuntu Server machine
2. Every laptop is automatically updated from the server when it's connected to the LAN.

I'm hoping that this could work without making my server Ubuntu Archive server or something.

Thanx in advance,

Sinisa Perovic

---

### Post by silverdarkness on 2007-07-12
sorry this post was in the wrong place

---

### Post by fishpie on 2007-07-12
Hi,

you can use a program called apt-cacher on your server. You then need to change the apt repositories on the laptops so that they update from the server. When a laptop requests a package from the server apt-cacher will either send a copy of the package from the cache to the laptop, or if the cache does not contain an up to date copy of the package apt-cacher will download the package from the ubuntu repositories and store the package in the cache so that It doesn't need to be downloaded again. There is an apt-cacher tutorial at [http://ubuntu-tutorials.com/2007/01/08/save-bandwidth-during-updates-with-apt-cacher-ubuntu-610/]("http://ubuntu-tutorials.com/2007/01/08/save-bandwidth-during-updates-with-apt-cacher-ubuntu-610/")

---

### Post by Gooorn on 2007-07-12
Thank you very much for help me out.

---

