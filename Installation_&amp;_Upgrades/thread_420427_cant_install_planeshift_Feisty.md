---
title: "cant install planeshift Feisty"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by regor210 on 2007-04-23
just installed Feisty Kubuntu I cant intall PLaneshift.

sudo chmod a+x planeShift_CBV0.3.018.bin

sudo ./PlaneShift_CBV0.3.018.bin

the Planeshift installer starts then crashes giving me this (Segmentation fault (core dumped)

i tried down loading from 2 different sources with no luck.

it allways worked on Edgy.

---

### Post by regor210 on 2007-04-25
Ok here is the deal.
 planeshift can be install in text mode using this
 
 sudo chmod a+x PlaneShift_CBV0.3.018.bin
 
 sudo ./PlaneShift_CBV0.3.018.bin --mode text
 
 The bad news is, Don't put it in your /home/nameDir or it will mess up your permissions and it will not let you back in.

---

### Post by regor210 on 2007-04-25
./PlaneShift_CBV0.3.018.bin
 
 Still gives me a Segmentation fault (core dump).
 
 Using 
 
 ./PlaneShift_CBV0.3.018.bin --mode text 
 
 and installing planeshift in /home/"your name DIR"/planeshift
 
 is the way to go. Iordhebe is right!
 
 so to install planeshift use
 
 
 sudo chmod a+x PlaneShift_CBV0.3.018.bin 
 
 ./PlaneShift_CBV0.3.018.bin --mode text
 
 when the installer asks where to install it use
 
 /home/"your name DIR"/planeshift

do not use "sudo" ./planeshift.bin

---

### Post by Obsidian McNite on 2008-01-16
what i have always done is install to opt<===?
and i can never access folder
im trying it your way, and ill see what happens
if it works, THANK YOU

---

### Post by ginderhulk on 2008-07-01
can some one help me download this from the beginning starting from a making it executable or something like that

---

### Post by regor210 on 2008-07-02
These days I'm using Ubuntu Hardy and Gusty. But I still use the same install proses.  

Download Planeshift linux (64 bit): or Linux (32 bit): Into your home folder. you can find it here.
[http://www.planeshift.it/download.html](http://www.planeshift.it/download.html)

open a Terminal:   In Ubuntu goto Applications>Accessories>Terminal

Set your permissions:   type this command into the terminal minus the $. Note make sure the name is the same as you downloaded. 

$  sudo chmod a+x PlaneShift-v0.4.01-x64.bin

Start the installer: type this command into the terminal minus the $.Note make sure the name is the same as you downloaded. 
$ ./PlaneShift-v0.4.01-x64.bin

when asked for Installation Directory, I think it best to place it in your home folder. Not /opt. so I use /home/regor210/ . If your not sure of the name of your home folder, in Ubuntu goto Places>Home Folder. so you would use /home/your name/

when asked for System wide install No

when asked What Window Manager are you using? If your using Ubuntu select Gnome.

when asked Install menu Icons? select yes.

when asked create desktop shortcuts? select yes.

when asked Set Permissions? say no 

Hope this helped

---

