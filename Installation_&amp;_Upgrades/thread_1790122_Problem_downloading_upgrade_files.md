---
title: "Problem downloading upgrade files"
date: 2011-06-24
forum: Installation &amp; Upgrades
---

### Post by gr384 on 2011-06-24
I've been having an odd problem when using Update Manager...I notice that as the files are downloaded (I've turned on the view details option so I can see the individual files and the percentages downloaded) when the file gets to 80% ( or similar) there is a brief QUEUED message in place of the percentage and then it goes back to 0% and it starts again. In these cases there are usually three or more files being downloaded simultaneously.
It may have something to do with the relatively slow connection speed (<10k) because I have noticed that when the speed is higher the download tends to work. Currently this is Ubuntu 10.04.
Unfortunately there's little I can do about the speed (it's a satellite connection as well) but otherwise the connection is fine. 
Any suggestions ?

g

---

### Post by jerrrys on 2011-06-24
open a terminal and enter

sudo apt-get update

and post any errors you get.  if no errors are present, in terminal

sudo apt-get upgrade

---

### Post by gr384 on 2011-06-25
I've done as you suggested: the update ran without problem and the upgrade started perfectly normally. But it showed exactly the same symptoms as I described previously, I couldn't see any error nor exception message, the relevant lines are below 

You can see that the first three Gets look fine, but then Get 4 repeats Get 1; I was watching and it got to about 85%, Then I let Get 4 (and the other 2, of course) run and again it got to the same sort of figure and Get 5 started - repeated Get 1/Get 4

It seems quite repeatable - but as I mentioned it may go away if the transfer speeds are higher - so if you need more information let me know.

g

:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  language-pack-gnome-fr
The following packages will be upgraded:
  adobe-flash-properties-gtk adobe-flashplugin apt apt-transport-https
  apt-utils dkms firefox firefox-3.5 firefox-3.5-branding
  firefox-3.5-gnome-support firefox-branding firefox-gnome-support gimp
  gimp-data grub-common grub-pc icedtea-6-jre-cacao initscripts libcurl3
  libcurl3-gnutls libgimp2.0 libldap-2.4-2 libmodplug0c2 libpoppler-glib4
  libpoppler5 libsvn1 libxml2 libxml2-utils openjdk-6-jdk openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib poppler-utils python-libxml2 qemu
  qemu-common qemu-kvm sysv-rc sysvinit-utils xulrunner-1.9.2
40 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 89.4MB/89.8MB of archives.
After this operation, 197kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main libxml2 2.7.6.dfsg-1ubuntu1.2 [829kB]
Get:2 [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) lucid-updates/main apt 0.7.25.3ubuntu9.5 [1,811kB]
Get:3 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner adobe-flashplugin 10.3.181.26-0lucid1 [5,142kB]
Get:4 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main libxml2 2.7.6.dfsg-1ubuntu1.2 [829kB]
Get:5 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main libxml2 2.7.6.dfsg-1ubuntu1.2 [829kB]
3% [2 apt 1,387kB/1,811kB 76%] [5 libxml2 134kB/829kB 16%] [3 adobe-flashplugin 1,387kB/5,142kB ^C

I terminated it with a CTRL/C

---

### Post by dino99 on 2011-06-25
open synaptic repo tab and select "main server" instead of gg. actually

---

### Post by gr384 on 2011-06-25
Sadly it doesn't seem to have improved - it did update the package info from the main server successfully (it had been Guernsey - I'm in the UK) but...

while I was watching - adobe-flashplugin 10.3.181.26-0lucid1 (5142 kB) got to 95%, then back to zero; apt 0.7.25.3ubuntu9.5 got to the 80s twice and then back to zero...

So no improvement, I'm afraid.

g

---

### Post by gr384 on 2011-06-26
No other suggestions ?

I have also noticed that if I unselect a number of items the download may go better - but only if the result of the reduced number of items is that there is only a single file being downloaded at a time. As I mentioned (see the posting with the copy of the terminal screen) usually it seems to download three files at a time.

So is there a parameter setting to restrict a single file at a time download ? (I have looked but couldn't find anything)

g

---

