---
title: "Can't update 12.04.4 server"
date: 2014-09-26
forum: Installation &amp; Upgrades
---

### Post by magpie03 on 2014-09-26
I'm running a small ubuntu server from my home serving static web pages. I have Cups installed as it also acts as a print server. There is no GUI and no mail packages installed. I am using Ubuntu 12.04.4 LTS, 32 bit. When trying to upgrade, is says no upgrade available.
Running this:
```
mikiee33@Server03:~$ sudo do-release-upgrade -d
[sudo] password for mikiee33: 
Checking for a new Ubuntu release
No new release found
mikiee33@Server03:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mikiee33@Server03:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mikiee33@Server03:~$ sudo apt-get update
Reading package lists... Done
mikiee33@Server03:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mikiee33@Server03:~$ 
```
I orginally had this error:
```
Err http://us.archive.ubuntu.com precise-backports/universe i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-backports/main Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-backports/main Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com precise-backports/multiverse Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
```
After running commands to correct it, I still cannot update.
```
mikiee33@Server03:~$ sudo rm /etc/apt/sources.list
mikiee33@Server03:~$ sudo cp /etc/apt/sources.list.save /etc/apt/sources.list
cp: cannot stat `/etc/apt/sources.list.save': No such file or directory
mikiee33@Server03:~$ sudo apt-get update
Reading package lists... Done
mikiee33@Server03:~$ sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
mv: cannot stat `/etc/apt/sources.list': No such file or directory
mikiee33@Server03:~$ sudo touch /etc/apt/sources.list
mikiee33@Server03:~$ sudo add-apt-repository "deb http://archive.ubuntu.com/ubuntu $(lsb_release -sc) main universe restricted multiverse"
sudo: add-apt-repository: command not found
mikiee33@Server03:~$ sudo apt-get update
Reading package lists... Done
mikiee33@Server03:~$ sudo apt-get update --fix-missing
Reading package lists... Done
mikiee33@Server03:~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
I have backups of my WWW folder in case I have to do a fresh install. I want to update because of the latest Bash flaw.
```
mikiee33@Server03:~$ env x='() { :;}; echo vulnerable' bash -c "echo this is a test"
vulnerable
this is a test
mikiee33@Server03:~$ 
```

Kind reguards all
Magpie

---

### Post by Bashing-om on 2014-09-26
magpie03; Yuk !

I look at this and seems there is no longer any sources.list files (??).
Any good result from:
```

ls -al /etc/apt/source*

```
May not be all bad ->

[INDENT][INDENT]let's see where we go from here
[/INDENT][/INDENT]

---

### Post by magpie03 on 2014-09-27
I think I figured it out. I'm running 32 bit server and the new Ubuntu server 14 only comes in 64 bit. Time to get a new server.
Thanks Bashing-om
magpie

---

### Post by ibjsb4 on 2014-09-27
32bit?
[http://releases.ubuntu.com/14.04/](http://releases.ubuntu.com/14.04/)

---

### Post by Bashing-om on 2014-09-27
magpie03; Hey;

Thanks for the sharing, you may have showed me a thing or 2 I was not aware of.

[INDENT][INDENT]buntu
[INDENT][INDENT][INDENT]1 for all and all for one
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by magpie03 on 2014-09-28
Thanks ibjsb4, I went to the main Ubuntu site and all they had was 64 bit. Guess I'm getting lazy and didn't look around enough. Got it downloaded and MD5SUM ok so I'll try to install it later. Thank you again Bashing-om. I ran that command you mentioned and here is the result:
```
3@Server03:~$ ls -al /etc/apt/source*
-rw-r--r-- 1 root root    0 Sep 26 09:09 /etc/apt/sources.list
-rw-r--r-- 1 root root    0 Jun 13 19:08 /etc/apt/sources.list~

/etc/apt/sources.list.d:
total 8
drwxr-xr-x 2 root root 4096 Nov 15  2013 .
drwxr-xr-x 6 root root 4096 Sep 26 09:09 ..
3@Server03:~$
```

Thanks again all.
Magpie

---

### Post by Bashing-om on 2014-09-28
magpie03; Looks good !

Should workie.

No GUI, current install all up to date:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
Make sure ''lts" is set:
```

cat /etc/update-manager/release-upgrades

```

As you have no proprietary driver in use, and no other 3rd party software installed, should now proceed with out a hitch to do that release upgrade:
```

sudo do-release-upgrade

``` note here there is no '-d' switch .. as the 'd' is to go to the 'd'evelopment version - 14.10 - that has not been released to this time.

Else; yeah
 with good backups, a Fresh install is always an option !

Let us know how it goes.

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

