---
title: "Problem in installing R on Ubuntu 16.04 LTS"
date: 2020-06-16
forum: Installation &amp; Upgrades
---

### Post by manasistr on 2020-06-16
Hello,
I am trying to install R 4.0 packages on my Ubuntu 16.04 LTS by following the instructions in [https://cran.r-project.org/bin/linux/ubuntu/README.html](https://cran.r-project.org/bin/linux/ubuntu/README.html) .

I added 
deb [https://cloud.r-project.org/bin/linux/ubuntu](https://cloud.r-project.org/bin/linux/ubuntu) xenial-cran40/

to my /etc/apt/sources.list file.

Then for secure apt I did -
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9 

Then I did -

sudo apt-get update
sudo apt-get install r-base

The sudo apt-get update runs fine but sudo apt-get install r-base gives the following error message - 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 r-base : Depends: r-base-core (>= 4.0.1-1.1604.0) but it is not going to be installed
          Depends: r-recommended (= 4.0.1-1.1604.0) but it is not going to be installed
          Recommends: r-base-html but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


I don't know how to fix this. I am new to installing R. Please help!

---

### Post by dino99 on 2020-06-17
Mainly its saying it is not happy with the version number found 
You might have better chance by installing that ppa [https://launchpad.net/~marutter/+archive/ubuntu/rrutter4.0](https://launchpad.net/~marutter/+archive/ubuntu/rrutter4.0)

---

### Post by manasistr on 2020-06-17
I added the ppa to my repository list. Then I did a sudo apt-get update. 

However, when I run sudo apt-get install r-base, it still gives the same error.

Regards,
Manasi

---

### Post by dragonfly41 on 2020-06-17
Any plans to install 18.04 or 20.04 since 16.04 is dated? Could that be the issue (although I admit I still have an old 16.04 which is just archived as a reference)?

---

### Post by manasistr on 2020-06-17
Unfortunately, I can't install 18.04 or 20.04. And we also dont know for sure that this is the problem. I do not want to get in the whole process of installing a new OS just to find out that it still doesnt work.

---

