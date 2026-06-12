---
title: "eagle-usb-2.3.2 ./configure error"
date: 2005-08-13
forum: Installation &amp; Upgrades
---

### Post by mozz10844 on 2005-08-13
cd eagle-usb-2.3.2
/eagle-usb-2.3.2$ ./configure
checking for gcc ...no
checking for cc ...no
checking for cc ..no
checking for ci ...no
configure: error: no acceptable c compiler in $PATH
see 'config.log' for more details.

thought i had the bugger sorted.but that comes along,ive also tried the same with an earlier version(1.9.8) but it has a similar error
i know ive made a few threads on this but i need help fast!
im pretty impatiant and wont use ubuntu if i have no internet access ](*,) 
please help
kthnxbye

---

### Post by PeP on 2005-08-13
use synaptic to install build-essential, <-this will solve the above error
and install linux-headers, automake, autoconf and gawk. <- this to prevent further errors

---

### Post by mozz10844 on 2005-08-13
i cannot use synaptic as i have no internet connection,installing this is how i fucking set it up! :mad: 
ive been told yo get a c compiler such  as gcc
ive downloaded a zip and put it on a disc,now how would i go about installing that?

---

### Post by PeP on 2005-08-13
don't you have a cd?

synaptic can install stuffs from the cd,and I am pretty sure that the cd includes build-essential.

else search the ubuntu repositories manually for the .deb files and use
sudo dpkg -i file.deb to install them

you will have to deal with dependances, so it might take some times to get all the needed packet

build-essential provides you gcc IIRC, if not just get it also from the cd

---

### Post by mozz10844 on 2005-08-13
i downloaded ubuntu so i have no cd,guide me from there.

---

### Post by PeP on 2005-08-13
I was supposing you had at least the install cd.

Then get it

[http://fr.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_10.1ubuntu1_i386.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_10.1ubuntu1_i386.deb)
i t will ask some dependancies (:-()

get them 

[http://fr.archive.ubuntu.com/ubuntu/pool/main/m/make/make_3.80-9_i386.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/m/make/make_3.80-9_i386.deb)
[http://fr.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.10.27ubuntu2_all.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.10.27ubuntu2_all.deb)
[...]

you might as well download the install cd and use it as a repository to install all theses stuffs,i recommend you that second option.
[edit] three options for you there, burn the cd and run, order the cd for free wait two weeks and run, copy the cd to your hd, mount it, edit your sources.list (/etc/apt/sources.list) to point to the mount point: you can use the iso and the mount command to simulate a cd+cdreader.

---

