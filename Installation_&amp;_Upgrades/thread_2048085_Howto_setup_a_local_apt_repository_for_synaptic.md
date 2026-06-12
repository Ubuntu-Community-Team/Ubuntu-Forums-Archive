---
title: "Howto setup a local apt repository for synaptic"
date: 2012-08-26
forum: Installation &amp; Upgrades
---

### Post by nab on 2012-08-26
Hi all,

since I tend to forget such things, here a summary of what I did:

1. Create the directory to put all the deb files you downloaded, in this case I'll create in my local directory <your user name>/debs
$ mkdir ~/debs

2. Put all the downloaded deb files into the directory
$ mv ~/Downloads/*.deb ~/debs

3. Since I am too lazy to do the override file, ... Just create Packages.gz inside /home/<your user name>/debs and ignore the complains:
$ cd ~/debs
$ sudo dpkg-scanpackages . /dev/null | gzip -c9 > Packages.gz

7. Add this line to /etc/apt/sources.list
$ deb file:///home/<your user name>/debs / #lokale Downloads

8. Resynchronize the package index files from their sources
$ sudo apt-get update

9. Install your application (in this case, anki)
$ sudo apt-get install anki

Since I found this information on many pages I choose one randomly:
[http://odzangba.wordpress.com/2006/10/13/how-to-build-local-apt-repositories/](http://odzangba.wordpress.com/2006/10/13/how-to-build-local-apt-repositories/)

Perhaps it helps somebody else. And please excuse the lacking formating since I'm just using a machine where the internet access is rather restricted (no scripts,...)

Niko

---

