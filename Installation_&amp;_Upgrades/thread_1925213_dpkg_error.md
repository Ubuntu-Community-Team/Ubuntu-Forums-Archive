---
title: "dpkg error"
date: 2012-02-14
forum: Installation &amp; Upgrades
---

### Post by Bray90820 on 2012-02-14
so i was using ubuntu and i tried to remove a package from the software center but it wont remove it has an error so i went to the terminal and tried to remove it and i got this output I am on ubuntu 11.10 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  tightvnc-java kwalletmanager dkms libuser1 python-libuser
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  samba system-config-samba
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 29.5 MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: file triggers record mentions illegal package name `libglib2.0-0:i386' (for interest in file `/usr/lib/i386-linux-gnu/gio/modules'): character `:' not allowed (only letters, digits and characters `-+._')
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

---

### Post by raghaven.kumar on 2012-02-14
Did you try
```
sudo apt-get -f install
```

---

### Post by cortman on 2012-02-14
Did you manually change the name of the file libglib2.0-0:i386? It looks like it has a wrong name. If raghaven.kumar's suggestion doesn't fix it, you could manually remove and reinstall the package.

---

### Post by Bray90820 on 2012-02-14
sudo apt-get -f install gave me this readout 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  tightvnc-java kwalletmanager dkms
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
dpkg: file triggers record mentions illegal package name `libglib2.0-0:i386' (for interest in file `/usr/lib/i386-linux-gnu/gio/modules'): character `:' not allowed (only letters, digits and characters `-+._')
E: Sub-process /usr/bin/dpkg returned an error code (2
```

---

### Post by cortman on 2012-02-14
Hm, odd. Run

```
sudo rm -r /var/lib/apt/lists/*
```

and be sure to copy/paste this code- don't mistype it as it has the potential to wipe your system if you get something wrong. Then run

```
sudo apt-get update
```

And see if you still get the error.

---

### Post by Bray90820 on 2012-02-14
i still get the same error what i think happend is somehow /usr/bin/dpkg got removed

---

### Post by cortman on 2012-02-14
The dpkg program still exists- as your original post said, the process ran but returned an error code. The binary for the dpkg program is located in /usr/bin, if you want to check for yourself.
Ok, here's another try. Open a terminal as root, using

```
gksu nautilus
```

and search for 

```
libglib2.0-0:i386
```

If you find a file with this name, delete it, then go back and run the commands given previously, in the order given.
It could be that I'm barking up an entirely wrong tree here, but it's a possible solution.

---

### Post by Bray90820 on 2012-02-14
it seems as if that file can not be found

---

### Post by cortman on 2012-02-14
Ok, like I thought, I WAS barking up the wrong tree. Sorry for the wasted time.

Here's the real fix: You need to edit the /var/lib/dpkg/triggers/File. Somehow an illegal character (in this case, a colon) crept in. Open it as root by running

```
gksu gedit /var/lib/dpkg/triggers/File
```

Then click the magnifying glass icon in gedit, and search for a colon- ':'. Delete all occurrences and save the file, then run

```
sudo apt-get update
```

---

### Post by Bray90820 on 2012-02-14
i got tired of dealing with it it seemed like once i fixed one problem another one poped up so i just went ahead and reinstalled thinks for your help

---

