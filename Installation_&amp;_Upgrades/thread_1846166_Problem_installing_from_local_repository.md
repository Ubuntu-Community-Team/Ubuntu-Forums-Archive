---
title: "Problem installing from local repository"
date: 2011-09-18
forum: Installation &amp; Upgrades
---

### Post by abhi45 on 2011-09-18
i recently borrowed a portable disk from my friend with an enitre repository of ubuntu 10.10 packages and copied it to my /home/xyz directory.
the directory structure of the mirror is
/ubuntu_mirror_10.10
  --/dists
    -/maverick -/maverick-backports -/maverick-security -/maverick-updates
  --/pool
       -/main -/multiverse -/restricted -/universe

Unfortunately there was not enough space in the "/"(filesystem), so i copied /ubuntu_mirror_1010/pool/main (just the /main directory)into another media --> /media/local/ from the portable disk and the rest in /home/xyz/
and added a symbolic link to '/media/local/main' in  directory "/home/xyz/ubuntu_mirror_1010/pool "

Now to install packages from this local mirror i modified the sources.list to contain following additional uri
deb file:///home/xyz/ubuntu_mirror_1010/ maverick main multiverse universe resticted
deb file:///home/xyz/ubuntu_mirror_1010/ maverick-backports  main multiverse  universe resticted
deb file:///home/xyz/ubuntu_mirror_1010/ maverick-security main multiverse  universe resticted
deb file:///home/xyz/ubuntu_mirror_1010/ maverick-updates main multiverse  universe resticted

After executing the sudo apt-get update command i tried to install gimp using sudo apt-get install gimp
but it showed the following errror 
E: Couldn't find package gimp
Is this the problem because of the symbolic link of /main ?? 
please give me  a solution
thx

---

### Post by abhi45 on 2011-09-18
still waiting for a solution :-\":-\"

---

### Post by Hakunka-Matata on 2011-09-19
> **abhi45 said:**
> i recently borrowed a portable disk from my friend with an enitre repository of ubuntu 10.10 packages and copied it to my /home/xyz directory.
the directory structure of the mirror is
/ubuntu_mirror_10.10
  --/dists
    -/maverick -/maverick-backports -/maverick-security -/maverick-updates
  --/pool
       -/main -/multiverse -/restricted -/universe

Unfortunately there was not enough space in the "/"(filesystem), so i copied /ubuntu_mirror_1010/pool/main (just the /main directory)into another media --> /media/local/ from the portable disk and the rest in /home/xyz/
and added a symbolic link to '/media/local/main' in  directory "/home/xyz/ubuntu_mirror_1010/pool "

Now to install packages from this local mirror i modified the sources.list to contain following additional uri
deb file:///home/xyz/ubuntu_mirror_1010/ maverick main multiverse universe [COLOR=Red]resticted[/COLOR]
deb file:///home/xyz/ubuntu_mirror_1010/ maverick-backports  main multiverse  universe [COLOR=Red]resticted[/COLOR]
deb file:///home/xyz/ubuntu_mirror_1010/ maverick-security main multiverse  universe [COLOR=Red]resticted[/COLOR]
deb file:///home/xyz/ubuntu_mirror_1010/ maverick-updates main multiverse  universe [COLOR=Red]resticted[/COLOR]

After executing the sudo apt-get update command i tried to install gimp using sudo apt-get install gimp
but it showed the following errror 
E: Couldn't find package gimp
Is this the problem because of the symbolic link of /main ?? 
please give me  a solution
thx

do those misspellings matter?

---

### Post by raja.genupula on 2011-09-19
+1 
yeah i think , thats the issue . 
man this link have very useful information for you 
just make a look at that 

[http://ubuntuforums.org/showthread.php?t=20217](http://ubuntuforums.org/showthread.php?t=20217)


all the best

---

### Post by abhi45 on 2011-09-19
ok thanks .. 
there was a typo indeed ..
so silly of me!! :oops:

---

