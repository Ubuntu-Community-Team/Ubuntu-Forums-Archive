---
title: "apt-gt dpkg error upgrading packages"
date: 2011-03-11
forum: Installation &amp; Upgrades
---

### Post by cjejuni on 2011-03-11
cannot update/upgrade pkgs error in:

SyntaxError: invalid syntax
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/software-center_3.0.7_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


any fix to     /var/cache/apt/archives/software-center_3.0.7_all.deb    ??? help?
thanks,
cj

---

### Post by cjejuni on 2011-03-11
it's actually 

apt-get 

thanks

---

### Post by Hakunka-Matata on 2011-03-11
What's the status?

---

### Post by cjejuni on 2011-03-11
no synaptic, dpkg, software-center, apt-get usable, gives the same error. trying to upgrade software-center=>3.0.7 
here is the shortened terminal output:

Do you want to continue [Y/n]? y
(Reading database ... 365591 files and directories currently installed.)
Preparing to replace software-center 3.0.7 (using .../software-center_3.0.7_all.deb) ...
  File "/usr/bin/pycentral", line 87
    raise ValueError, 'unknown version info %s' % vinfo
                    ^
SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
  File "/usr/bin/pycentral", line 87
    raise ValueError, 'unknown version info %s' % vinfo
                    ^
SyntaxError: invalid syntax
dpkg: error processing /var/cache/apt/archives/software-center_3.0.7_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
  File "/usr/bin/pycentral", line 87
    raise ValueError, 'unknown version info %s' % vinfo
                    ^
SyntaxError: invalid syntax
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/software-center_3.0.7_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


thanks.


Ubuntu 10.10 Maverick meerkat
python3.1.2

---

### Post by Hakunka-Matata on 2011-03-11
can you open synaptic and check on broken packages?  ?

---

### Post by cjejuni on 2011-03-11
synaptic does not come back with broken pkgs. just leaves the pkgs window empty. tried to install ax.25 apps. much of the same error, could not copy of the detailed output.
here is  the error gui report:


E: /var/cache/apt/archives/software-center_3.0.7_all.deb: subprocess new pre-removal script returned error exit status 1

---

### Post by Hakunka-Matata on 2011-03-11
It appears you're very comfortable manuevering around in synaptic, yes?  You're saying synaptic does not report any broken packages, either in the bottom line of the gui, or in Custom Filters > Broken?  
Does looking at File > history in synaptic help at all?

---

### Post by Hakunka-Matata on 2011-03-11
[http://ubuntuforums.org/showthread.php?p=10471350]("http://ubuntuforums.org/showthread.php?p=10471350")

if  you haven't already found this thread, it appears very similar to your situation.

---

### Post by cjejuni on 2011-03-11
just got out of aptitude. it tells me that **software-center** is **half-configured**. this pkg does not want to get processed. tried renaming it, but still not processed.

dpkg: error processing /var/cache/apt/archives/**software-center_3.0.7_all.deb** (--unpack):
 subprocess new pre-removal script returned error exit status 1

can't get rid/replace of this pkg! it is holding all updating/upgrading...

---

### Post by cjejuni on 2011-03-11
> **Hakunka-Matata said:**
> [http://ubuntuforums.org/showthread.php?p=10471350](http://ubuntuforums.org/showthread.php?p=10471350)

if  you haven't already found this thread, it appears very similar to your situation.



no there is another one that uses aptitude. explains why it is not working. 
so i followed this one. i think it just got worse. new error now:

E: Could not open file /var/lib/dpkg/status - open (2: No such file or directory)
E: The package lists or status file could not be parsed or opened.


i don't where this is going now!@#$^#&

---

### Post by Hakunka-Matata on 2011-03-18
>                                   **Re: Black screen and login required after update**             

The following is copied out of a thread here on these forums, don't recall thread #
                                                                
Boot to recovery mode and drop to the command line terminal. 
If you have any 3rd party repositories in your */etc/apt/sources.list* (this includes those all too often problematic PPA repos), then comment them out 
(i.e., put a **#** in front of them. Also comment out any third party repos that may be lurking in files in your */etc/apt/sources.list.d/* directory.
Then try running this:
     Code:
     ```
sudo apt-get update
sudo apt-get dist-upgrade
sudo reboot 
```If that does not fix it, then try from recovery mode:
     Code:
     ```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get dist-upgrade
sudo reboot 
```If that does not help then try from recovery mode:
     Code:
     ```
sudo dpkg --clear-avail && sudo apt-get update
sudo apt-get dist-upgrade
sudo reboot 
```     Quote:
                                                                              
                 *I can see older versions of ubuntu  in the boot screen and ubuntu 10.10-25 opens fine but I cant check for  updates.. I get "Check your connection", although firefox works  normally.*
                                 
Also try loading a different mirror if you can from: system >  administration > software sources, or the software sources in  Synaptic Package Manager.

And welcome to the Ubuntu forums!
                                                                                                        
   **Black screen and login required after update**             
                                                                Hello all..
Yesterday I found that ubuntu needs to be updated, so I did update and  all files were downloaded but I had an error that not all packages could  be installed..
I figured I would restart and then try to install the rest of the packages, but now I have a black screen that says:

Ubuntu 10.10 Dell-Inspiron-1564 tty1
Login:
Password:

I tried my ubuntu username and password but I get "Login incorrect"
I tried repair from the recovery menu but that didn't work..

I can see older versions of ubuntu in the boot screen and ubuntu  10.10-25 opens fine but I cant check for updates.. I get "Check your  connection", although firefox works normally.
What can I do to fix this?
[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=10556889")Hoping this might help........

---

