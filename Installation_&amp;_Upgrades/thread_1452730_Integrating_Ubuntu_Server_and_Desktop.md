---
title: "Integrating Ubuntu Server and Desktop"
date: 2010-04-12
forum: Installation &amp; Upgrades
---

### Post by kdev10 on 2010-04-12
[FONT=Comic Sans MS][SIZE=4]Hi Everyone , 

I have installed Ubuntu Server on my Laptop , i know i can download the Ubuntu Desktop package and use Ubuntu but is it possible to install the package using the Ubuntu 9.10 CD or DVD ? , rather than downloading the package since internet is too slow for me. If so please guide me. 

Thanks .

Dev
[/SIZE][/FONT]

---

### Post by Calmor on 2010-04-12
You'll have to forgive me as I don't have a Ubuntu machine in front of me.

If you have Ubuntu Server 9.10 installed and an Ubuntu Desktop 9.10 CD (both of the same architecture, 32-bit or 64-bit), you should be able to use the desktop CD to install the Desktop packages.

You can then edit your /etc/apt/sources.list (or sources.lst?) file and uncomment the CD lines (should be near the top).  To ensure you use the CD, you might want to disconnect from the internet, but my understanding is that it uses the first one it finds that has that package.  

You'll have to rebuild your package list after you change the sources file, though I forget how to do that off the top of my head (instructions may be in the sources.list file).

Hope this helps

---

