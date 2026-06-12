---
title: "Canon Pixima IP 1600 printer drivers"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by meltonrj on 2007-09-24
1. libcnbj-2.6_0-1_i386.deb
2. bjfilter-2.6_1-1_i386.deb
3. pstocanonbj_3.3-1_i386.deb


I need to find out where to get these dirvers so I can get my printer working again.

Thanks,

Richard Melton

---

### Post by rsambuca on 2007-09-24
Aren't they [here]("http://arzanulhaq.blogspot.com/2007/06/how-to-setup-canon-pixma-ip1600-and.html")?

---

### Post by meltonrj on 2007-09-24
they are but the site is no longer there this is the error I get:


Forbidden

You don't have permission to access /~takushi/ubuntu/ on this server.
Apache Server at mambo.kuhp.kyoto-u.ac.jp Port 80 when I click on get drivers here.

Richard Melton

---

### Post by rsambuca on 2007-09-24
If you follow the instructions on the Details page, he tells you to add a repository and use apt-get to install everything.  Did you try that?

---

### Post by meltonrj on 2007-09-26
I can download  libcnbj-2.6, bjfilter-2.6 but I can't download this file at all pstocanonbj it just tells me that the cups version is not the same.

---

### Post by Fidelio on 2007-10-07
You can download the rpms of the ip2200 from canon and convert them to debs. They work fine.

---

### Post by Guardian-Mage on 2007-10-20
does anyone know how to install the Canon Pixma IP1600 on Ubuntu Linux 7.10 Gutsy Gibbon. Ubuntu can't even install my printer, and nobody here will give me any help!!!!!

