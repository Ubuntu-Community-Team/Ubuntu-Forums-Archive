---
title: "SUMO tools installation failed Ubuntu 14.04"
date: 2014-08-19
forum: Installation &amp; Upgrades
---

### Post by nadeendra on 2014-08-19
hi for my academic work I need to install [sumo tools]("http://sumo-sim.org/") (simulation of urban mobility) and I'm using ubuntu 14.04 in VmWare workstation I followed the instruction in this[ link]("http://sumo-sim.org/wiki/Downloads")  and entered following command 
```

[COLOR=#000000][FONT=monospace]sudo add-apt-repository ppa:sumo/stable
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]sudo apt-get update [/FONT][/COLOR][COLOR=#000000][FONT=monospace]
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]sudo apt-get install sumo sumo-tools sumo-doc
[/FONT][/COLOR]
```


and I get the following output 

> @ubuntu:~$ sudo apt-get install sumo sumo-tools sumo-docReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 sumo : Depends: libgdal1 (>= 1.9.0) but it is not installable
E: Unable to correct problems, you have held broken packages.


sen I try the ubuntu software center and try to install it from there it also failed and give me "Package dependencies cannot be resolved" error with following details
> 
The following packages have unmet dependencies:


sumo: Depends: libc6 (>= 2.15) but 2.19-0ubuntu6.1 is to be installed
      Depends: libgcc1 (>= 1:4.1.1) but 1:4.9-20140406-0ubuntu1 is to be installed
      Depends: libgdal1 (>= 1.9.0) but it is not going to be installed
      Depends: libproj0 (>= 4.8.0-1) but 4.8.0-2ubuntu2 is to be installed
      Depends: libstdc++6 (>= 4.6) but 4.8.2-19ubuntu1 is to be installed




I badly need this tool and ns2 (which is already installed) to do my project. Please help me to resolve this issue

---

### Post by slickymaster on 2014-08-19
That version of sumo, from that PPA, depends on **libgdal1**. This package is not available from the Trusty repositories as you can confirm [here]("http://packages.ubuntu.com/search?suite=trusty&keywords=libgdal1").

You don't need that PPA, which apparently doesn't seem to be properly updated for Trusty. Why don't you use the [sumo version that is available in the repos]("http://packages.ubuntu.com/trusty/science/sumo")? (which by the way use **libgdal1h - **a different version of the same)

---

