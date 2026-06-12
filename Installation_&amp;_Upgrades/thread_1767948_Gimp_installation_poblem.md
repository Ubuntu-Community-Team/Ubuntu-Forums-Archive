---
title: "Gimp installation poblem"
date: 2011-05-26
forum: Installation &amp; Upgrades
---

### Post by Jeroen De Dauw on 2011-05-26
I had Gimp installed on Kubuntu 10.10, and after upgrade to 11.04, it's not installed anymore. Now when I try to install it again, I get this:

```
sudo apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gimp : Depends: libwebkitgtk-1.0-0 (>= 1.3.10) but it is not going to be installed
E: Broken packages
```

I tried a bunch of things (that did not solve the issue), but am relatively new to Linux, so am probably missing the obvious fix :)

---

### Post by SeijiSensei on 2011-05-26
First try "sudo apt-get -f install gimp" which may fix the problem on its own.  Otherwise you could install the missing dependency manually:

```
sudo apt-get install gimp libwebkitgtk-1.0-0
```

libwebkitgtk should have been installed automatically since it's in GIMP's dependency list, so the "-f" switch may fix the problem for you.

---

### Post by Jeroen De Dauw on 2011-06-06
Unfortunately that did not work, still getting the broken packages error.

```
jeroen@O:~$ sudo apt-get -f install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gimp : Depends: libwebkitgtk-1.0-0 (>= 1.3.10) but it is not going to be installed
E: Broken packages
```

```
jeroen@O:~$ sudo apt-get install gimp libwebkitgtk-1.0-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libwebkitgtk-1.0-0 : Depends: libwebkitgtk-1.0-common (>= 1.3.13) but it is not going to be installed
E: Broken packages
```

Any more ideas on how to fix this?

---

### Post by SeijiSensei on 2011-06-06
Try adding libwebkitgtk-1.0-common to the list of packages to be installed?  

The problem is called "broken dependencies."  A well-formed package includes a list of all other packages on which it depends so that apt can include them in the installation automatically.  The GIMP package you're trying to install doesn't seem to have the correct dependencies defined.

Are you installing GIMP from the normal repositories, or from some third-party location?  I've had no problems installing GIMP on Kubuntu 10.10 or 11.04, which makes me think you're trying to install it from somewhere else like a PPA.  Maybe you're trying to install 2.7 or 2.8?

If you get additional complaints about missing packages, just keep adding them to the installation list or, better yet, use the 2.6 package in the normal repositories.

---

### Post by Jeroen De Dauw on 2011-06-06
Adding that fixed it - I got Gimp installed now - thnx a lot for the help :)

I don't have any PPA for Gimp, just installed 2.6.

---

