---
title: "installing wine"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by bruceleelinux on 2008-11-12
hi to all linux users.i have a problem in installing wine in ubuntu.my package is debian and for ubuntu 8.10 but when i install it this message will shown:error:depency is not satisfiable.
please help me to solve this problem i need wine urgently.
thanks very much

---

### Post by Partyboi2 on 2008-11-12
Welcome, what is the dependency that it is not satisfied?
Are you trying to install wine by add/remove? Or from a downloaded deb?

---

### Post by brucelinuxlee on 2008-11-19
> **Partyboi2 said:**
> Welcome, what is the dependency that it is not satisfied?
Are you trying to install wine by add/remove? Or from a downloaded deb?
hi to all ubuntu community.
its dependency is audiolib2 is not satesfiable
i download deb package for ubuntu 8.10 from internet and want to install it but this error appeared that mentioned.
i download source package but it has an error when configuring that says flex is not found
please help me i really need wine.
tnx

---

### Post by Partyboi2 on 2008-11-19
If you have internet connection you can open Applications>  add/remove and install wine or open a terminal (Applications>Accessories>Terminal) and type
```
sudo apt-get install wine
``` that will take care of the dependencies.

---

### Post by brucelinuxlee on 2008-11-25
> **Partyboi2 said:**
> If you have internet connection you can open Applications>  add/remove and install wine or open a terminal (Applications>Accessories>Terminal) and type
```
sudo apt-get install wine
``` that will take care of the dependencies.

ok thank u verymuch i hope it works.

---

### Post by arjay27529 on 2008-12-16
have attempted many variations of installation for wine.  package installer gave message:

error: dependency is not satisfiable: binfmt-support

then read this thread and tried:

sudo apt-get install wine  

result:

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
E: Broken packages

looks like binfmt-support is the villain, but as a linux newbie i have no idea what that is or how to correct it.  any suggestions?

---

### Post by Partyboi2 on 2008-12-16
Open a terminal and fix the broken package with
```
sudo apt-get -f install
```
then try to install binfmt-support by itself.
```
sudo apt-get install binfmt-support
```
then try installing wine again
```
sudo apt-get install wine
```

---

### Post by arjay27529 on 2008-12-18
partyboi2

many THANKS for the instructions.  i now have wine installed.  hopefully wont need any help in making it work, but we ll see.  

i would close this thread except thread tools dont give me that choice.  

hows the weather in australia?  winter is hitting the usa pretty hard early this year, but my garlic crop is up through the ground as it is supposed to be.  

again THANKS.

---

### Post by Partyboi2 on 2008-12-18
> **arjay27529 said:**
> partyboi2

many THANKS for the instructions.  i now have wine installed.  hopefully wont need any help in making it work, but we ll see.  

i would close this thread except thread tools dont give me that choice.  

hows the weather in australia?  winter is hitting the usa pretty hard early this year, but my garlic crop is up through the ground as it is supposed to be.  

again THANKS.
Good to hear you got it installed. With closing a thread only the original poster can mark their  thread solved. 
The weather here has been wet lately but hopefully soon it will be hot and sunny. \\:D/

---

