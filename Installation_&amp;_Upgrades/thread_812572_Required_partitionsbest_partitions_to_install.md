---
title: "Required partitions/best partitions to install"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by klemencic on 2008-05-30
I have just brought a 300GB drive which I intend to use for Ubuntu - clean install and I am looking for information as to what partitions are required and what size
I have googled this and most sites recommend 2GB swap partition (I have 1GB ram,)a 100mb root partition and the rest as /home, I was also thinking of a couple of 20GB partitions for virtual machines
Should I aso have a seperate /usr patition?
I want to set this drive up so if I have a problem or install a new version, I can do this upgrade without have to reinstall any additional packages and games that I have installed
Appreciate any thoughts and comments

---

### Post by pytheas22 on 2008-05-30
> I want to set this drive up so if I have a problem or install a new version, I can do this upgrade without have to reinstall any additional packages and games that I have installed

Then right, you'd want /usr and /home on separate partitions--installed applications will be in /usr and your personal preferences and settings will be in /home.  If you have to reinstall the system, just keep the /usr and /home partitions the same without reformatting and everything will be preserved pretty transparently.

You don't really need to make a separate partition for virtual machines as long as you store them in your /home directory (which I think vmware and Virtual Box will do by default); they won't be erased during a reinstall.  I also don't really think it's necessary to have /root on its own partition, especially on Ubuntu, where root barely exists.  And yes, 2GB is good for swap.

---

### Post by marufaberlin on 2008-05-30
under debian-based systems I would also recommend several gigs as /opt/ and /var/ as apt caches some files there.

---

