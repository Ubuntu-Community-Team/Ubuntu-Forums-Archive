---
title: "Unattended ttf-mscorefonts-installer"
date: 2012-08-06
forum: Installation &amp; Upgrades
---

### Post by binaryoutlaw on 2012-08-06
I want to install ttf-mscorefonts-installer unattended.

I did some searching to find out how I can get "apt-get install" to assume yes to the EULA

I came across a post with what seemed like the solution
[http://askubuntu.com/questions/16225/how-can-i-accept-the-agreement-in-a-terminal-like-for-ttf-mscorefonts-installer](http://askubuntu.com/questions/16225/how-can-i-accept-the-agreement-in-a-terminal-like-for-ttf-mscorefonts-installer)

Made a file msttcorefonts.conf, inserted into it

**ttf-mscorefonts-installer msttcorefonts/accepted-mscorefonts-eula select true**

uploaded to a file storage account with direct link access, put it into my install sh script.

here is what I have so far
```

mk dir ~/working
cd ~/working
wget http://{myaccount}/msttcorefonts.conf
sudo /usr/bin/debconf-set-selections "~/working/msttcorefonts.conf"
sudo apt-get install ttf-mscorefonts-installer --quiet
```This doesn't work, the EULA still pops up.

Not sure what I did wrong, any help would be much appreciated.

---

### Post by zvacet on 2012-08-08
Did you tried to accept EULA?

---

### Post by binaryoutlaw on 2012-08-08
Automating and installation so it has to be able to accept itself or assume acceptance as default.

---

### Post by binaryoutlaw on 2012-08-19
bump

---

### Post by Hedgehog1 on 2012-08-19
May I offer an alternate solution?

When I need to install a large number of systems with Ubuntu, I do the following:

Create a small install (about 10-12 gigs) on a drive and setup all the applications and options you want.

Once I am happy with the install, I use the dd command to make an image of the install:

```
sudo dd bs=1M if=/dev/sdg of=/home/marc/Folding/shuttle8.img
```

Then I create as many HDD, SSD or USB sticks with the install that I need:

```
sudo dd bs=1M if=/home/marc/Folding/shuttle8.img of=/dev/sdg
```

Once I boot each 'replicate' system, I then change the name of the system by editing the name in these two files:

```
sudo nano /etc/hosts
sudo nano /etc/hostname
```

You can expand the install to fill a larger drive using gparted.

***The Hedge***

:KS

p.s. this is the method I use for [USB sticks for my server farm]("http://imageshack.us/photo/my-images/826/foldingfarm02.jpg/").

---

