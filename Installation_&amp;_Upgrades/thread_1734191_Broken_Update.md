---
title: "Broken Update?"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by usaar on 2011-04-20
I tried updating as normal and got this error. What should I do?

```

john@sicherheit:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up language-selector-common (0.6.7) ...
dpkg: error processing language-selector-common (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of language-selector:
 language-selector depends on language-selector-common (= 0.6.7); however:
  Package language-selector-common is not configured yet.
dpkg: error processing language-selector (--configure):
 dependency problems - leaving unconfigured
Processing triggers for python-central ...
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Errors were encountered while processing:
 language-selector-common
 language-selector
E: Sub-process /usr/bin/dpkg returned an error code (1)
john@sicherheit:~$ 

```

---

### Post by tommcd on 2011-04-20
Try running:
```
sudo dpkg-configure -a
sudo apt-get update
sudo apt-get dist-upgrade
```
You should use *dist-upgrade* instead of *upgrade*. Using only upgrade will not allow installing new packages that come along once in a while.

Are you using any 3rd party repos, including those all too problematic PPA repos? Or do you just have the standard Ubuntu repos?

And welcome to the Ubuntu forums!

---

### Post by CalsMum on 2011-04-20
I have repeatedly tried to upgrade today and keep getting the following message:
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.35-28-generic_2.6.35-28.49_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.35-28-generic_2.6.35-28.49_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.2.153.1ubuntu0.10.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.2.153.1ubuntu0.10.10.1_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.35-1028.49_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.35-1028.49_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/v/vsftpd/vsftpd_2.3.0~pre2-4ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/v/vsftpd/vsftpd_2.3.0~pre2-4ubuntu2.1_i386.deb) 404  Not Found [IP: 91.189.88.31 80]

My internet connection is working fine, and I am at a loss.

---

### Post by tommcd on 2011-04-21
> **CalsMum said:**
> I have repeatedly tried to upgrade today and keep getting the following message:
My internet connection is working fine, and I am at a loss.
The mirror you are using seems to be down at the moment.
Open Synaptic Package Manager and select a different mirror. Then reload your sources and see if you can update.

And welcome to the Ubuntu forums!

---

### Post by usaar on 2011-04-21
> **tommcd said:**
> Try running:
```
sudo dpkg-configure -a
sudo apt-get update
sudo apt-get dist-upgrade
```
You should use *dist-upgrade* instead of *upgrade*. Using only upgrade will not allow installing new packages that come along once in a while.

Are you using any 3rd party repos, including those all too problematic PPA repos? Or do you just have the standard Ubuntu repos?

And welcome to the Ubuntu forums!

Upon running the first command I get 

```
john@sicherheit:~$ sudo dpkg-configure -a
sudo: dpkg-configure: command not found
```

sudo apt-get update completes successfully, the other gives an error.

```
john@sicherheit:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up language-selector-common (0.6.7) ...
dpkg: error processing language-selector-common (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of language-selector:
 language-selector depends on language-selector-common (= 0.6.7); however:
  Package language-selector-common is not configured yet.
dpkg: error processing language-selector (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Processing triggers for python-central ...
Errors were encountered while processing:
 language-selector-common
 language-selector
E: Sub-process /usr/bin/dpkg returned an error code (1)
john@sicherheit:~$ 
```

This is the same error I got the first time. It occurred primarily when the Update Manager tried to update. It gave the same exact error. I then attempted to do it from the terminal only to get the same error. After following your instructions (the same thing I did before seeking help here), the error persists. I have no third-party anything. It's all standard/stock.

Also, thanks for welcoming me. It's nice to see such friendliness here.

---

### Post by AlanR8 on 2011-04-21
The command is

> sudo dpkg --configure -a

---

### Post by usaar on 2011-04-21
> **AlanR8 said:**
> The command is > sudo dpkg --configure -a

```
john@sicherheit:~$ sudo dpkg --configure -a
Setting up language-selector-common (0.6.7) ...
dpkg: error processing language-selector-common (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of language-selector:
 language-selector depends on language-selector-common (= 0.6.7); however:
  Package language-selector-common is not configured yet.
dpkg: error processing language-selector (--configure):
 dependency problems - leaving unconfigured
Processing triggers for python-central ...
Errors were encountered while processing:
 language-selector-common
 language-selector
john@sicheheit:~$
```
Errors galore!

---

### Post by vuetrip on 2011-04-21
I had problems with language-selector & language-selector-common just last week, 


there is a new version that fixes th above bug in 0.6.7 run sudo apt-get update -f in terminal and all should be well again :D

---

### Post by tommcd on 2011-04-22
> **AlanR8 said:**
> The command is
Thanks for posting that. 
Sorry for the typo usaar.

---

### Post by usaar on 2011-04-25
Thanks. All seems to be working now.

---

### Post by mohamedirfanzubair on 2011-04-26
I am getting the following problem while updating..

Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release.gpg
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg                             
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) maverick/main Translation-en              
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en             
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_IN
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en_IN
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) maverick/main Translation-en_IN
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release           
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release           
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources/DiffIndex
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main i386 Packages/DiffIndex
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_IN
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages/DiffIndex
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main i386 Packages
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources      
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main i386 Packages
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_IN
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Err [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main i386 Packages                       
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources      
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_IN
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_IN
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_IN
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_IN
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_IN
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release.gpg
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en_IN
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_IN
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_IN
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_IN
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe i386 Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse i386 Packages
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted i386 Packages
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main i386 Packages
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse i386 Packages
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe i386 Packages
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/maverick/Release.gpg](http://linux.dropbox.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://linux.dropbox.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2](http://linux.dropbox.com/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://linux.dropbox.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz)  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by tommcd on 2011-04-27
> **mohamedirfanzubair said:**
> I am getting the following problem while updating..

Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg
  Something wicked happened resolving 'proxy-host:http' (-5 - No address associated with hostname)

Are you behind a proxy? If so, there seems to something wrong with your proxy settings.
Try not to use a proxy if you can.
If you must use a proxy, see this for setting up proxy settings in Synaptic Package Manager:
[http://www.ubuntugeek.com/how-to-configure-ubuntu-desktop-to-use-your-proxy-server.html#more-2584](http://www.ubuntugeek.com/how-to-configure-ubuntu-desktop-to-use-your-proxy-server.html#more-2584)

---

