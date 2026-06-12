---
title: "Can't remove broken sun-java6 packages"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by Alameda del Cobre on 2010-03-22
Hi. I'm a relatively new ubuntu user. Yesterday I installed java and my computer went off in the middle of the process and some packages didn't install correctly. I decided to reinstall them but it doesn't let me. I have tried to remove them using the synaptic manager, I also tried to remove them manually. I've tried:
apt-get -f install 

also. 
I tried to re-install it using:

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts


but this error comes up

Errors were encountered while processing:
 sun-java6-jdk
 sun-java6-fonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

Help! Thanks!

---

### Post by bumanie on 2010-03-22
Try>  sudo apt-get install -for > sudo apt-get install --fix-missing

---

### Post by Alameda del Cobre on 2010-03-22
Thanks but i've tried both and it gives me the same error:


>  0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up sun-java6-jdk (6-15-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing sun-java6-jdk (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up sun-java6-fonts (6-15-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing sun-java6-fonts (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 sun-java6-jdk
 sun-java6-fonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
 

---

### Post by bumanie on 2010-03-22
Sun-java-jdk is a development environment ; sun-java-jre is the runtime enviornment. You seem to have the correct code in terminal. If it were me, I would purge the whole lot and start again. But you may not wish to do this - it's up to you. > sudo aptitude purge sun-java6-jre sun-java6-plugin sun-java6-fontsIf you think this is the way to go. I can't understand why sun-java-jdk is trying to download when you have the code for sun-java-jre. Also, you could try booting into recovery mode and choosing to fix broken packages from there (there's a menu where you choose by using arrow keys and then hitting enter) and see if that works.

---

### Post by Alameda del Cobre on 2010-03-31
Well I tried this and thought the problem was over, but today I was removing a program from the package manager and this came up after it removed the program:

> E: sun-java6-jdk: subprocess installed post-installation script returned error exit status 2
E: sun-java6-fonts: subprocess installed post-installation script returned error exit status 2

What else can I try?

---

### Post by Anton_E on 2010-04-02
Did anything work?? Im having a similar problem... I can no longer install anything as whenever i do it says i have an error with java. I am using ubuntu 9.10 i686 if that helps?

For example during an install of 7zip i got this message (which is the normal message now):

(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 143451 files and directories currently installed.) 
Unpacking p7zip-full (from .../p7zip-full_9.04~dfsg.1-1_i386.deb) ... 
Processing triggers for man-db ... 
Setting up sun-java6-bin (6-15-1) ... 
update-alternatives: error: /var/lib/dpkg/alternatives/javaws corrupt: invalid status 
dpkg: error processing sun-java6-bin (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up p7zip-full (9.04~dfsg.1-1) ... 
Errors were encountered while processing: 
 sun-java6-bin

i have no idea what this mean as im a new user to ubuntu.

---

### Post by Alameda del Cobre on 2010-04-02
I am still able to install other programs but after they are installed, it gives me the error I posted above. :S

---

### Post by pbhill on 2010-05-08
> **Alameda del Cobre said:**
> I am still able to install other programs but after they are installed, it gives me the error I posted above. :S

Same here. Very annoying.

---

