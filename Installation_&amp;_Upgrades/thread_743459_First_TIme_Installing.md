---
title: "First TIme Installing"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by syntheticz on 2008-04-02
I decided that I needed to learn how to install software on Ubuntu that is not present in synaptic, I decided that I would like to install a program called avant-window-navigator.

This is where I downloaded the package from

[http://code.google.com/p/avant-window-navigator/](http://code.google.com/p/avant-window-navigator/)

I then followed the instructions here

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

However, when I tried to run the script "./config" it said that I needed 2 packages.
The first one I found on Synaptic
The second which is called "gconf-2.0" I cannot find on synaptic, I tried installing the ones that sounded similar when I searched "gconf" but to no success. 

Am I right in thinking that I need to add something called a repository so Synaptic can find it? If so what is a repository and how can I find and install it?

Thanks

---

### Post by annda on 2008-04-02
hi,

you don't need to install AWN from source. it is in repositories so you can use those wiki instructions:
[http://wiki.awn-project.org/DistributionGuides#Ubuntu](http://wiki.awn-project.org/DistributionGuides#Ubuntu)

also you might want to check out ths links:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) (very old, but you can get the idea)

---

### Post by Crafty Kisses on 2008-04-02
With 7.10, I think AWN is in the repositorys.

---

### Post by Pumalite on 2008-04-02
First add  AWN repo: (this is a two-line command, paste the entire thing into the terminal at once.)
Code:

echo 'deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator' | sudo tee -a /etc/apt/sources.list

Then add the apt key:
Code:

wget [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)
sudo apt-key add reacocard.asc
rm reacocard.asc

Then install AWN:
Code:

sudo apt-get update
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bz

---

### Post by wireddad on 2008-04-02
You can also get it from [http://www.getdeb.net/](http://www.getdeb.net/)

---

### Post by moonbeam on 2008-04-02
As an awn/awn-extras developer I'd just like to make a couple comments.

First the code.google.com awn repository has been abandoned for several months and has extremely outdated code.

I recently wrote a post in another thread that has some other relevant info.

[http://ubuntuforums.org/showpost.php?p=4638557&postcount=10](http://ubuntuforums.org/showpost.php?p=4638557&postcount=10)

What is comes down to... we recommend binary repos for Ubuntu Gnome users, specifically the official Gutsy repo (if you don't want applets), reacocard's ppa repo, or the awn-testing ppa repository.

---

### Post by syntheticz on 2008-04-02
I tried entering the codes and doing what it said on the wiki and it says that it cannot find the package  :S

---

### Post by syntheticz on 2008-04-02
Ah so that could be why it is not working? 

So how would I add the repos?

---

### Post by moonbeam on 2008-04-02
> **syntheticz said:**
> Ah so that could be why it is not working? 

So how would I add the repos?

Reacocard's tutorial has excellent step by step instruction (including adding the repos)  if there is some discomfort with the process:   [http://ubuntuforums.org/showthread.php?t=385981&highlight=avant+window+navigator](http://ubuntuforums.org/showthread.php?t=385981&highlight=avant+window+navigator)

I can't recommend Reacocard's support thread enough for those who are new to the process.

---

