---
title: "How to upgrade software."
date: 2012-02-21
forum: Installation &amp; Upgrades
---

### Post by crazypony on 2012-02-21
How do I upgrade Zoneminder 1.24.2 to 1.24.4 or 1.25.0? 

I am using Ubuntu 11.04 64bit Desktop and Zoneminder 1.24.2

I'm looking for a walk-through of sorts.
Thank you in advance :D

---

### Post by cortman on 2012-02-21
That depends how you installed it. Did you download it from the Ubuntu repositories, or from the Zoneminder site? If from the repositories, you can just run

```
sudo apt-get upgrade
```

otherwise I'm not sure that apt-get will upgrade it; you may need to download and install the newer version.

---

### Post by crazypony on 2012-02-21
> **cortman said:**
> That depends how you installed it. Did you download it from the Ubuntu repositories, or from the Zoneminder site? If from the repositories, you can just run

```
sudo apt-get upgrade
```otherwise I'm not sure that apt-get will upgrade it; you may need to download and install the newer version.




Thank you for responding. I installed Zoneminder through the terminal using the wiki on their respective site.  I have been struggling to find any documentation that instructs me through a successful upgrade.

I used the command I quoted above and this is what it said:

~$ sudo apt-get upgrade
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
~$

---

### Post by snowpine on 2012-02-21
I think you can get it here: [http://www.zoneminder.com/downloads](http://www.zoneminder.com/downloads)

And see also here: [http://www.zoneminder.com/wiki/index.php/Ubuntu](http://www.zoneminder.com/wiki/index.php/Ubuntu)

---

### Post by cortman on 2012-02-21
> **crazypony said:**
> Thank you for responding. I installed Zoneminder through the terminal using the wiki on their respective site.  I have been struggling to find any documentation that instructs me through a successful upgrade.

I used the command I quoted above and this is what it said:

~$ sudo apt-get upgrade
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
~$

So apparently that doesn't work. At least we know that now.
Snowpine has some good links, and [here's]("http://www.zoneminder.com/wiki/index.php/Ubuntu_Server_11.04_64-bit_with_ZoneMinder_1.25.0_from_compiled_SVN._FFmpeg_from_distribution_repos,_libjpeg-turbo,_Webmin,_Cambozola_installed_from_.deb") the installation instructions for 11.04 64 bit, but I'll admit they give me the creeps. I suppose if you managed to successfully install it once, you should be able to do so again...

---

### Post by snowpine on 2012-02-21
Actually it looks like Zoneminder is in the Ubuntu repos. Therefore it (theoretically) can be easily installed through Software Center or Synaptic.

If you use the latest Ubuntu then you will automatically get the latest Zoneminder too: [http://packages.ubuntu.com/precise/zoneminder](http://packages.ubuntu.com/precise/zoneminder)

---

### Post by crazypony on 2012-02-21
I've searched the Ubuntu Software Center for the newest version and all I can find is the version I presently have installed (1.24.2). Thankfully Ubuntu has allowed me to be a little oblivious to how my system updates most software because it has been doing it automatically.

I've also tried installing 1.25.0 using my terminal from the .tar on the downloads site listed above and partway through I wind up getting "permission denied" and everything seems to roll back to normal.

My real problem may be that I don't understand where I'm going wrong and I don't know what to show you guys since I've rarely had to ask for help before :/

---

### Post by wojox on 2012-02-21
Have you tried looking for a ppa [ZoneMinder]("https://launchpad.net/~iconnor/+archive/zoneminder")

---

### Post by crazypony on 2012-02-26
Ok, this was a test of my reading comprehension.

After mulling around a lot on the zoneminder site, it occurred that 1.24.2 is the highest version I can install on Ubuntu 11.04. It requires an upgrade to 11.10 to use 1.24.4 and 12.04 for 1.25.0. 

I give myself a 71% on this comprehension test. Everything is upgraded and running the same (if not better) than usual.

Thank you to everyone who responded.

Thanks be to Ubuntu! [-o<

---

### Post by cortman on 2012-02-26
Great! Glad it's (sorta) solved. :) We all misread sometimes.

Mark this thread as [SOLVED] then, if you would, using the thread tools in the upper right.

Have fun with Ubuntu!

---

### Post by blind0wl on 2012-04-18
I'm on 11.10 and 1.24 is the only package in the repo

---

