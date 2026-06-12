---
title: "How to install the latest netbeans?"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by Bucephalus01 on 2008-08-27
I see that netbeans 6.5 beta is out.
When I use synamptic, it only lists netbeans 6.01.
How do I install the latest netbeans with the recommended method of program installation for Ubuntu? Even if the latest one I can get is netbeans 6.1. I don't really want to be installing 6.01 when I know 6.1 and 6.5 is out.

regards
Bucephalus

---

### Post by tangibleorange on 2008-08-27
> **Bucephalus01 said:**
> I see that netbeans 6.5 beta is out.
When I use synamptic, it only lists netbeans 6.01.
How do I install the latest netbeans with the recommended method of program installation for Ubuntu? Even if the latest one I can get is netbeans 6.1. I don't really want to be installing 6.01 when I know 6.1 and 6.5 is out.

regards
Bucephalus

OK well i just had a look on the netbeans website and it seems they distribute the installer as a .sh file. this new version is not available in the ubuntu repos, so you will need to download the .sh file from the netbeans website. before installing, make sure you remove your old version via synaptic (in the normal way).
once you've downloaded the correct .sh file, do the following. I assume you downloaded the file to your desktop - if not, simply 'cd' to the correct download directory.
```
cd Desktop
sudo chmod +x netbeans-*
sudo ./netbeans-*
```
and that should start the installer.

---

### Post by lyceum on 2008-11-28
> **tangibleorange said:**
> OK well i just had a look on the netbeans website and it seems they distribute the installer as a .sh file. this new version is not available in the ubuntu repos, so you will need to download the .sh file from the netbeans website. before installing, make sure you remove your old version via synaptic (in the normal way).
once you've downloaded the correct .sh file, do the following. I assume you downloaded the file to your desktop - if not, simply 'cd' to the correct download directory.
```
cd Desktop
sudo chmod +x netbeans-*
sudo ./netbeans-*
```
and that should start the installer.

Thanks! I found:

[http://newsintegrator.wordpress.com/2008/11/20/installing-netbeans-65-on-linux-ubuntu](http://newsintegrator.wordpress.com/2008/11/20/installing-netbeans-65-on-linux-ubuntu)

which has a great walk through, but the code for terminal was not working, but I found yours, and it worked perfectly.

---

### Post by snova on 2008-11-28
Well, usually the preferred way to install software on Ubuntu is via the package manager, but as you've noticed, it doesn't always have the latest versions.

In the case of NetBeans, they provide installers (unusual for Linux) on their website. Just make sure to get the right one. Download it, mark it as executable, and run it.

---

### Post by lyceum on 2008-11-28
> **snova said:**
> Well, usually the preferred way to install software on Ubuntu is via the package manager, but as you've noticed, it doesn't always have the latest versions.

In the case of NetBeans, they provide installers (unusual for Linux) on their website. Just make sure to get the right one. Download it, mark it as executable, and run it.

I found the method I linked easier to understand, it was good for a dummy like me :)

-edit-

Just in case anyone comes looking for how to get the latest and greatest NetBeans for the same reason I did, to make Rails sites, here is how to update rubygems, as 

> $ gem update --system
ERROR:  While executing gem ... (RuntimeError)
    gem update --system is disabled on Debian. RubyGems can be updated \
    using the official Debian repositories by aptitude or apt-get

in terminal run (switch the version # if later than 1.3.1 to the new version number):

$ wget [http://rubyforge.org/frs/download.php/45905/rubygems-1.3.1.tgz](http://rubyforge.org/frs/download.php/45905/rubygems-1.3.1.tgz)

then

$ tar xzf rubygems-1.3.1.tgz

then

$ cd rubygems-1.3.1

then

$ sudo ruby setup.rb

then check it to be sure it worked with:

$ gem -v

This should spit out 1.3.1, or newer if you are doing this after 1.3.1

then run:

$ sudo gem install rails

or you can install new gems in NetBeans via Tools/Ruby Gems (wait for it to find your installed gems) click on the "_N_ew Gems" tab and double click on any gem you need.

Hope this helps someone some day 

:D

---

