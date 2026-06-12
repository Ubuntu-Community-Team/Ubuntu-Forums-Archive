---
title: "could not upgrade anything in ubuntu 10.04 LTS"
date: 2013-05-27
forum: Installation &amp; Upgrades
---

### Post by 1sezgin on 2013-05-27
Since long time I am using ubuntu 10.04 LTS,
Because of some problems I decided to upgrade to 12.04 LTS but I could not. Now I am trying to upgrade the packages.
For any package it always give the same error and then ubuntu crash.

I tried many things to solve dpkg error but it does not help 
Thanks in advance

Setting up linux-image-2.6.32-47-generic (2.6.32-47.109) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing linux-image-2.6.32-47-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libpackagekit-glib2-12 (0.5.7-0ubuntu2.2) ...

Setting up packagekit (0.5.7-0ubuntu2.2) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: /usr/lib32/libstdc++.so.5 is not a symbolic link

Errors were encountered while processing:
 linux-image-2.6.32-47-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.32-47-generic (2.6.32-47.109) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing linux-image-2.6.32-47-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.32-47-generic

---

### Post by ajgreeny on 2013-05-27
I am not quite sure what you mean or what version of ubuntu you currently have, but 10.04 can no longer be updated as it has lost support.

I suspect the best way forward for you is to backup all your personal files and folders from your home, including all hidden content, and then do a clean install of 12.04.  If you don't like unity have a look at Xubuntu 12.04.

Once you have the new version up and running you can restore the files/folders of your old home.

---

### Post by 1sezgin on 2013-05-27
But if I make a clean install of 12.04, I have to install all programs again.
Is there any way to save installed programs?
Thanks

---

### Post by sudo san on 2013-05-27
Maybe the package files are corrupt. Try cleaning them:

```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update && sudo apt-get dist-upgrade
```

You could then try and upgrade ubuntu:
```
sudo sed -i 's/lucid/precise/g' '/etc/apt/sources.list'
sudo apt-get update
sudo apt-get dist-upgrade -y
sudo update-grub
sudo dpkg --configure -a
```

The last two commands are just for good measure to make sure that even if a few packages did not get configured, they will, and that grub is all set to boot into 12.04.

This is the procedure I use when upgrading ubuntu. It also keeps all your programs. Be aware that you might need to reset your background and ensure that you backup all your stuff before you upgrade as stated by [COLOR=#000000]ajgreeny[/COLOR].

Hope it helps.:)

---

### Post by 1sezgin on 2013-05-27
Thanks for your answer,
But while I was doing command 
sudo apt-get update && sudo apt-get dist-upgrade
at the end the system crashed. After some tries I succeed to restart and now it gives following error
sezgin@sezgin1:~$ sudo apt-get dist-upgrade
Bus errorackage lists... 0%
sezgin@sezgin1:~$ sudo apt-get clean
sezgin@sezgin1:~$ sudo apt-get autoclean
Bus errorackage lists... 0%

---

### Post by ibjsb4 on 2013-05-27
> **1sezgin said:**
> But if I make a clean install of 12.04, I have to install all programs again.
Is there any way to save installed programs?
Thanks

[http://ubuntuforums.org/showthread.php?t=261366&p=1521615&viewfull=1#post1521615](http://ubuntuforums.org/showthread.php?t=261366&p=1521615&viewfull=1#post1521615)

You may have to install "dselect", but that would be on the fresh install and not 10o4.

---

### Post by 1sezgin on 2013-05-27
Thanks for your advices but unfortunately I was not talking about installed package by ubuntu. 
I installed some analysing program which are not in that list. It seems I will lose all of it.

---

### Post by ibjsb4 on 2013-05-27
That is not so good news.  Give me the name of the program and I will look for a way to save it.

---

### Post by sudo san on 2013-05-27
> **1sezgin said:**
> Thanks for your answer,
But while I was doing command 
sudo apt-get update && sudo apt-get dist-upgrade
at the end the system crashed. After some tries I succeed to restart and now it gives following error
sezgin@sezgin1:~$ sudo apt-get dist-upgrade
Bus errorackage lists... 0%
sezgin@sezgin1:~$ sudo apt-get clean
sezgin@sezgin1:~$ sudo apt-get autoclean
Bus errorackage lists... 0%

I do not see an error message but "Bus errorackage lists" does look quite strange, do you have ubuntu installed in a different language?
Also, do you have a low amount of R.A.M? If you do, you will find it very difficult running 12.04. You could always install lubuntu-desktop or xubuntu-desktop and remove ubuntu-desktop.

---

### Post by deadflowr on 2013-05-27
> **1sezgin said:**
> Thanks for your advices but unfortunately I was not talking about installed package by ubuntu. 
I installed some analysing program which are not in that list. It seems I will lose all of it.

If you installed it, then reinstall it.
Backup the files needed and reinstall.

If the packages don't install, I'd advise to look into alternatives as a package which doesn't install is probably out of date and potentially harmful.

---

### Post by 1sezgin on 2013-06-01
Unfortunately there was a bad sector and I could not install ubuntu on that harddisk. I got an external hdd and used for install.

---

