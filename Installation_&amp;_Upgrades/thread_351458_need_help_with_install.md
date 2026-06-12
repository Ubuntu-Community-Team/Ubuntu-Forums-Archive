---
title: "need help with install"
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by crazyone on 2007-02-02
im new to linux but i know a few things so i went and wanted to try the server install and after i did that and trying it for a few days i didnt liek it to much and prefered to use the desktop ferson for my server for now. nwo that i am trying to install the desktop again i keep getting the server install screen for the first part and if i move all the parrts to a diferent mobo and cpu it gives me the normal install screen for the desktop install.is the anyway to fix the mobo so it doesnt have the server install screen anymore.thanks for the help. and im trying to install edgy on both install disks.

---

### Post by seshomaru samma on 2007-02-02
Sorry but your post is not that clear:
can you tell us the specs of your machine(/s)
also, how many CPU's and motherboards are involved in the story?

what do you mean by "move all the parrts to a diferent mobo and cpu"?
do you mean you put the hard disc in a different box? why would you do that?

generally , when you fresh install an OS can format the discs so you will not get any former OS remains
a new desktop install should wipe out the old server install.
you can add a desktop environment to a server install and get the same results 

please give some more details and we will help you.

---

### Post by crazyone on 2007-02-02
what i ment by movied all parts to differnt mobo and cpu was that i took the cd room sata controller video card adn hdds to my main pc to see if it was just on that machine which it was.i did that just to see if it was the on the hdds or the mobo for some odd reason.
my specs are
server:
amd sempron 2200+ socket a
maxtor 200gb sata hdd
2 40gb wd hdds
512mb ram 
pc chips m848a rev 2.1
dimond fire 1k pro 64mb video card
 SYBA SD-SATA-4P PCI SATA Controller Card
300watt psu
my main 
dfi lanparty ultra-d nf4
sapphire ati x1300xt 512mb pci-x
maxtor 200gb hdd
light-on dvd rw
opteron 175
xfi extreme music
1gb ocz ram
550 antec he psu

i also tried a 6.4gb and 2 differnt 8.4gb hdds in the server adn they were wiped clean before trying and it still came up with the same screen.if it is posibile to do a regual install with the server screen do i just type in install or what? thanks for the help and hopw the new info helps out better

---

### Post by seshomaru samma on 2007-02-03
Sorry , but what do you mean by "server screen"?
Which CD are you using to install Ubuntu?
If you want a desktop install you just use the regular Ubuntu Cd and it will install the graphic environment and will allow you to wipe the HD clean (if you wish)
You can also add a graphic envoronment to a server install 
For example if you run these commands on your server you will get a very basic (fluxbox) graphic environment:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install x-window-system-core xserver-xorg
sudo apt-get install fluxbox 
sudo apt-get install xterm
sudo apt-get install xmms
sudo apt-get install gaim
sudo apt-get install firefox
sudo apt-get install abiword 
sudo apt-get install xpdf
```
I would recommand a fresh install though

---

