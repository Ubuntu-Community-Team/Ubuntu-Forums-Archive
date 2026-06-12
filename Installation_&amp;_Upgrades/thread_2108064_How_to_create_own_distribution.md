---
title: "How to create own distribution?"
date: 2013-01-23
forum: Installation &amp; Upgrades
---

### Post by Carro on 2013-01-23
hey all,
 I finished installing a 12.10 core install
and have everything i needed .. works great and uses 20MB memory :)
now i need to distribute it and when i look at the disk size its almost 1GB of stuff downloaded while installing .. 
how can i make it small enough to distribute while not breaking

* ethenet networking ( no wireless , didnt install it either )
* lighttpd 
* one libcrypto.so i need
* gnome-terminal 
* basic sudo/bash etc

Can someone guide me please ?


thanx all

---

### Post by tgalati4 on 2013-01-23
How do you plan to distribute it?  CD (700MB)?  The Ubuntu team has made a decision to break the 700MB barrier so you are now forced to use a DVD or USB to carry the larger footprint.

A google search of "respin ubuntu tutorial" brings up a bunch of hits.  This one is older and may not work correctly: (But it does outline the basic steps.)

[http://www.tuxradar.com/content/build-your-own-linux-distribution-easy-way](http://www.tuxradar.com/content/build-your-own-linux-distribution-easy-way)

---

### Post by Carro on 2013-01-26
Is there no one available to help ?

---

### Post by sudodus on 2013-01-26
How do you want to distribute it? What media, what amounts?

I suggest to upload a compressed image to some cloud server and let people download it and install it. With this method there is no sharp limit of the size.

---

### Post by Carro on 2013-01-28
The plan is to do a 4shared like distribution 
but i am interested to find out why we need 1GB of stuff to run a small ubuntu server
and if there is a way to "clean" the system of unneeded things
lets say i am 100% sure i wont be installing anything else on this machine.

regards
Carro

---

### Post by BlinkinCat on 2013-01-28
> **Carro said:**
> Is there no one available to help ?

Hi,

Just a reminder, it is considered acceptable to bump your thread every 24 hours in the forum unless you get an answer in the meantime of course -

Cheers - :)

---

### Post by Cheesehead on 2013-01-28
> **Carro said:**
> why we need 1GB of stuff to run a small ubuntu server

You certainly don't need 1GB of packages to run a small server. And there are several ways to easily distribute what you want...if you keep an open mind.

For example, do you really need to distribute everything in the install media? Honestly, what you are trying to distribute seems more like a metapackage than an whole new distro. Or managing your own install media (do you really want to support failed-install support requests?)

Another example, why Gnome-terminal -which drags in all of Xwindows and Gnome- for a mere terminal? You have six ttys already. Most servers don't use X.

Just about everything you want is on the Minimal Install iso: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
This installs everything in the ubuntu-minimal metapackage.

From there, most users upgrade to the ubuntu-standard metapackage.

You can easily build your own metapackage on top of either. Your users download and install the metapackage, and it pulls in all of the dependencies you want.

If you REALLY want to customize the installer, look into using a preseed file:  [https://help.ubuntu.com/8.04/installation-guide/i386/preseed-using.html](https://help.ubuntu.com/8.04/installation-guide/i386/preseed-using.html)

---

### Post by Carro on 2013-01-29
I DID do a minimal install last week .. i forget but i am pretty sure it was over 50--600 mb .. ( i might have ****** up something tho )
but i am thinking along the lines of 
tinycore/damm small linux 
( the issue with tiny core is i cannot get a decent presistent system going )
dsl i started looking into yesterday 
but i really wanted to stick to ubuntu as i am comfortable with apt-get :)

so is there like a +atime thing i can use , see what files have no been used since the last 3 hours ( randomly ) and delete the rest of the stuff ?

thanx guys for the help.


and sorry ..you are right about gnome-terminal ..dont know why i put it there .. i need ssh on the box so i dont need gnome-terminal .. i will be sshing in
or using the lighttpd pages

---

### Post by sudodus on 2013-01-29
What should be possible to do with your own distribution? Maybe you can list what you want:

- graphics or not
- wired internet, wifi
- internet tools (browser, email client ...)?
- local tools (editors, readers for documents, players for music, video)
- servers (ssh (with or without GUI), samba, vnc, ...)
- ...

