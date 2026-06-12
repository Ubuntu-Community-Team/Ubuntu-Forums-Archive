---
title: "Can't upgrade to beta (from alpha 3)?"
date: 2010-03-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Naatan on 2010-03-19
My update manager has been empty for 2 days now, it shows 2 entries in the upgrade section but they are greyed out.

When I run dist-upgrade via the terminal I get:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  parted udisks
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

Anyone know what I should do ?

---

### Post by jppr on 2010-03-19
Why you don´t upgrade in synaptic?

---

### Post by Naatan on 2010-03-19
Managed to "update" the two packages mentioned by running:

$ sudo apt-get install libparted0

Still no new updates available in the update manager though.. :(

---

### Post by grandtoubab on 2010-03-19
> **Naatan said:**
> My update manager has been empty for 2 days now, it shows 2 entries in the upgrade section but they are greyed out.

When I run dist-upgrade via the terminal I get:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  parted udisks
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```Anyone know what I should do ?

If you are in alpha 3 no need to use dist-upgrade only
```
sudo apt-get update
``````
sudo apt-get upgrade
```

---

### Post by Naatan on 2010-03-19
> **grandtoubab said:**
> If you are in alpha 3 no need to use dist-upgrade only
```
sudo apt-get update
``````
sudo apt-get upgrade
```

I know that, I was using dist-upgrade as a last resort.

Neither upgrade nor dist-upgrade gives anything.

---

### Post by grandtoubab on 2010-03-19
> **Naatan said:**
> I know that, I was using dist-upgrade as a last resort.

Neither upgrade nor dist-upgrade gives anything.

so you are up to date :p  why do you think beta 1 is different of an alpha3 up to date ?

---

### Post by Uncle Spellbinder on 2010-03-19
I guess the March 18th Daily Build I installed yesterday was the Beta. No updates at all.

```
unclespellbinder@lucid:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
unclespellbinder@lucid:~$
```

---

### Post by Naatan on 2010-03-19
hmm ok.. I figured the beta would include at least a daily update.. guess not then. Oh well.

---

### Post by jppr on 2010-03-19
[http://feeds.ubuntu-nl.org/LucidChanges](http://feeds.ubuntu-nl.org/LucidChanges)

---

### Post by kansasnoob on 2010-03-19
I see you got the parted issue sorted but I was going to point you here:

[http://ubuntuforums.org/showpost.php?p=8956551&postcount=12](http://ubuntuforums.org/showpost.php?p=8956551&postcount=12)

Otherwise there probably are no updates currently.

Although you may want to check the version number of "libmysqlclient16" by running:

```
aptitude show libmysqlclient16|head -4
```

The correct version is **5.1.41-3ubuntu7**.

The **[COLOR="Red"]BAD[/COLOR]** version is **[COLOR="Red"]7.0.9-1[/COLOR]**.

That comes from the release notes:

> Security Issue when upgrading from Lucid Alpha 2

If you installed Lucid prior to Alpha 3, you may have libmysqlclient16 7.0.9-1 installed. This package was present in the Ubuntu archive by mistake and was retracted, but because it has a later version number than the real libmysqlclient16 package, the real package will not be installed automatically on upgrade. To ensure that you have the official package installed on your Lucid system and will receive security support for it throughout Ubuntu 10.04 LTS, it is important that you run sudo apt-get install libmysqlclient16/lucid and follow the instructions. 

Example:

```
lance@lance-desktop:~$ aptitude show libmysqlclient16|head -4
Package: libmysqlclient16
State: installed
Automatically installed: no
Version: 5.1.41-3ubuntu7

```

---

### Post by kansasnoob on 2010-03-19
> **Uncle Spellbinder said:**
> I guess the March 18th Daily Build I installed yesterday was the Beta. No updates at all.

```
unclespellbinder@lucid:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
unclespellbinder@lucid:~$
```

That's correct, at least regarding i386.

---

### Post by Naatan on 2010-03-19
Thanks kansasnoob, looks like I'm running the latest version then :)

---

### Post by rahilm on 2010-03-19
It says [_here_]("http://www.ubuntu.com/testing/lucid/beta1") that the beta sports complete removal of HAL. but HAL is still there when i did an upgrade from alpha 3

---

### Post by Uncle Spellbinder on 2010-03-19
"Complete removal" has been a misnomer for a while. While HAL is still installed, from what i understand, it is no longer used.

I'm sure if I'm wrong, someone will be along shortly to correct me.

---

### Post by sdowney717 on 2010-03-19
I did the dist-upgrade to lucid yesterday. Today when I run the command I only get this

> scott@scott-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  empathy-doc libempathy-common libempathy-gtk-common libempathy-gtk28
  libempathy30
The following NEW packages will be installed:
  empathy-common nautilus-sendto-empathy
The following packages will be upgraded:
  empathy
1 upgraded, 2 newly installed, 5 to remove and 0 not upgraded.
Need to get 1,462kB of archives.
After this operation, 2,232kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
scott@scott-desktop:~$ 


---

