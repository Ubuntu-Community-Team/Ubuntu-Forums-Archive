---
title: "Help with Installation."
date: 2012-07-20
forum: Installation &amp; Upgrades
---

### Post by Madvayne on 2012-07-20
Hello. Im new with ubuntu. I downloaded Horst 3.0 from [http://br1.einfach.org/tech/horst/](http://br1.einfach.org/tech/horst/)
unzipped the Tar file into a folder Horst 3.0. There is one file called horst.sh inside it which needs to execute for installation but after trying everything i could i'm still not able to execute that script. Things ive tried are:

./configure
./horst.sh
sh horst.sh

From both root user and my own user. I keep getting this error.

./horst.sh: 16: ./horst.sh: horst: not found

Any help will be appreciated. I need to install this tool on Ubuntu 12.04 - 64 bit. Thank you.

---

### Post by dino99 on 2012-07-20
you need the required packages first for doing installation, like make & built-essential and to unzip like p7zip-rar

[http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-file](http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-file)

---

### Post by dino99 on 2012-07-20
no need dupes here :(

---

### Post by nothingspecial on 2012-07-20
From the README

> "horst" is just a simple tool, so "libncurses" is the only requirement (be sure
to install it's header files too). therefore building is as simple as typing:

	$ make

---

### Post by Madvayne on 2012-07-20
Thank you. I installed ncurses and I was able to build/make horst after that.

---

