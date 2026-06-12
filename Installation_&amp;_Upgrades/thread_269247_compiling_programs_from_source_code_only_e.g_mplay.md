---
title: "compiling programs from source code only e.g mplayer"
date: 2006-10-01
forum: Installation &amp; Upgrades
---

### Post by wigglezZA on 2006-10-01
Hi, I'm a very new ubuntu/linux user and don't know much about it. The problem i have is that i don't have an internet connection on my PC so i can't use reposistories to install new programs. I have acces to an internet connection though and i can download the source codes of the programs i want to install (e.g xmms, gnomebaker, vlc, mplayer). Can someone please explain to me how to compile and configure programs from source code only. some of them also have other plugins you must install with them, could you please also explain how to do this.

---

### Post by Dinerty on 2006-10-01
The most common method of compiling programs from source is:

```
sudo apt-get install build-essential
```

say you download a program to desktop, you would do this:

```
cd Desktop
```

then

```
 cd <name> 
```

then

```
./configure
```

then

```
make
```

then finally

```
sudo make install
```

Now if all goes well this should work, but don't be surprised if you get errors regarding missing dependecies (Files which are needed to make the program work). Most of the time these can be download from Synaptic Package Manager or google them. (Sometimes you might even have to install dependecies of dependices, gets very confusing then).

Without a internet connection it could be hard work.

If the program comes with a un-install script you can simply:

```
 make uninstall
```

Installing plugins can also be the same method as described above, best thing to do is download the progam/plugin and check for the docs, to see if it says any special install procedures.

Hope this helps

---

### Post by Kilz on 2006-10-01
> **wigglezZA said:**
> Hi, I'm a very new ubuntu/linux user and don't know much about it. The problem i have is that i don't have an internet connection on my PC so i can't use reposistories to install new programs. I have acces to an internet connection though and i can download the source codes of the programs i want to install (e.g xmms, gnomebaker, vlc, mplayer). Can someone please explain to me how to compile and configure programs from source code only. some of them also have other plugins you must install with them, could you please also explain how to do this.

You could just download the deb files from the [Ubuntu packages page]("http://packages.ubuntu.com/") and install them. It may be a little easier.

---

### Post by londonbabs on 2006-10-01
I also have the same problem, and even installing manually doesn't work because it fails on the dependencies, I'm going bonkers over this problem cos nothing worked out yet...
alternatively, have a look there:
[http://ubuntuforums.org/showthread.php?t=206692](http://ubuntuforums.org/showthread.php?t=206692)
or my own thread (although it doesn't sort much...) [http://ubuntuforums.org/showthread.php?t=268302](http://ubuntuforums.org/showthread.php?t=268302)
Hope you'll have better luck than I did so far !

---

### Post by wigglezZA on 2006-10-02
Thanks for the help but is there a way i can install the new packages/dependencies that i've downloaded using the Synaptic Package Maganager? Or maybe create local repositories with the packages/dependencies?

---

### Post by barrosz on 2006-10-02
if you have trouble with the dependencies, uninstall mplayer and do sudo apt-get build-dep mplayer, then you can compile it without worrying about dependencies.

---

