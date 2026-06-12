---
title: "shtools installation problem"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by farleysbeat on 2008-11-13
i am trying to install shtools ([http://www.ipgp.jussieu.fr/~wieczor/SHTOOLS/SHTOOLS.html](http://www.ipgp.jussieu.fr/~wieczor/SHTOOLS/SHTOOLS.html)) on my xubuntu 8.10 using the make all command. however i always get this error massage

         make: /bin/tcsh: Command not found
         make: *** [all] Error 127

any tips? thanks.

---

### Post by MaindotC on 2008-11-13
There's a package in the repositories called tcsh:
```
root@amd64-desktop:/home/amd64# apt-cache search tcsh
csh - Shell with C-like syntax, standard login shell on BSD systems
ledit - line editor for interactive programs
tcsh - TENEX C Shell, an enhanced version of Berkeley csh
tcsh-kanji - TENEX C Shell, transitional package
root@amd64-desktop:/home/amd64#

```
It looks to me like you need to install it.

```

apt-get install tcsh

```

---

### Post by farleysbeat on 2008-11-13
sir strAlan thanks for the reply. i did what you told...

i entered 

```
sudo apt-get install tcsh
```

but i got the following response

```
Reading package lists... Done
Reading dependency tree
Reading state information... Done
E: Couldn't find package tcsh

```

i then tried

```
sudo -i apt-get install tcsh
```

then got the result

```
/usr/bin/apt-get: /usr/bin/apt-get: cannot execute binary file
```

:confused:

---

### Post by MaindotC on 2008-11-13
Ubuntu has access to many different repositories (repo's) that contain these installation packages.  For whatever reason, you can decide to have access or deny access to different repo's.  In this case it seems you don't have access to the repo that houses the tcsh package - the universe repo.  Instead of using apt, it's probably better for you to use Synaptic Package Manager which is sort of a graphical user interface (gui) for package installation.

Go to System -> Administration -> Synaptic package manager.  In the Synaptic window, it should say File, Edit, Package, Settings, Help across the top of the window.  Click Settings -> Repositories.  You should be prompted with this window:
[[IMG]http://img227.imageshack.us/img227/8921/screenshotsoftwaresourcpi8.png[/IMG]](http://imageshack.us)
[[IMG]http://img227.imageshack.us/img227/screenshotsoftwaresourcpi8.png/1/w483.png[/IMG]](http://g.imageshack.us/img227/screenshotsoftwaresourcpi8.png/1/)

Click the box next to the "Universe" repository.  Click "Close".  You should then be prompted to "Reload" the repositories.  Click "Reload" to continue.  Then, click the button that says "Search" and enter the tcsh text.  You should see the following:
[[IMG]http://img148.imageshack.us/img148/1261/screenshotwq6.png[/IMG]](http://imageshack.us)
[[IMG]http://img148.imageshack.us/img148/screenshotwq6.png/1/w1024.png[/IMG]](http://g.imageshack.us/img148/screenshotwq6.png/1/)
Click the checkbox to the left of the package name and then click "Apply" which is the green checkbox at the top of the Synaptic window.  It may inform you that other packages will be installed as a result of installing the tcsh package (these are called "dependencies").  I advise you accept these changes.  Hope this helps!

---

### Post by farleysbeat on 2008-11-14
sir strAlan,

thank you for exerting much effort (you even posted screen shots to make it easier). i finally made it work thanks to your guidance. =)

---

### Post by MaindotC on 2008-11-14
It was my pleasure to help and I appreciate your thanks :)  Please mark the thread as "Solved" which I believe is under "Thread Tools" at the top of the page.

---

