---
title: "dpkg issue"
date: 2014-07-01
forum: Installation &amp; Upgrades
---

### Post by olesia2 on 2014-07-01
Hello!

I know i have made a mistake - namely deleted dpkg folders from /usr/bin
Now trying to run apt-get install im getting a error
```

Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)

```

Some output:
```
sudo apt-get install dpkg
dpkg is already the newest version.


```
```

sudo dpkg --configue-a
The program 'dpkg' is currently not installed. You can install it by typing:
apt-get install dpkg


```

```

sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.


```
as mentioned here [http://ubuntuforums.org/archive/index.php/t-1516119.html](http://ubuntuforums.org/archive/index.php/t-1516119.html) , post #5 i have downloaded dpkg_1.15.5.6ubuntu4_i386.deb, but can't install binultils, because dont have a valid C compiler, that requires a dpkg, it comes to a circle.

Could you give me a piece of advice how it would be possible to fix the situation?

---

### Post by xc3RnbFO8P on 2014-07-01
Read this:
[http://people.adams.edu/~cdmiller/posts/Ubuntu-dpkg-recovery/]("http://people.adams.edu/~cdmiller/posts/Ubuntu-dpkg-recovery/")

---

### Post by bapoumba on 2014-07-01
[http://ubuntuforums.org/showthread.php?t=1516119&p=9500205#post9500205](http://ubuntuforums.org/showthread.php?t=1516119&p=9500205#post9500205)
May be here. You'll have to adjust for Trusty and your architecture : [http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/](http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/)
Current version here is :
```
Installed: 1.17.5ubuntu5.3
```

Thing is, there is no dpkg folder in /usr/bin :
```
ls -a /usr/bin/dpkg*
/usr/bin/dpkg                     /usr/bin/dpkg-query
/usr/bin/dpkg-deb                 /usr/bin/dpkg-split
/usr/bin/dpkg-divert              /usr/bin/dpkg-statoverride
/usr/bin/dpkg-maintscript-helper  /usr/bin/dpkg-trigger

```
Is dpkg the only file you deleted ?

---

### Post by xc3RnbFO8P on 2014-07-01
This is mine:
> ringi@ringi-Lenovo-Ideapad-Flex-15:~$ ls -a /usr/bin/dpkg*
/usr/bin/dpkg                 
/usr/bin/dpkg-gencontrol          
/usr/bin/dpkg-scansources
/usr/bin/dpkg-architecture    
/usr/bin/dpkg-gensymbols          
/usr/bin/dpkg-shlibdeps
/usr/bin/dpkg-buildflags      
/usr/bin/dpkg-log-summary         
/usr/bin/dpkg-source
/usr/bin/dpkg-buildpackage    
/usr/bin/dpkg-maintscript-helper  
/usr/bin/dpkg-split
/usr/bin/dpkg-checkbuilddeps  
/usr/bin/dpkg-mergechangelogs     
/usr/bin/dpkg-statoverride
/usr/bin/dpkg-deb             
/usr/bin/dpkg-name               
/usr/bin/dpkg-trigger
/usr/bin/dpkg-distaddfile    
/usr/bin/dpkg-parsechangelog      
/usr/bin/dpkg-vendor
/usr/bin/dpkg-divert          
/usr/bin/dpkg-query
/usr/bin/dpkg-genchanges      
/usr/bin/dpkg-scanpackages
ringi@ringi-Lenovo-Ideapad-Flex-15:~$ 

---

### Post by olesia2 on 2014-07-02
> **Ringi said:**
> Read this:
[http://people.adams.edu/~cdmiller/posts/Ubuntu-dpkg-recovery/](http://people.adams.edu/~cdmiller/posts/Ubuntu-dpkg-recovery/)

Hello Ringi and thank you for your idea, i get the following error:
```
root@starit4:/var/cache/apt/archives# dpkg --force-depens -i dpkg_1.17.5ubuntu5.3_amd64.deb
The program 'dpkg' is currently not installed. You can install it by typing:
apt-get install dpkg

```

apt-get install doesnt work either
```
root@starit4:/var/cache/apt/archives# apt-get install dpkg
Reading package lists... Done
Building dependency tree
Reading state information... Done
dpkg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 32 not upgraded.


```
would there be a way to install it again without aptget?

---

### Post by olesia2 on 2014-07-02
Hello Bapoumba,
dpkg is the only think i deleted, meaning all the dpkg-* _folders_ from /usr/bin

output:
```

root@starit4:/usr/bin# ls -a /usr/bin/dpkg*
ls: cannot access /usr/bin/dpkg*: No such file or directory

```

---

### Post by olesia2 on 2014-07-02
Bapoumba, thank you for a link,
i dont have gdebi or ar installed, so i can't follow the advice > So you will have to use `ar' to unpack the .deb archive (debian packages are `ar' type archives).
```

root@starit4:/usr/bin# ar x dpkg*.deb data.tar.gz
The program 'ar' can be found in the following packages:
 * binutils


```
i got binutils via wget, but the following error prevents me from installing it:
```

root@starit4:/home/azureuser/binutils-2.24# ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln works... yes
checking whether ln -s works... yes
checking for a sed that does not truncate output... /bin/sed
checking for gawk... gawk
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: in `/home/azureuser/binutils-2.24':
configure: error: no acceptable C compiler found in $PATH


```
downloaded build-essential, this happens
```

root@starit4:/build-essential-11.6ubuntu6# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for dpkg-architecture... no
configure: error: The dpkg development files (dpkg-dev) must be installed to build this package.

```

is there any way out of the circle? 
any help appreciated

---

### Post by xc3RnbFO8P on 2014-07-02
> **olesia2 said:**
> Hello Ringi and thank you for your idea, i get the following error:
```
root@starit4:/var/cache/apt/archives# dpkg --force-depens -i dpkg_1.17.5ubuntu5.3_amd64.deb
The program 'dpkg' is currently not installed. You can install it by typing:
apt-get install dpkg

```

apt-get install doesnt work either
```
root@starit4:/var/cache/apt/archives# apt-get install dpkg
Reading package lists... Done
Building dependency tree
Reading state information... Done
dpkg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 32 not upgraded.


```
**would there be a way to install it again without aptget?**

Get these dpkg files in /usr/bin/ from another computer (i386) and paste them into /usr/bin/ in your computer

or try this (the third option, 2nd answer):
[http://askubuntu.com/questions/94542/how-can-i-repair-my-installation]("http://askubuntu.com/questions/94542/how-can-i-repair-my-installation")

---

### Post by olesia2 on 2014-07-02
Hi Ringi!
Following your advice i have copied dpkg files from another ubuntu computer
Now i have the following:
```

root@starit4:/usr/bin# ls -a dpkg*
dpkg      dpkg-divert              dpkg-query   dpkg-split         dpkg-trigger
dpkg-deb  dpkg-maintscript-helper  dpkg-repack  dpkg-statoverride


```

but apt-get install still doesnt work, the same error as before appears:
```

Extracting templates from packages: 100%
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)

```

```

root@starit4:/usr/bin/partial# dpkg --configure -a
bash: /usr/bin/dpkg: No such file or directory

```

```

root@starit4:/var/backups# whereis dpkg
dpkg: /usr/bin/dpkg /etc/dpkg /usr/lib/dpkg /usr/bin/X11/dpkg /usr/share/dpkg /usr/share/man/man1/dpkg.1.gz

```

thank you

---

### Post by bapoumba on 2014-07-02
Is /usr/bin/dpkg owned by root:root ?

Installing with apt-get wont work until dpkg does, as apt-get hands on the instal/remove/purge jobs to dpkg.

---

### Post by olesia2 on 2014-07-02
Hi, Bapoumba

thank you for your answer,
here is hte output of files ownership
```

root@starit4:/usr/bin# ldd /usr/bin/dpkg
        not a dynamic executable
root@starit4:/usr/bin# ls -la dp*
-rwxrwxr-x 1 root root 260328 Jul  2 09:27 dpkg
-rwxr-xr-x 1 root root 120876 Jul  2 09:27 dpkg-deb
-rwxr-xr-x 1 root root 124940 Jul  2 09:27 dpkg-divert
-rwxr-xr-x 1 root root  17222 Jul  2 09:27 dpkg-maintscript-helper
-rwxr-xr-x 1 root root 128964 Jul  2 09:27 dpkg-query
-rwxr-xr-x 1 root root   8793 Jul  2 09:27 dpkg-repack
-rwxr-xr-x 1 root root  59212 Jul  2 09:27 dpkg-split
-rwxr-xr-x 1 root root  50992 Jul  2 09:27 dpkg-statoverride
-rwxr-xr-x 1 root root  63260 Jul  2 09:27 dpkg-trigger

```

---

### Post by bapoumba on 2014-07-02
Hmm. I need to go, so my thoughts for now : either the system does not know you have a (maybe, maybe not) working dpkg or apt-get does not know. 
Does dpkg -l <some_package> work ?

---

### Post by olesia2 on 2014-07-02
Hello!

dpkg -i <package> didnt work for any package. 
i have rebooted a computer, then again downloaded dpkg files from another ubuntu machine, and then followed the process  (found here [http://askubuntu.com/questions/401514/dpkg-error-cannot-scan-updates-directory-var-lib-dpkg-updates-no-such-fil](http://askubuntu.com/questions/401514/dpkg-error-cannot-scan-updates-directory-var-lib-dpkg-updates-no-such-fil) ) first answer
and now apt-get works! so seems like dpkg is back

thank you for your help

---

### Post by steeldriver on 2014-07-02
Are you sure you copied the /usr/bin/dpkg* binaries from a machine with the same architecture? The 'not a dynamic executable' (when you're sure it is) tends to indicate a mismatch i.e. 32-bit versus 64-bit. Can we see

```

file $(which dpkg)

file $(which bash)

```

---

### Post by bapoumba on 2014-07-02
> **olesia2 said:**
> Hello!

dpkg -i <package> didnt work for any package. 
i have rebooted a computer, then again downloaded dpkg files from another ubuntu machine, and then followed the process  (found here [http://askubuntu.com/questions/401514/dpkg-error-cannot-scan-updates-directory-var-lib-dpkg-updates-no-such-fil](http://askubuntu.com/questions/401514/dpkg-error-cannot-scan-updates-directory-var-lib-dpkg-updates-no-such-fil) ) first answer
and now apt-get works! so seems like dpkg is back

thank you for your help
Do you mean just creating the /var/lib/dpkg/updates/ file or the rest of the answer too ?
These are not in /usr/bin :)

---

### Post by olesia2 on 2014-07-03
Hello!
Steeldriver, here is the output
```

root@starit4:/home/azureuser# file $(which dpkg)
/usr/bin/dpkg: ELF 64-bit LSB  executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=3641052f5f185a248e8f255073259ff144027b30, stripped
root@starit4:/home/azureuser#

root@starit4:/home/azureuser# file $(which bash)
/bin/bash: ELF 64-bit LSB  executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=796da7aa73903b1e5608a8ff8433669b7e00e980, stripped

```
Bapoumba, i meant that i was trying to install *deb package with dpkg, and dpkg didnt itself work correctly :/ now its ok :)

---

### Post by bapoumba on 2014-07-03
OK thanks, in the future please remember to keep both eyes open when playing with the root filesystem :)

---

