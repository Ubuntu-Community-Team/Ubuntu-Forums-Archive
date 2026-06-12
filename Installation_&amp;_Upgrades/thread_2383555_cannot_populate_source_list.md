---
title: "cannot populate source list"
date: 2018-01-26
forum: Installation &amp; Upgrades
---

### Post by azazelazure on 2018-01-26
Hello,

I recently installed Ubuntu 16.04, and during an attempt to install Wine I ran into numerous problems with the apt-get command.  I have deleted the /etc/apt/sources.list file, reset the sources in Software & Update Gui, and have no other sources in my gui.  Currently when I run sudo apt-get I get the following
```

 sudo apt-get update
Err:1 http://security.ubuntu.com/ubuntu xenial-security InRelease              
  Cannot initiate the connection to security.ubuntu.com:80 (2001:67c:1562::16). - connect (101: Network is unreachable) [IP: 2001:67c:1562::16 80]
Err:2 http://us.archive.ubuntu.com/ubuntu xenial InRelease                     
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::16). - connect (101: Network is unreachable) [IP: 2001:67c:1562::16 80]
Err:3 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::16). - connect (101: Network is unreachable) [IP: 2001:67c:1562::16 80]
Reading package lists... Done
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::16). - connect (101: Network is unreachable) [IP: 2001:67c:1562::16 80]
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease  Cannot initiate the connection to security.ubuntu.com:80 (2001:67c:1562::16). - connect (101: Network is unreachable) [IP: 2001:67c:1562::16 80]
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::16). - connect (101: Network is unreachable) [IP: 2001:67c:1562::16 80]
W: Some index files failed to download. They have been ignored, or old ones used instead.


```

I have looked around a lot for solutions. I have tried change changing the server in the Software & Update gui, and when I close the window it gives me a notification that it fails to update. when i list sources i receive this 

```

cat /etc/apt/sources.list
deb http://us.archive.ubuntu.com/ubuntu/ xenial main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ xenial-security multiverse restricted universe main
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse restricted universe main
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main universe restricted multiverse #Added by software-properties


```

Which is notably better than the first time I opened the file and it was empty, however it still isn't working.  I have checked into IPv6 settings, as I have read there has been issues with Ubuntu mirrors and IPv6, however I'm not certain the changes I made were correct or taken.  I am working online via a mobile hotspot, and have tried connecting through both 2.4ghz and 5ghz settings with no avail.  I'm not sure what to do about this.  I am new to Ubuntu.

Thank you

---

### Post by deadflowr on 2018-01-26
You and try a force ipv4:
```
sudo apt-get -o Acquire::ForceIPv4=true update
```
if that runs smooth then
```
sudo apt-get -o Acquire::ForceIPv4=true dist-upgrade
```
to apply the updates you most likely have.

For reference see: [https://www.vultr.com/docs/force-apt-get-to-ipv4-or-ipv6-on-ubuntu-or-debian]("https://www.vultr.com/docs/force-apt-get-to-ipv4-or-ipv6-on-ubuntu-or-debian")

---

### Post by azazelazure on 2018-01-26
I tried to force IPv4, result below 

```

sudo apt-get -o Acquire::ForceIPv4=true update
Err:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
  Could not connect to us.archive.ubuntu.com:80 (91.189.91.23). - connect (111: Connection refused) [IP: 91.189.91.23 80]
Err:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.23 80]
Err:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
  Could not connect to security.ubuntu.com:80 (91.189.91.26). - connect (111: Connection refused) [IP: 91.189.91.26 80]
Reading package lists... Done                         
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease)  Could not connect to us.archive.ubuntu.com:80 (91.189.91.23). - connect (111: Connection refused) [IP: 91.189.91.23 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease](http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease)  Could not connect to security.ubuntu.com:80 (91.189.91.26). - connect (111: Connection refused) [IP: 91.189.91.26 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.23 80]
W: Some index files failed to download. They have been ignored, or old ones used instead.


```

---

### Post by deadflowr on 2018-01-26
See here, maybe:[https://askubuntu.com/questions/678285/111-connection-refused]("https://askubuntu.com/questions/678285/111-connection-refused")

---

### Post by azazelazure on 2018-01-26
Checking that i get the following 
```

~$ cat /etc/apt/apt.conf
cat: /etc/apt/apt.conf: No such file or directory

```

I don't know if I need to be in a particular directory for this to work.  I ran this both normally and with the sudo prefix and nothing changed.   Can I create this file?

::Edit::

I created the file via gedit, but left it blank.  It opens with both gedit and nano, however addition of the file did not change anything.

---

### Post by deadflowr on 2018-01-26
Look in /etc/apt/apt.conf.d directory for any file which might indicate proxy.
Post what you see of the files in said directory if you don't know what is what.

---

### Post by azazelazure on 2018-01-26
Nothing looks like a proxy. 

```

/etc/apt/apt.conf.d$ ls
00aptitude            10periodic       50appstream
00trustcdrom          15update-stamp   50unattended-upgrades
01autoremove          20archive        70debconf
01autoremove-kernels  20auto-upgrades  99update-notifier
01-vendor-ubuntu      20dbus

```

---

### Post by azazelazure on 2018-01-26
I decided to check the server lists and add a mirror manually from the mirror list.  I ran the test for "Select Best Server" and received a notification saying "No suitable download server was found: Please check your internet connection."  I am on the network and PC that I'm testing the servers on, so I know my internet works.

---

### Post by azazelazure on 2018-01-28
Fixed.  Issue was not with ubuntu, it was with my hotspot.   Reset the phone and ubuntu connected to mirrors.   Thanks for the help.

---

