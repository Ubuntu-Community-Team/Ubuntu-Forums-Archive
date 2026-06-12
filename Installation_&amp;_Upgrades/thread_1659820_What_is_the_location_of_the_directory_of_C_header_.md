---
title: "What is the location of the directory of C header files"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by EN1ac3R on 2011-01-04
Hi there everyone ):P

okay here we go....

I am running VMware inside windows 7 64bit.I have installed ubuntu 2.8 ultimate edition on a 20gb partition and used 1gb of ram....everything is updated etc and running good.

I checked in the VMware tools bar the entity tab,and says tools is not installed.

So when i run the install everything goes well untill it reaches the point where it says

"What is the location of the directory of C header files that match your running kernel?

I have tried everything,different tutorials,installed a build package etc and it still asks for the directory.
here is the uname r output :

 uname r : 2.6.35-24-generic



i have been twisting my head all week over this,i hope someone can help me ...:confused:

thanks so much:p

---

### Post by wojox on 2011-01-04
Did you run:

```
sudo apt-get install linux-headers-`uname -r`
```

Also the header files should be in

```
/lib/modules/Your-Kernel/build/include
```

---

### Post by EN1ac3R on 2011-01-04
Hi wojox,thanks for your reply so soon.

output for 

output for : sudo apt-get install linux-headers-`uname -r`

[sudo] password for tux: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.35-24-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tux@tux-virtual-machine:~$ 

-----------------------------------------------------------------------------------------------

output for 
: What is the location of the directory of C header files that match your running
  kernel? /lib/modules/2.6.35-24-generic/build/include                                          

  The path "/lib/modules/2.6.35-24-generic/build/include" is not valid.
   Would you like to change it? [yes]  :confused:




not sure if changing the path is what i have to do ?


thanks again wojox for quick reply before,main reason i like ubuntu is that it has a great community of people that help,
how ever simple or complex your questions are :)

---

### Post by wojox on 2011-01-05
Did you change it and did it work?

---

### Post by EN1ac3R on 2011-01-05
Hi wojox  I tried as you wrote and it says i have the latest headers.

I entered here my 2.6.35-24-generic and it comes up with 


: The path "/lib/modules/2.6.35-24-generic/build/include" is not valid.
   Would you like to change it? [yes] :confused:


Should it of found the location or is it okay to change it ?  not sure what to do..

Thanks wojox.

---

### Post by wojox on 2011-01-05
I would answer Yes. Change it.

---

### Post by EN1ac3R on 2011-01-05
Hi wojox

Im just trying again now then i will report straight back....

Here goes....

---

### Post by EN1ac3R on 2011-01-05
Hi wojox,

I entered yes to changing the path then it comes up with 

:  What is the location of the directory of C header files that match your running kernel? 


how can i find the location of the header files,i looked in the lib folder/binary and didnt find anything......?

---

### Post by MrCll on 2012-10-03
sudo ln -s /lib/modules/`uname -r`/build/include/generated/utsrelease.h /lib/modules/`uname -r`/build/include/linux/utsrelease.h

sudo ln -s /lib/modules/`uname -r`/build/include/generated/autoconf.h /lib/modules/`uname -r`/build/include/linux/autoconf.h

Enjoy :)

---

