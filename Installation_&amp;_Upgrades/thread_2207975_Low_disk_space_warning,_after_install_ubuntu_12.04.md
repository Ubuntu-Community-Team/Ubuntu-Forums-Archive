---
title: "Low disk space warning, after install ubuntu 12.04"
date: 2014-02-26
forum: Installation &amp; Upgrades
---

### Post by jantinusw on 2014-02-26
Hi im very new to ubunt, i wanted to give it a try, after reading good stories on the internet
I installed ubuntu on a different partition than my windows 7, 
everything went fine, but after an hour of installing some programs i get the warning low disk space, even tough the partitions is 486.7 GB.
when i check the Disk Usage Analyzer i can see that the / is completely full
unfortunately im very new to ubuntu and i cant seem to find a solution on the internet
can any of you help me?

---

### Post by mörgæs on 2014-02-26
Hi, welcome to the fora.

If you reboot and run the commands

```
sudo apt-get clean
sudo apt-get update
sudo apt-get autoremove

```
do you get some free space?

---

### Post by jantinusw on 2014-02-26
Hi morgaes,

i ran the commands in the terminal, 
i got only 200 mb more free space, which is less than i hoped for, 

i should have about 450 gb free space, i dont get why it tells me i have low diskspace, 
maybe it matters maybe it doesnt, 
i have installed wine, and tried to install a game, 
and i have one account wich i use

jantinusw

---

### Post by mastablasta on 2014-02-26
you have 35,6GB total space reserved for Ubuntu / and it's fool (it's like having C:\ drive full in windows).

did you maybe use Wubi when you instaled Ubuntu? can you run boot repair tool and then create boot info script (you don't need to repair your boot so leave that alone) and post the results here.

---

### Post by jantinusw on 2014-02-26
i used the windows installer to install ubuntu (that wubi right??)

i got a link to the result of the boot repair, info, 

[http://paste.ubuntu.com/7001638/](http://paste.ubuntu.com/7001638/)

i hope it is of some use :)

thanks in advance :)

---

### Post by mastablasta on 2014-02-27
oh yes that is wubi. this installs ubuntu into a virtual disk drive inside windows. so the system is not actually comepltely separated form windows. furthermore virtual drive has a size limit which i think you reached. well actually i think it's probably the windows file system (NTFS) that is limiting it all here.

you can unintsall wubi from windows control panel and create the propper dual boot.

something is bothering me where are partitions sda3 and sda4? did you maybe ran the info script from wubi? try from live session (boot from USB or DVD)


simple solution for dualboot.
1. make sure you have max 3 primary partitions
2. delete the partition you plan to install ubuntu to. this will create unallocated/unformated (empty) disk space.
3. boot from Ubuntu media (DVD/USB) and run install. during install select the option to install ubuntu alongside windows.

if the install alongside windows option doesn't pop up it may mean:
1. something is wrong with partitioning (too many primary partitions)
2. empty disk space is in such places that installer doesn't really recognise it or something like that. anyway this can be then solved by choosing something else.

---

### Post by jantinusw on 2014-03-01
hi mastablasta,
sorry for the late response , i was super busy.
i installed ubuntu using a bootable usb,
i already installed some stuff, and i dont get warinings so i think everything is fixed!

thanks for the help :)

---

### Post by mörgæs on 2014-03-01
Good, please mark the thread 'solved'.

---

