---
title: "dependancy issues"
date: 2011-09-29
forum: Installation &amp; Upgrades
---

### Post by ciscoboy on 2011-09-29
hello, 

I've been having trouble installing a program on my computer due to dependancy issues. Is there something I can try or do that will work for any dependancy issues?

Thanks!

Ciscoboy

---

### Post by dino99 on 2011-09-29
maybe somebody will help if you dont set your config/app issue as a secret ;)

---

### Post by gordintoronto on 2011-09-29
What program, and how are you installing it? What version of Ubuntu?

---

### Post by ciscoboy on 2011-09-30
> dino99:  

maybe somebody will help if you dont set your config/app issue as a secretwhat do you mean by "don't set your config/app issue"?

> gordintoronto: 

What program, and how are you installing it? What version of Ubuntu?     I'm runing ubuntu 10.04 LTS 32 bit, and the program that i'm trying to install is inssider version 0.1.1.0429, and I'm trying to install it through a .deb file, because I have been unable to locate it in synaptic.

---

### Post by dino99 on 2011-09-30
use this one: [http://www.metageek.net/products/inssider/linux/](http://www.metageek.net/products/inssider/linux/)

download it into an empty folder, then into a terminal:

sudo dpkg -i *.deb

---

### Post by ciscoboy on 2011-09-30
> dino99

use this one: [http://www.metageek.net/products/inssider/linux/](http://www.metageek.net/products/inssider/linux/)
download it into an empty folder, then into a terminal: sudo dpkg -i *.deb           I tried to enter the command that you gave me; in my case, it's:

ubuntu@ubuntu:~$ sudo dpkg -i inssider_0.1.1.0429_i386.deb


And the response I got was: 

dpkg: error processing inssider_0.1.1.0429_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 inssider_0.1.1.0429_i386.deb

I put the file in a new folder, I transfered it on the desktop, and I even deleted another one that I had previously downloaded, so that the computer couldn't be confused with which one to pick. 

Any ideas of what to do or what that reply means?

---

### Post by gordintoronto on 2011-09-30
Yes, it means that you need to CD to the folder you downloaded the program into.

However... It would be easier to just use the Nautilus file manager, click your way to the folder, then double-click on the downloaded file.

Your initial post said there were dependency issues. If there are, they will show up at this point. Carefully note what files are needed, and use Synaptic to install them, if possible.

I can't help you at that point, because I haven't used 32-bit for two+ years, on desktop or laptop.

---

### Post by ciscoboy on 2011-10-01
I never thought of using synaptic to download additional dependancies. However, I'm not sure how to do that; the precise error that pops-up is:


Error: Dependency is not satisfiable: libmono-system-web2.0-cil (>= 2.6.7)

I checked, and saw through synaptic that libmono...2.0 had already been installed, so I reinstalled it, and even downloaded the version 1.0 without success. Is there any helpthat you could bive me?

> I can't help you at that point, because I haven't used 32-bit for two+ years, on desktop or laptop.     What do you mean by that? is there a difference in between 32bit and 64 bit ubuntu, and if there is, what is it?

> It would be easier to just use the Nautilus file manager

I also noticed that I have nautilus already downloaded. How can I use it as a file manager and how does it work?

---

### Post by dino99 on 2011-10-01
you will not be able to install it with Lucid due to missing libmono required version packages

packages.ubuntu.com/en/lucid/cli-mono/

install oneiric to get the required libmono packages

---

### Post by gordintoronto on 2011-10-01
> **ciscoboy said:**
>  is there a difference in between 32bit and 64 bit ubuntu, and if there is, what is it?

I also noticed that I have nautilus already downloaded. How can I use it as a file manager and how does it work?

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit) 

If you click on any selection under Places, the program which starts is Nautilus.

---

### Post by ciscoboy on 2011-10-01
> you will not be able to install it with Lucid due to missing libmono required version packages

packages.ubuntu.com/en/lucid/cli-mono/ install oneiric to get the required libmono packagesI first tried to install several dependancies through the website you gave me, without success. The problem, was that everytime I tried to install a dependancy, I would need another one, and so on... And I tried to install oneric, but unfortunately I couldn't get it on google, or on synaptic; I even tried it through the terminal without success. Could you help me through it? I also noticed that I have roughly the same dependancy already installed on my computer, but I guess it's a previous version than what I need. (I just thought it might be worth mentioning).

Thanks for your support

Ciscoboy

---

### Post by directhex on 2011-10-03
> **ciscoboy said:**
> I first tried to install several dependancies through the website you gave me, without success. The problem, was that everytime I tried to install a dependancy, I would need another one, and so on... And I tried to install oneric, but unfortunately I couldn't get it on google, or on synaptic; I even tried it through the terminal without success. Could you help me through it? I also noticed that I have roughly the same dependancy already installed on my computer, but I guess it's a previous version than what I need. (I just thought it might be worth mentioning).

Thanks for your support

Ciscoboy

The problem you have is inSSIDer is built to require Mono 2.6.7, which is newer than the version in Lucid.

Try [http://badgerports.org/](http://badgerports.org/)

You will face ultimate and total failure by trying to install Mono packages built for a post-lucid release on Lucid, but specially made backports are fine.

---

### Post by searchfgold6789 on 2011-10-03
Oneiric Ocelot is the code name for the latest unstable release of Ubuntu, which is 11.10 - 11 (2011) 10 (October). [Here is the link]("ftp://mirror.anl.gov/pub/ubuntu-iso/CDs/oneiric/") for the selection of .iso files for it, if you have a standard Intel chip that's 32 bit (like most people), you can just get it [here]("ftp://mirror.anl.gov/pub/ubuntu-iso/CDs/oneiric/ubuntu-11.10-beta2-desktop-i386.iso"). If you download that and install Ubuntu from there, you'll have a better chance getting what you are trying to do to work. If you don't want to go through all that trouble, you can just wait a few weeks and install it using the Update Manager.

---

### Post by ciscoboy on 2011-10-05
okay; I tried to install the mono packages through badgerport, and as soon as I was done, the system would not restart. So, I had to reload a previous version of the ubuntu that I had backed-up. My uncle (which is him that loaned me the laptop I'm using) warned me to try and stay away from the 11.04 release, but it has been a while,  so I'll try it, see what happens and get back to you guys.

Thanks!

Ciscoboy

---

### Post by ciscoboy on 2013-01-05
for anyone having the same problem wanting an answer, check-out this thread:

[http://ubuntuforums.org/showthread.php?t=1805154](http://ubuntuforums.org/showthread.php?t=1805154)

---

