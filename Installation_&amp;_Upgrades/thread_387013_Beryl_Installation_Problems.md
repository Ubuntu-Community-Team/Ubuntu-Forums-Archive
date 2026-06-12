---
title: "Beryl Installation Problems"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by peterpan_champ on 2007-03-17
I only been using Ubuntu for a few days and I decide to install beryl.

After I do everything on every how-to I could find, I try to install using "sudo apt-get install beryl emerald-themes" and I get this output:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
:~$ sudo apt-get install beryl emerald-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  beryl: Depends: beryl-core but it is not going to be installed
         Depends: libberylsettings0 but it is not going to be installed
         Depends: beryl-plugins but it is not going to be installed
         Depends: beryl-settings but it is not going to be installed
         Depends: beryl-manager but it is not going to be installed
  emerald-themes: Depends: emerald (>= 0.1) but it is not going to be installed
E: Broken packages


I also try to use the synaptic package manager and got basically the same thing.  

If anyone could give me some feedback on this problem it would be much appreciated.

---

### Post by adam.tropics on 2007-03-18
Looks like 2 problems. 1) You are trying to install from the command line while synaptic is open. You need to have synaptic closed if you wich to install from the command line. and 2) A broken package.

First open synaptic. Then go to the edit menu. You will find 'fix broken packages'. It will probably uninstall the offending package when you hit Apply. The when thats done, select the packages you wish to install again, and hit apply. If you want to install them from the command line, just close synaptic first.

---

### Post by peterpan_champ on 2007-03-18
Thanks for the info.  And I did have synaptic close while running the command line.  I tried synaptic after I couldn't get the command line to work.  But I will try what you said and hope it works out.  Thanks again.

---

### Post by adam.tropics on 2007-03-18
> **peterpan_champ said:**
> Thanks for the info.  And I did have synaptic close while running the command line.  I tried synaptic after I couldn't get the command line to work.  But I will try what you said and hope it works out.  Thanks again.

All good...while I'm at it the same applies to Update manager.

---

### Post by peterpan_champ on 2007-03-18
I tried what you said and I'm getting the same thing.  

The following packages have unmet dependencies:
  beryl: Depends: beryl-core but it is not going to be installed
         Depends: libberylsettings0 but it is not going to be installed
         Depends: beryl-plugins but it is not going to be installed
         Depends: beryl-settings but it is not going to be installed
         Depends: beryl-manager but it is not going to be installed
  emerald-themes: Depends: emerald (>= 0.1) but it is not going to be installed
E: Broken packages


Any other ideas?

---

### Post by russo.mic on 2007-03-18
I'm getting the same thing on a beryl-settings and such.  I think the repos are broken.

Give it some time.

---

### Post by peterpan_champ on 2007-03-18
Alright man, I'll do that.  

Thanks

---

