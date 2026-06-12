---
title: "Problems w/ installation and updates"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by roke on 2008-02-07
I am brand new to Ubuntu, and have encountered a problem:

Whenever I go to install updates, or try to add new software (through the add/remove or by downloading from the internet), I get an error message: 

files list file for package `fftw3' is missing final newline

I thought I could fix the problem by removing and reinstalling the fftw3 package. I went to Synaptic to do this, but interestingly enough I get a message that removing this package will require three other packages to be removed. But then I get another error message that libtunepimp5-mp3 can not be removed because 

files list file for package `fftw3' is missing final newline

So what do I do? I seem to be caught inside a vicious circle....

Thanks in advance.

---

### Post by Partyboi2 on 2008-02-08
```
sudo mv /var/lib/dpkg/info/fftw3.list /home/user/Desktop
```
(Change user to your username)
then
```
sudo apt-get remove --purge fftw3 
```
If that solves the problem then you can safely delete the fftw3.list that is now on your desktop. If it does not work then I suggest moving that file back to /var/lib/dpkg/info.

---

### Post by roke on 2008-02-09
That did it! Thank you!

---

