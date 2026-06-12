---
title: "Trouble Installing Wine"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by Taslia on 2008-01-27
Hello all, I am an Ubuntu newbie so please excuse me.

I went into terminal and typed the following:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

sudo apt-get update

--------------------------

I then tried to go into Applications > Add/Remove Applications in order to install Wine on my Ubuntu. Wine is on the list, but when I check it, I get the following message:
```

Cannot install 'wine'

This application conflicts with other installed software. To install 'wine' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.
```

--------------------------

I then go into the Synaptic Package Manager to try and solve the problem BUT, I get the following error:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

Any clue on what's wrong?

---

### Post by Rocket2DMn on 2008-01-27
Do the command it says, then install wine
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install wine
```

---

### Post by gvartser on 2008-01-27
A tip is to always check with the repository before trying to compile and install an application manually.

This is much easier as someone else has created a package for you, and you do not have to compile or having the chance of missing out on some important dev libs etc. 

Then its not said that if you want to learn, of course its an good idea to try to compile yourself.

And another reason to compile your self is that sometimes you would want the latsest version, and you do not always get that from the repositories.

Use Synaptic package manager and perform a search for the application you want or use apt-cache.

```
apt-cache search <application>
```

/g

---

### Post by Taslia on 2008-01-27
Okay, I have installed Wine. Now, I want to download my Adobe Photoshop CS 2. When I go to it, right click, there is no option to "Open with Wine" and when you select other applications, Wine is not on that list. 

What do I do now? Thanks for all the help, which is greatly appreciated.

---

### Post by zvacet on 2008-01-27
>  and when you select other applications, Wine is not on that list

But on the right you have browse box.Use it to find Wine.it is in** usr/bin**.

---

### Post by Rocket2DMn on 2008-01-27
Navigate to the directory in terminal where you have the installer file for photoshop and run it with the command "wine"
```
wine *PhotoShopInstaller.exe*
```
If the file is an msi instlal file, run
```
msiexec /i *PhotoShopInstaller.exe*
```
Naturally, replace *PhotoShopInstaller.exe* with the name of the real install file.

---

### Post by zvacet on 2008-01-27
One more solution is to go to the home direcrory>view<show hidden files>.wine and copy your exe in Program Files.after that go to the programs<accessories>winefile>C>Program Files<double click on exe.

---

