---
title: "Synaptic not reading from installation CD"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by rafciu123 on 2007-02-10
Hi,

One of community members gave me the following advice for one of my questions:

"Run Synaptic, enable MultiUniverse repositors and install linux-restricted-modules that match your kernel. They contain the madwifi drivers needed."

I run synaptic and try to add those packages but it tries to get them from the internet instead of installation CD. I get the following message:

Failed to fetch [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu), ...... <-- url to the package
Temporaty failure resolving security.ubuntu.com

My network doesn't work because I need to install those packages.

When I check Add Cd-ROM it scans installation CD and in panel where all packages are displayed it displays none without returning any error message.

How do I force synaptic to read packages from installation CD?

---

### Post by Bil-E-daKid on 2007-02-10
Hi there,

The best way to 'force' apt to use the CDROM only, is to modify the file /etc/apt/sources.list and comment out all the non-CDROM lines.

Don't forget to run sudo apt-get update afterwards to make apt read the indexes from the CDROM.

Also, don't forget to uncomment out those lines once you're done!  :-)


Regards
Bil-E-daKid

---

### Post by rafciu123 on 2007-02-11
I edit sources.list int text editor but I cannot save it. It says that I have no permission to save the file.

During installation I was prompted to provide just one username x and password. Now when I type su command and enter password for  user x, it says it is the wrong password.

---

### Post by taurus on 2007-02-11
```
gksudo gedit /etc/apt/sources.list
```
or
```
sudo nano -w /etc/apt/sources.list
```

---

### Post by Bil-E-daKid on 2007-02-11
Hello rafciu123,

Given taurus has already shown you how to get to the file as a superuser, I'll let you know why I think you got the 'wrong password' message.

I think if you just type 'su' then the password you are being prompted for is the root password - but the root account is disabled by default so, if you entered your normal user password, you get told it's the wrong one - because it's not the root password.

However, if you use sudo or gksudo, you get prompted to reauthenticate your normal user (the first user created during installation which has sudo rights).

Does that make sense?

Regards
Bil-E-daKid

---

