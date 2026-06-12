---
title: "Amarok"
date: 2005-08-13
forum: Installation &amp; Upgrades
---

### Post by speedemonV12 on 2005-08-13
i am trying to install amaroK and this is the error that i am getting....

dpkg: dependency problems prevent configuration of amarok:
 amarok depends on amarok-arts | amarok-engines | amarok-engine; however:
  Package amarok-arts is not installed.
  Package amarok-engines is not installed.
  Package amarok-engine is not installed.
 amarok depends on libsqlite3-0 (>= 3.0.8); however:
  Package libsqlite3-0 is not installed.
 amarok depends on libtag1 (>= 1.3.1); however:
  Package libtag1 is not installed.
 amarok depends on libtunepimp2 (>= 0.3.0); however:
  Package libtunepimp2 is not installed.
dpkg: error processing amarok (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 amarok


anyone know what to do...and i dont have to have amaroK i am just looking for something to replace Juk in gnome (juk has that thing that you can modify file properties like artist name, track name and all that stuff the track edditor)...if you know of another player let me know...otherwise please help with this problem...

thanks
speedy

---

### Post by otherdave on 2005-08-23
I just tried to install Amarok and got a similar error. What did I forget to turn on in sources.list?

root@hocus-pocus:~# apt-get install amarok
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  amarok: Depends: amarok-arts but it is not going to be installed or
                   amarok-engines but it is not going to be installed or
                   amarok-engine

---

### Post by cmh_ubuntu on 2005-08-25
I am having a very similar problem trying to install AmaroK using Synaptic on Ubuntu (Hoary).  I'm not sitting in front of my linux machine, so I can't post the exact error, but I'm glad to see I am not the only one.

---

### Post by angkor on 2005-08-25
@speedemon.

Are you using 'sudo apt-get install amarok' or are you using 'dpkg -i amarok'?

Cause all the errors I see are just saying you don't have all the dependencies installed. Install them all and you should be able to install amarok.

Apt will install the dependencies automagically if you install amarok, if not, please post your /etc/apt/sources.list

good luck

---

