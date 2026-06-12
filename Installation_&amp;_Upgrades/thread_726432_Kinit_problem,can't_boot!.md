---
title: "Kinit problem,can't boot!"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by solikos on 2008-03-16
Hi!! i have ubuntu 7.1 and 2.6.22-14-generic kernel.Actually,when i am trying to boot my system,this message is appeared:   Kinit:No resume image,doing normal boot.....
Ufortunately i can t boot...What can i do??

---

### Post by kellemes on 2008-03-16
What do you mean, you can't boot.. aren't there any more messages? Is there something going on after "doing normal boot.." ?

---

### Post by solikos on 2008-03-16
> **kellemes said:**
> What do you mean, you can't boot.. aren't there any more messages? Is there something going on after "doing normal boot.." ?

No,it doesn't show me any more messages.Just this....

---

### Post by linuxtoindia on 2008-03-22
simple

press ctrl+alt+f1

after that login in command type env

then ''sudo dpkg-reconfigure xserver-xorg''

after all that screen options
type gdm
gdm reinstall
or somethg like that...
after all u been set ,, download kde from synaptic as ur gnome will nomore work properly with good graphics and high resolution/

---

### Post by solikos on 2008-03-24
the problem is that i can t reach to command line when pressing ctl+alt+f1 because the same message appears:"NO RESUME IMAGE,DOING NORMAL BOOT".I've tried to press f2,f3 ..etc but without success.I've also tried the recovery mode and live cd,when i wrote your commands there.But nothing...
With live cd,i managed to install kde,but i can't boot my disk with kde....Any solution????

---

### Post by solikos on 2008-03-26
> **linuxtoindia said:**
> simple

type gdm
gdm reinstall
or somethg like that...
after all u been set ,, download kde from synaptic as ur gnome will nomore work properly with good graphics and high resolution/

To be more concise,can i access terminal via live cd,run your commands and save those changes to the /dev/sda2 partition???

---

### Post by linuxtoindia on 2008-03-27
wiat ...
 can u see a terminal there?
 press ctrl+alt+f1

and then login and type the passsward


and then type/

''sudo dpkg-reconfigure xserver-xorg''


after all setting


type startx

after that gdm
or sudo gdm update 
all gdm commands


after it gets 
over

update ur system

this is a major bug and will be solved by update ur system up to date!

---

### Post by linuxtoindia on 2008-03-27
no need of using live cd!

this commands shold definately work!


or nothing then finally format and update ur system
..


and this time try edubuntu/.

its more stable!

---

### Post by solikos on 2008-03-27
> **linuxtoindia said:**
> wiat ...
 can u see a terminal there?
 press ctrl+alt+f1

and then login and type the passsward


The problem is that i can t see anything except"RESUME IMAGE,DOING NORMAL BOOT",when i try ctrl+alt+f1.I can't access terminal by this way!:(

that's why i try to use live cd...I can't find any other way to access terminal.

---

### Post by linuxtoindia on 2008-03-27
finally format!
 
 
now theres no way as no terminal!
 
or try boot fix cds

---

### Post by linuxtoindia on 2008-03-27
> **solikos said:**
> The problem is that i can t see anything except"RESUME IMAGE,DOING NORMAL BOOT",when i try ctrl+alt+f1.I can't access terminal by this way!:(

that's why i try to use live cd...I can't find any other way to access terminal.
finally format!
 
 
now theres no way as no terminal!
 
or try boot fix cds

---

### Post by solikos on 2008-03-27
> **linuxtoindia said:**
> finally format!
 
 
now theres no way as no terminal!
 
or try boot fix cds


that's what i was afraid of!](*,)

---

### Post by linuxtoindia on 2008-03-28
formattttttt!! aand this time install two linux os!
i=one open suse and sec ond ubuntu

---

