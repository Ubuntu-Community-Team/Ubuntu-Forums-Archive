---
title: "Apache2 installation messed up"
date: 2019-11-05
forum: Installation &amp; Upgrades
---

### Post by boschma1 on 2019-11-05
Hi there

I have messed up my Apache2 installation on my Ubuntu 18.04.3 LTS. I have tried to completely uninstall all Apache2 components and now - while trying to reinstall using sudo apt install apache2, I obtain this here: 

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 apache2 : Depends: apache2-utils (= 2.4.29-1ubuntu4.11) but 2.4.41-1+ubuntu16.04.1+deb.sury.org+5 is to be installed
           Depends: apache2-data (= 2.4.29-1ubuntu4.11) but 2.4.41-1+ubuntu16.04.1+deb.sury.org+5 is to be installed
           Recommends: ssl-cert but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Any ideas what to do to resolve this issue and how to get back to my working Apache2 environment? Thank you.

Best,
Markus

---

### Post by SeijiSensei on 2019-11-05
First, try "sudo dpkg --configure -a" and "sudo apt-get -f install" to see if those will fix the dependencies problems.  

Did you run "sudo apt update" before trying any of this? You should always run "update" to insure you have the most up-to-date package lists from the repositories.

---

### Post by boschma1 on 2019-11-05
I tried all of the above. In the meanwhile, I have updated to Ubuntu 19.04 and now I get the same message with different version numbers when entering [COLOR=#000000]sudo apt install apache2[/COLOR].

```
The following packages have unmet dependencies:
 apache2 : Depends: apache2-data (= 2.4.38-2ubuntu2.3) but 2.4.41-1+ubuntu16.04.1+deb.sury.org+5 is to be installed
           Depends: apache2-utils (= 2.4.38-2ubuntu2.3) but 2.4.41-1+ubuntu16.04.1+deb.sury.org+5 is to be installed
           Recommends: ssl-cert but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by deadflowr on 2019-11-05
It looks like at some point you added the sury/apache2 ppa.
So you can try to either re-enable it for your release or try cleaning up whatever mess it caused.

---

### Post by boschma1 on 2019-11-05
That's right. I have added the PPA of sury for apache2. I have added it again:
```
sudo add-apt-repository ppa:ondrej/php
sudo apt-get update
```

But the result is the same. I would like to clean it up if I knew how...

---

### Post by deadflowr on 2019-11-05
Remove the ppa
then try
```
sudo apt clean
sudo apt update
sudo apt upgrade
```
post back the outputs in code tags.

---

### Post by boschma1 on 2019-11-05
I found it myself. If using this PPA for php it makes sense to use it for Apache2 as well. Hence, 

[FONT=courier new]sudo add-apt-repository ppa:ondrej/apache2[/FONT]
[FONT=courier new]sudo apt-get update 
[/FONT]
did the trick.


Thanks.

---

### Post by deadflowr on 2019-11-05
That works (fingers crossed that it will remain working)
I probably should have paid closer attention to which ppa you originally posted adding.
If things work as expected, please go ahead and [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

