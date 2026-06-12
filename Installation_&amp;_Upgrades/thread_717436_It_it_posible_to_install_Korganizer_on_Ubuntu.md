---
title: "It it posible to install Korganizer on Ubuntu?"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by AQ_LIVE on 2008-03-07
Hi eneryone

I've been using Kubuntu and got pritty fond of the Korganizer. Then I changed to Ubuntu and I can't seem to install Korganizer on ubuntu. Does anyone know how to work arround this issue?

I would like to be able to use Korganizer but on my Ubuntu installation.

Hope to hear from you wissards :)

---

### Post by zvacet on 2008-03-07
I don´t use Kubuntu but I don´t see any problem.Package is in synaptic.Just install it.

---

### Post by kellemes on 2008-03-07
> **AQ_LIVE said:**
> Hi eneryone

I've been using Kubuntu and got pritty fond of the Korganizer. Then I changed to Ubuntu and I can't seem to install Korganizer on ubuntu. Does anyone know how to work arround this issue?

I would like to be able to use Korganizer but on my Ubuntu installation.

Hope to hear from you wissards :)

What's not going right?
You can use synaptic like previous poster said..
or you can type the following from terminal..
```
sudo apt-get install korganizer
```

---

### Post by Sef on 2008-03-07
> 
Code:

sudo apt-get install korganizer



Before using sudo ap-get install  program_name, update the repositories first:

```
sudo apt-get update
```

---

### Post by marckie on 2008-03-07
> **Sef said:**
> Before using sudo ap-get install  program_name, update the repositories first:

```
sudo apt-get update
```

I agree with them... If it is in the Repo then there'll be no problem at all. But before anything else do

```
sudo apt-get update
sudo apt-get upgrade 
```

then

```

sudo apt-get install korganizer
```

---

### Post by j0nn0 on 2008-03-07
Chances are this will also install most of KDE at the same time, as it will need some of the libraries that the rest of KDE runs on (QT etc.), so be prepared for a lengthy download <not an expert opinion, just a guess!> 

If you have a decent connection, why not download the kdesktop meta-package while you're about it?  Then you will have the option of choosing a fine, friendly KDE desktop at login, instead of a bland, boring gnome one!   (just kidding, gnomesters!)

---

