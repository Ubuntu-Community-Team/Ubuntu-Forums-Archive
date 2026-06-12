---
title: "Problem with Synaptic package manager!"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by gagea on 2010-05-11
Hello,

I installed ubuntu 9.10. But there is problem with installing some software. I can not use these commands. 

sudo apt-get update
sudo apt-get install r-base

the returns is here:

root@ubuntu:/home/ubuntu# sudo apt-get install r-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package r-base
root@ubuntu:/home/ubuntu# 


root@ubuntu:/home/ubuntu# sudo apt-get update
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Translation-en_US
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources
Reading package lists... Done
root@ubuntu:/home/ubuntu#




I desperately need to solve the problem. Please help me.

---

### Post by tommcd on 2010-05-11
> **gagea said:**
> 
I installed ubuntu 9.10. But there is problem with installing some software. I can not use these commands. 

sudo apt-get update
sudo apt-get install r-base

the returns is here:

root@ubuntu:/home/ubuntu# sudo apt-get install r-base
....
Firstly, if you are running the system as **root**, this is a BIG security risk!! You are guaranteed to have problems if you are running the system as root. 
If you have just enabled the root account, but are logging in as a regular user and using su to gain root privileges when you need them, then this is less of a problem.
Please note that enabling the root account is not recommended in Ubuntu.
I have been using Ubuntu for 5 years. I have never found it necessary or beneficial in any way to enable the root account in Ubuntu.
Second, you would not even need to use sudo if you are running the system as root, or if you have enabled the root account and used su to gain root privileges. 
> **gagea said:**
> 
I desperately need to solve the problem. Please help me.
The output from your "*sudo apt-get update*" does not list the *universe* repository. Note that r-base is in the universe repository:
[http://packages.ubuntu.com/karmic/r-base](http://packages.ubuntu.com/karmic/r-base)
To enable the universe and mulitiverse repositories, see this:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
BTW, Ubuntu 10.04 is the current version. You may want to install Ubuntu 10.04 since the newest version of Ubuntu may have a more up to date version of r-base.

---

### Post by gagea on 2010-05-11
> **tommcd said:**
> Firstly, if you are running the system as **root**, this is a BIG security risk!! You are guaranteed to have problems if you are running the system as root. 
If you have just enabled the root account, but are logging in as a regular user and using su to gain root privileges when you need them, then this is less of a problem.
Please note that enabling the root account is not recommended in Ubuntu.
I have been using Ubuntu for 5 years. I have never found it necessary or beneficial in any way to enable the root account in Ubuntu.
Second, you would not even need to use sudo if you are running the system as root, or if you have enabled the root account and used su to gain root privileges. 

The output from your "*sudo apt-get update*" does not list the *universe* repository. Note that r-base is in the universe repository:
[http://packages.ubuntu.com/karmic/r-base](http://packages.ubuntu.com/karmic/r-base)
To enable the universe and mulitiverse repositories, see this:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
BTW, Ubuntu 10.04 is the current version. You may want to install Ubuntu 10.04 since the newest version of Ubuntu may have a more up to date version of r-base.

Thanks a lot for advice re-root account. I tried [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources), and it did work with r-base. But, the other problems still exist. There is no "artha" and other softwares that exist before in package manager any more. About, the latest version of ubuntu, 10.04, I have already downloaded it, but I could not burn it on a CD. I am using my external hard driver for ubuntu, so for making a start up USB, I need the liveCD (I think, as I am doing it for my current version). Do you have any idea of how to do it.

---

### Post by dino99 on 2010-05-11
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

---

### Post by gagea on 2010-05-11
> **dino99 said:**
> [http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)


Thanks a lot. But I can not understand it. Anything simpler I can get it?

---

### Post by tommcd on 2010-05-12
> **gagea said:**
>  There is no "artha" and other softwares that exist before in package manager any more. 
Artha is in the Ubuntu Lucid 10.04 repos:
[http://packages.ubuntu.com/lucid/artha](http://packages.ubuntu.com/lucid/artha)
Again, it is in the *universe* repository. So make sure you have the universe repo enabled.
> **gagea said:**
> 
About, the latest version of ubuntu, 10.04, I have already downloaded it, but I could not burn it on a CD.
How are you burning it to CD? 
What problem(s) did you have?
Are you burning the CD from Windows or Ubuntu?
And what program are you using to burn the CD
Did you check the md5sum of the Ubuntu 10.04 iso you downloaded?
You need to be specific here.

---

