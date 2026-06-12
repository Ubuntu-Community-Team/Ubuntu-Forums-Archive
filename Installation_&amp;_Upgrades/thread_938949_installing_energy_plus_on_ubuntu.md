---
title: "installing energy plus on ubuntu"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by anantyk on 2008-10-05
Has anyone attempted installing EnergyPlus (a building energy simulation software) in Ubuntu 8.04?

I followed the instructions but could not install. have added the output in the terminal window for ref.

root@energytrac:/home/kjit/EnergyPlusV220/install# chmod +x install.sh
root@energytrac:/home/kjit/EnergyPlusV220/install# ./install.sh
#############################################
#### Find Operating System version etc...
#############################################
#### Find ENERGYPLUS_DIR :
./.setup.sh: 36: pushd: not found
./.setup.sh: 38: popd: not found
#### EnergyPlus directory is /home/kjit/EnergyPlusV220/install
#### Check writability of /root/.cshrc , .profile , .bash_profile
#############################################
######## Check for install , uninstall
#############################################
#### Install EnergyPlus at directory /home/kjit/EnergyPlusV220/install
#### Write energyplusenv.csh , energyplusenv.sh
#### Modify .cshrc , .profile , .bash_profile
#############################################
# To update your environment variables, you #
# need to log in your system again.         #
#############################################
cp: cannot create regular file `install/profile.beforeEnergyPlus': No such file or directory
./.setup.sh: 201: cannot create install/instfils.lis: Directory nonexistent
#############################################
#### Install done. 
#############################################
root@energytrac:/home/kjit/EnergyPlusV220/install# 
root@energytrac:/home/kjit/EnergyPlusV220/install# 

any help or suggestions are welcome. . . 

kanwarjit

---

### Post by cariboo on 2008-10-05
I just tried it. Installing as root, it is looking for the files in /root that's why you are getting an error. If you install it as a regular user it will install properly:

```
~/EnergyPlusV220/install$./install 
```

will do the trick.

Jim

---

### Post by anantyk on 2008-10-06
[I]sorry Jim, still getting the same error when installing as normal user not su.

wonder where theproblem is?
[/I]
kjit@energytrac:~$ cd EnergyPlusV220/install
kjit@energytrac:~/EnergyPlusV220/install$ dir
energyplusenv.csh0  install.sh	  instfils.lis
energyplusenv.sh0   instdirs.lis  uninstall.sh
kjit@energytrac:~/EnergyPlusV220/install$ chmod +x install.sh
kjit@energytrac:~/EnergyPlusV220/install$ ./install.sh
#############################################
#### Find Operating System version etc...
#############################################
#### Find ENERGYPLUS_DIR :
./.setup.sh: 36: pushd: not found
./.setup.sh: 38: popd: not found
#### EnergyPlus directory is /home/kjit/EnergyPlusV220/install
#### Check writability of /home/kjit/.cshrc , .profile , .bash_profile
#############################################
######## Check for install , uninstall
#############################################
#### Install EnergyPlus at directory /home/kjit/EnergyPlusV220/install
#### Write energyplusenv.csh , energyplusenv.sh
#### Modify .cshrc , .profile , .bash_profile
#############################################
# To update your environment variables, you #
# need to log in your system again.         #
#############################################
cp: cannot create regular file `install/profile.beforeEnergyPlus': No such file or directory
./.setup.sh: 201: cannot create install/instfils.lis: Directory nonexistent
#############################################
#### Install done. 
#############################################
kjit@energytrac:~/EnergyPlusV220/install$ 


[I]somebody from energy plus support wrote to me yesterday with a solution that I am pasting below. but I am not competent to make sense of it. . .
[/I]
I just isntalled EnergyPlus v2.2.0 for linux on Kubuntu (Ubuntu) 8.04 Hardy 
Heron.  The installation script, .setup.sh, by virtue of its first line:

#! /bin/sh

is executed via /bin/sh.  On Ubuntu systems, /bin/sh is a symlink to dash, a 
shell that doesn't implement the pushd and popd commands, among other things.  
Correspondingly, on Ubuntu, the ENERGYPLUS_DIR environment variable is set 
to "<somepath>/EnergyPlusV220/install" instead of the 
correct "<somepath>/EnergyPlusV220".

One possible solution might be to change install.sh to purposefully exec via 
bash if bash is available, something like:

BASH=$(which bash)
if [ -x "$BASH" ]; then
    exec "$BASH" .setup.sh install
else
    exec .setup.sh install
fi
echo "Failed to exec the setup program" >&2
exit 1

---

