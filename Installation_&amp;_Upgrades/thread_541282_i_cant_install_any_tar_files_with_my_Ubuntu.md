---
title: "i cant install any tar files with my Ubuntu"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by hesham on 2007-09-02
I download some tar.gz files & after extract them always when i type ./ configure i received this :- ( this example for a game called stratagus )
___________________________________________________________________________

root@hesham-desktop:/home/hesham/stratagus-2.2.4# ./configure 
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output... configure: error: C++ compiler cannot create executables
See `config.log' for more details.
root@hesham-desktop:/home/hesham/stratagus-2.2.4#  
___________________________________________________________________________

Can any one help me please ?

---

### Post by Pumalite on 2007-09-02
sudo apt-get install build-essential

---

### Post by Steveway on 2007-09-02
sudo apt-get install stratagus 
or
sudo apt-get install stratagus-gl
You should use Synaptic to install programs and be sure that you have your multiverse and universe repos enabled.

---

### Post by hesham on 2007-09-02
i tried all thats & got this error :-

root@hesham-desktop:~# sudo apt-get install g++2.95
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@hesham-desktop:~# sudo aptitude install build-essentail
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

so whats this meaning ??
can you help me

---

### Post by Pumalite on 2007-09-02
Close Synaptic.

---

### Post by rsambuca on 2007-09-02
You can't use apt-get or aptitude in a terminal if the Synaptic Package Manager is open.

---

