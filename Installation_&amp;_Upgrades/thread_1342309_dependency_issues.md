---
title: "dependency issues"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by jaden93 on 2009-11-30
hello. recently i had to reinstall Ubuntu 9.10 because i had a certain issure, but that is not my problem. my problem is when i reinstalled ubuntu. when i reinstalled ubuntu and had everything running i had several missing dependenies. i never had this problem before, thats why i feel somthing is wrong. can you please explain to me what happened and why im missing so many dependency packages, and if i should reinstall ubuntu or not.

---

### Post by NoaHall on 2009-11-30
Can you run ```
sudo apt-get update && sudo apt-get upgrade
``` and list any problems please?

---

### Post by jaden93 on 2009-11-30
i had no problems running the command, but when i try to download somthing that i KNOW i should be able to download (like sun java6 and other programs) it won't work.

---

### Post by NoaHall on 2009-11-30
How are you downloading them?
Can you run ```
sudo apt-get install programname
```
where program name is the name of a program which doesn't download?
Post the output for me.

---

### Post by jaden93 on 2009-11-30
here's what i get when i try to download a package like dockbarx 
```
jade@jadez-comp:~$ sudo apt-get install dockbarx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  dockbarx: Depends: python-gnome2-desktop but it is not installable
            Depends: python-numpy but it is not installable
E: Broken packages

```

then this is what i get when i try to download the dependencies 

```
jade@jadez-comp:~$ sudo apt-get install python-gnome2-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-gnome2-desktop is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package python-gnome2-desktop has no installation candidate
```

---

### Post by mickie.kext on 2009-11-30
On top panel go to 

System ---> Administration ---> Software sources

and in "downdload from" select some another server. You can click "other" and then select manualy, any will do.

---

### Post by jaden93 on 2009-11-30
wow, thank you it worked. you were a big help. :)

---

