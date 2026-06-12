---
title: "uninstalling a manual install without package manager"
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by jacob01 on 2007-07-20
i installed a couple of game manually with out the package manager or with apt -get, how would i uninstall them

---

### Post by dougfractal on 2007-07-20
> i installed a couple of game manually 

do you mean they were tar.gz's and you had to type sudo ./install.sh or something similar?
if you did the look for the uninstall.sh that came in the archive and type ```
cd ./gamefolder/
sudo ./uninstall.sh
```

If the games were only installed in your home the you will not need to sudo

---

### Post by ubanchaos on 2007-07-20
how do i manually install limewire its  tar.gz file

---

### Post by jacob01 on 2007-07-20
use frost wire its the same network but its like lime wire pro so its faster and has more features. the way i installed both lime wire and frost wire is go to the sight and download the .deb wich is installed through the package manager its alot easier that compiling from source

you might have the .deb right click the tar.gz and extract the files inside


no i got enemy territory and i need to uninstall, i installed it using a .sh file through the terminal

---

### Post by jacob01 on 2007-07-20
i also have a bunch of java versions that i installled with the terminal that are not detected in synaptic so they i can not uninstall it with a package manager i was wondering if i could uninstall those also

---

### Post by ubanchaos on 2007-07-20
thanks man 


happt ubuntuing

---

### Post by Gremlinzzz on 2007-07-20
did ya try
sudo apt-get autoremove nameofgame

---

### Post by jacob01 on 2007-07-20
no doesn't work like i said i didnt install it using and package manager i did it my self with a terminal so synaptic doesn't recognize it.

any other ideas

i was reading a thing were it said you could uninstall a package by going to the directory then typing make uninstall but it also said i had to enable that command

---

### Post by dougfractal on 2007-07-20
> make uninstall but it also said i had to enable that command

```
apt-get install make 
apt-get install gcc

```

If you compiled it i.e.  ```
./configure
make
sudo make install
```

then you could ```

sudo make uninstall
```

but im guessing you installed a binary and not source blob.

check the website that you got them from, or use a genral linux question.

last resort and BE CAREFUL an error/typo here could delete everything!!!!!!! "rm  -r /opt/nameofdirectory". you would have to be sudo to work.

```
rm --help
man rm

```

to find files of the game use
```
find / -name "nameofgame" 

```
may take a while as it will search every where that it has premission for.

---

