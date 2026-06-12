---
title: "More Wine issues... [Gutsy]"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by indiechixor on 2007-11-03
So I had tried to install WoW using Wine under Feisty, and had some issues...

Well I just installed Gutsy, and now i have a new set up errors.

I followed the very easy install steps, with no issues..then when i try to run sudo apt-get install wine, I get this error

```
root@Hikaru:/home/indie# sudo apt-get install wine
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
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: libaudio2 but it is not installable
E: Broken packages
root@Hikaru:/home/indie# 

```

I already ran 
wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
and 
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list
along with sudo apt-get update...

any help would be lovely!

---

### Post by zvacet on 2007-11-03
**synaptic>edit>fix broken packages**

---

### Post by rafar on 2007-11-05
The synaptic fix broken packages did not work for me either. 
I'm using fresh new installation of Gutsy 7.10. 

[INDENT]Error message:
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: ia32-libs (>= 1.6) but it is not installable
        Depends: lib32asound2 (> 1.0.14) but it is not installable
        Depends: libc6-i386 (>= 2.6-1) but it is not installable
E: Broken packages
[/INDENT]

Thanks for suggestions.

---

### Post by minglis on 2008-03-03
Hi, I'm new here and I'm not sure if this has now been answered anywhere else, but I had this problem and found a solution so thought I might update this post for the answer as well. The issue is that it is trying to install a package that it is not allow to by default...

to fix this go to Synaptic Package Manager -> Settings -> Repository -> and enable 'universe'
Once done, reload the package information and try to install wine again.

This worked for me. I was then able to install wine with no problem.

---

