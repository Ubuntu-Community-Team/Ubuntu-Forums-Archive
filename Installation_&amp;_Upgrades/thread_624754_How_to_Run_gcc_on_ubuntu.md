---
title: "How to Run gcc on ubuntu?"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by kiuri on 2007-11-27
hey.. So I've been looking for a how to but can't find it anywhere, or maybe can't understand properly what everybody seems to bee saying..

I want to compile some c programs using the gcc compiler because I heard it was the best, so I've installed gcc, with build essential and also sudo apt-get install gcc..
I've searched for it in usr/bin and it is there..
My problem is How to Run it???

Do I open the terminal and start writing the program? How can I start using it ?

thanks for your help in advance.

---

### Post by finer recliner on 2007-11-27
if you have a file called "helloWorld.c"

you would open a terminal and cd to the directory your helloWorld.c file is and then type:
```

gcc helloWorld.c

```

after your program is compiled, you can run the executable with this command:
```

./a.out

```


that will get you started


for more help type the following in a terminal
```
man gcc
```

---

### Post by kiuri on 2007-11-27
Thank you!
where can I find this helloWorld.c file?
I've searched for it in the file system hd and it found only this files:
helloworld.js
helloworld.bsh
helloworld.jar
helloworld.java
helloworld.pyc
helloworld.py


not the .c one..
Is there anything else that I have to do?

---

### Post by finer recliner on 2007-11-27
there is no file called helloWorld.c

that was just meant as an example. you have to code the file yourself.

---

