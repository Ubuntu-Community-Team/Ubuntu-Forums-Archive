---
title: "apt-get update - different errors"
date: 2011-08-13
forum: Installation &amp; Upgrades
---

### Post by astbis on 2011-08-13
Hi Forum

I have the weirdest problem and I can't find any usable solution on the net due to often user terms.

Hope you guys can help.

I try to run 
#apt-get update
and receive a lot of different errors. F.eks.

bzip2: Data integrity error when decompressing

404  Not Found

W: Kunne ikke hente gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_natty-security_universe_source_Sources Hashsum stemmer ikke
(...which means in english: Couldn't get fil hashsum doesn't match)

My sources.list and the apt-get update result you find here:

sources.list
[http://pastebin.com/TSRU9FZP](http://pastebin.com/TSRU9FZP)

apt-get update
[http://pastebin.com/JkCHazLb](http://pastebin.com/JkCHazLb)


What am I missing?

---

### Post by Sef on 2011-08-13
> I try to run 
#apt-get update
and receive a lot of different errors. F.eks.

What happens if you run 

```
sudo apt-get update
```?

---

### Post by astbis on 2011-08-13
> **Sef said:**
> What happens if you run 

```
sudo apt-get update
```?

I was in a root shell :-) sudo bash :-)

So it happens what i mentioned above.

---

### Post by raja.genupula on 2011-08-13
please  paste your output of update command . we need more 
details.

---

### Post by garvinrick4 on 2011-08-13
This below will clear up /var/lib/apt/lists errors:
```
sudo rm /var/lib/apt/lists/* -vf 
``````
sudo apt-get clean all 
``````
sudo apt-get update

```> W: Kunne ikke hente [http://dk.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-i386/Packages](http://dk.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-i386/Packages) 404  NoMeans cannot find or not any such. If it keeps up comment it out in sources.list
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by astbis on 2011-09-02
Thanks for the reply garvinrick4.

I tried your solution, but the only difference is, that i get more error messages of the same kind.

A lot of 
- hashsum doesn't match
- bzip2: Data integrity error
- Encountered a section with no Package: header

Any other suggestions?

Regards

---

### Post by astbis on 2011-09-02
> **raja.genupula said:**
> please  paste your output of update command . we need more 
details.

The entire update output is posted in the first post.

Latest apt-get update output after the suggested chainges.
[http://pastebin.com/nweZBA1w](http://pastebin.com/nweZBA1w)

---

