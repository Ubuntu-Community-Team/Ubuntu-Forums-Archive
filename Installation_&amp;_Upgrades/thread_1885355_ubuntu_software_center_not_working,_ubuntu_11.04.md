---
title: "ubuntu software center not working, ubuntu 11.04"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by tediuskalangwa on 2011-11-23
ubuntu software center is not working,i want to install skype but if i type skype in the search button, it keeps on loading.am using ubuntu 11.04
please help

---

### Post by WasMeHere on 2011-11-23
Welcome to the Ubuntu Forums, tediuskalangwa,

Start a terminal window with ***ctrl + alt + t*** and type or cut and paste the following command line, finish with the Enter key!
```
sudo apt-get install skype
```
This will install skype in the same way (without using the graphical user interface)

Have fun finding out about Ubuntu :-)
Olle

---

### Post by tediuskalangwa on 2011-11-23
I have tried to install it using terminal but it gave the following message 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
linknet@linknet-OptiPlex-GX620:~$

---

### Post by bluexrider on 2011-11-23
[http://ubuntuguide.net/install-skype-on-ubuntu-11-04-natty-narwhal-3264-bit](http://ubuntuguide.net/install-skype-on-ubuntu-11-04-natty-narwhal-3264-bit)

meanwhile you have another issue with your "lists" file

In terminal:

sudo rm /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricte  d_binary-i386_Packages

sudo apt-get update

---

### Post by WasMeHere on 2011-11-23
What happens if you try to update your system?
```
sudo apt-get update
sudo apt-get upgrade
```
Does it work or do you get errors? Sometimes hints are written in 'human readable language'. If errors please post them. Someone here might understand from the output what to do.

---

### Post by tediuskalangwa on 2011-11-23
I have tried to update the system at the end it gives me this message
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
linknet@linknet-OptiPlex-GX620:~$

---

### Post by mörgæs on 2011-11-23
What happens if you boot the computer, run 

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean

```

and then the two commands from post 5?

---

### Post by tediuskalangwa on 2011-11-23
i tried this command line 
sudo apt-get install libqt4-dbus libqt4-network libqt4-xml libasound2
 and gives me the same as above.

---

### Post by WasMeHere on 2011-11-23
Read man apt-get to find out what can be done from the command line.
Try
```
sudo apt-get update --fix-broken
```
and
```
sudo apt-get update --fix-missing
```

An alternative is to use Synaptic (a graphical user interface). Maybe you need to check for the program sources.

---

### Post by tediuskalangwa on 2011-11-23
hi it has worked for me i have now installed skype,thanks a lot for your help,may the lord bless everyone.

---

