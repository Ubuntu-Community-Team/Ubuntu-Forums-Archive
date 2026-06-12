---
title: "Newbie - package install question"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by carputer.irl on 2010-03-18
Hi folks, 
 
I'm another new user to ubuntu and I'm trying ot setup Squid / SARG.
 
I have them installed and working on ubuntu server 9.10 but there is a bug in the version of sarg (2.2.5) that i've installed using the "apt-get install sarg" command.
 
I see that sarg 2.2.6 and 2.2.7 are both available, but how do I get either of these updates installed - without having to compile code etc ... is there a simple command like the "apt-get install" command that will upgrade SARG from 2.2.5 to 2.2.7 for me ???
 
 
Any help would be very much appreciated ...

---

### Post by MelDJ on 2010-03-18
how about 
```
sudo apt-get upgrade sarg
```

---

### Post by carputer.irl on 2010-03-18
Thanks for this suggestion. However this reports that there are no upgrades available.
 
When I check using "dpkg -s sarg" I see that I have 2.2.5-2 installed.
 
Any other suggestions on how to get 2.2.6 or 2.2.7 installed ?

---

### Post by Sef on 2010-03-18
Go to [sarg]("http://sarg.sourceforge.net/sarg.php")'s website to download 2.2.7.

---

### Post by phillw on 2010-03-18
Hi, the latest one showing on my Synaptics Package Manager is 2.2.6-1

(System --> Administration --> Synaptics Package Manager)

Which does it show on yours ? If it shows the same, then click on the box and mark for upgrade.

Regards,

Phill.

---

### Post by carputer.irl on 2010-03-18
@phillw: I'm running in server mode - no GUI. I have 2.2.5-1 installed and when I run the "sudo apt-get upgrade sarg" command the system say's that there are no upgrades available. I'd settle for 2.2.6-1, this has corrected the issue I'm seeing with sarg compiling reports. 
 
@Sef: I have looked at the sarg website, and downloaded both the 2.2.6-1.deb and 2.2.7-1.deb packages but when I try to install these using the dpkg command i'm told that this is not a valid DEB package, which is why I'm looking for help.
 
I'm a total newbie on linux - but I have spent most of today looking for answers on the web, but nothing I've found seems to work.

---

### Post by warlockvix on 2010-03-23
I'm also on 9.10 and was bit with the reporting bug. While I normally don't do this because of all sorts if nastiness that can happen if you are not careful, I added the below lines to my /etc/apt/sources.list file -

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe

Then I - 
sudo apt-get update
sudo apt-get upgrade sarg

After the upgrade ran, I had 2.2.6 installed. I also removed the above lines from sources.list after the upgraded completed.

Squid will tell you it can't find the sarg.conf. The path for sarg will need to be changed from the default /etc/squid/sarg.conf to /etc/sarg/sarg.conf. 

So far it's working great and the bug in 2.2.5 seems have been fixed.

---

