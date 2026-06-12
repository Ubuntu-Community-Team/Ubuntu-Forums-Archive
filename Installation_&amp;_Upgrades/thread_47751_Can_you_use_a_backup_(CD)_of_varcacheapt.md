---
title: "Can you use a backup (CD) of /var/cache/apt?"
date: 2005-07-09
forum: Installation &amp; Upgrades
---

### Post by t2kburl on 2005-07-09
I have to reinstall Ubuntu on a secondary PC ...  can I use a backup of the packages in /var/cache/apt/archives so I don't have to download them all again?

If so, how?

300+ megs takes me forever to download

---

### Post by llamakc on 2005-07-10
On Debian you would run

sudo dpkg --get-selections > /home/you/box1.packages

to get a list of packages and then copy those packages over to the second box, placing them in /var/cache/apt/archives.

Now on box2 run (after copying the box1.packages file to your home on box2):

sudo dpkg --set-selections < /home/you/box1.packages

Now sudo apt-get update, apt-get upgrade

This _may_ work for you. Let us know if & what fails.

---

### Post by t2kburl on 2005-07-10
since I just copied the archives folder to a CD, I'll have to copy it again into a folder in my home directory after I install. Then I can use  

sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz

then set that directory as a repository for synaptic


credit to this post:   [http://ubuntuforums.org/showpost.php?p=237819&postcount=10](http://ubuntuforums.org/showpost.php?p=237819&postcount=10)

for showing me the light

---

### Post by llamakc on 2005-07-10
Glad you found an answer.

---