[http://ubuntuforums.org/showthread.php?p=3574490#post3574490](http://ubuntuforums.org/showthread.php?p=3574490#post3574490)

---

### Post by rsambuca on 2007-10-20
> **Guardian-Mage said:**
> does anyone know how to install the Canon Pixma IP1600 on Ubuntu Linux 7.10 Gutsy Gibbon. Ubuntu can't even install my printer, and nobody here will give me any help!!!!!

[http://ubuntuforums.org/showthread.php?p=3574490#post3574490](http://ubuntuforums.org/showthread.php?p=3574490#post3574490)

Be patient and give people that know how to figure these things out the time to do so.  Gutsy just came out, and not everyone has installed it yet.

---

### Post by davidpaul2020 on 2007-10-28
download the files from [http://www.aprendelinux.es/manual/19/instalar-impresora-canon-ip1700-o-ip1600/](http://www.aprendelinux.es/manual/19/instalar-impresora-canon-ip1700-o-ip1600/)

---

### Post by pat_bateman on 2007-10-30
Here is a trick to install the PIXMA IP1600 on Ubuntu gutsy using the iP2200 driver.
1- install Alien
```
sudo apt-get update && sudo apt-get install alien libxml1 libpng3
```

2-Get the ip 2200 driver
```
wget http://software.canon-europe.com/files/soft24301/software/iP2200_Linux_260.tar.gz
```

3-Unzip it
```
tar -zxf iP2200_Linux_260.tar.gz
```
and suppress useless ones
```
rm -f cnijfilter-common-2.60-1.src.rpm cnijfilter-ip2200-lprng-2.60-1.i386.rpm
```

4-Convert RPM to DEB packages
```
sudo alien cnijfilter-common-2.60-1.i386.rpm
sudo alien cnijfilter-ip2200-2.60-1.i386.rpm
```

5-Install drivers
```
sudo dpkg -i cnijfilter-common_2.60-2_i386.deb
sudo dpkg -i cnijfilter-ip2200_2.60-2_i386.deb
```

6-Create magic links to make stuff working :) and update the library
```
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
sudo ldconfig
```

7-Restart the printing manager
```
sudo /etc/init.d/cupsys restart
```

8-Configure the new printer using Gnome
System=>Administration=>Printers
Create a new printer.
Pick the "iP2200 Ver.2.60" driver for you iP1600.
And here we are :) your printer should work now.

PS : thanks to mouling for the explanation. ([http://forum.ubuntu-fr.org/viewtopic.php?id=61554&p=1](http://forum.ubuntu-fr.org/viewtopic.php?id=61554&p=1))

---

### Post by UNOwen on 2007-11-18
Thanks for list of commands. I now have a working Canon printer!

The only problem that I encountered was that I couldn't find the ip2200 ver2.60 driver listed when trying to create a new printer through Gnome. I solved that problem by using the CUPS interface ([http://localhost:631](http://localhost:631)) where it was listed. I just followed the instructions and it worked.

---

### Post by angelsguitar on 2008-01-21
> **pat_bateman said:**
> Here is a trick to install the PIXMA IP1600 on Ubuntu gutsy using the iP2200 driver.
1- install Alien
```
sudo apt-get update && sudo apt-get install alien libxml1 libpng3
```

2-Get the ip 2200 driver
```
wget http://software.canon-europe.com/files/soft24301/software/iP2200_Linux_260.tar.gz
```

3-Unzip it
```
tar -zxf iP2200_Linux_260.tar.gz
```
and suppress useless ones
```
rm -f cnijfilter-common-2.60-1.src.rpm cnijfilter-ip2200-lprng-2.60-1.i386.rpm
```

4-Convert RPM to DEB packages
```
sudo alien cnijfilter-common-2.60-1.i386.rpm
sudo alien cnijfilter-ip2200-2.60-1.i386.rpm
```

5-Install drivers
```
sudo dpkg -i cnijfilter-common_2.60-2_i386.deb
sudo dpkg -i cnijfilter-ip2200_2.60-2_i386.deb
```

6-Create magic links to make stuff working :) and update the library
```
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
sudo ldconfig
```

7-Restart the printing manager
```
sudo /etc/init.d/cupsys restart
```

8-Configure the new printer using Gnome
System=>Administration=>Printers
Create a new printer.
Pick the "iP2200 Ver.2.60" driver for you iP1600.
And here we are :) your printer should work now.

PS : thanks to mouling for the explanation. ([http://forum.ubuntu-fr.org/viewtopic.php?id=61554&p=1](http://forum.ubuntu-fr.org/viewtopic.php?id=61554&p=1))

I followed this steps, and my iP1600 worked perfectly...until the last CUPS Ubuntu update. :(  Does anyone else has the same problem? I've searched the Internet but had not found anything useful yet.  If any of you out there found a solution, please help. Thanks in advance.

---

### Post by huizemiriam on 2008-02-21
Thanx!!

---

### Post by justleen on 2008-02-22
> **angelsguitar said:**
> I followed this steps, and my iP1600 worked perfectly...until the last CUPS Ubuntu update. :(  Does anyone else has the same problem? I've searched the Internet but had not found anything useful yet.  If any of you out there found a solution, please help. Thanks in advance.

[I followed this guide, that worked for me. ]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200")

---

### Post by Kossilar on 2008-03-16
Does anybody know why CUPS consistently refuses to accept my password? I've been trying to get this damn thing working for days, but it refuses to recognize me. Its intensely frustrating.

EDIT:

Okay, I figured out why the printer manager was refusing to accept my password. I have multiple users on this system, but only the first user created during installation is added to the 'lpadmin' group which is required in order to be able to manage any printers on the system. 

So to solve the problem I had to do this:

> 
System -> Administration -> Users and Groups
"Manage Groups"
lpadmin -> "Properties"
Check your username in the box that appears.

That allowed me to immediately add the printer with no further password issues. (Original post can be found here: [http://ubuntuforums.org/showthread.php?t=637507&highlight=printer+manager+password](http://ubuntuforums.org/showthread.php?t=637507&highlight=printer+manager+password))

My printer still doesn't work, even though its been correctly added to the system. But that's as likely a printer issue as an issue with Ubuntu. Thanks for the HOW-TO.

---

