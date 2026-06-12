---
title: "Restoring only non-system apps after fresh install of Ubuntu 12.04"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by S. Cornelissen on 2012-05-05
Dear all,

[Please forgive me if I am not using the correct terms, I am a somewhat experienced user, but not an expert]

I want to do a fresh install of Ubuntu 12.04 on a laptop that currently has 11.10. As I want to introduce encryption, I need a total formatting of the disk. Afterwards, I would like to be able to easily re-install the software I installed. I know and have previously used the method of generating an installed packages list and re-installing that using:

```
sudo dpkg --get-selections > packages.txt
```

**However**, the largest share of that list is drivers / plugins etc. or what I would call "system apps". Only a small share are things like a music player, backup software or graphic software I installed or "non-system apps". 

My experience is that re-installing all system apps can lead to conflicts with display and sound drivers in the new Ubuntu. (That is pretty much the reason that a fresh install usually has better effect than an upgrade, I presume.)

Is there a way to only re-install the non-system apps? I am afraid not, but any help is appreciated.

(Handpicking them from the generated list is not an option as A) the list is 2,500+ apps long and B) there are many apps of which I am unsure in which category I should put them)

---

### Post by dino99 on 2012-05-05
maybe you might consider your own cd installer based on:

- ubuntu core
- [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

---

### Post by oldfred on 2012-05-05
I have used the dpkg, but this time I am going from 10.10 to 12.04 and there are a lot of changes.

I did find that installing aptitude and running it can generate a more manageable list of top level - no depends list of about 350 apps in my case. I still have to delete some things as OpenOffice and some other apps are now the new default but list is manageable.

I have not use aptitude to do it but saved these:
Top level only - no depends
sudo apt-get install aptitude
aptitude --disable-columns -F '%p' search '~i!~M!~R(~i)' > toplevel 
or
aptitude search '?installed ?not(?reverse-depends(?installed))'

Install with aptitude
aptitude --display-format '%p' search '?installed!?automatic' > ~/my-packages
sudo xargs aptitude --schedule-only install < my-packages
sudo aptitude install

I think list with just %p, is like the dpkg list and would work to install with dpkg.

I was possibly going to do this, but now it is archived and you have to scroll down a lot to get to the pos and look for kdford as post# is not theret.
HowTo: Create a list of installed packages
Compare two lists: kdford post #70
[http://ubuntuforums.org/archive/index.php/t-261366.html](http://ubuntuforums.org/archive/index.php/t-261366.html)

---

### Post by S. Cornelissen on 2012-05-11
Thanks dino99 and oldfred for the replies.

Dino99: your solution seems a bit too complicated, especially as I will probably need to use the alternate installer.

oldfred: I have used your method to generate the toplevel list. It has 613 entries. What exactly does toplevel/no depends mean? Is that that no other package depends on this package? In other words: standalone packages that were not installed alongside other ones? I see how this can be in the direction that I am looking for. Still, e.g. some drivers could be standalone too right? How did it work out for you going to 12.04?

---

### Post by oldfred on 2012-05-11
It is my understanding that top level is just that, nothing else depends on it, but when you reinstall of course you may get a lot of depends. I like K3b, so when I install that in Ubuntu I get a lot of Kubuntu or qt type depends.

I have about 10 main apps that I auto install as part of my new install script. I am finding a lot of older apps and am still reviewing and trying to figure out if I still want them or not. My list is still over 300 without the one's I know I do not want for sure.

---

