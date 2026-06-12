---
title: "Ubuntu 10.04 Repository dvd not recognised"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by biswarupg on 2010-09-02
Hi, I have installed Ubuntu 10.04 Lucid Lynx on my PIV machine and I have a collection of 8 dvds containing full Lucid repository for ix86. Now I want to add those repositories in Synoptic. Plz suggest how can I use those repo dvds in my Ubuntu box.

---

### Post by biswarupg on 2010-09-02
Plz help! I want to install additional packages from Ubuntu repository and they are on dvds. I don't know how to add them as package source dvd. I've done this before in Debian by 'sudo apt-cdrom add' command. It's not working here.

---

### Post by shankara on 2010-09-02
Hi.

I only read about downloading and making off line copy of repository DVDs and not yet done.  Please follow the article whose link is given here below. Please go through carefully. Somewhere in the middle or near the end it has been given how to use the newly made DVDs of repositories. Concept is simple, adding your media, in the synaptic package manager, to look for installable files( new softwares). 

[http://ubuntuforums.org/showthread.php?t=352460](http://ubuntuforums.org/showthread.php?t=352460)

regards

---

### Post by schbonn on 2010-11-02
Open terminal and login as root:
```
su
```Mount the contents of the DVD to the mount point /cdrom by typing:
```
mount -t iso9660 /dev/sr0 /cdrom
sudo apt-cdrom add
```The DVD scan should begin by now!!

---

