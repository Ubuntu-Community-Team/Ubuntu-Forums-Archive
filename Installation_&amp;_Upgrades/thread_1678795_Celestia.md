---
title: "Celestia"
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by TimmyK. on 2011-01-31
Hello. I have Celestia running on Ubuntu 10.10 and I just downloaded some textures for the moon and some other planets from the Celestia motherlode. It says I need to replace some files in the Celestia resources folder. How do I get to this folder?

---

### Post by Morat on 2011-02-09
> **TimmyK. said:**
> Hello. I have Celestia running on Ubuntu 10.10 and I just downloaded some textures for the moon and some other planets from the Celestia motherlode. It says I need to replace some files in the Celestia resources folder. How do I get to this folder?

If you do the following command in a console:
```
find / -name celestia -print
```
it will show you all the locations of any file or folder called 'celestia'. On my system I get this (along with a shed-load of access denied messages if you don't run it with root privilages):
```
/usr/share/celestia
/usr/share/apps/celestia
/usr/share/doc/celestia
/usr/share/doc/kde/HTML/en/celestia
/usr/bin/celestia
/etc/alternatives/celestia
/home/alistair/.kde/share/apps/celestia
/var/lib/dpkg/alternatives/celestia
```
From my playing around with it last night, the location you want is probably /usr/share/celestia. Textures go into the 'textures' folder in there. There is a sub-folder for each of the low, medium and hi-res textures.

--- Alistair

---

### Post by Frogs Hair on 2011-02-09
I don't know if any of this is helpful on Linux or not , but may worth looking at . 
[http://www.celestiamotherlode.net/catalog/documentation.html](http://www.celestiamotherlode.net/catalog/documentation.html)

---

### Post by TimmyK. on 2011-02-14
OK, one final problem: I do not have permission to edit anything in the Celestia folder. How do I change the permissions for the folder?

---

### Post by Morat on 2011-02-15
> **TimmyK. said:**
> OK, one final problem: I do not have permission to edit anything in the Celestia folder. How do I change the permissions for the folder?

'sudo' is your friend.

In case you don't know, sudo stands for [s]uper [u]ser [do]. If, on the command line, you prefix a command with 'sudo', Ubuntu will prompt you for your password to confirm permissions and, as long as you are in a list of people allowed to use sudo (which you will be), that command will be run with super-user permissions.

So, assuming you have your hi-res textures in a folder called hires, then on the command line type:
```
sudo cp hires/* /usr/share/celestia/textures/hires
```

If you want to use the file browser (nautilus), you can do that too:
```
sudo nautilus
```

--- Alistair.

---

