---
title: "help me a lot people"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by pat boy on 2008-08-02
i can not download updates??

my system does not have any applications on it?? 

i can not you dvd play on my system music on it???
:mad::mad::mad::mad::mad:

---

### Post by Sealbhach on 2008-08-02
Do you have an internet connection?


.

---

### Post by pat boy on 2008-08-02
yes and i works bordband

---

### Post by Sealbhach on 2008-08-02
I'm having trouble undrstanding you.

To get effective help on the forum you need to be very specific about what's not working.

Like, I don't know what you mean by this?
> 
my system does not have any applications on it??  

:confused:

.

---

### Post by pat boy on 2008-08-02
i can not run any disks ie dvds, 

when i try to download updates this is what come up

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i dont understand what is wrong!

---

### Post by oldos2er on 2008-08-02
> **pat boy said:**
> i can not run any disks ie dvds, 

when i try to download updates this is what come up

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i dont understand what is wrong!

 Open a terminal and run "sudo dpkg --configure -a"

---

### Post by pat boy on 2008-08-02
you will have to tell me how to do that as i dont understand this system very yet

---

### Post by dje on 2008-08-02
> **pat boy said:**
> you will have to tell me how to do that as i dont understand this system very yet

open a terminal (Applications >> Accessories >> Terminal) and type the following:
```
sudo dpkg --configure -a
```
press return after typing it and enter your password if required (there will be no visual feedback, it is being recognised just type your password and press return) then let it do its thing

dje

---

### Post by pat boy on 2008-08-02
i did what you said to do and this is what come up


dpkg: error processing eog (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 eog


now what do i do??

---

### Post by dje on 2008-08-02
> **pat boy said:**
> i did what you said to do and this is what come up


dpkg: error processing eog (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 eog


now what do i do??

in the terminal run the code below:
```
sudo apt-get install --reinstall eog
```

dje

---

### Post by pat boy on 2008-08-02
thank you it is working now :)

the next thing i need help with is 

i can not run cd/dvd, or download any thing. it comes up and says that there is no application to run it. can you help me with this??

---

### Post by dje on 2008-08-02
> **pat boy said:**
> thank you it is working now :)

the next thing i need help with is 

i can not run cd/dvd, or download any thing. it comes up and says that there is no application to run it. can you help me with this??

no worries, glad it is working :)

for cd's and dvd's look [here]("http://www.ubuntu1501.com/2008/04/easy-media-codec-installation-for-hardy.html")

what applications are you trying to run, .exe's? these are windows applications that do not run natively on linux. wine is a compatibility layer capable of running some windows applications, install it with:
```
sudo apt-get install wine
```
to see which applications work with wine have a look [here]("http://appdb.winehq.org/")

dje

---

### Post by Pumalite on 2008-08-02
You can also do:
sudo apt-get install ubuntu-restricted-extras
( in response to your query)

---

### Post by pat boy on 2008-08-02
ok you have fix that problem as well thank you a lot.


one more to go 

when i start up my computer it goes to a black screen and gives me a chose to use xp or ubuntu??

how can i remove xp so i run on ubuntu and not xp ???

---

### Post by dje on 2008-08-02
> **pat boy said:**
> ok you have fix that problem as well thank you a lot.


one more to go 

when i start up my computer it goes to a black screen and gives me a chose to use xp or ubuntu??

how can i remove xp so i run on ubuntu and not xp ???

you want to delete xp completely? or just remove it from the menu or have it not ask you and just automatically boot ubuntu?

---

### Post by pat boy on 2008-08-02
not sure?

my xp has a vires and does not work well any more. so if i delet it will it matter? can ubuntu run ok with out it?
:confused:

---

### Post by Pumalite on 2008-08-02
Press 'Esc' and see if you get a Grub menu.

---

### Post by pat boy on 2008-08-02
if i do then what?

---

### Post by Valsodar on 2008-08-02
> **pat boy said:**
> not sure?

my xp has a vires and does not work well any more. so if i delet it will it matter? can ubuntu run ok with out it?
:confused:

Well, ubuntu does not require XP to run properly, unless you have installed ubuntu with WUBI. Other that that you may freely delete windows and how to do that involves a bit of work. Alternatively you can not do anything (leave windows as it is) and there will be no problem. I recommend reinstalling windows, but that also requires some grub configuration.

-> here is how to delete it:
1. run a partitioner and remove the windows partition.
2. fix your grub by following the following url:[http://sidrit.wordpress.com/2008/07/23/fixing-grub-after-windows-install/](http://sidrit.wordpress.com/2008/07/23/fixing-grub-after-windows-install/)

-> here is how to reinstall it:
1. reinstall windows xp on the partition it is on
2. 2. fix your grub by following the following url:[http://sidrit.wordpress.com/2008/07/23/fixing-grub-after-windows-install/](http://sidrit.wordpress.com/2008/07/23/fixing-grub-after-windows-install/)

---

### Post by dje on 2008-08-02
do you want to have xp or do you want to use only ubuntu?

---

### Post by Pumalite on 2008-08-02
Choose what you want. If you want to eliminate an item from Grub; you have to edit menu.lst
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
Edit:
gksudo gedit /boot/grub/menu.lst
Comment out (put a # in front) the item you want not to appear in Grub.
Save>File>Save
Exit
reboot

---

### Post by pat boy on 2008-08-02
Valsodar what do you mean by this ?

ubuntu does not require XP to run properly, unless you have installed ubuntu with WUBI

i download it for the inter net when i was useing window xp

---

### Post by dje on 2008-08-02
> **pat boy said:**
> Valsodar what do you mean by this ?

ubuntu does not require XP to run properly, unless you have installed ubuntu with WUBI

i download it for the inter net when i was useing window xp

did you burn a cd from the iso and boot from it or not?
do you wish to have xp on your system or only ubuntu?

---

### Post by pat boy on 2008-08-02
ok i will have to think about what i want to do with xp for some time 

thank you all 


i am trying to in still some thing and a error comes up with this 


exception exception in module dwarclinetEN.exe 

and there is some more to it,


can any one help me to fix this,
 plz any one

---

### Post by Sealbhach on 2008-08-02
Hi Pat Boy,

good to see you've been getting help from the good folks here. 

What are you trying to install? Some windows app in wine?

Maybe there's a linux alternative...


.

---

### Post by pat boy on 2008-08-03
i am trying to download an clinet thing for a game from to the internet.

---

