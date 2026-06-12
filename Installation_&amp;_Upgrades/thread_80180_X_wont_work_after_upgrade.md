---
title: "X wont work after upgrade"
date: 2005-10-21
forum: Installation &amp; Upgrades
---

### Post by Nasso on 2005-10-21
I cant get xorg to work after i upgraded hoary -> breezy. 
All i get is a dialog that tells me that it couldnt start and it asks me if i want to see the logs. I cant select anything though and in i few seconds the dialog becomes the "background" of the terminal and everything i type in with the keybord happends in the terminal.

is there any easy way to reinstall the entire x-system using apt?
im kind of handicapped without synaptic :)

---

### Post by Kyral on 2005-10-21
Its nothing so drastic. All you have to do is a quick reconfigure of your Drivers (NVidia or ATI?) and X.

For NVidia its "sudo dpkg-reconfigure nvidia-glx"

For X its "sudo dpkg-reconfigure xserver-xorg"

Then just restart X with

sudo /etc/init.d/gdm restart

---

### Post by Nasso on 2005-10-21
i got ati, how does the command look then?

---

### Post by Kyral on 2005-10-21
Install the package fglrxconfig (or something close to that, do an "apt-cache search fglrx" if thats not the name) and then "sudo fglrxconfg". Its VERY detailed, allows you to trick out every option of your ATI card

---

### Post by Kyral on 2005-10-21
Oh the install command is

sudo apt-get install <packagename>

---

