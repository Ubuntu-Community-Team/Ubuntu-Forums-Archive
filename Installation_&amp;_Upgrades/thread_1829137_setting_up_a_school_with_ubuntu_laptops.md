---
title: "setting up a school with ubuntu laptops"
date: 2011-08-20
forum: Installation &amp; Upgrades
---

### Post by jarrah-95 on 2011-08-20
the following is hypothetical for a school project, but it would be awesome to see implemented

the school i am at is looking to set up a 1:1 laptop ratio with all students (about 1100 of them) to do this i am looking at using Kubuntu based laptops ([http://zareason.com/shop/Teo-Pro-Netbook.html](http://zareason.com/shop/Teo-Pro-Netbook.html)). 
but i have a few questions as to how i should go about it. 
[LIST=1]
[*]what is the easiest way to set up user accounts (remembering there is 1100 students with seperate accounts?
[*]how would i go about mapping the network drive for each student? (it is a different folder on a HDD per student) 
[*]do you think the netbook linked above would be reasonable to do this? 
[*]How much of a learning curve is there between windows and kubuntu, and how would i train the whole school to use it?
[/LIST]

thanks, your help is much appreciated 

Jarrah

---

### Post by Basher101 on 2011-08-20
uhm...is kubuntu preinstalled? if not then the user accounts are created during the installation process. What you want is a server where they all have access to, but only on a single folder in there with pre-configured size. This can be achieved with permissions on the server so it should not be alot of a hassle. The netbook will be enough to run Kubuntu, although i would not recommend using KDE as it is quite the heavyweight of Desktop Environments. You should take a look at XFCE or LXDE as they are alot more lightweight and recourse friendly. The learning curve of linux altogether is nothing for everybody. All you need is a) time and b) the will not to dump it in the first 60 minutes as you realise "this is not windows". If all your students never used linux before, they should install it with Wubi first. This creates a virtual partition inside windows so it does not mess up anything, as in the actual installation process newbies are likeley to mess up. But wubi is just for "taking a look" at ubuntu. Should be enough to prepare your students

---

### Post by jarrah-95 on 2011-08-20
thanks,
they would be pre-installed at purchase, but the OS can be changed at the vendor. the main reason for kde is having that familiar feel, i didn't want to throw them i'm with gnome of xfce. however lxde could work. 
the permissions would already be set up, as the folders already exist and a filled, but how would i map the folder as a drive on each computer without having to Manuelly do it?
as for wubi, that would defeat the purpose of using Linux in the first place. Linux allows me to do this at a smaller cost, with much of the software free, while buying copys of windows, or windows machines would be much more expensive.

---

### Post by Basher101 on 2011-08-20
i did not mean for you using wubi, but your students. i guess they already have a PC at home that runs (very likeley) windows. Its just so they could get use to it. Also ubuntu is ubuntu, it does not matter if its KDE, Gnome, XFCE or LXDE. It still functions in the same way, only the applications are different and the interface.

edit: about the server, you should probably open a new thread and ask about how to set up a server like that, as i do not know how..

---

### Post by grahammechanical on 2011-08-20
consider researching Edubuntu. It comes with administration applications and student record keeping applications. There are three groups of programs that can be installed according to the age of the students.

[http://www.edubuntu.org/]("http://www.edubuntu.org/")

The Edubuntu people might have already figured out the answers that you need.

Regards.

---

### Post by jarrah-95 on 2011-08-20
thanks, i had originally looked at both, and decided on kubuntu, but have now looked again, and changed my mind, edubuntu it is. as for the network drive,its only a report, so i might skim over that section.

---

### Post by Basher101 on 2011-08-22
Just the thought that with this we get 1100 ubuntu users+ in one fell swoop. Almost like a dream haha^^

---

### Post by jarrah-95 on 2011-08-23
kinda wish it wasn't for a school project, just for that fact!

---

### Post by dino99 on 2011-08-23
Starting point:

[https://wiki.ubuntu.com/Education/EdubuntuServer](https://wiki.ubuntu.com/Education/EdubuntuServer)
[https://edubuntu.org/](https://edubuntu.org/)

---

