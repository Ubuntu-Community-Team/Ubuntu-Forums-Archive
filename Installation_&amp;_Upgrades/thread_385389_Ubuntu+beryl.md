---
title: "Ubuntu+beryl"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by A-Pock on 2007-03-15
hello all, i'm a rookie at this linux world we live in and i'd like you pros to give me some instructions on how to do a couple of things.

So, my idea is this: install beryl on my ubuntu desktop.

here are my specs:
AMD ATHLON XP 1900+
768 DDR RAM
Nvidia Geforce4 FX 5200
Ubuntu 6.10 (fresh install)


What i would like is a step by step guide to install nvidia drivers (i had to install ubuntu 3 times because i couln't make drivers work, they said it didnt detect my graphics card), xgl, beryl and it's themes. If you can please refer the packages names i need and how i get them, terminal commands etc, i'm really noob:( 


i did some search on the foruns and i found a lot of info on how to install the drivers, though i really never made them work anyway and i cant figure out why :(


So now you guys know my specs and since i have ubuntu fresh installed i hope you guys can help.


thanks in adavance and sorry for any inconvinience.

---

### Post by shrini on 2007-03-15
You can try **[Envy]("http://albertomilone.com/nvidia_scripts1.html") **script which automates install of nvidia and ati drivers. It worked for me when all manual installs failed.

---

### Post by Slim Odds on 2007-03-15
For an FX 5200 based card, just download the latest driver package from NVidia and run it.

Then go to the beryl site an use the Ubuntu instructions. It's pretty easy.

---

### Post by A-Pock on 2007-03-15
i downloaded envy and used it, installed fine but i had the same problem i had when i installed manually, only this time the error was about my X not beeing the same version as the driver, and it asked me to make sure i have a compatible GPU (wich i know i do).

how do i solve this?

i re-installed ubuntu again :(, i dont know how to revert my driver installation so i have to re-install everytime i cant acess my graphic interface, can anyone help on this?

---

### Post by A-Pock on 2007-03-15
im doing all the updates now, i hope it will work after that :-|

---

### Post by errhec on 2007-03-15
You dont have to do the reinstall.
Youst run the :

sudo dpkg-reconfigure xserver-xorg

and chose the right driver for your graphic card.

LP

---

### Post by A-Pock on 2007-03-16
> **errhec said:**
> You dont have to do the reinstall.
Youst run the :

sudo dpkg-reconfigure xserver-xorg

and chose the right driver for your graphic card.

LP

thanks for that info, very useful =D> 


what about the xgl and beryl installation, can anyone help on that?

---

### Post by Slim Odds on 2007-03-16
> **A-Pock said:**
> thanks for that info, very useful =D> 


what about the xgl and beryl installation, can anyone help on that?

With the NVidia driver you don't need xgl.

---

### Post by A-Pock on 2007-03-16
> **Slim Odds said:**
> With the NVidia driver you don't need xgl.

so what do i need? i installed beryl from synaptic and it ran a first time, but i accidentaly ticked a "force xgl" option and beryl has been crashing ever since, is there anyway to roll back to the way it was before?

---

### Post by bulldog on 2007-03-16
Yes un-tick force-XGL I think.:) 
When started up,open the beryl-manager and choose metacity as your window manager instead of beryl.
Now change the things which aren't good and restart beryl as your window manager and see how it goes.

---

### Post by A-Pock on 2007-03-17
> **bulldog said:**
> Yes un-tick force-XGL I think.:) 
When started up,open the beryl-manager and choose metacity as your window manager instead of beryl.
Now change the things which aren't good and restart beryl as your window manager and see how it goes.

ok i've done that but one problem remains, when i use beryl as the window manager the titlebars dont show and i cant see anything resembling a theme (i applyed a vista theme).

am i doing something wrong?

---

