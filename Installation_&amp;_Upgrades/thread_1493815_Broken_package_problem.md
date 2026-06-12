---
title: "Broken package problem"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by debojyoti on 2010-05-26
Dear Friend,

I am very new to Ubuntu and thus suggest me simply. Last night I tried to upgrade my pc from 9.10 to 10.04 version with the alternative cd as the update manager was not showing the new release. There were some problem in installation and the process stopped somewhere. Then, when I tried with the update manager I got some error.

(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `human-theme' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of compiz-gnome:
 compiz-gnome depends on compiz-core (= 1:0.8.4-0ubuntu15); however:
  Version of compiz-core on system is 1:0.8.4-0ubuntu2.1.
 compiz-gnome depends on compiz-plugins (= 1:0.8.4-0ubuntu15); however:
  Version of compiz-plugins on system is 1:0.8.4-0ubuntu2.1.
dpkg: error processing compiz-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 compiz-gnome


Please suggest me how to get rid of this error.

Thanks in advance...........

Kunal

---

### Post by dv3500ea on 2010-05-26
Try:
Go to Applications -> Accessories -> Terminal
Enter ```
sudo apt-get install -f
```

---

### Post by debojyoti on 2010-05-27
Thanks dv3500ea.........I had tried what you had suggested too.....but it gave me the same result......from the command line I got the same error message.....please suggest me some other tricks

:(

---

### Post by dino99 on 2010-05-27
open synaptic repo and check you only use genuine lucid repo (no other release, no third party, no ppa) 

if you previously had grub1 with its menu.list, you need to completly remove them, only grub-pc and grub-common have to be installed with lucid

into console:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

sudo dpkg --configure -a

sudo rm -f /etc/X11/xorg.conf
sudo shutdown -F -r now

---

### Post by theKovenant on 2010-05-27
try to pick up another mirror (system > administration > software channels)

i was having a similar issue here trying to update my system + install Zabbix... it was configured to download from Brazilian mirrors.. now it's configured to the Official channel and i could download the updates.

---

### Post by debojyoti on 2010-05-28
Thanks friends for your reply........

@dino99:: "open synaptic repo and check you only use genuine lucid repo (no other release, no third party, no ppa)

if you previously had grub1 with its menu.list, you need to completly remove them, only grub-pc and grub-common have to be installed with lucid"

didn't understand.....please tell me exactly what I have to do to make this change.........

@theKovenant:: I think its not the mirror problem.........one package "compiz" didn't updated properly (package is broken) and now the updation process is not progressing.

Waiting eagerly for your help.......

---

### Post by Soul-Sing on 2010-05-28
```
 sudo apt-get --reinstall install compiz-gnome
```

---

### Post by debojyoti on 2010-05-28
thanks leoquant.......but the code written by you gave the same results........

Anyone help

---

### Post by Soul-Sing on 2010-05-28
then remove it via /var/lib/dpkg/info
(maybe via nautilus: ```
gksudo nautilus
```)
after this close nautilus and run a
```
sudo apt-get update
```

that should do the trick.

---

### Post by debojyoti on 2010-05-28
Thanks leoquant.......but there are still some problem. Please check the output:

debojyoti@debojyoti:/var/lib/dpkg/info$ gksudo nautilus
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


Please suggest.......

---

### Post by Soul-Sing on 2010-05-28
[COLOR="Red"]first close all -apt/dpkg/softwaremanagers[/COLOR]

```
gksudo nautilus
```



navigate via nautilus to /var/lib/dpkg/info
and remove [COLOR="Red"]compiz-gnome[/COLOR] (use the searchoption rightabove)

close nautilus

run: ```
sudo apt-get update
```

---

### Post by debojyoti on 2010-05-28
I used the code "gksudo nautilus" and a box opened. I navigated to the location /var/lib/dpkg/info and removed (moved to trash) all compiz-genome.*. Then I tried with the command sudo apt-get -f install and got same type of error:

debojyoti@debojyoti:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libfreebob0 libffado1 libxml++2.6-2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  compiz-core compiz-plugins
Suggested packages:
  nvidia-glx
The following packages will be REMOVED:
  compiz-wrapper
The following packages will be upgraded:
  compiz-core compiz-plugins
2 upgraded, 0 newly installed, 1 to remove and 797 not upgraded.
1 not fully installed or removed.
Need to get 0B/757kB of archives.
After this operation, 123kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 
dpkg: warning: files list file for package `compiz-gnome' missing, assuming package has no files currently installed.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `human-theme' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)


I removed all the files associated with compiz and got the error:

(Reading database ... 
dpkg: warning: files list file for package `compiz-gnome' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `compizconfig-backend-gconf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `compiz-wrapper' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `compiz-fusion-plugins-main' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `compiz-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `compiz-plugins' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `compiz-fusion-plugins-extra' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `compiz' missing, assuming package has no files currently installed.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `human-theme' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)


what mistake have I done?

---

### Post by Soul-Sing on 2010-05-28
and what is the outcome of:

```
sudo apt-get update
```
```
sudo apt-get safe-upgrade
```

---

### Post by debojyoti on 2010-05-28
debojyoti@debojyoti:~$ sudo apt-get update 
[sudo] password for debojyoti: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_IN
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_IN
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_IN
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages
Reading package lists... Done                      
debojyoti@debojyoti:~$ sudo apt-get safe-upgrade
E: Invalid operation safe-upgrade
debojyoti@debojyoti:~$

---

### Post by Soul-Sing on 2010-05-28
I think you are out of troubles. dpkg/apt looks fine.No errors
try ```
sudo apt-get upgrade
```

---

### Post by debojyoti on 2010-05-31
sorry leoquant......."sudo apt-get upgrade" command returns me:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  compiz-gnome: Depends: compiz-core (= 1:0.8.4-0ubuntu15) but 1:0.8.4-0ubuntu2.1 is installed
                Depends: compiz-plugins (= 1:0.8.4-0ubuntu15) but 1:0.8.4-0ubuntu2.1 is installed
E: Unmet dependencies. Try using -f.

PLease help..........

---

### Post by Soul-Sing on 2010-05-31
you tried:
```
sudo apt-get -f install
```?

---

### Post by debojyoti on 2010-05-31
Thanks leoquant for your constant support........Output of "sudo apt-get -f install" reads as: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libfreebob0 libffado1 libxml++2.6-2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  compiz-core compiz-plugins
Suggested packages:
  nvidia-glx
The following packages will be REMOVED:
  compiz-wrapper
The following packages will be upgraded:
  compiz-core compiz-plugins
2 upgraded, 0 newly installed, 1 to remove and 797 not upgraded.
1 not fully installed or removed.
Need to get 0B/757kB of archives.
After this operation, 123kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 
dpkg: warning: files list file for package `compiz-gnome' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `compizconfig-backend-gconf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `compiz-wrapper' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `compiz-fusion-plugins-main' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `compiz-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `compiz-plugins' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `compiz-fusion-plugins-extra' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `compiz' missing, assuming package has no files currently installed.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `human-theme' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

Same error, I think.....

---

### Post by debojyoti on 2010-06-01
Anybody please suggest.........

---

