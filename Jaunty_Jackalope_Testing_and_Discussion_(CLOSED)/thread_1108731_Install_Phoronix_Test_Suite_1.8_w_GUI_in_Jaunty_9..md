---
title: "Install Phoronix Test Suite 1.8 w/ GUI in Jaunty 9.04"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by budluva04 on 2009-03-28
Just spent a good chunk of my friday night (good thing I'm sick and have nothing better to do) installing the newest version of the Phoronix Test Suite. If your not familiar with this great app, read more about it here [http://www.phoronix-test-suite.com/]("http://www.phoronix-test-suite.com/")

Anyway...moving on...it seems that the newest version 1.8, which is in beta, has a GUI now. But it seemed to be a bit tricky, for me atleast to install, so I thought I would write this HOW-TO

THIS HOWTO WAS WRITTEN FOR THE COMMAND LINE
Applications -> Accesories -> Terminal

1) Download 

```
cd ~/
wget http://www.phoronix-test-suite.com/download.php?file=development/phoronix-test-suite-1.8.0b2
```

2) Move & Extract

```
mv phoronix-test-suite-1.8.0b2.tar.gz ~/
tar zxvf phoronix-test-suite-1.8.0b2.tar.gz
```

this will have created a directory in your home, ~/phoronix-test-suite

3) CD to directory

```
cd ~/phoronix-test-suite
```

4) Install

```
sudo ./install-sh
```

5) Verify

```

phoronix-test-suite version
```

this should output...
```
Phoronix Test Suite v1.8.0b2 (SELBU)

```
There now, Phoronix Test Suite 1.8 is installed...now onto the GUI install...the Phronix GUI requires PHP-GTK2 which is unmaintained and dated, I found out that a patch needs to be applied to get php-gtk to compile...moving on...

1) Download & Extract

```
cd ~/
wget http://gtk.php.net/do_download.php?download_file=php-gtk-2.0.1.tar.gz
tar zxvf php-gtk-2.0.1.tar.gz
```

2) Install required dependancies
```

sudo apt-get install build-essential php5-cli php5-dev libgtk2.0-dev libglade2-dev
```

3) Download & Apply Patch

```
cd php-gtk-2.0.1
wget http://www.opsat.net/temp/buildfix.diff

```
**NOTE This patch must be DOWNLOADED via wget or whatever method, you CAN NOT copy/paste this into a file you created.

```
patch -p1 < buildfix.diff
```

4) Compile

```
./buildconf
./configure
make
make install
```

5) Edit php.ini and load php-gtk module

```
sudo nano /etc/php5/cli/php.ini
```

Find "Dynamic Extensions" Section and add

```
extension=php_gtk2.so

```
6) Test

```
cd demos/
php phpgtk2-demo.php

```
There you have it!!! You now have the newest Phoronix Test Suite w/ GUI!!!

Now let's add a menu entry...

```
alacarte
```

Go to "System Tools" then "New Item"
Type: Application
Name: Phoronix Test Suite
Command: phoronix-test-suite gui

And there you have it folks!! ENJOY!!!

---

### Post by budluva04 on 2009-03-31
no one here into benchmarking or what? should i bother posting an install howto when this gets out of beta and released?

---

### Post by WSmart on 2009-04-06
It just released.  Did you see the comments on the Phoronix article?  Micheal mentions the edit.  

Your post was a great help.  I guess I missed something obvious on the PHP-GTK, like a read me file.  The ./buildconf was not working.  Definitely a bit tricky, as you say.

Thanks!

---

### Post by super.rad on 2009-04-06
> **budluva04 said:**
> should i bother posting an install howto when this gets out of beta and released?

Wouldn't be much need for a howto once it's released as they make a .deb for it (pretty sure it's in jaunty repo's aswell, can't check at the moment as I'm not on ubuntu)

---

### Post by WSmart on 2009-04-06
It's the new GUI that's the issue.  The regular command line stuff is OK.   PHP-GTK must be downloaded and compiled, and there's a patch for that, and there's a small edit that apparently is needed too.

---

### Post by MKdx on 2009-04-06
I've installed this deb package from unofficial repositories:
[_php5-gtk2_]("http://deb.orangearchive.net/pool/dists/hardy/main/php5-gtk2_2.0.1-1_i386.deb")

and the phoronix test suit worked fine without compiling.

---

### Post by rockorequin on 2009-04-06
Thanks, I couldn't find an amd64 deb file for php5-gtk2 so its build instructions were helpful.

---

### Post by super.rad on 2009-04-08
Didn't realise the gui needed an extra file which had to be built, thanks for the guide

---

