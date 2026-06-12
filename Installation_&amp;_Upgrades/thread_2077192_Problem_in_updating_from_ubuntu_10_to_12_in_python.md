---
title: "Problem in updating from ubuntu 10 to 12 in python-minimal"
date: 2012-10-27
forum: Installation &amp; Upgrades
---

### Post by zarzor_2010 on 2012-10-27
Hello All,

I have a problem in updating ubuntu from 10 to 12

when I do 
```

sudo apt-get dist-upgrade

```I get the following
E: Could not perform immediate configuration on 'python2.7-minimal'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)

Then I tried

```

sudo apt-get install python-minimal

```I got the following

The following packages have unmet dependencies:
  libglib2.0-0: Breaks: gnome-control-center (< 1:3) but 1:2.30.1-0ubuntu2 is to be installed
                Breaks: gvfs (< 1.8) but 1.6.1-0ubuntu1build1 is to be installed
  libpango1.0-0: Breaks: plymouth (< 0.8.2-2ubuntu19) but 0.8.2-2ubuntu2.2 is to be installed
  ppp: Breaks: network-manager (<= 0.8.0.999-1) but 0.8-0ubuntu3.3 is to be installed
E: Broken packages


Any help please. I need to get this resolved ASAP as all my work is not working now because most of the packages are broken.

Thank you in advance
Mina

---

### Post by zarzor_2010 on 2012-10-28
Any help please?

Thanks

---

### Post by jerrrys on 2012-10-28
This is not an update, but a release upgrade. 10 to 12? 10.04; 10.10; 12.04; 12.10?   Which one are you on right now?  If your not sure; in terminal enter:

lsb_release -a

-----------------------

apt-get dist-upgrade

Will not give you a release upgrade

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

-----------------------

Also in terminal try this:

sudo apt-get clean

sudo apt-get update

And post any errors

---

### Post by zarzor_2010 on 2012-10-28
Thank you for your reply

I did  "lsb_release -a" and the results are:

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise

Initially I had ubuntu 10 and when I updated using "update manager" now I have ubuntu 12.04.

However most of the packages are broken as mentioned in my first post.

Thank you
Mina

---

### Post by jerrrys on 2012-10-28
And what about my last suggestion?  Clean; update and post.

---

### Post by zarzor_2010 on 2012-10-28
Sorry,
I have tried 
sudo apt-get clean
sudo apt-get update

and no errors. Here are the last lines

"Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Packages [8,218B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [182kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [4,395B]
Fetched 1,029kB in 3s (329kB/s)                       
Reading package lists... Done"

---

### Post by jerrrys on 2012-10-28
Then your good.  Now do a:

sudo apt-get upgrade

sudo apt-get dist-upgrade

---

