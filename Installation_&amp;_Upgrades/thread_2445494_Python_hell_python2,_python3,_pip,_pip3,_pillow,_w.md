---
title: "Python hell: python2, python3, pip, pip3, pillow, wheel...HELP!"
date: 2020-06-15
forum: Installation &amp; Upgrades
---

### Post by johantonissen on 2020-06-15
Hi there everyone.

Over the past years I have had enormous problems Python package management. Because of the existence of python2.7 and python3.8 and their own versions of PIP etc I&#8217;ve run into a lot of installation problems. 

My problem here is that I don&#8217;t have a overview of package management. Therefore i&#8217;d like to ask some help here. Not for a general coding problem i&#8217;m having but rather advice on the &#8216;practical guidelines&#8217; on python management.

Im facing the following problems:

- How to manage python installations alongside eachother ?
- How should i best incorporate python dependencies in PATH ?
- How should i install packages for python2 and python3 alongside each other ?
- How should i best manage pip and pip3 installations ?

Whats happening now is that i&#8217;m trying to install pip package and i get an error. I google for the error and try to fix it. The problem here is that over time my python installations seem to become one big mess of spaghetti and more complex errors emerge.

I don&#8217;t know if its important but i&#8217;m using a lot of SBC&#8217;s like the tinkerboard S and Rockpi. I&#8217;m currently trying to install motioneye on my tinkerboard. Motioneye is python2 based requires pillow, and installation became a huge mess there. My tinkerboard S is running armbian based on Ubuntu 20. The reason i&#8217;m asking the question here is because i think my problems are a result of my lack of knowledge of linux because my knowledge self taught and therefore not very structured.

What am i looking for?

The internet is filled with a huge information database. I have however not found a nice website or post on the python management on ubuntu. I hope that you more experienced engineers can point me out to a good starting position to gain more insight into python package management.

Thank you in advance.

Johan

---

### Post by dragonfly41 on 2020-06-15
I would explore [miniconda]("https://docs.conda.io/en/latest/miniconda.html") to orchestrate your various python installations in different environments you can setup.

---

### Post by oldfred on 2020-06-15
With my new 20.04 install, I prevent any applications from installing python2. The one or two I like, I am currently just doing without. Almost everything is python3.
I have a program that I converted from python2 to python3 several years ago, so I do not really need python2 anymore.

See also this recent thread:
[https://ubuntuforums.org/showthread.php?t=2444887](https://ubuntuforums.org/showthread.php?t=2444887)

---

### Post by dragonfly41 on 2020-06-15
Unfortunately some apps the OP is playing with "[COLOR=#000000]Motioneye is python2 based" are still dependent on Python2.

At the risk of confusing OP I would go one step up the ladder of languages and explore what [HaXe.org]("https://haxe.org/") can offer.

HaXe is a high level transpiler which can generate python 3 .. or other languages .. from a common code base. But HaXe only supports Python3 today not Python2
It offers the option of transpiling into python3, C++ or other supported languages. i can generate Electron apps for example..[/COLOR]

---

