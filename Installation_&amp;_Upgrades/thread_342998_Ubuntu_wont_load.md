---
title: "Ubuntu wont load"
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by guaterickie on 2007-01-20
hi im havin trouble with ubuntu. i downloaded the new ubuntu from here: [https://wiki.ubuntu.com/install.exe/Prototype](https://wiki.ubuntu.com/install.exe/Prototype)

i installed it and rebooted my computer afterwards i chose ubuntu at the OS chooser (im running ubuntu and windows xp home) but then a black screen with the words UBUNTU in graphics and a load up thing came up but doesnt load after that it just stays there. i think this is the splash screen...am i right...it wont load after that.

---

### Post by guaterickie on 2007-01-20
its been thirty minutes doesnt anyone know how to resolve this?

---

### Post by NeoLithium on 2007-01-20
Ok, well I looked around on that page, and the only thing I can suggest is that you try to reconfigure your x-server since you didn't specifiy if there were any errors during the installation. 

Ctrl-Alt-F1, log in, and run: sudo dpkg-reconfigure xserver-xorg, then reboot

---

### Post by guaterickie on 2007-01-20
ermm i didnt understand a word of what you just said. im not familiar with all this OS lingo.

in english please

---

### Post by NeoLithium on 2007-01-20
Ctrl-Alt-F1.  Log in, then type:

 sudo dpkg-reconfigure xserver-xorg

just answer the options that you know the answers to, if you don't know an answer, use the default option; then reboot; and see if that helps.

---

### Post by guaterickie on 2007-01-20
ok this is going to be a stupid response but i know nothing. you want me to reboot and press Ctrl-Alt-F1 at the splash screen where it doesnt load or right now on my windows version (which doesnt work)

sorry man im new at this

---

### Post by NeoLithium on 2007-01-20
Well, the suggestion I posted was from some of hte FAQ's at the page you linked to; so I'm guessing that the Graphical Server isn't set up right; so when it's at the splash screen, Ctrl+Alt+F1 should take you to the command line mode; where you should be able to log in, and make the adjustments.

---

### Post by guaterickie on 2007-01-20
ah ok i rebooted real quick and tried it at the splash screen and i went to a black screen with some text i get before i get to the splash screen im guessing thats the command line mode but there is no log in before that so ill just try typing down what you suggested and see what happens.

---

### Post by guaterickie on 2007-01-20
hey neolithium i tried it and it didnt work i tried typing in what you suggested but that didnt do anything. it doesnt give me a log in screen or anything like a login all i get is a black screen with some text and a blinking cursor where i typed in sudo dpkg-reconfigure xserver-xorg

nothing happened. any more suggestions?

---

### Post by NeoLithium on 2007-01-20
Hmmm, I'm probably out of ideas, I'm used to the traditional instalation, and that method is basically a giant prototype, however intruguing in it's own right.  Since there's no data that could be lost; maybe try to reinstall to make sure that nothing happened on the last one?

---

### Post by puneit on 2007-01-20
Firstlly, Can you post your hardware configuration?

Secondly, I know you didn't intend to do it in the first place.. but since Ubuntu is not loading up, run a Live CD and then see if you can get it working.
There are some configurations, on which Ubuntu doesn't work that easily. Though I have never tried install.exe but then I guess it would have the same effect. So it is better to use the Live CD first

---

### Post by guaterickie on 2007-01-21
uhh harware configuration? u mean like the processor and RAM. idk

Compaq Deskpro
Intel Pentium III processor
792 MHz, 192 MB of RAM

---

