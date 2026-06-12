---
title: "How to clean up system after upgrade?"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Stason on 2010-03-23
Each upgrade takes additional disk space although most of the packages are just updated and thus should not take too much additional space. How to clean this up and free some disk space?

---

### Post by cariboo on 2010-03-23
All the packages you downloaded during the upgrade are located in /var/cache/apt/archives. To clean them out open a terminal and type:

```
sudo apt-get clean
```

To remove any unneeded dependencies, in the same terminal type:

```
sudo apt-get autoremove
```

The two commands above help clear out a lot of packages not needed any more.

---

### Post by obscur156 on 2010-03-23
One word, BLEACHBIT . 
Nice little app that cleans a lot of crap.

It is in the repos.Software center synaptic or terminal.

sudo aptitude install bleachbit

Best regards.

---

### Post by KrazyPenguin on 2010-03-23
......... or Ubuntu-Tweak it!!!!!

---

### Post by jaoc223 on 2010-03-24
obscur156, I installed bleachbit via sudo apt-get, I noticed when you try to select the apt options, in my case anyway, bleachbit was not able to execute due to permissions in various apt directories. Is there a way to set it so you can do apt-clean and apt autoremove?
Thanks

---

### Post by _h_ on 2010-03-24
> **jaoc223 said:**
> obscur156, I installed bleachbit via sudo apt-get, I noticed when you try to select the apt options, in my case anyway, bleachbit was not able to execute due to permissions in various apt directories. Is there a way to set it so you can do apt-clean and apt autoremove?
Thanks

You have to run bleachbit as root in order to clean out those kinds of directories. Bleachbit doesn't exactly like to run as a normal user.

---

### Post by dino99 on 2010-03-24
> **jaoc223 said:**
> obscur156, I installed bleachbit via sudo apt-get, I noticed when you try to select the apt options, in my case anyway, bleachbit was not able to execute due to permissions in various apt directories. Is there a way to set it so you can do apt-clean and apt autoremove?
Thanks

hey, you have to understand how to use it: it's very powerfull and you need to read comments about each line, because it can wipe out settings, passwords, bookmarks ... and destroy your system if you check everything without plugging your brain first.

You can use it as Admin with root rights (see the menu list)

---

### Post by jaoc223 on 2010-03-24
Thanks for the heads up guys, I will take care when running bleachbit.

---

### Post by emarkay on 2010-03-24
Another positive endorsement for BleachBit - again, it can basically remove not only history and clutter, but anything you have added since your original install, other than the programs and apps themselves - think about it...  It's that powerful...

Also, I had an issue where it trashed the OS when I was using a Beta version so stick with the version in the repos unless you have time and PC's to spare... :

---

