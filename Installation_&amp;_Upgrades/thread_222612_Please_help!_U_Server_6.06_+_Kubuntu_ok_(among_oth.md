---
title: "Please help! U Server 6.06 + Kubuntu ok (among other questions)"
date: 2006-07-25
forum: Installation &amp; Upgrades
---

### Post by bohsocks on 2006-07-25
Ok so I have a bit of a loaded question:

First off... I installed Server... but I want a GUI with it, so I tried to put Desktop of top of that... and Server installed fine, but Desktop won't install from anywhere but when it is running off the CD in the desktop environment (won't install like a normal OS installer, from the BIOS).  And when it installs that way, it always gets bogged down at the Keyboard Layout part....

So I was wondering if this is because I have less than 192mb of RAM.  I am installing the normal version because I was going to upgrade RAM later...  If it isn't because of the RAM, what would cause this issue.... 

a) If it's the RAM, I'll just install the Alternate CD version... 
b) If not, I'll install Kubuntu.... which leads me to my next question:

Will Ubuntu Server installed + Kubuntu Desktop (Alternate) screw up my Server installation?

PS: I tried booting up Server and **sudo apt-get install ubuntu-desktop** and none of it ever worked... EVER... it either couldn't find the package, wouldn't upgrade, asked me if I was root, or did nothing.... what am I doing wrong?

As you can tell I'm a major **newbie**

Please help!

---

### Post by tseliot on 2006-07-25
> **bohsocks said:**
> Ok so I have a bit of a loaded question:

First off... I installed Server... but I want a GUI with it, so I tried to put Desktop of top of that... and Server installed fine, but Desktop won't install from anywhere but when it is running off the CD in the desktop environment (won't install like a normal OS installer, from the BIOS).  And when it installs that way, it always gets bogged down at the Keyboard Layout part....

So I was wondering if this is because I have less than 192mb of RAM.  I am installing the normal version because I was going to upgrade RAM later...  If it isn't because of the RAM, what would cause this issue.... 

a) If it's the RAM, I'll just install the Alternate CD version... 
b) If not, I'll install Kubuntu.... which leads me to my next question:

256 megabytes are the minimum requirement for Ubuntu or Kubuntu.

You should use Xubuntu instead.

Try with:
```
sudo apt-get install xubuntu-desktop
```

Before doing this **MAKE SURE YOU HAVE ALL THE REPOSITORIES ENABLED**

---

### Post by az on 2006-07-25
> **bohsocks said:**
> Ok so I have a bit of a loaded question:

First off... I installed Server... but I want a GUI with it, so I tried to put Desktop of top of that... and Server installed fine, but Desktop won't install from anywhere but when it is running off the CD in the desktop environment (won't install like a normal OS installer, from the BIOS).  And when it installs that way, it always gets bogged down at the Keyboard Layout part....!

You cannot install anything "on top" of an existing installation using the CD.  The CD will wipe out an existing install.  But that's not what you want to do.  You want to install the extra desktop packages from within your existing server install.


> **bohsocks said:**
> 
So I was wondering if this is because I have less than 192mb of RAM.  I am installing the normal version because I was going to upgrade RAM later...  If it isn't because of the RAM, what would cause this issue.... !

Both.

> **bohsocks said:**
> 
a) If it's the RAM, I'll just install the Alternate CD version... 
b) If not, I'll install Kubuntu.... which leads me to my next question:!

You can install kubuntu-desktop too.

> **bohsocks said:**
> 
Will Ubuntu Server installed + Kubuntu Desktop (Alternate) screw up my Server installation?!

No.  Not at all.

[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

> **bohsocks said:**
> 
PS: I tried booting up Server and **sudo apt-get install ubuntu-desktop** and none of it ever worked... EVER... it either couldn't find the package, wouldn't upgrade, asked me if I was root, or did nothing.... what am I doing wrong?!

You were not online, or you did not have the main package repository enabled as mentioned.

[https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

---

### Post by bohsocks on 2006-07-25
> You were not online, or you did not have the main package repository enabled as mentioned.

[https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)[/QUOTE]

Well sudo apt-get update worked, so I guess my internet connection had to be ok.

So when I use either Ubuntu or Kubuntu alternate, I want to forego the Server, boot off the CD, and use the install on the desktop?  And it will work this time because my CPU will meet the requirements, and won't (essentially) timeout in the Keyboard Layout step?

Awesome!

---

### Post by az on 2006-07-25
> **bohsocks said:**
> 

boot off the CD, and use the install on the desktop?  And it will work this time because my CPU will meet the requirements, and won't (essentially) timeout in the Keyboard Layout step?

Awesome![/QUOTE]

You won't get a desktop at all.  You will get a text-mode installer.  You have enough memory for it.

Once you reboot, you will be at the desktop.

---

