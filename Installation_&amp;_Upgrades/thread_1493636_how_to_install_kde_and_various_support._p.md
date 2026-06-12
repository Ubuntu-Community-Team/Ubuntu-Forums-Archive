---
title: "how to install kde and various support. p"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by digvijay.pu on 2010-05-26
i have installed ubuntu 10.04 and want to install kde on it. please guide me how to do it. i also want to know how i can download various softwares using synaptic package manager.

---

### Post by dino99 on 2010-05-26
select the packages into synaptic to install them

remove/purge (right click) ubuntu-desktop, then install kubuntu-desktop

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get install -f

sudo dpkg --configure -a

---

### Post by kestrel1 on 2010-05-26
If you wanted the KDE Desktop, why not just install Kubuntu instead of Ubuntu.

---

### Post by cascade9 on 2010-05-26
> **dino99 said:**
> select the packages into synaptic to install them

remove/purge (right click) ubuntu-desktop, then install kubuntu-desktop


You dont have to remove ubuntu-dekstop to install kubuntu-desktop. 

I'd probably install kde-minimal myself, but I think I've seen kubuntu users here saying that kde-minimal is buggy.

---

### Post by drpjkurian on 2010-05-26
Hi
I am using both KDE and GNOME in my desktop. Please see the following link
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)
It will definitely help you out

---

### Post by unmole on 2010-05-26
> **drpjkurian said:**
> Hi
I am using both KDE and GNOME in my desktop. Please see the following link
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)
It will definitely help you out

+1 Psychocat's tutorial is the best I have seen to date.

---

