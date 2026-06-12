---
title: "Upgrade Ubuntu 6.06 from Ubuntu 5.10 using CD."
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by jewelewu on 2006-07-04
Im using ubuntu 5.10. I got cd ubuntu LTS 6.06. Now i want to upgrade it using this CD without partitioning & without deleting old ubuntu files.How it is possible?Another way i can upgrade it from internet i want upgrade from 6.06 LTS cd. When i boot this cd its start new installation, no upgrade option....so anyone can tell me plz.....how can i just ipgrade ubuntu 5.05 to ubuntu 6.06 LTS using CD? Thx in advance.

---

### Post by reacocard on 2006-07-04
maybe you can add the cd as a repository? open synaptic, go to settings -> repositories, and click add cdrom. once it's added it, do a "sudo gedit /etc/apt/sources.list" and replace all occurences of breezy with dapper. now go back to synaptic, click reload, then click mark all upgrades, then apply. it will download some packages from the net (the ones that have updates since the cd was created) but most should come from the cd.

---

### Post by argie on 2006-07-04
I upgraded just some 6 hours ago.

1. Added the CD-ROM by Synaptic > Edit > Add CDROM (couldn't find it in the Repos section :D)
2. Then went and commented out everything except the CDROM in sources.list (which I'd already backed up)
3. Then sudo apt-get upgrade && apt-get dist-upgrade did the trick.

I did (2) because I just spent a day getting the Alternate CD ISO using jigdo and didn't want to download 616MB again like apt wanted to do.

---

### Post by dananimal on 2006-07-05
I tryed this after commenting out all lines apart from the dapper cd and recieved this response.

```
me@myubuntu:~$ sudo apt-get upgrade && apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  cpp cpp-4.0
The following packages will be upgraded:
  binutils fakeroot make
3 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/1787kB of archives.
After unpacking 848kB of additional disk space will be used.
Do you want to continue [Y/n]?

```

It seems a bit minimal to me, is this correct or am I missing something

---

### Post by confused57 on 2006-07-05
Are you using the Dapper alternate CD?  Maybe I missed it in your posts, you probably already know you can't upgrade from the Dapper Desktop Live CD.

Edit:  I saw argie mentioned it.

---

### Post by pixelized on 2007-06-23
hello

i am running ubuntu(dapper 6.06) is it possible for me to upgrade to feisty fawn using the cd?or even kubuntu 7.04 also using the cd?

any help would be appreciated..

thanks!

---

