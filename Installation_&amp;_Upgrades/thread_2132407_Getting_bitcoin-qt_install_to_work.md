---
title: "Getting bitcoin-qt install to work"
date: 2013-04-04
forum: Installation &amp; Upgrades
---

### Post by Mark Lytle on 2013-04-04
I have followed the intructions here to install bitcoin-qt on Ubuntu 12.04:

[http://www.distrogeeks.com/install-bitcoin-qt-ubuntu/]("http://www.distrogeeks.com/install-bitcoin-qt-ubuntu/")

which are:

sudo apt-add-repository ppa:bitcoin/bitcoin

sudo apt-get update

sudo apt-get install bitcoin-qt

Everything seemed to go normally, but from the terminal, typing bitcoin-qt, it attempted to initailize, but said wallet corrupted.
It recommended to delete everything from the installed directory but wallet.dat.

On performing a whereis on bitcoin-qt, I got this:

bitcoin-qt: /usr/bin/bitcoin-qt /usr/bin/X11/bitcoin-qt

Seems redundant if nothing else, and I'm clearly not going to delete my X11 directory, a lot of stuff is in there.

Anyone have any ideas how to proceed?    Thanks in advance!

---

### Post by superdaveozzborn on 2013-04-04
1. open Nautilus file manager and make sure you are in your home directory.
2. Press (CTRL-h) to show hidden files.
3. you will see a ".bitcoin" folder. inside that is the file "wallet.dat".
4. copy it to your desktop and then clean out the ".bitcoin" folder by deleting every thing inside. 
5. restart bitcoin-qt and it will recreate everything needed and begin to download the chain info. This will take quite some time depending on your internet connection. can be several minuts to hours.
6. once you see the GUI is fully updated. close it, "copy" your "wallet.dat" file back to the ".bitcoin" folder in your home directory. 

restart bitcoin-qt and all should be fine.

also it would not hurt to keep a copy of the wallet.dat file on a thumb drive for safe keeping. just in case.......

Hope this helps.
feel free to contact me about any of my posts in the future.

---

