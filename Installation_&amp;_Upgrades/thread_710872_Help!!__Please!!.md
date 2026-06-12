---
title: "Help!!  Please!!"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by Drewmanfuu on 2008-02-28
I recently installed ubuntu on an old laptop with no CD-ROM drive via Unetbootin and i got thru the installation but when i booted ubuntu everything was in command prompt not like a desktop like a normal computer. I have no clue what to do, can anyone help?

---

### Post by Bubba64 on 2008-02-29
I most likely can't help you but post your computers specs and the program you downloaded the people who can help you will probably respond with more information faster, good luck

---

### Post by Wake Rider on 2008-02-29
I'm not exactly sure if this will work, others please correct me if I'm wrong:

sudo aptitude install gnome 

or

sudo apt-get install gnome

That should install gnome, a gui

or if you want kde

sudo aptitude install kde

or 

sudo apt-get install kde

---

### Post by zvacet on 2008-02-29
After you login type** startx**.If that doesn´t give you GUI  type 

```
sudo nano /etc/apt/sources.list
```

and add this line 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe multiverse

Ctrl+o(this will save file)>Enter>Ctrl+x (exit file)

```
sudo apt-get update && sudo apt-get upgrade
```

To install GUI

```
sudo apt-get install ubuntu-desktop
```

For KDE

```
sudo apt-get install kubuntu-desktop
```

and if you have less then 256MB of ram 

```
sudo apt-get install xubuntu-desktop
```

---

