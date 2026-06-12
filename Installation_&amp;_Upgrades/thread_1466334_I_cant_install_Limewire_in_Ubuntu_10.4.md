---
title: "I cant install Limewire in Ubuntu 10.4"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by londonlad on 2010-04-30
hi all, im having real probs trying to install limewire, i keep getting this (below pic), any ideas folks?

thanks.


[[IMG]http://img87.imageshack.us/img87/8599/screenshotpb.png[/IMG]](http://img87.imageshack.us/i/screenshotpb.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by londonlad on 2010-04-30
so i then tried frostwire, & i get this:

[[IMG]http://img121.imageshack.us/img121/5036/screenshot2fb.png[/IMG]](http://img121.imageshack.us/i/screenshot2fb.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

any help appreciated, thanks.

---

### Post by note32 on 2010-04-30
do you have java installed? , i think you need the proprietary java version installed

---

### Post by londonlad on 2010-04-30
> **note32 said:**
> do you have java installed? , i think you need the proprietary java version installed


how do i do that?

---

### Post by .:PiXi²:. on 2010-04-30
[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html]("http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html")

---

### Post by note32 on 2010-04-30
try this:

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

---

### Post by londonlad on 2010-04-30
> **note32 said:**
> try this:

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

yup, tried that, & i just get this:

simonrogers@simonrogers-laptop:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate
simonrogers@simonrogers-laptop:~$

---

### Post by note32 on 2010-04-30
i forgot they changed java versions in 10.04

Sun Java moved to the Partner repository

For Ubuntu 10.04 LTS, the sun-java6 packages have been dropped from the Multiverse section of the Ubuntu archive. It is recommended that you use openjdk-6 instead.

If you can not switch from the proprietary Sun JDK/JRE to OpenJDK, you can install sun-java6 packages from the Canonical Partner Repository. You can configure your system to use this repository via command-line:

     add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"

then try it again

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

---

### Post by londonlad on 2010-04-30
> **note32 said:**
> i forgot they changed java versions in 10.04

Sun Java moved to the Partner repository

For Ubuntu 10.04 LTS, the sun-java6 packages have been dropped from the Multiverse section of the Ubuntu archive. It is recommended that you use openjdk-6 instead.

If you can not switch from the proprietary Sun JDK/JRE to OpenJDK, you can install sun-java6 packages from the Canonical Partner Repository. You can configure your system to use this repository via command-line:

     add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"

then try it again

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

sorry note32, im still quite new to all this, & what you have said really doesnt make sense! :(

---

### Post by note32 on 2010-04-30
its ok:P

open up terminal and copy paste this:

add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"

then hit enter

then

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

hit enter and see if that works for you

---

### Post by londonlad on 2010-04-30
> **note32 said:**
> its ok:P

open up terminal and copy paste this:

add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"

then hit enter

then

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

hit enter and see if that works for you


simonrogers@simonrogers-laptop:~$ add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"
Error: must run as root
simonrogers@simonrogers-laptop:~$ sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"
simonrogers@simonrogers-laptop:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate
simonrogers@simonrogers-laptop:~$

---

### Post by note32 on 2010-04-30
first type sudo -s you have to be root user

then do

open up terminal and copy paste this:

add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"

then hit enter

then

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

---

### Post by londonlad on 2010-04-30
SUSSED IT!  :)

i added that 'deb' thingy to the software sources, it updated itself, i then installed 'java6' & i then installed limewire no probs, THANKYOU TO NOTE32 FOR THE HELP! :D

[[IMG]http://img98.imageshack.us/img98/8206/screenshotsc.png[/IMG]](http://img98.imageshack.us/i/screenshotsc.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by note32 on 2010-04-30
yup anytime):P

---

### Post by kostkon on 2010-04-30
londonlad only had to enable the Partner repo in the Software Sources and didn't have to do all this complicated stuff. As you can see the entry for the Partner repo was already there.

---

### Post by note32 on 2010-04-30
> **kostkon said:**
> londonlad only had to enable the Partner repo in the Software Sources and didn't have to do all this complicated stuff. As you can see the entry for the Partner repo was already there.

awwwww yea i forgot about that](*,) thanks for pointing that out

---

### Post by kostkon on 2010-04-30
> **note32 said:**
> awwwww yea i forgot about that](*,) thanks for pointing that out
;)

---

### Post by londonlad on 2010-04-30
yup, well spotted that man, but note32 did put himself out & help me...

---

### Post by fherdelpino on 2010-05-07
try 
sudo apt-get update

before the "sudo apt-get install sun-java6-jre..."

if you add a new repo, it is good to update the sources!

---

### Post by Dayofswords on 2010-05-07
why didnt you just get frostwire? its in the repos

---

### Post by CoreyB. on 2010-05-08
> **Dayofswords said:**
> why didnt you just get frostwire? its in the repos

FrostWire is not in the repos.  It is in GetDeb.

---

### Post by Custom Cowboy on 2010-05-22
Thanks note32, your information is on the money. I was having same problem, now I am smiling again.

---

### Post by yoiam on 2010-07-23
I had the same problem  trying to get sudo apt-get update to work in the terminal then I realized that I was using a proxy go figure lol.

But my big ? is I went to the bathroom while it was running and my system went in to hibernation mode.
When I came back I had to log back on.    The program stopped so I closed the terminal and re did the process and it wont let me type my password    Help please.

---

### Post by arunmanoj on 2010-09-13
after issuing the "**deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner**" command, goto **--> System --> administration --> software sources --> other software (tab)** select(if already selected then reselect & select) the following sources,**[url"]http://archive.canonical.com/ubuntu[/url] lucid partner**" & " **[http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner**" then close...it will ask whether you want to reload the packages...select reload" ,now issue "**sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk**"...now it will work

---

