---
title: "removing graphics drivers and installing again"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by hlekat on 2007-12-07
I am working with Ubuntu about a month ( 7.04 updated to 7.10) , i am newbie so try to explain as easy as you can :lolflag: .

My graphic adapter is radeon x1600.
I am trying to install catalyst 7.11 . 

I followed the installation guide @ [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.11_Driver_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.11_Driver_Manually")

but i also tried and with some others guides, that's why i believe that i have to purge some files which i have added from all the guides. ( maybe i don't because autoremove does not make anything ).

Know i am using the restricted driver manager. 

In the wiki installation guide i get the first error @ debconf libstdc++5 linux-headers-generic

and then when i config the driver, the aticonfig does not start and when i try to config the driver manual i canot find in the xorg.conf these options : 

Option		"VideoOverlay"		"on"
Option		"OpenGLOverlay"		"off"  

Thanks.

---

### Post by Pumalite on 2007-12-07
Maybe you need this:
sudo apt-get install linux-headers-`uname -r`

---

### Post by hlekat on 2007-12-08
again when i type debconf libstdc++5 linux-headers-generic :

debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied

Can't exec "libstdc++5": No such file or directory at /usr/share/perl/5.8/IPC/Open3.pm line 168.

open2: exec of libstdc++5 linux-headers-generic failed at /usr/share/perl5/Debconf/ConfModule.pm line 58


can this be responsible for the driver ?

---

### Post by Pumalite on 2007-12-08
Did you upgrade? Have you kept up with the updates?

---

### Post by i586 on 2007-12-08
Copy & paste this in a terminal:

```

sudo apt-get install -y linux-headers-$(uname -r) build-essential

```This should install required files to either build and/or configure the driver.

Regards.

---

### Post by hlekat on 2007-12-08
i always update + upgrade , 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.22-14-generic is already the newest version.
build-essential is already the newest version.

although nothing changed when i type the debconfig...

---

### Post by Pumalite on 2007-12-08
Looks like the upgrade from 7.04 to 7.10 was messy. Consider saving data and /home and doing a clean install of 7.10

---

### Post by hlekat on 2007-12-08
Maybe this is the solution because i saw in the forum that you have to make some changes in the repositories and some other things but i haven't do anything, just upgrade.

Is there a way to find out for sure that i need to make the installation from the beginning ?

---

### Post by Pumalite on 2007-12-08
You can wait for somebody with a better answer.

---

### Post by PmDematagoda on 2007-12-08
Pumalite, the Nvidia installer requires the kernel source, not just the headers.

Install the source using:-
```

sudo apt-get install linux-source-2.6.22
```

Then try installing the drivers again.

---

### Post by hlekat on 2007-12-08
> **PmDematagoda said:**
> Pumalite, the Nvidia installer requires the kernel source, not just the headers.

Install the source using:-
```

sudo apt-get install linux-source-2.6.22
```

Then try installing the drivers again.


Setting up linux-source-2.6.22 (2.6.22-14.46) ...
$ sudo debconf libstdc++5 linux-headers-generic
[sudo] password for user:
Can't exec "libstdc++5": No such file or directory at /usr/share/perl/5.8/IPC/Open3.pm line 168.
open2: exec of libstdc++5 linux-headers-generic failed at /usr/share/perl5/Debconf/ConfModule.pm line 58


you are saying for nvidia installer,
is ati catalyst also have nvidia installer ? :confused:

edit: i am using the following guide for install the 7.11 driver
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.11_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.11_Driver_Manually)

---

### Post by PmDematagoda on 2007-12-08
Sorry, are you installing the Nvidia drivers or ATi ones?

---

### Post by hlekat on 2007-12-08
ati :KS

---

### Post by PmDematagoda on 2007-12-08
Oh, that complicates matters for me since I have never installed the ATi driver, only Nvidia ones, I am afraid I cannot help you further, sorry.

I hope you find the solution to this soon.

---

### Post by hlekat on 2007-12-08
it okey ;) thanks. 

i think that the solution in a couple of months away, until the 7.11 driver  will be found at synaptic.

---

