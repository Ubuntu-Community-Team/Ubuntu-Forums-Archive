---
title: "need help urgently with install"
date: 2010-07-18
forum: Installation &amp; Upgrades
---

### Post by gamepanther on 2010-07-18
Hi i am relatively new to linux and need help installing this program which is vital to me remaining a ubuntu user [http://www.abgx360.net/download.html](http://www.abgx360.net/download.html)

ps im running 64-bit lucid lynx

---

### Post by theozzlives on 2010-07-18
Looks like you'll have to compile it. There should be a readme file, but it basically goes configure, make, make install. BE SURE to read the readme!!!

---

### Post by gamepanther on 2010-07-18
i can get as far as the make and then this shows up
fergal@fergal-laptop:~/Desktop/abgx360-1.0.2$ make
make all-am
make[1]: Entering directory `/home/fergal/Desktop/abgx360-1.0.2'
make[1]: Leaving directory `/home/fergal/Desktop/abgx360-1.0.2'
fergal@fergal-laptop:~/Desktop/abgx360-1.0.2$ sudo make install
[sudo] password for fergal: 
make[1]: Entering directory `/home/fergal/Desktop/abgx360-1.0.2'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
/usr/bin/install -c 'abgx360' '/usr/local/bin/abgx360'
make[1]: Nothing to be done for `install-data-am'.
make[1]: Leaving directory `/home/fergal/Desktop/abgx360-1.0.2'
fergal@fergal-laptop:~/Desktop/abgx360-1.0.2$ ^C

---

### Post by davidmohammed on 2010-07-18
have you been following this [step-by-step]("http://www.ubuntugeek.com/stealth-checking-xbox-360-games-with-abgx360-and-nautilus.html") guide to compile?

i.e. did you remember to run ./configure first?

---

### Post by digitalcitizenx on 2010-07-18
There is a tutorial on the website - [here's the link]("http://www.youtube.com/watch?v=oHg5SJYRHA0").

---

### Post by gamepanther on 2010-07-18
sorry noob mistake i did do it all correctly but i expected to find ab icon in applications but you had to either run from turmunal or download a gui and use it to run it. thanks very much my Ubuntu is now perfect

---

