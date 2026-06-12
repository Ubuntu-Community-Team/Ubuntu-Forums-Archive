---
title: "Can't Update"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by potayto9 on 2008-09-03
I am using Hardy, and I am having some trouble updating. In short, I cannot. Not from the updater, or the terminal, or synaptic.

I keep getting this:
> E: /var/cache/apt/archives/libglib2.0-dev_2.16.4-0ubuntu3_i386.deb: files list file for package `evolution-data-server' contains empty filename

I am mostly a novice at this and I need some help.

---

### Post by Partyboi2 on 2008-09-03
Try moving the evolution-data-server.list out of the way and reinstalling the package.
Open a terminal (Applications>Accessories>Terminal)
```
sudo mv /var/lib/dpkg/info/evolution-data-server.list /var/lib/dpkg/info/evolution-data-server.list.old
```
then try to reinstall the evolution-data-server package
```
 sudo apt-get  --reinstall install evolution-data-server
```

---

### Post by potayto9 on 2008-09-16
thanks so much. That cleared some things up. But now I have this
> W: Failed to fetch [http://repository.akirad.net/dists/akirad-hardy/main/binary-i386/Packages.gz](http://repository.akirad.net/dists/akirad-hardy/main/binary-i386/Packages.gz)  500 Internal Server Error

---

### Post by Partyboi2 on 2008-09-16
Try removing the akirad's repo that you have in your 3rd party Software list  from Software Sources (System>Admin>Software Sources>Third Party Software) then try renewing akirad repo by[FONT=monospace]
[/FONT]```
sudo wget http://akirad.cinelerra.org/dists/hardy.list -O /etc/apt/sources.list.d/akirad.list
wget -q http://akirad.cinelerra.org/dists/akirad.key -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by akir4d on 2008-09-17
and why not addakirad.deb that automagically fix all akirad repository errors?

follow this istructions:
[URL="http:// akiradproject.net/repository"]
http://akiradproject.net/repository[/URL]

or this
[http://cinelerra.org/getting_cinelerra.php#ubuntu]("http://cinelerra.org/getting_cinelerra.php#ubuntu")

byez

Paolo Rampino aka Akirad

---

### Post by potayto9 on 2008-09-17
Thank you. that seemed to help. I'll see if I have any more problems now.

---

