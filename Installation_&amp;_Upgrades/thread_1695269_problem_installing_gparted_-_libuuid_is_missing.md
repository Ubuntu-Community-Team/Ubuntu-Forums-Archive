---
title: "problem installing gparted - libuuid is missing"
date: 2011-02-25
forum: Installation &amp; Upgrades
---

### Post by SaaTeeVaaGreen on 2011-02-25
Hi all,

ive been trying to install gparted (from source) but configure fails with the error

```
configure: error: *** uuid library (libuuid) not found
```

which is odd because it looks like libuuid is installed, i think its installed as part of e2fsprogs which is installed (according to synaptic). Does anyone know how i might resolve this? or is it safe to compile anyway?

as a side question, i was going to install with synaptic, but the version of gparted there was 0.6.2 while the version on the website was 0.8.0. i tried apt-get update and apt-get upgrade but the package manager version was always 0.6.2. is it usual for the package manager version to be out of step like this, or is there something else i could have done to update it?

thanks

---

### Post by thefasterblueone on 2011-02-25
First thing I would like to say is, you cannot partition a mounted partition, so having the newest version installed on your harddrive won't do you much good. You will still need to use a live cd.


With that said, to get a clean start:

```
sudo apt-get remove gparted
```


To make sure you have all the tools to compile:

```
sudo apt-get install build-essential
``` 


To make sure you have all the dependencies for gparted:

```
sudo apt-get build-dep gparted
``` 

Then install gparted from source.

---

### Post by SaaTeeVaaGreen on 2011-02-28
First thing i would like to say is thanks for trying to help, i appreciate all help and advice i receive on this site.

that said i find it a little patronizing that you feel the need to state the obvious as the first line of your reply. especially since i hadnt said anything about wishing to partition a drive, mounted or otherwise. there are a number of other things i can do with gparted, and there are a number other drives on my computer. i know when i can use the gui and when i need a live cd.

moving on, thanks again for the suggestion but, after trying, i am still getting the same "libuuid is missing" configure error. can you or anyone else think of anything else i might try?

thanks again all:)

---

