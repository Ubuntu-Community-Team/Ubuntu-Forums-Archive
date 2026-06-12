---
title: "installing barry step by step in ubuntu 12.04"
date: 2012-07-20
forum: Installation &amp; Upgrades
---

### Post by orosman on 2012-07-20
I'm trying to setup or install barry on ubuntu 12.04 laptop to be able to sync my blackberry to thunderbird or evolution as I would to do on windows, but I'm struggling to do so. I really need a step by step way to setup or install barry so that I can sync my barry to thunderbird or evolution 100% and proper. I've tried looking on the internet, but can't find proper step by step in installing barry. I've tried linberry, but doesn't have the feature in syncing your calendar, contacts and so on to thunderbird or evolution. From what I understand on sites on the internet, that this quite possible. Please assist me in this.
:(

---

### Post by dino99 on 2012-07-20
open a terminal and run:

sudo apt-get install barrydesktop

if you then still have some trouble, here is an old thread about it in case of needs

[http://ubuntuforums.org/archive/index.php/t-854716.html](http://ubuntuforums.org/archive/index.php/t-854716.html)

---

### Post by Sofox on 2012-08-28
I hate bumping threads, but I'm having the same problem and " sudo apt-get install barrydesktop" just doesn't work: 

```
$  sudo apt-get install barrydesktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package barrydesktop is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'barrydesktop' has no installation candidate

```

Now I have been doing some deb installing, so maybe not everyone will get this exact message, but the fact is barrydesktop no longer seems to be available in the repositories.

---

### Post by wnafm1 on 2012-09-12
I just ran across this exact same thing.

Edit your /etc/apt/sources/list and remove the line that points to,

[http://download.barry.netdirect.ca](http://download.barry.netdirect.ca)

Add the following,

deb [http://ftp.ca.debian.org/debian](http://ftp.ca.debian.org/debian) sid main

From terminal run,

sudo apt-get update

Then,

sudo apt-get install barrydesktop


Hope this helps!

---

### Post by tweaked on 2012-09-22
> **wnafm1 said:**
> I just ran across this exact same thing.

Edit your /etc/apt/sources/list and remove the line that points to,

[http://download.barry.netdirect.ca](http://download.barry.netdirect.ca)

Add the following,

deb [http://ftp.ca.debian.org/debian](http://ftp.ca.debian.org/debian) sid main

From terminal run,

sudo apt-get update

Then,

sudo apt-get install barrydesktop


Hope this helps!

One thing wrong in 12.04.

/etc/apt/sources/list should read /etc/apt/sources.list

For the code line averse, it is easy to click Applications>System Tools>Administration>Update Manager>Settings>Other Sources

---

### Post by 6541984 on 2013-01-27
<strike>Oh, this is #$%&^ annoying.</strike>

---

### Post by 6541984 on 2013-01-29
I checked the site and followed instructions:

[http://www.netdirect.ca/software/packages/barry/installdebian.php](http://www.netdirect.ca/software/packages/barry/installdebian.php)

I added:

*deb [http://download.barry.netdirect.ca/barry-latest/](http://download.barry.netdirect.ca/barry-latest/) ubuntu1204 main*

Then, I did these too:
[I]gpg --keyserver pgp.mit.edu --recv-key B6C2250E
gpg --armor --export B6C2250E > barry.key
sudo apt-key add barry.key[/I]

I ran the update:
*sudo apt-get update*

Well, this line DOES NOT WORK, "unable to locate,"
*sudo apt-get install barrydesktop*

---

