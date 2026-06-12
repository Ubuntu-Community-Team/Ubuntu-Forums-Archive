---
title: "Couldn't find the package gnup"
date: 2012-01-19
forum: Installation &amp; Upgrades
---

### Post by poojasaraff on 2012-01-19
When i type the following in my shell:

sudo apt-get install git-core gnupg vim flex bison gperf build-essential \
zip curl zlib1g-dev libc6-dev lib32ncurses5-dev ia32-libs \
x11proto-core-dev libx11-dev lib32readline5-dev lib32z-dev \
libgl1-mesa-dev g++-multilib mingw32 tofrodos python-markdown \
libxml2-utils sun-java6-jdk

it says:
E: couldn't find the package gnup
---------------------------------------------------
I tried to google bt I am not sure if gnup is same as GnuPG. What should I do next?

Thanks

---

### Post by raja.genupula on 2012-01-20
have you tried install gnupg alone ,. just try to install alone.may be by that we can found which package is the exact cause for errors.

All the best.

---

### Post by ottosykora on 2012-01-20
hmmm, gnupg is supposed to be installed as default during installation otherwise checking of the sigs will not work at all.

---

### Post by raja.genupula on 2012-01-20
ok then first try to install gnupg alone .:D. hope it works .

Let us know what you got .

---

### Post by poojasaraff on 2012-01-20
I tried to install gnupg and I got following :
(Reading database ... 124678 files and directories currently installed.)
Preparing to replace gnupg 1.4.10-2ubuntu1 (using gnupg_1.4.10-2ubuntu1_amd64.deb) ...
Unpacking replacement gnupg ...
Setting up gnupg (1.4.10-2ubuntu1) ...

Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for doc-base ...
Processing 26 changed doc-base file(s)...
Registering documents with scrollkeeper...
------------------------------------------------------------
I am not sure if installation is done.. since it never gave me confirmation. 
---------------------------------------------------------------
I tried my previous command again however it still says: couldnt fine the pakage gnup.

P.S. - 1. i did check thru ubuntu software center and it says GnuPG installed
          2. I am using ubuntu as a guest OS on windows 

Thanks

---

### Post by ottosykora on 2012-01-20
it just reinstalled it

gnupg is part of the distro in any case, otherwise you could not really install uch from the repository probably as it is used to check the signature of the files. 
So no need to install it, unless for some reason someone managed to unistall it for no particular reason.

---

### Post by poojasaraff on 2012-01-20
@ottosykora : thanks

What does then "gnup" stand for? I tried googling (no help) I wonder if there is something like gnup :D

---

