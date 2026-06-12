---
title: "Reinstall libc6"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by akshayas1986 on 2007-06-11
Hello

Well i was trying to install Limewire on Ubuntu Dapper Drake and it showed some error about libc6. In almost every forum regarding this, people said that Ubuntu always has a very old version of libc6 and newer versions are required for Limewire. One suggested that I go and get the latest one from Debian repositories. So I went to the Debian site and downloaded the latest version of libc6 only to realize after installation that it was an UNSTABLE version.

Now things are quite bad with my comp. Lot of error keep popping up quite often--even when I use simply open gedit.

How do I restore the older version of libc6, which originally came with Ubuntu Dapper??

I tried > sudo apt-get install --reinstall libc6 

But got this error messgae > Reading package lists... Done
Building dependency tree... Done
Reinstallation of libc6 is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Please help me out here :(

Thanks and regards
Akshaya Srivatsa

---

### Post by akshayas1986 on 2007-06-12
Please help me out.. If I open Gedit it says

> (gedit:8740): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(gedit:8740): Gdk-WARNING **: locale not supported by C library


If I try to install some packages or softwares, I get this

>  libc6 (= 2.3.6-0ubuntu20.4) but 2.5-10 is to be installed
E: Broken packages


Please help me out :(

---

### Post by jrusso2 on 2007-06-12
Upgrading libc6 is difficult as everything is based off that.  Would be easier to just upgrade to Feisty

---

### Post by akshayas1986 on 2007-06-12
Oh god!!! Is ther no way out of this??? :( :( :(

---

### Post by az on 2007-06-12
Updating libc6 is bad advice.  You should *never* mix repositories.  Always keep the only the same version of Ubuntu repos active.

The reason your app did not run is because it was a binary-only version.  However, limewire is written in Java which has nothing to do with libc6.  Perhaps you tried to install a bizarre version of Java that was not meant for Ubuntu?  See the RestrictedFormats wiki page on how to install Java in Ubunut - it's in the repos.

As for fixing libc6, download and install the Ubuntu version by hand.  Make sure all your repos are the same version (and distro!) and run

sudo apt-get -f install

---

### Post by akshayas1986 on 2007-06-12
Ya I know that limewire is developed on Java. In fact I downloaded java directly from Sun's site. But what baffles me is that it clearly said--libc6 dependencies are unmet. There is only one thing I can do-Reinstall Ubuntu and not to mess with libc libraries ever again.

Thanks people.. I appreciate your help.

---

### Post by az on 2007-06-13
> **akshayas1986 said:**
> In fact I downloaded java directly from Sun's site. But what baffles me is that it clearly said--libc6 dependencies are unmet.

Then the version of java you installed was not built for your version of libc6.  Use the version of java that comes with Ubuntu.  It's in the repos.

---

### Post by akshayas1986 on 2007-06-13
You know this is damn funny!!

If you people have seen, I have posted on a lot of errors with my computer to sound. libc6 failure was a blessing in disguise. I took "az" advice quite seriously and downloaded feisty and upgraded my Ubuntu.. The funny part is that practically all my issues are solved-No Nvidia driver problem, No cursor problem, no sound card problem. And Feisty is brilliant..

Thanks az

Akshaya Srivatsa :)

---

### Post by Chappy7777 on 2007-06-15
Sorry I can't help you, but fwiw thnx for posting this. I downloaded Limewire the other day and got the exacvt same libc6 error. Last eve I spent nearly 2 hrs downloading and installing Java, since I know Limwire needs Java. Also, I was told to do that. So far I have seen no problems coming from the Java install, maybe because I installed it thru Ubuntu's Synaptic. However, Limewire still throws the same error re: libc6 at me when I try to open it.

I wonder if this problem exists w/Frostwire? Can someone tell me.please. I don't mind using Frostwire if I can get it to work. But I don't wanna have both a useless copy of Limewire and Frostwire on here. If I do install Frostwire is it ok to go to the folder w/Limewire and delete Limewire?

---

### Post by Chappy7777 on 2007-06-24
> **Chappy7777 said:**
> Sorry I can't help you, but fwiw thnx for posting this. I downloaded Limewire the other day and got the exacvt same libc6 error. Last eve I spent nearly 2 hrs downloading and installing Java, since I know Limwire needs Java. Also, I was told to do that. So far I have seen no problems coming from the Java install, maybe because I installed it thru Ubuntu's Synaptic. However, Limewire still throws the same error re: libc6 at me when I try to open it.

I wonder if this problem exists w/Frostwire? Can someone tell me.please. I don't mind using Frostwire if I can get it to work. But I don't wanna have both a useless copy of Limewire and Frostwire on here. If I do install Frostwire is it ok to go to the folder w/Limewire and delete Limewire?


BUMP

---

### Post by coffeecups on 2007-12-10
Help!! Am new to Linux and ubuntu. Have been trying to get my DVD player working for weeks now....have installed gxine, libdvdnav4, libdvdplay0, libdvdread3, Automatix and today tried medibuntu all seemed to go well until I tried to install w64 codecs in terminal got a message that said:
 dpkg: error processing w64codecs (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 w64codecs
sue@sue-desktop:~$ sudo apt-get install w64codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
w64codecs is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  w64codecs: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is to be installed
             Depends: libgcc1 (>= 1:4.2.1) but 1:4.1.2-0ubuntu4 is to be installed
             Depends: libstdc++6 (>= 4.2.1) but 4.1.2-0ubuntu4 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
sue@sue-desktop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Reading the reinstall libc6 thread on this forum has left me wondering if I should be trying to do anything with libc6 ?? I'm using feisty fawn and have added all the updates suggested, must be the root as no other users on my computer, what's happening??how come I have to download so much extra stuff to get dvd's to play??
Please help

---

