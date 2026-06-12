---
title: "unable to install anything in ubuntu 18.04"
date: 2018-07-29
forum: Installation &amp; Upgrades
---

### Post by macadarsh on 2018-07-29
whenever I try to install any software I get a same error message. 

I have installed Ubuntu on my 32 Gib SanDisk pendrive, (not in live or persistance mode) I used a live cd to boot and (disconnected my internal hard drive) install ubuntu (and bootloader also) on my penDrive.

Everything works fine, I can make new files and save them, next time when i boot again all the previous files, bookmarks, settings etc are there. System is behaving very much same as if a had a normal install on my hard drive. Except this:

I can browse internet using Mozilla Firefox, I use college proxy settings to connect to internet (provided proxy in settings > networks > networks proxy > apply system wide)
but i can not install any program through terminal nor from Ubuntu Software Center.
 
What is wrong here? 

--------------------------------------------------------------------------------------------------------------------------------------------------------------------
```
mac@macUbuntu:~$ sudo apt-get install vlc

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package vlc
```


--------------------------------------------------------------------------------------------------------------------------------------------------------------------
```
mac@macUbuntu:~$ sudo apt-get update

Ign:1 cdrom://Ubuntu 18.04.1 LTS _Bionic Beaver_ - Release amd64 (20180725) bionic InRelease
Err:2 cdrom://Ubuntu 18.04.1 LTS _Bionic Beaver_ - Release amd64 (20180725) bionic Release
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease
  Could not connect to archive.ubuntu.com:80 (91.189.88.161). - connect (111: Connection refused) Could not connect to archive.ubuntu.com:80 (91.189.88.152). - connect (111: Connection refused) Could not connect to archive.ubuntu.com:80 (91.189.88.162). - connect (111: Connection refused) Could not connect to archive.ubuntu.com:80 (91.189.88.149). - connect (111: Connection refused)
Err:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates InRelease
  Unable to connect to archive.ubuntu.com:http:
Err:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports InRelease
  Unable to connect to archive.ubuntu.com:http:
Err:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security InRelease
  Unable to connect to archive.ubuntu.com:http:
Reading package lists... Done
E: The repository 'cdrom://Ubuntu 18.04.1 LTS _Bionic Beaver_ - Release amd64 (20180725) bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

---

### Post by deadflowr on 2018-07-29
You need to set the apt proxy settings:
[https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy]("https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy")

Note use the command
```
sudo -H gedit
```
instead of gksudo, as gksudo no longer exists.

---

### Post by macadarsh on 2018-07-29
Thanks deadflower!

I was working on this for past 2 days, tried a lot to search for this on  my own on internet, but got no success. And you just answer in 15  minutes. You rocks!:guitar:


I can now download VLC, Kontact and other applications.

1). but still i am getting this, Do I need to do something more?
```
mac@macUbuntu:~$ sudo apt-get update
Ign:1 cdrom://Ubuntu 18.04.1 LTS _Bionic Beaver_ - Release amd64 (20180725) bionic InRelease
Err:2 cdrom://Ubuntu 18.04.1 LTS _Bionic Beaver_ - Release amd64 (20180725) bionic Release
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports InRelease
Hit:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security InRelease
Reading package lists... Done
E: The repository 'cdrom://Ubuntu 18.04.1 LTS _Bionic Beaver_ - Release amd64 (20180725) bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

2). Just curious to konw: when i was using ubunrtu 16.04 there was no need for a separate proxy settings for this [B]apt-get thing.
So is it something new in Ubuntu1 8.04 or I am missing something.

---

### Post by deadflowr on 2018-07-29
> 1). but still i am getting this, Do I need to do something more?
Open the Program Software and Updates and uncheck the installable from cdrom option.

> 2). Just curious to konw: when i was using ubunrtu 16.04 there was no need for a separate proxy settings for this [B]apt-get thing.
So is it something new in Ubuntu1 8.04 or I am missing something.
It's not a new thing, but it's not clear what differences you had between the 16.04 setup and the 18.04 setup

---

### Post by macadarsh on 2018-07-29
Thanks! again, Did same as what you suggested, now no error message.

---

### Post by macadarsh on 2018-07-29
My problem Solved here.:)

---

### Post by padre13 on 2019-01-25
Merci beaucoup : je n'arrivais pas à télécharger R, c'est OK
    cordialement

---

