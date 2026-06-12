---
title: "Midori on Intrepid"
date: 2008-09-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Sef on 2008-09-13
I got the howto from [Ubuntu Geek's blog]("http://www.ubuntugeek.com/midori-a-lightweight-web-browser.html") (just changed gutsy to intrepid):

> Install Midori Web Browser in ubuntu


 Open your apt sources.list file for editing with the following terminal command:


 ```
gksudo gedit /etc/apt/sources.list
```


 Add the following two lines to the bottom of the file


 deb [http://ppa.launchpad.net/stemp/ubuntu](http://ppa.launchpad.net/stemp/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/stemp/ubuntu](http://ppa.launchpad.net/stemp/ubuntu) intrepid main


 Save and exit the file


 issue the following terminal command to update apt:


 ```
sudo aptitude update
```


 Still in the terminal, enter the following command to install the package:


 ```
sudo aptitude install midori
```


 This will complete the midori web browser installation.


---

### Post by ShirishAg75 on 2008-09-13
That ppa does more than just midori, it also does 

swfdec & webkit with their associated libraries.

---

### Post by olskar on 2008-09-13
A small typo, deb [http://ppa.launchpad.net/stemp/ubuntu](http://ppa.launchpad.net/stemp/ubuntu) intepid main should be deb [http://ppa.launchpad.net/stemp/ubuntu](http://ppa.launchpad.net/stemp/ubuntu) intrepid main :)

It segfaulted for me on a lot of pages but it felt fast and nice

---

### Post by plun on 2008-09-13
To avoid any problem....

PPA
[https://launchpad.net/~stemp/+archive](https://launchpad.net/~stemp/+archive)

About Midori
[http://www.twotoasts.de/index.php?/pages/midori_summary.html](http://www.twotoasts.de/index.php?/pages/midori_summary.html)


Thanks Stephane !  Midori is fast as Gooogle Chrome, nice !

Also swfdec 0.8... testing !

:)

---

### Post by Sef on 2008-09-13
> A small typo, deb [http://ppa.launchpad.net/stemp/ubuntu](http://ppa.launchpad.net/stemp/ubuntu) intepid main should be deb [http://ppa.launchpad.net/stemp/ubuntu](http://ppa.launchpad.net/stemp/ubuntu) intrepid main 

It segfaulted for me on a lot of pages but it felt fast and nice.

Thank you for catching that error.

---

### Post by 2cute4u on 2008-10-21
Midori is out with a new version 0.1, but Stepanie hasn't updated her ppa since mid September.   Is there another repository, that has the most up to date versions, of Webkit and Midori?

---

