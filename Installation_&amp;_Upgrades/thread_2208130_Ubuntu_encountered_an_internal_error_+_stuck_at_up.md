---
title: "Ubuntu encountered an internal error + stuck at upgrades for new kernel"
date: 2014-02-26
forum: Installation &amp; Upgrades
---

### Post by thedardanius on 2014-02-26
Hello,

I'm a fairly new Ubuntu user and from the installation on nothing seemed to have gone wrong. Until one day, I saw the update manager wanted me to update certain things, including a newer kernel+source, but when it reached that update it got stuck, and i couldn't continue it or end it. That was really strange.
Then, after a while, Ubuntu starts to receive internal errors, and my firefox crashes unexpectedly continuously. The error reports that certain packages are not matching the required version or sth... so maybe some of the system files are getting corrupted? I had a hard disk corruption a short while before this all happened, but I'm using SSD and windows managed to solve all corrupted windows files, so maybe linux is corrupted? Please help me out, its very confusing. Is there also some sort of ubuntu checker that could verify whether or not it is still working?
Then one day, i read about the md5 checksum or something like that which you need to verify to image of ubuntu when you installed it from downloaded image, which is what i did. However, nowhere on the site indicated to me i had to do some checksum to check my image I burned on the cd, so maybe my image was missing some bits? The installation process was successful, nevertheless.
Please help me out, i want to use ubuntu and develop in C++ for linux, which is now virtually impossible ...

---

### Post by mörgæs on 2014-02-28
First, please run 

```
sudo apt-get update
sudo apt-get dist-upgrade
uname -a
```

and post the results in CODE tags.

---

### Post by thedardanius on 2014-02-28
I ran apt-get update:
After downloading the libs, its says:
Reading package lists... Error!
E: Read error - read (5: Input/Output error)
E: Problem opening /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_quantal-security_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

THe problem is, I cant use firefox on ubuntu (it suddenly crashes all the time), ubuntu is receiving internal all the time... I cant follow the steps directly, so I forgot to do the other 2 steps you mentioned. Hope this enough information.

---

### Post by mörgæs on 2014-03-01
As I mentioned we prefer people using CODE tags. It's no big deal here because the output was short but please use next time.

> **thedardanius said:**
> 
E: Read error - read (5: Input/Output error)

often indicates physical errors, which aligns well with what you mentioned in the first post.

Is the system stable enough for you to read SMART data from the hard disk?

---

### Post by Elfy on 2014-03-01
If you don't know how to use code tags, then - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by thedardanius on 2014-03-01
How do I test that?

---

### Post by mörgæs on 2014-03-02
I don't know much about Ubuntu as I only use X/Lubuntu, but I guess there should be a Disk Tool or something like that.

---

### Post by thedardanius on 2014-03-02
Where do I get one? Which do you recommend? And in case it should be in there as default, how do I find it? Mind you, I cant download anything due to mozilla firefox crashes persistently.

---

### Post by mörgæs on 2014-03-03
Maybe I wasn't clear, but it's there in a default installation. You can use it without internet access.

---

### Post by thedardanius on 2014-03-08
How do I access it? Where do I find it? Im a newbie in Ubuntu by the way ;p

---

### Post by ibjsb4 on 2014-03-08
> Read error - read (5: Input/Output error)

As already stated, this often indicates physical errors and running a disk check should be done first.  This can be checked with "Disk Utility" which I think is already installed as part of the default install.

[https://apps.ubuntu.com/cat/applications/precise/gnome-disk-utility/](https://apps.ubuntu.com/cat/applications/precise/gnome-disk-utility/)

There is also a chance that /dpkg/status has been corrupted and you could try replacing it.

```
sudo mv --backup --suffix=.broke /var/lib/dpkg/status-old /var/lib/dpkg/status

```

---

### Post by thedardanius on 2014-03-09
I did the SMART test with disk utility, it reported 1300+ read errors from raw disk!!! I dont know if that is normal.
The bad thing is, I cant use firefox on ubuntu and software centre is crashing, update-apt-xapian-index stopped abruptly as well, and the system reported several internal errors when I entered Ubuntu, mainly the I/O error. It failed to parse lists/status files indeed as it reported, in this case: /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_quantal-security_main_binary-i386_Packages, this package couldnt be parsed. BTW im posting this from windows, why cant i copy paste into this adv reply window???
I tried your command line with mv, but it reported that it couldn't find the old one... so I have no backup? Anyway, the function you gave me didnt work out.

---

### Post by mörgæs on 2014-03-09
I guess it's obvious that the installation is falling apart, and I doubt it's worth trying to save it.
Do you have any important data on the system?

---

### Post by thedardanius on 2014-03-09
A system falling apart? That must be my fault. But I followed all the steps for installation, I just read lately about a md5checksum or sth to check your image of ubuntu you downloaded...didnt know about that at all. The image I burned on my disk looked good. But after installation, no problems occurred. It has been lately that my windows partition experienced multiple hard disk corruptions... maybe that is the cause? BTW My ubuntu OS is for me to use linux and to develop for linux (C++) but there is no data on there that I have not on windows 7, so no backup is needed at all. Are you hinting that I need to reinstall Ubuntu?

---

### Post by ibjsb4 on 2014-03-09
> lately that my windows partition experienced multiple hard disk corruptions... 

I think your hard drive is in the process of crashing.  You better backup your windows files before it does.

---

