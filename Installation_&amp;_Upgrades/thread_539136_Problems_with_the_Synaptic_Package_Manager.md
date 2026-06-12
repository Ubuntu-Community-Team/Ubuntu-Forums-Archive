---
title: "Problems with the Synaptic Package Manager"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by fulio on 2007-08-30
When ever i try to open Synaptic Package Manager i always get An error occured it says:
E: Type '"deb' is not known on line 44 in source list /etc/apt/source.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

and if i go to ADD/REMOVE applications i get "
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

can anyone please try to help me, im trying to uninstall steam

---

### Post by merlinus on 2007-08-30
Look at /etc/apt/sources.list for possible problems.

If nothing comes to mind, post it here.

-merlin

---

### Post by fulio on 2007-08-30
i tryd to open source.list and it wouldnt open.

---

### Post by Pumalite on 2007-08-30
Did you get an error?. If so, post it.

---

### Post by rsambuca on 2007-08-30
Copy and paste this into a terminal:```
cat /etc/apt/sources.list
```

---

### Post by fulio on 2007-08-30
There was no error . when i clicked it, it just didnt open i try it agn same thing.

---

### Post by Pumalite on 2007-08-30
If above rec doesn't work; in Nautilus or Konqueror go to /etc/apt and see if souces.lst exist.

---

### Post by fulio on 2007-08-31
yes it does exist. but its like pissing me off

---

### Post by Pumalite on 2007-08-31
Let's see if changing permissions we get something: in Terminal:
sudo chmod 777 /etc/apt/sources.list
cat /etc/apt/sources.list

---

### Post by lieuhon on 2007-10-11
I've got the same problem but fixed now.

It is very likely that your sorces.list file was corrupted. So do the following stpes:

 1. Go to [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic).  This is a sources.list file generator,  Follow the stpes to generate a sources.list file. Then save it as a text file (on the desktop would be handy!!)

2. Delete the original sources.list in /etc.apt (use sudo command)

3. Copy or move the new sources.list to /etc/apt

4. start the updater or the package manager again.

That what I did and it works.  Hopefully it will fix your problem.

Cheers
Lieu Hon

---

