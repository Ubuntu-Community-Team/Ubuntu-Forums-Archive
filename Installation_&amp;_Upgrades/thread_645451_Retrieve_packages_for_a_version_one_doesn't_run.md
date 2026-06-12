---
title: "Retrieve packages for a version one doesn't run"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by Tink on 2007-12-20
Hi,

Is there an easy way to retrieve packages for a version I 
don't have installed? 

I installed my brother in law a dapper 6.06.01 server (running 
7.04 myself). He's on dial-up, and I'd like to d/l the packages he 
needs to get via my broadband and burn them onto CD ... I can't
face the thought of getting around 250MB on a -umm, challenged-
serial line while I'm at his place.


Cheers,
Tink

---

### Post by Partyboi2 on 2007-12-21
Have a look at APTonCD it might meet your needs.
[http://blog.mypapit.net/2007/03/put-apt-get-repository-on-dvdcd-ubuntudebian.html](http://blog.mypapit.net/2007/03/put-apt-get-repository-on-dvdcd-ubuntudebian.html)
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)
I came across another program that does something along the same lines, but I haven't been able to remember the name or find the link for it. :lolflag:

---

### Post by Tink on 2007-12-21
Thanks mate,

But my problem isn't burning deb's that I already have 
downloaded to CD (or making a portable apt-repo), but 
how to download a whole lot of packages needed for a 
DIFFERENT version of Ubuntu w/o having to go through
the directory structure on the ftp server and getting the
latest versions of what what he has installed manually.


Cheers,
Tink

---

### Post by taurus on 2007-12-21
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Tink on 2007-12-21
Very funny :}

So I can search them manually via http rather than ftp :D

Thanks, anyway.

I created the list of stuff he has installed via dpkg -get-selection,
how will the link help me in NOT having to manually donlwload
them one by one?


Cheers,
Tink

---

### Post by Partyboi2 on 2007-12-22
Is using the "**Generate Package Download Script" **under Synaptic Package Manager a option?
If not sure how it works, here is a how-to do it for your situation.

_** On the Dapper machine**_
Open up "Synaptic Package Manager"
Mark all the packages you want to install/upgrade, but [COLOR=Red]**do not**[/COLOR] click on the "**[COLOR=Lime]Apply[/COLOR]**" button instead go to "File" and select "Generate Package Download Script"
Save the script as dapper.sh (I tried saving to Desktop and it didn't save, But saving it to my home folder worked, go figure)
Take the dapper.sh file to the Feisty machine.

_** On the Feisty machine**_
Make a folder on the Desktop  called "downloads". Copy the saved dapper.sh file into the "downloads" folder. 
Open a terminal on the Feisty machine and change to the directory where the script is
```
cd Desktop/downloads
```and run the script
```
sh dapper.sh
```It will download all the packages you need for the Dapper machine into the downloads folder(all going well) 
Then after it has downloaded all the packages that are required. Go back to the Dapper machine, taking with you the "downloads" folder 

_**Back on Dapper Machine**_
Open "Synaptic Package Manager" again, go to "File" and select "Add Downloaded Packages" 
Browse to the directory where the "downloads" folder is (probably Desktop)
Then "**[COLOR=Lime]Apply[/COLOR]**" to install them.

---

