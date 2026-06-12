---
title: "evolution"
date: 2006-10-02
forum: Installation &amp; Upgrades
---

### Post by hvaughn on 2006-10-02
when entering sudo apt-get install hotway hotsmtp

i get:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package hotway

what am i doing wrong?

thanks

---

### Post by unisol on 2006-10-02
try downloading it from [http://sourceforge.net/projects/hotwayd/](http://sourceforge.net/projects/hotwayd/)

---

### Post by hvaughn on 2006-10-02
dumb question...but which one. there are 3 .rpm files and a .bz2 and a .gz file.

---

### Post by henriquemaia on 2006-10-02
Hummmmmmmmm. Looks like you don't have the right repositories enabled.

I have tried to install hotway myself and the package was available. 

Do you have multiverse enabled?

---

### Post by hvaughn on 2006-10-02
multiverse? 
don't know.
what's that?

---

### Post by henriquemaia on 2006-10-02
Ok. Do this:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```This will backup your file of your repositories.

Then do:

```
sudo gedit /etc/apt/sources.list
```Now, in gedit, look for the entries with **universe** in it and add **multiverse** after it.

Like this:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse main restricted

Check if they are not commented out (with a **#** before it).

Save the file. Close gedit. Then do:

```
sudo aptitude update
```Then:

```
sudo aptitude install hotway
```

---

### Post by henriquemaia on 2006-10-02
I was reading other thread and I found this link:

[https://help.ubuntu.com/community/Repositories/Ubuntu#head-a86dddc6826cec4a3847d8441b24051d07b8dc64](https://help.ubuntu.com/community/Repositories/Ubuntu#head-a86dddc6826cec4a3847d8441b24051d07b8dc64)

It's much easier to follow than my dull explanation. Follow that and then try to install hotway.

---

