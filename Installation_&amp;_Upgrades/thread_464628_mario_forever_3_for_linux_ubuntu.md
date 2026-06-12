---
title: "mario forever 3 for linux ubuntu?"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by higashi on 2007-06-04
Hi, I found this game called "mario forever 3" for windows and I want to download it onto ubuntu. The problem is that I'm not really much of a gamer. I usually either play the games that come with my system or online games. Anyways, assume that I have no clue at all about anything on linux. I need to know how to download this game in full details. I need to know what programs I need, where to get them from, what type of file to download, how to install it, etc...
Thanks for your help :D

PS: you can find one place to download mario forever at [http://www.download.com/Mario-Forever/3000-7435_4-10344976.html](http://www.download.com/Mario-Forever/3000-7435_4-10344976.html)

---

### Post by cowkiller on 2007-06-05
Hi there higashi

Firstly, greetings for at least trying to get into linux. I hope it will be fine.

I would recommend you to install Automatix firstly. I assume that you have installed Ubuntu Feisty Fawn, so you will be able to install it easily with the [HowTo included in Automatix web]("http://www.getautomatix.com/wiki/index.php?title=Installation")

This program will allow you to easily install and configure several programs, codecs, drivers, etc. 
Once you run this program, in the "virtualization" tab you'll find a program called wine. This will allow  you to "emulate" Windows and run executables like the Mario installer. You will just have to right click on the executable and select  "open with wine"

Another easy way (if you don't wanna install Automatix)  would be:

- Open a command terminal then type:

>  sudo apt-get install wine

---

### Post by higashi on 2007-06-05
thanks, but I already tried to use wine. It worked fine and now it's on my desktop but I can't open it. When I downloaded it with wine, three things came onto my desktop: something called "mario forever", something called "mario forever.ink" and something called "mario worker.ink" (mario worker comes with mario forever). I tried to open them with wine but only the .ink ones let me select "open with wine". When I try to open them with wine, I get two error pop ups and then it opens for a second and automatically closes. What should I do?

PS: Just for the record, I'm not a beginner in linux... just the gaming. My dad got me addicted to linux a few years ago.

---

### Post by cowkiller on 2007-06-06
ahhh okok so you maybe know more than me, since I am a beginner indeed :D

Anyway I don't understand a few things. You say that you downloaded it with wine? I dunno how could it be done. You should have downloaded the .exe... or maybe try to rename Mario_forever for Mario_forever.exe
This may work... anyway, what's on the error popups you get?

The only thing you must right click & "open with wine" is the installer. Then Wine should make a new tab in your application menu with the programs installed.

Anyway, I had problems with wine too. Right now it works, but just for lazyness I use virtualbox with WinXp installed on it. (A bad solution, ok, but it works for me :roll: )

---

### Post by higashi on 2007-06-06
heh yeah I meant install... not download.

Anyways, pop up #1 says "Cannot use control \"ControlName\" registered at {8856F961-340A-11DO-A96B-00C04FD705A2} in this computer registry: Unable to find any programming interface."

pop up #2 says pretty much the same thing.

Do you maybe know of any programs for this other than wine?

---

