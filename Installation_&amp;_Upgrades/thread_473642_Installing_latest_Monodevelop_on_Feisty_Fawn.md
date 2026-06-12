---
title: "Installing latest Monodevelop on Feisty Fawn"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by Todi on 2007-06-14
Hi all.

Monodevelop 0.14 was recently released, and i would like to install it on my Ubuntu Feisty Fawn installation.

However, the latest version i can find in Synaptic seems to be the older 0.12 version.

I've tried building Monodevelop on my own from the source but despite installing a bunch of dependencies, i'm getting nowhere. I should probably add that i am a beginner on Ubuntu, i don't usually (ever) build stuff on my own. 

So what are my options now? How long does it take before the latest versions show up in the depositories? (or does it have to be classified as stable or something first?)

I appreciate any help you can give =)

**Edit: With the help of a workmate i was finally able to get Monodevelop compiled and running. It seems so easy now afterwards that i'm almost ashamed.. but you learn something new every day.**

---

### Post by macross3003 on 2007-06-16
> **Todi said:**
> Hi all.

Monodevelop 0.14 was recently released, and i would like to install it on my Ubuntu Feisty Fawn installation.

However, the latest version i can find in Synaptic seems to be the older 0.12 version.

I've tried building Monodevelop on my own from the source but despite installing a bunch of dependencies, i'm getting nowhere. I should probably add that i am a beginner on Ubuntu, i don't usually (ever) build stuff on my own. 

So what are my options now? How long does it take before the latest versions show up in the depositories? (or does it have to be classified as stable or something first?)

I appreciate any help you can give =)

**Edit: With the help of a workmate i was finally able to get Monodevelop compiled and running. It seems so easy now afterwards that i'm almost ashamed.. but you learn something new every day.**
Hi Todi
I'm looking for the same solution as you were but none of my workmates can help me :(
Could you, please, write a few steps for getting monodevelop0.14 works on feisty? ;)

thanks a lot

---

### Post by mattisking on 2007-06-16
When the previous version of a package already exists the quickest way to get prepared for building the next version is to start with:
sudo apt-get build-dep <package> (in this case monodevelop)

You should be able to do the same with each of the other monodevelop packages that you wish to use. Unless you're wanting to go against the latest in SVN  you should be able to download the release from [www.monodevelop.com](www.monodevelop.com) and compile and build as usual. I'm assuming you know the basics...

---

### Post by macross3003 on 2007-06-17
i just downloaded the rpm from the oficial repos at [http://www.monodevelop.com/Download](http://www.monodevelop.com/Download) and just alien it with
$ fakeroot alien monodevelop-0.14-0.novell.noarch.rpm
and then 
$ sudo dpkg -i monodevelop_0.14-1_all.deb

it's not the greatest solution but works

---

### Post by zakk on 2007-06-18
> **macross3003 said:**
> i just downloaded the rpm from the oficial repos at [http://www.monodevelop.com/Download](http://www.monodevelop.com/Download) and just alien it with
$ fakeroot alien monodevelop-0.14-0.novell.noarch.rpm
and then 
$ sudo dpkg -i monodevelop_0.14-1_all.deb

it's not the greatest solution but works

Doesn't work for me :( The rpm conversion and the deb install went fine, but the new monodevelop doesn't start (lot of error messages). Just downgraded to 0.12.

---

### Post by mattisking on 2007-06-18
I just ran across this site... maybe give it a shot?

[http://www.getdeb.net/search.php?keywords=monodevelop](http://www.getdeb.net/search.php?keywords=monodevelop)

---

### Post by zakk on 2007-06-19
> **mattisking said:**
> I just ran across this site... maybe give it a shot?

[http://www.getdeb.net/search.php?keywords=monodevelop](http://www.getdeb.net/search.php?keywords=monodevelop)

THX, it works!

---

### Post by simion314 on 2007-06-26
hi i downloaded the .deb from getdeb web site but i have an error:dependency is not satisfaible libc6|libc6.1. Please help?

---

