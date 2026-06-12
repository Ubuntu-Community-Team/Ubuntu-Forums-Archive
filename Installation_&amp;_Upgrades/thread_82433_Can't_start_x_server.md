---
title: "Can't start x server"
date: 2005-10-26
forum: Installation &amp; Upgrades
---

### Post by Sureshot324 on 2005-10-26
I'm trying to install ubuntu linux, and when it gets to the point where it's the first time I log on, it tries to start x server without success. I get an error:

Failed to start the X server

It gives me the option to check the log, and when i scroll to the bottom of it this is what i see:

ATI Mach64 in slot 5:0:0 could not be detected
ATI Mach64 in slot 5:0:1 could not be detected

No devices detected
Fatal server error:

no screens found


To make matters worse, i can't get root access! The installation never prompted me for a root password (maybe that part of the installation happens after x is started). When i enter su command it asks for root password, and i tried using the same password as the account i created, and a blank password, but it won't work. This makes in almost impossible to do anything at all.

Here is my list of hardware:
athlon64 3000
dfi lanparty nf4 ultra-d
1gb corsair value ram
ati x800xl pci-e
audigy 2zs
hauppauge tv tuner
hitachi cml174 lcd monitor

I'm using the amd64 version of ubuntu 5.10. Can anyone help?

---

### Post by Koybe on 2005-10-26
You can do 
```
sudo su
```
to get on the root account using the same password as the current user.
Then you can this to get X server working :
```
dpkg-reconfigure xserver-xorg
```

Or even simply use :
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by abiezerm on 2005-10-27
ok, i have a emachines athlon x64 and works properlly :D

---

