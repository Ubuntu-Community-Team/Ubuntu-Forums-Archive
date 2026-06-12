---
title: "Installing programs at all... *teh noob*"
date: 2005-05-26
forum: Installation &amp; Upgrades
---

### Post by karmah on 2005-05-26
OK, hi!!
Im a complete noob at linux in any form, and i need help installing programs.
I've tried to follow the readme:s or installing guides comming with the programs i dl but nothing works so far. And i've been searching this forum and not finding any help to install stuff.

I have downloaded RPM packages and source code stuff...

Thx in advance for any help! :)

---

### Post by XDevHald on 2005-05-26
[QUOTE=karmah]OK, hi!!
Im a complete noob at linux in any form, and i need help installing programs.
I've tried to follow the readme:s or installing guides comming with the programs i dl but nothing works so far. And i've been searching this forum and not finding any help to install stuff.

I have downloaded RPM packages and source code stuff...

Thx in advance for any help! :)[/QUOTE]
 Very simple :)

**System > Administration > Synaptic Package Manager**

Then once that is open, goto the **Search** button and type in the application that you would like to be installed, if you're not sure of what you would like, then simply scroll on the main catgory page of Synaptic and read through the applications of what each one of them do and see what you find is/could be useful to you.

Please post any other questions you might have and we'll be more than happpy to help you :)

Now as far as dpkg on .debs, follow f.prissons sudu commands and you'll be fine :)

---

### Post by f.prisson on 2005-05-26
The easiest way to install rpms is to convert them to deb files with```
sudo alien *.rpm
``` and then install them with ```
dpkg -i *.deb
``` If you have source code you have to compile and install it. There is always a readme or install text file delivered with source code which you have to follow. Generelly you install it with ```
./configure
make
sudo make install
```

---

### Post by karmah on 2005-05-26
yaay! :D thank you very much.
I will need to install a c++ compiler so i can compile the sourcecodes i believe...cuz ive tried the installation method you talked about (./configure make make install...such) but i get the error "Invalid or no c compiler found" or similar.
thx :)

---

### Post by bored2k on 2005-05-26
[QUOTE=karmah]yaay! :D thank you very much.
I will need to install a c++ compiler so i can compile the sourcecodes i believe...cuz ive tried the installation method you talked about (./configure make make install...such) but i get the error "Invalid or no c compiler found" or similar.
thx :)[/QUOTE]
 From the synaptic manager, install build-essential. Once compiling, if you get a "programX" not found and you know you have it, it's because it's looking for the development files, so you would search for "programX-dev".

---

### Post by karmah on 2005-05-26
I believe i installed the gcc compiler from synaptic, but it still says i dont have any c compiler :/

---

### Post by bored2k on 2005-05-26
[QUOTE=karmah]I believe i installed the gcc compiler from synaptic, but it still says i dont have any c compiler :/[/QUOTE]
 Install build-essential package.

---

### Post by karmah on 2005-05-26
more precisely:
"configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
configure failed for srclib/apr"

OK, Ill try it!
thx :)

---

### Post by karmah on 2005-05-26
Yay, thx dude its working....!!
sorry for being really nooby and helpless but i cant figure out how to run it >.<

---

### Post by bored2k on 2005-05-26
[QUOTE=karmah]Yay, thx dude its working....!!
sorry for being really nooby and helpless but i cant figure out how to run it >.<[/QUOTE]
 ./configure
make
sudo make install

There's a little file called INSTALL or README//

---

### Post by karmah on 2005-05-26
yeh, ive installed it all allright but the ultimate nooby thing about it is that i dont know how to run the program >.>

---

### Post by bored2k on 2005-05-26
[QUOTE=karmah]yeh, ive installed it all allright but the ultimate nooby thing about it is that i dont know how to run the program >.>[/QUOTE]
 What did you install, what dir ?

---

### Post by karmah on 2005-05-26
lol, not sure...i just ran default 
"
./configure
make
sudo make install
"
and never specified any folder that i know of... :P

---

### Post by bored2k on 2005-05-26
[QUOTE=karmah]lol, not sure...i just ran default 
"
./configure
make
sudo make install
"
and never specified any folder that i know of... :P[/QUOTE]
 Yeah but what are you trying to compile dude.

---

### Post by karmah on 2005-05-26
Apache HTTP server, ive compiled it allready... just dunno how to run it now

---

### Post by karmah on 2005-05-27
Nevermind ill figure it out!

---

### Post by bored2k on 2005-05-27
[QUOTE=karmah]Nevermind ill figure it out![/QUOTE]
 [Q: How to install Apache HTTP Server for HTTP (Web) Server service?](http://ubuntuguide.org/#apachehttpserver) ;)

---

### Post by karmah on 2005-05-27
Hah! ty dude, ive figured out how to install from source and with synaptec thx to you guys now..AND i can run programs !! (LOOOL) :D

---

### Post by XDevHald on 2005-05-27
[QUOTE=karmah]Hah! ty dude, ive figured out how to install from source and with synaptec thx to you guys now..AND i can run programs !! (LOOOL) :D[/QUOTE]
 Nice, glad you figured it out :D Things don't always come as easy like it does for others, patience is a virtue ;)

Job Well Done!

---

