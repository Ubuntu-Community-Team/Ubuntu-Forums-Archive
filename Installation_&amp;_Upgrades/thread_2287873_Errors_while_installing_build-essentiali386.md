---
title: "Errors while installing build-essential:i386"
date: 2015-07-22
forum: Installation &amp; Upgrades
---

### Post by ms5000 on 2015-07-22
I am using Ubuntu 14.04 LTS. I want to install build-essential:i386 package. I am fairly new to Linux so I am having a difficult time resolving this. I searched on this forum and pretty much tried most of the solutions available on the forum. 

Below is what I get when I try to install:

$ sudo apt-get install build-essential:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 build-essential:i386 : Depends: gcc:i386 (>= 4:4.4.3) but it is not going to be installed
                        Depends: g++:i386 (>= 4:4.4.3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


When trying to install from Ubuntu Software Center, this is what I get:
The following packages have unmet dependencies:

build-essential:i386: Depends: gcc (>= 4:4.4.3) but 4:4.8.2-1ubuntu6 is to be installed
                      Depends: g++ (>= 4:4.4.3) but 4:4.8.2-1ubuntu6 is to be installed




Can you please help? 

Thank you.

---

### Post by watchpocket on 2015-07-23
```
sudo apt-get autoremove
```

should come in handy here.  From man apt-get: *autoremove is used to remove packages that were automatically installed  to satisfy dependencies for some package and that are no more needed.*

Also ```
sudo apt-get clean
```

But back up your package dirs first.

---