Do you want a persistent live system (to run from a CD or USB drive)?
- If you  want a live system, I think you should start with an existing distro with a image for a live system.

Do you want a portable system, that will boot from most computers?
- An 'installed Ubuntu system' can also be portable (when installed to a USB drive), as long as you don't install any proprietary drivers.

Do you expect people to use the system of your distro as it is, or to use it to make installations into internal drives?

And why is it so important, to make it as small as possible?
--
The answers to these questions will make a big difference.
--
*Edit:* Yes, you can use ***find*** to find files with time-stamps newer than a limit. See ```
man find
``` Example: the following command will list the files created during the previous 24 hours in the current directory excluding hidden files and files in hidden directories.
```
sudo find * -ctime -1 -type f
```
This command will find the hidden ones too.
```
sudo find . -ctime -1 -type f
```

---

### Post by Cheesemill on 2013-01-29
It's going to be very difficult to get a usable Ubuntu installation in under 1GB, take a look at the results I got when testing out different minimal installations of Ubuntu:
[http://ubuntuforums.org/showpost.php?p=12156448&postcount=10](http://ubuntuforums.org/showpost.php?p=12156448&postcount=10)

Bear in mind that all of those installations were command line only - no GUI.

---

### Post by Cheesehead on 2013-01-29
> **Carro said:**
> I DID do a minimal install last week .. i forget but i am pretty sure it was over 50--600 mb .. ( i might have ****** up something tho )

Seems likely. The Minimal Image is only 28MB, not 500.
Try building again from ubuntu-minimal. VMs are handy for that...so are chroots.

---

### Post by Carro on 2013-01-29
Ok lets list the things i need
this needs to run in a virtualbox/vmware only not installed on physical machine so 


* ssh server of some kind ( i need to run scripts from host machine to access into the guest linux , the one we are trying to create )

* http server to server up pages static , i have used microhttpd today and does what i need it to do .

* i have a binary images that runs in about 60 MB memory and the size of the file is about 120MB  so i need 4 ( different versions of the similar image ) images stored , so hd space needs to be atleast 500 MB usabe and free 

* network connectivity so the vm can run scripts and wget new configs from the server on the internet 


thats all really !!

in my mind this should be under 50MB install and use about the same amount of memory 


question is how the heck do i do it :(


thanx guys !!

---

### Post by Carro on 2013-01-29
Delete duplicate

---

### Post by Carro on 2013-01-29
Delete duplicate

---

### Post by Carro on 2013-01-29
Delete duplicate

---

### Post by Cheesehead on 2013-01-29
> **Carro said:**
> question is how the heck do I do it :(

How do you create it? Or how do you distribute it?
There are several ways to do both.

Create: Create a VM, install using the Minimal image, then add the packages you want, and change the config files and data files you want to change. Keep careful track of what you add. Consider using a version control system to help you track changes and revert mistakes. Stop when you have a working system.

So far, all you have described can installed on top of ubuntu-minimal with this. Networking is already included in ubuntu-minimal
```
apt-get install dropbear micro-httpd
wget your_binary_url -o /var/www/
```

Distribute: The easiest may be to simply distribute the VM image. Or simply distribute the install script for the user to run after installing the Minimal image. If there are a lot of packages, but no config changes, then a metapackage is a simple way to go. If you have really customized the system and want the maintenance overhead, use a preseed file.

---

### Post by JOHNNYG713 on 2013-01-29
starting from scratch, with a ubuntu stock install, install synaptic package manager, open settings,preferences, and untick "consider recommended packages as dependencies", install "bleachbit" to clean up both user and root, mark for complete removal all unwanted applications, be careful, after you have installed and tweaked your release, the last step is to use bleachbit, to clean up, and "Disk usage analyzer" to see how big you disk is! but again as stated before you might find it hard to get below 1Gig, and building from a ubuntu mini install, you will have to know what dependencies are needed for some things, and what basic applications are missing, this can be very tedious and mind numbing !! 
also you may want to install ubuntu tweak, as it has a very good janitor that cleans stuff that bleachbit misses ! Good luck my friend ! :KS

---

### Post by Carro on 2013-01-30
Ok guys :( spent another 2 days on this and i am defeated
is there any kind soul who can create this for me please ?
i a small vm disk with aptget working ..
i can put mini_httpd and my binaries in there 
if you can help please please do 


thanx all

---

