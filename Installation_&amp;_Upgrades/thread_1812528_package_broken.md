---
title: "package broken"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by malakar.subhendu on 2011-07-26
when trying to install kde-plasma desktop from ubuntu software centre, it shows the following error:

> **Package dependencies cannot be resolved**
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.


Then it shows that the package catalog is broken. it tries to repair it but fails.

---

### Post by jerrrys on 2011-07-26
try this:

open a terminal and enter

sudo apt-get update && sudo apt-get install kde-plasma-desktop

and post back any errors

---

### Post by malakar.subhendu on 2011-07-26
> **jerrrys said:**
> try this:

open a terminal and enter

sudo apt-get update && sudo apt-get install kde-plasma-desktop

and post back any errors
It showed the error:
> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 kde-plasma-desktop : Depends: kdebase-runtime (>= 4:4.5.1) but it is not going to be installed
                      Depends: plasma-desktop (>= 4:4.5.1) but it is not going to be installed
                      Depends: kdebase-workspace (>= 4:4.5.1) but it is not going to be installed
                      Depends: kdebase-apps (>= 4:4.5.1) but it is not going to be installed
                      Recommends: kdm (>= 4:4.5.1) but it is not going to be installed
E: Broken packages


---

### Post by jerrrys on 2011-07-26
copy and paste to terminal

sudo dpkg --configure -a && sudo apt-get autoclean && sudo apt-get clean && sudo apt-get autoremove && sudo apt-get update && sudo apt-get install kde-plasma-desktop

do any good?

EDIT: and to be sure; you are running ubuntu 10.10

---

### Post by malakar.subhendu on 2011-07-27
> **jerrrys said:**
> copy and paste to terminal

sudo dpkg --configure -a && sudo apt-get autoclean && sudo apt-get clean && sudo apt-get autoremove && sudo apt-get update && sudo apt-get install kde-plasma-desktop

do any good?

EDIT: and to be sure; you are running ubuntu 10.10
i have installed kde-plasma-desktop, but when tried to use the above script, it showed the following error:
> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2803C1B16950EC00


---

### Post by jerrrys on 2011-07-28
why the key is missing, i do not understand.  out of curiosity i loaded the plasma desktop without issue.  anyhow you need to install the key.  this will give you the idea:

 [https://answers.launchpad.net/ubuntu/+source/update-manager/+question/59304](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/59304)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=The+following+signatures+couldn%27t+be+verified+because+the+public+key+is+not+available&sa=Search&cof=FORID:9#1001](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=The+following+signatures+couldn%27t+be+verified+because+the+public+key+is+not+available&sa=Search&cof=FORID:9#1001)

---

### Post by malakar.subhendu on 2011-07-31
thanks fro the help.
I found the problem and the solution is:

[http://ubuntuforums.org/archive/index.php/t-1221323.html]("http://ubuntuforums.org/archive/index.php/t-1221323.html")
or basically enter the following command with the hexadecimal codes:
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys xxxxxxxxxxxxxxxx

write your hexadecimal code in place of the 'xx...xx'.

---

