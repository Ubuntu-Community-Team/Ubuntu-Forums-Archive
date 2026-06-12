---
title: "Kickstart update"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by SkyHiRider on 2010-04-28
I want to automate reinstalling. How can I make Kickstart mount my existing /Home partition while purging and mounting the other partitions that I have. 

Basically I want to save all my configuration and files while having a new and fresh Ubuntu install that comes with all the neat new packages.

---

### Post by zvacet on 2010-04-29
Good way to save settings and files is to have separate home.If you don't have one you can make it following [this]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") guide.

---

### Post by SkyHiRider on 2010-04-29
I have a separate home partition. I just want to know how to set up the kickstart configuration that it mounts my existing home while wiping other partitions so that it pours fresh new binaries in them.

---

### Post by zvacet on 2010-04-29
> Basically I want to save all my configuration and files while having a new and fresh Ubuntu install that comes with all the neat new packages.

If you have separate home partition then your data/settings are safe.Back them up just in case.

---

### Post by ezsit on 2010-04-29
[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

Look into this. I have used remastersys with the last few version os Ubuntu to create complete backups and redistributable, customized, remastered ISOs useful for installing the identical setup on multiple computers.

---

### Post by SkyHiRider on 2010-05-05
Anyone knows how to set the boot options during the ubuntu installer so that it loads the kickstart configuration file form the cd/iso?

---

### Post by bruno9779 on 2010-05-05
Yes, at the partitioning step you choose the manual option.

Then you will have to right click you old home and define it as mount point /home and MAKE SURE THE TICK BOX FOR FORMATTING IS UNTICKED.

all other partitions should be formatted (except for swap).

then go ahead normally.

I have reinstalled this way 3 days ago, with no issues a all.

(an option on my motherboard destroyed irrecoverably my / partition)

---

### Post by SkyHiRider on 2010-05-05
> **bruno9779 said:**
> Yes, at the partitioning step you choose the manual option.

Then you will have to right click you old home and define it as mount point /home and MAKE SURE THE TICK BOX FOR FORMATTING IS UNTICKED.

all other partitions should be formatted (except for swap).

then go ahead normally.

I have reinstalled this way 3 days ago, with no issues a all.

(an option on my motherboard destroyed irrecoverably my / partition)

Problem is I can't get the kickstart file to load/work. I copied a kickstart config from a Ubuntu documentation pdf but it won't load the file, tried both http and local file. Probably doing something terribly wrong.

Does kickstart tell you when there is an error in the file or it just ignores it during install without feedback?

---

