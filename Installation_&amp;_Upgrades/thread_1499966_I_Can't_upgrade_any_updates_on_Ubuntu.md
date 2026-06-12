---
title: "I Can't upgrade any updates on Ubuntu"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by new 2 linux on 2010-06-02
Hello everybody new 2 linux here, ok i can't update any of my programs or update anything in Ubuntu, becuz evrytime i try to i get this error message:


is there a way to fix this?  and thx again

---

### Post by new_tolinux on 2010-06-02
It seems that you don't have a connection with the internet on that machine.
Probably you can use another (local?) server (see System - Administration - Software sources).

By the way, why did you install 8.04 (Hardy) as 10.04 is already out in the wild?

---

### Post by lindsay7 on 2010-06-02
Looks like you need a key for Hardy.  Get the key and install it.  Better yet. Upgrade to a newer version.

---

### Post by new 2 linux on 2010-09-09
thx 4 the feedback you guys i'll try an upgrade

---

### Post by new 2 linux on 2011-06-01
I tried to upgrade from 8.04 to 10.04 and a partial upgrade window showed up, so then i tried the partial upgrade and I got this error message....

---

### Post by mörgæs on 2011-06-01
A partial upgrade is dangerous: 
[http://ubuntuforums.org/showthread.php?t=1751299](http://ubuntuforums.org/showthread.php?t=1751299)

Now the damage is done, you could try to boot the computer and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```Please post the error messages, if any.

---

### Post by new 2 linux on 2011-06-02
i tried the sudo apt-get clean it said "unable to resolve host daniel", but then when i tried the sudo apt-get update i got this......

---

### Post by mörgæs on 2011-06-02
You could try to change the software mirror, but after all it seems like there are so many problems that a fresh install is probably faster. Here is some advice:

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by new 2 linux on 2011-06-02
so a fresh install would be my best choice?

---

### Post by wamarobert on 2011-06-02
> **mörgæs said:**
> A partial upgrade is dangerous: 
[http://ubuntuforums.org/showthread.php?t=1751299](http://ubuntuforums.org/showthread.php?t=1751299)

Now the damage is done, you could try to boot the computer and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```Please post the error messages, if any.
Code:.......
                  
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

rgds
R.Bakyayita- [email]wamarobert@hotmail.com[/email]

---

### Post by tgm4883 on 2011-06-02
The initial issue looks like the 8.04 repos aren't available anymore. I usually don't run a release for more than 12 months, so this may be expected since 8.04 is no longer supported for the Desktop (server it is, which may mean that other repos are still active (eg. security))

---

### Post by new 2 linux on 2011-06-04
so this means i should upgrade to the next version of ubuntu thts supports long tern support and I thought LTS last up to 3 years?

---

### Post by tgm4883 on 2011-06-04
> **new 2 linux said:**
> so this means i should upgrade to the next version of ubuntu thts supports long tern support and I thought LTS last up to 3 years?

3 years from 8.04 is 11.04 (eg. April 2011). It is currently June 2011, so it has been 3 years and 2 months.

---

### Post by nm_geo on 2011-06-04
Lucid 10.04 LTS is very stable and will be supported until April, 2013.

---

### Post by new 2 linux on 2011-06-15
Thts only a 2 years from now hmm so i how would i upgrade if i keep getting network connection problems even though im connected to the internet.

---

### Post by mörgæs on 2011-06-15
Try a live boot of 10.04. If it works, go for a fresh install.

---

### Post by new 2 linux on 2012-03-01
Hello everybody I successfully upgraded to Ubutnu 11.10, however now I am getting a Disk 
utility error saying I have Hard Disk problems.

---

### Post by raja.genupula on 2012-03-01
ok do fsck .
[https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)

---

