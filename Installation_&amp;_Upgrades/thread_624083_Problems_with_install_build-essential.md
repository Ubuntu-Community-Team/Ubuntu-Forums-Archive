---
title: "Problems with install build-essential"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by jandeman on 2007-11-26
I tried to install HPLIP on my PC with origional UBUNTU 7.10 +KUBUNTU and ran into the following problem 
see also end of  [https://answers.launchpad.net/hplip/+question/18598](https://answers.launchpad.net/hplip/+question/18598)

===========
sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

==============

What to do to resolve this?
Jandeman

---

### Post by oldos2er on 2007-11-26
Open Synaptic Package Manager, look under the 'Edit' menu, for 'Fix Broken Packages.'

---

### Post by jandeman on 2007-11-28
Fix Broken Packages does complete successful but does not solve the problem.[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by Pumalite on 2007-11-28
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

---

### Post by jandeman on 2007-11-28
Unfortunately also not solving the problem
libc6-dev wants 2.6.1-lubuntu9 and libc6 is 2.6.1-lubuntu10 as Synaptic shows me.

---

### Post by Pumalite on 2007-11-28
What kernel are you using?
Post:
uname -r

---

### Post by jandeman on 2007-11-28
Installed Ubuntu 7.10 with Kubuntu for KDE. Kernel is 2.6.22-14-generic

---

### Post by Pumalite on 2007-11-28
Build-essential for that kernel is in the repos and you shouldn't be having a dependency problem.

---

### Post by jandeman on 2007-11-28
Might be true that it I should not have problems, but I unfortunately I do.
libc6-dev is required but can not be installed:

sudo apt-get install libc6-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.6.1-1ubuntu9) but 2.6.1-1ubuntu10 is to be installed
E: Broken packages

---

### Post by Pumalite on 2007-11-28
You should start looking at all the packages that you installed and figured out which one is producing this conflict. I installed build essential in LinuxMint 4.0 with a 22-14-generic kernel yesterday without any problems. Have you use unapproved 3rd parties?

---

### Post by jandeman on 2007-11-28
I am not aware of any 3rd parties. The whole thing started as I wanted to start hplip, see first message. Anyway, I will have a check on the packages.

---

### Post by jandeman on 2007-11-29
Simple question:
Is there no libc6-dev bases on 2.6.1-lubuntu10, because this might solve the problem.
See the attached snapshot of synaptic

---

### Post by Pumalite on 2007-11-29
You don't loose anything installing it. I don't assure you it will solve the problem.

---

### Post by jandeman on 2007-11-30
Reinstall of Ubuntu 7.10 + kubuntu-desktop solved the problem - Faster than all searches:)

---

### Post by Pumalite on 2007-11-30
Good choice.

---

