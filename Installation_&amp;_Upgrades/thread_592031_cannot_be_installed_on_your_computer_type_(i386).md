---
title: "cannot be installed on your computer type (i386)"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by ldisplay on 2007-10-26
just installed 7.10 on my compaq. got my wireless card to work still have to get my ati radeon express 200m graphic card to work.

the problem is when I click on the add/remove programs I get a message  

(application) cannot be installed on your computer type (i386)
Either the application requires special hardware features or the vendor decided to not support your computer type.

---

### Post by taurus on 2007-10-26
Close that Add/Remove window.  Then, post the outputs of these two commands from a terminal.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ldisplay on 2007-10-26
nope still nothing

I have the amd 64 3500+ but I think I installed the 32 bit version of 7.10

---

### Post by taurus on 2007-10-26
You can install x86 on a x86_64 machine.  However, you cannot install or run any 64bit apps on it.  You can only install x86 stuff.

Are you trying to install 64bit stuff on that now?

---

### Post by ldisplay on 2007-10-26
i don't think so I click on applications on the top screen and then add/remove programs

---

### Post by xfred on 2007-10-26
Not sure if this helps, but I just had the same problem and found a solution that worked in my case.  For some reason some of the sources in /etc/apt/sources.list were commented out with a note about them being commented out during setup due to "failure to verify" or somesuch.  I uncommented the ones that had been commented out with the above note, restarted add/remove and everything seems to be working fine again.

Hope that helps.

---

### Post by xakira on 2007-10-27
I had the same problem when using 7.10 and fixed it by clicking on the "Preferences" button in the lower left of the "Add/Remove Applications" window and enabling all the "Downloadable from the Internet" sources.

---

### Post by yarrowfell on 2007-10-27
> **xakira said:**
> I had the same problem when using 7.10 and fixed it by clicking on the "Preferences" button in the lower left of the "Add/Remove Applications" window and enabling all the "Downloadable from the Internet" sources.
I had been struggling wih this as well and xakira's solution worked just fine. Thanks!

---

### Post by God_Bless on 2007-11-11
I had the same problem with amd64 message. xakira answer worked for me also. Thanks for the help xakira and thanks for the thread ldisplay.

---

### Post by chatterjee on 2007-11-13
Thanks Xakira your answer solved my problem!

---

### Post by komputes on 2007-12-07
> **ldisplay said:**
> 
(application) cannot be installed on your computer type (i386)


I got this error many times on 7.10 and this is what I did to resolve the issue.

Open a terminal and do the following, one line at a time.

```
sudo apt-get clean
```
```
sudo gedit /etc/apt/sources.list
```

Erase the content of sources.list and paste this in:

```
# Ubuntu supported packages
deb http://us.archive.ubuntu.com/ubuntu gutsy main restricted 
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted

# Ubuntu community supported packages
deb http://us.archive.ubuntu.com/ubuntu gutsy universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security universe multiverse
```

If you are not in the US and you want a local sources.list there is a generator here:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

Then simply do

```
sudo apt-get update
```
```
sudo apt-get upgrade -y
```

Reboot and try downloading the program again.

Please let me know if this works for you.

UPDATE 2007-12-13: I was able to reproduce this, and my post (above) did not work. Had this issue when adding VMware, I believe this is an issue specific to the VMware currently in the repositories, causing the error "VMware Player cannot be installed on your computer type (i386)". Will contact VMware and the repo admins about this. Workaround: Installing VMware from source (compiling it yourself) works for now.

UPDATE 2007-12-26: It seems that the VMware package in the repositories is broken and will give this error. Until an update is released, you will have to compile the VMware player from source.

---

### Post by sboots on 2008-01-05
Seems to occur (still in 7.10) if your computer isn't connected to the net when installing ubuntu (xfred mentioned the 'cannot contact security servers' that results in commenting out the sources when installing.)   Thanks, Xakira and xfred for your instructions!

So, I guess I'll make sure my computer is plugged in to the net before I install next time!  The "cannot be installed on your computer type" error message is a bit misleading, I'd say.

---

### Post by RobbMeex on 2008-01-06
Pretty sure you solved mine as well! :)

---

### Post by ashishgoel on 2008-02-17
@komputes.... u're solution worked...

---

### Post by Pumalite on 2008-02-17
> **komputes said:**
> I got this error many times on 7.10 and this is what I did to resolve the issue.

Open a terminal and do the following, one line at a time.

```
sudo apt-get clean
```
```
sudo gedit /etc/apt/sources.list
```

Erase the content of sources.list and paste this in:

```
# Ubuntu supported packages
deb http://us.archive.ubuntu.com/ubuntu gutsy main restricted 
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted

# Ubuntu community supported packages
deb http://us.archive.ubuntu.com/ubuntu gutsy universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security universe multiverse
```

If you are not in the US and you want a local sources.list there is a generator here:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

Then simply do

```
sudo apt-get update
```
```
sudo apt-get upgrade -y
```

Reboot and try downloading the program again.

Please let me know if this works for you.

UPDATE 2007-12-13: I was able to reproduce this, and my post (above) did not work. Had this issue when adding VMware, I believe this is an issue specific to the VMware currently in the repositories, causing the error "VMware Player cannot be installed on your computer type (i386)". Will contact VMware and the repo admins about this. Workaround: Installing VMware from source (compiling it yourself) works for now.

UPDATE 2007-12-26: It seems that the VMware package in the repositories is broken and will give this error. Until an update is released, you will have to compile the VMware player from source.

Check your generator link.

---

