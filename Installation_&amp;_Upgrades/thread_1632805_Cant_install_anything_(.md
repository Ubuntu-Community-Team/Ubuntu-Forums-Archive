---
title: "Cant install anything :("
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by wavey234 on 2010-11-28
hi guys

i recently got a server and it was going fantastically well, but just recently when i tried installing something using apt-get install .... ( i tried irssi, firefox/iceweseal, tightvncserver) it downloads asks for a questions i press y for yess then i get this error

E: Internal Error, Could not perform immediate configuration (2) on mountall

and then it doesnt install, this is really frustrating. 

any help would be much appreciated

thank you

---

### Post by sikander3786 on 2010-11-28
Welcome to the forums :-)

Please try and post the output of

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

---

### Post by ajgreeny on 2010-11-28
You say this is a server;  do you have a GUI desktop installed?

If not those applications will not install, or if they do, they will also bring with them the numerous packages required to enable a GUI, eg gnome.

---

### Post by wavey234 on 2010-11-28
i dont think i have GUI desktop installed, just ubuntu server. is it easy to install a GUI desktop??

the outputs to those commads: 

> 
root@ns213899:~# sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 311 not upgraded.



and the other one didnt produce any output

---

### Post by sikander3786 on 2010-11-28
> i dont think i have GUI desktop installed, just ubuntu server. is it easy to install a GUI desktop??

Do you really want to add a GUI? What are your hardware specs? What is this server intended for? If a critical one, I would advise to leave it as is...

Not too difficult I believe.

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get install ubuntu-desktop
```

---

### Post by ajgreeny on 2010-11-28
Well, with no desktop environment (gnome/kde/xfce/lxde etc etc) you will not get firefox/iceweasel to work as it's a graphical application, but I've no idea about the others you asked about.

---

### Post by wavey234 on 2010-11-28
well are there any other options to get firefox/iceweasl, also irssi i thought that was a command line irc, surely that should work?

i googled gui dekstop and i have heard people say its heavy on the cpu and a waste. would i be better off installling another distro. i only want gui to vnc into the server and use firefox and then irssi as well?



here are the specs



Processor                     Intel Xeon i7 W3520
4x 2.66+ GHz                          
8 Mb                                                               L2 -                                                                     QPI                                      4.8 GT/sec                                      [URL="http://www.intel.com/technology/turboboost/"]
[/URL]Architecture64 bits                               RAM                      12 GB DDR3                                 Hard disk                             2x 1500 GB - SATA2

---

### Post by sikander3786 on 2010-11-28
> Processor Intel Xeon i7 W3520
4x 2.66+ GHz
8 Mb L2 - QPI 4.8 GT/sec
Architecture64 bits RAM 12 GB DDR3 Hard disk 2x 1500 GB - SATA2

That is a damn powerful machine :P

What are you using it for currently? That should not feel the load of GUI at all :-)

Somebody else will have to reply the issue regarding vnc etc. No experience with that :-(

---

### Post by wavey234 on 2010-11-28
i use it for multiple things tbh, game server the main use.

i think that the vnc requires a gui, i hope lol

so if i install the gui it wont effect the performance of my server??

---

### Post by sikander3786 on 2010-11-28
> **wavey234 said:**
> i use it for multiple things tbh, game server the main use.

i think that the vnc requires a gui, i hope lol

so if i install the gui it wont effect the performance of my server??
I can't say exactly.... It is capable of doing something bad....

Please wait for some consensus to develop. Wait for some other replies.

---

### Post by wavey234 on 2010-11-28
someone told me about fluxbox so everything is fine now

thank you :D

its solved

---

