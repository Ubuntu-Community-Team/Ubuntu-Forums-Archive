---
title: "Chicken and the Egg situation with g++ , apt-get and limodem drivers , need help!"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by dempl_dempl on 2007-05-10
Hi,
 Here it goes:

  So far I've had Mandrake 9.1 and decided to move onto Kubuntu 7  ( feisty) .
  Since I use Dial-Up , I've tried to install Lucent modem:

  dule@localhost~/linmodem#  ./configure 

..and got the responce:

  ... ok
  ... ok
  Bla bla bla...
Error:
 g++ is not configured properly... bla bla bla
...

##end of output##
Then I've tried to compile some simple Hello, World! program to test gcc , and it could not compile
(although gcc  was present , libraries were  configured  badly )


So the problem was with gcc...

I've searched the Net and found that soulution is with :
#apt-get 'base-build' 

Well, I cant get gcc  because I don't have acces to the Net, and can't get access because I don't have gcc... 

I've tried to download gcc packages from ubuntu site whitin Windows, but there was simply to much depency packages...

Anyone having idea what to do?


BTW, I've found g++ .deb package on my installation CD, but it needed some packages   which were not on 
CD.

Thanks in advance.

---

### Post by taurus on 2007-05-10
The build-essential package is on the CD so insert the CD into a drive, open a terminal, and type

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```
As you can see, there is no chicken and egg or catch 22 here.

---

### Post by dempl_dempl on 2007-05-10
Thanks  :)

Now, one more thing... I've found a 'restricted-drivers' package ubuntu site. It has LinModem driver listed.
I'm just downloading it. 

What's the apt-get way to install it?

Ok, I promise I'll learn to use apt-get, as soon as I install this modem.

---

### Post by taurus on 2007-05-10
If it's a .deb, then you can install it with

```
sudo dpkg -i filename.deb
```

---

### Post by dempl_dempl on 2007-05-10
Whoa, that was fast!!!
I didn't even get to finish download.

Thanks again :)

---

