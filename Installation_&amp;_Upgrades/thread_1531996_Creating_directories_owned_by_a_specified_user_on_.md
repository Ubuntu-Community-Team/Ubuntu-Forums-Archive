---
title: "Creating directories owned by a specified user on SSD"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by dsub42 on 2010-07-15
Hi I have just  installed an SSD as a secondary hard drive and formatted as ext4. (the  Ubuntu installation is on a different drive)

Im very new to linux, Could someone inform me how I would go about  creating a directory on the SSD that is owned by the user 'Test user'

Im sorry if this is a daft question, im just moving from windows to  linux and struggling a lot.

Any help would be appreciated

---

### Post by mörgæs on 2010-07-15
Welcome to the free world!

Just add a user to the system with that name, log in as him and create the directory. 
The command **ls -l** will show you the contents of a directory along with the owner name.

Here is a good manual on Ubuntu:
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

---

### Post by dsub42 on 2010-07-16
> **mörgæs said:**
> Welcome to the free world!

Just add a user to the system with that name, log in as him and create the directory. 
The command **ls -l** will show you the contents of a directory along with the owner name.

Here is a good manual on Ubuntu:
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

but how do i create it on the ssd? how do i say create a directory but on that drive ... ubuntu is not installed on this drive

for example in windows, lets say windows was installed on the c drive ... i want to create a directory on the g drive..

---

### Post by dino99 on 2010-07-16
mountmanager is a nice tool ( into synaptic) to deal with partitions and devices

with ubuntu the partitions are identified as /dev/xxx, check them into a console with: fdisk -l

then with the file manager (nautilus) you can add dirs with the menu

---

