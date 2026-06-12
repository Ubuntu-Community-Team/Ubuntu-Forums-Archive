---
title: "(Pentablet_drivers) XP Pen Drivers for Linux"
date: 2018-09-21
forum: Installation &amp; Upgrades
---

### Post by janpialbarran on 2018-09-21
How could I install the Pentablet_Driver for linux? 
I have a XP Pen Deco 01 graphic tablet and I got Ubuntu 18.04.
I can use the tablet, it works perfectly well but I need to install Pentablet so I can customize the bottoms and the stylus funtions. 
I downloaded the package succesfully but I can't figure out the way to install it. 

Does anyone had the same problem and knows how to solve it? 

Here is the Pentablet  link---> [https://www.xp-pen.com/download/index/cid/36.html](https://www.xp-pen.com/download/index/cid/36.html)

---

### Post by Holger_Gehrke on 2018-09-21
It's an archive file (tar.gz). Unpack it wherever you want and execute the shell script (Pentablet_Driver.sh). Don't call the executable which is also in the archive directly, the script sets LD_LIBRARY_PATH to the 'lib' directory from the archive which contains some libraries the program needs.

Holger

---

### Post by janpialbarran on 2018-09-21
Thank you Holger for answering. 
So far I have unpacked the archive but when I try to execute the Pentablet_Driver.sh the following message shows up:

--Don't know how to handle 'file:///home/name/Downloads/Linux_Pentablet_V1.2.3/Pentablet_Driver.sh'--

I don't know what goes wrong... could it be the package is broken or something?

---

### Post by Holger_Gehrke on 2018-09-22
The package is not really broken, but there's a small problem: the script and the program aren't set executable. Open a terminal and enter:```
cd ~/Downloads/Linux_Pentablet_V1.2.3/
chmod +x Pentablet_Driver.sh Pentablet_Driver
./Pentablet_Driver.sh
```
(change to the directory with the driver, set the executable bit for the two files, execute the script)
If you want to start the Driver from your Desktop Environment, you'll have to create a '.desktop' file for it and put it in '~/.local/share/applications/'. Further explanations for this can be found in the [wiki]("https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles") (a bit older and mainly for Unity but most of it still applies, no matter what Desktop you use) and in several threads here on the forum.

Holger

---

### Post by janpialbarran on 2018-09-22
I really thank you, it worked!

---

### Post by cpt-blueberry on 2018-09-29
Hello,
Thanks a lot for this post. I still have problems, does anyone knows a solution to this?

For me the files "Pentablet_Driver.sh" and "Pentablet_Driver" are already executable but when i execute "Pentablet_Driver.sh" this happens : 
```

cpt_blueberry@UbuntuOne:~/Desktop/Files/Linux_Pentablet_V1.2.3$ ./Pentablet_Driver.sh
cpt_blueberry@UbuntuOne:~/Desktop/Files/Linux_Pentablet_V1.2.3$ 

```

So actually it happens nothing as you can see. And if i try to execute the other file this happens : 
```

cpt_blueberry@UbuntuOne:~/Desktop/Files/Linux_Pentablet_V1.2.3$ ./Pentablet_Driver
./Pentablet_Driver: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5: version `Qt_5.10' not found (required by ./Pentablet_Driver)

```

---

### Post by eliterdaboss on 2018-12-04
> **cpt-blueberry said:**
> Hello,
Thanks a lot for this post. I still have problems, does anyone knows a solution to this?

For me the files "Pentablet_Driver.sh" and "Pentablet_Driver" are already executable but when i execute "Pentablet_Driver.sh" this happens : 
```

cpt_blueberry@UbuntuOne:~/Desktop/Files/Linux_Pentablet_V1.2.3$ ./Pentablet_Driver.sh
cpt_blueberry@UbuntuOne:~/Desktop/Files/Linux_Pentablet_V1.2.3$ 

```

So actually it happens nothing as you can see. And if i try to execute the other file this happens : 
```

cpt_blueberry@UbuntuOne:~/Desktop/Files/Linux_Pentablet_V1.2.3$ ./Pentablet_Driver
./Pentablet_Driver: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5: version `Qt_5.10' not found (required by ./Pentablet_Driver)

```
I am having the same issue too! Anyone have a solution?

---

### Post by cpt-blueberry on 2019-05-05
Well I've got a solution to that Qt Problem.

Just go to ***/etc/ld.so.conf.d*** and create a file (what ever name you like) but it should end with .conf like --> ***pentablet_qt_driver.conf***
Than edit the file and write inside, the directory of your /lib folder which is inside of your Pentablets Folder like --> ***/home/$USER/Linux_Pentablet_V1.2.5/lib***

Save the file and do this in the terminal: 
```
ldconfig
```

That will tell system where to look for libraries. But unfortunately i am stuck with another ****** Problem. Every time I execute the **Pentablet_Driver.sh** (with sudo). I get this message:

```
QStandardPaths: XDG_RUNTIME_DIR not set, defaulting to '/tmp/runtime-root'
```

:confused: it would be nice if anyone had a solution to that which he/she were interested to share.

---

