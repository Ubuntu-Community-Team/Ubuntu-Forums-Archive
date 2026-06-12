---
title: "Update Not Working - Error Authenticating Some Packages"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by flackboy on 2008-09-11
I've been having a problem with the update manager for the last couple of weeks and have been trying to fix things myself, but keep running out of ideas.  I was hoping I could find some help here...

My update manager keeps telling me I have multiple updates available, yet when I run it, it tells me that NOT ALL UPDATES CAN BE INSTALLED and that a Partial Upgrade is all I can do.

Choosing that options starts the manager and it 'prepares to upgrade' but then tells me there were errors authenticating the following packages:

initscripts
libavc1394-0
sysv-rc
sysinit-utils

I suspect I need a key for one of the software sources, but I'm sort of out of my depth at this point.

Can anyone give me any pointers?

Many thanks,

Brian...

---

### Post by flackboy on 2008-09-11
Update: The error message from trying an apt-get update is: 


W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277

If that's any help...

---

### Post by tcarlin on 2008-09-24
I am very new to linux, but i had a similar problem.  if you to system on the top bar and then go to systym administration then to the Software Sources then to the tab that says third party software there should be one line there that says [http://ftp.debian.org](http://ftp.debian.org) etch release.  uncheck that box and i think it will take care of your problem.  it took care of mine.

---

### Post by chrisdee on 2009-07-31
Hey. This worked for me to.
Thanx.

---

### Post by bhodi tree on 2009-07-31
I am having a similar problem, but receive this error message each time I try to update or add software:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Any ideas on why and what I need to do.  I do not know how to run it manually.

thank you in advance.

---

### Post by drs305 on 2009-07-31
> **bhodi tree said:**
> I am having a similar problem, but receive this error message each time I try to update or add software:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Any ideas on why and what I need to do.  I do not know how to run it manually.

thank you in advance.

Open a terminal with ALT-F2.

```
sudo dpkg --configure -a
```

Tick "Run in terminal" , then "Run". It will open a regular terminal window. when you type your password you won't see anything. That's a security feature. Just type in your password and ENTER.

Added: You can also open a terminal via the Applications, Accessories, Terminal.

---

### Post by sauravd07 on 2011-05-21
login from root...goto the folder where list of all packages are stored.Delete all the files ,restart and try updating again,most probably your problem will be fixed!!

---

