---
title: "installation problem in adobe flash player"
date: 2012-11-19
forum: Installation &amp; Upgrades
---

### Post by coolguysraju on 2012-11-19
Hi everyone,
         Recently i try to install adobe flash plugin from ubuntu software center when i click install it will show the error in new window like:


"Package dependencies cannot resolved
This error could be required additional software packages which are missing or not installable.Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

Details
the following packages have unmet dependencies:

flashplugin-installer:"


How can i  install flash player,  if there is another way plz tell me with full procedure.

---

### Post by zvacet on 2012-11-20
In Ubuntu software center>edit>software repositories and be sure you have universe and multiverse repositories enabled.After that close and run 

```
sudo apt-get update
```

I think it will be good to install synaptic package manager.

```
sudo apt-get install synaptic
```

Then in synaptic search box type flashplugin-installer and when you find it install it.I hope that is all you will have to do.

---

### Post by ibjsb4 on 2012-11-20
If zvacet solution does not work, try installing it in terminal.  This will give you a detailed error report to help troubleshoot the problem.

sudo apt-get install flashplugin-installer

---

### Post by coolguysraju on 2012-11-21
sudo apt-get install flashplugin-installer

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 flashplugin-installer : Depends: libnspr4-0d but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by ibjsb4 on 2012-11-21
Two things to try ..

sudo apt-get install -f

If thats a no go, libnspr4-0d should be part of a bigger package which should be installed anyhow.  It contains restricted video formats.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

