---
title: "problem about apt-get install aptitude"
date: 2011-04-23
forum: Installation &amp; Upgrades
---

### Post by float_c on 2011-04-23
i want to install aptitude using apt-get, but some problems happen like this


The following packages have unmet dependencies:
 aptitude : Depends: libapt-pkg-libc6.10-6-4.8
            Depends: libept0 (>= 0.5.30) but it is not going to be installed
E: Broken packages


(before do this ,i have used command apt-get update and apt-get upgrade)
so,could someone  tell me how to handle this.

---

### Post by KegHead on 2011-04-23
Hi!

Did you try;


sudo apt-get install aptitude

KegHead

---

### Post by KegHead on 2011-04-23
Hi!

Also try;

system...admin...synaptic package manager..

Type in "aptitude"

Install.

KegHead

---

### Post by float_c on 2011-04-23
> **KegHead said:**
> Hi!

Did you try;


sudo apt-get install aptitude

KegHead


thank you,but i try all that using root..

---

### Post by KegHead on 2011-04-23
Hi!

How about post #3?

KegHead

---

### Post by dino99 on 2011-04-23
To fix broken packages

        Choose Edit > Fix Broken Packages from the menu.

        Choose Apply Marked Changes from the Edit menu or press Ctrl + P.

        Confirm the summary of changes and click Apply. 

If that does not help, then please follow this procedure:

[https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

note: using apt-get is far better than using aptitude (not the same features AND their databases are different so can conflict if the user use them both alternatively.)

---

### Post by varunendra on 2011-04-24
> **float_c said:**
> Depends: libept0 (>= 0.5.30) but it is not going to be installed

I recently read in some post that this kind of version limitations are a result of default availability of modules only upto a certain level for a certain version of OS. For example, by default the module version >= 0.5.30 will only be available for Ubuntu 10.10 and higher.

So if a user is using Ubuntu 10.04 or lower, either he should upgrade to Ubuntu 10.10, or should manually install all the dependencies to satisfy dpkg. This may cause extra headache of finding all dependencies and install them in correct sequence. Plus this may also cause (potentially) some incompatibility issues with other modules (or maybe even with the kernel itself), although I've done it successfully many times before.

---

