---
title: "in 8GB USB with persistent mode with &quot;Universal-USB-Installer-1.9.7.7&quot;..."
date: 2017-04-01
forum: Installation &amp; Upgrades
---

### Post by spi2 on 2017-04-01
hello,


in 8GB USB with persistent mode with "Universal-USB-Installer-1.9.7.7" but I try and with "unetbootin-windows-625" I make bootable USB.


after boot I running in Terminal mode:
sudo apt-get update
sudo apt-get upgrade
after shutdown not boot again.
df -v is enough space...
I try upgrade and from graphical mode, but the same, not boot...


what the mistace?

---

### Post by sudodus on 2017-04-01
It is risky to run

```
sudo apt-get update
sudo apt-get upgrade
```

in a persistent live drive, because the casper-rw file for persistent might get full and it will break the system. Instead you should 'only' keep some crucial program packages up to date.

In order to keep a persistent live up to date, you can remove all files and directories from the casper-rw partition except **.../upper/home** and back it up somewhere else. Then you can create a new persistent live drive and restore the home directory to a corresponding location in the new drive. That will preserve user files and tweaks, but you have to reinstall the program packages that you have installed separately.

---

### Post by spi2 on 2017-04-01
I have create USB bootable from Windows 8.1 64 bit
also I have run
sudo apt-get update
sudo apt-get upgrade
but nothing...
I don't understand what can I do?

---

### Post by C.S.Cameron on 2017-04-01
The kernel is part of a read only file in a persistent install and can not be upgraded.
You can update, but this can quickly fill the casper-rw file.

---

### Post by spi2 on 2017-04-01
How in linux Mint about 1 year in 8Gb USB is upgraded without any problem and have many free spaces(also kernel)?

---

### Post by sudodus on 2017-04-01
You seem to have another problem (not that you have filled the casper-rw partition). But there is another 'typical' problem with persistent live systems - they are more sensitive to corruption after several updates compared to an installed system.

Even though I have created and used such systems for a long time, I keep the .../upper/home directory but clear the rest of the content in the casper-rw partition and start with a fresh system.

If you use mkusb, you will get two shellscript files 'backup' and 'restore' and it is a good idea to backup the system at regular internals (the content of the casper-rw partition). You can make your own scripts or use some other method and run your own backup.

---

