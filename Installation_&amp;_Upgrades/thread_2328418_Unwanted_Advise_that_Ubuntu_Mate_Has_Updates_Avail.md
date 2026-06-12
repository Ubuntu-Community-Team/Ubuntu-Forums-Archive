---
title: "Unwanted Advise that Ubuntu Mate Has Updates Available"
date: 2016-06-20
forum: Installation &amp; Upgrades
---

### Post by Plumtreed on 2016-06-20
I have Ubuntu 14.04 on my desktop but recently I downloaded Ubuntu-Mate for a trial. I used 'Startup Disk Creator' to load it on a USB drive....all went as it should! 

I now get update advice via "Update Notifier" advising that there are upgrades available, however, I don't need them because I have removed the USB drive and used it to install Ubuntu Mate on another machine.

What do I have to do to shut down these unwanted notifications?

---

### Post by vasa1 on 2016-06-21
Please post the output of ```
apt-cache policy ubuntu-mate-desktop
``` from the machine on which you're receiving these notifications.

I don't have ubuntu-mate-desktop installed and I see this (on 16.04):```
$ apt-cache policy ubuntu-mate-desktop
ubuntu-mate-desktop:
  Installed: (none)
  Candidate: 1.154
  Version table:
     1.154 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
$ 
```Could it be that you have inadvertently installed it on your system?

Also, please post the output of```
ls -l /usr/share/xesssions
```

And what exactly do you mean by > recently I downloaded Ubuntu-Mate for a trialCould you explain what you did there step-wise?

---

### Post by Plumtreed on 2016-06-21
Hi, I have no results to provide....I copied & pasted and tried as root,

apt-cache policy ubuntu-mate-desktop
N: Unable to locate package ubuntu-mate-desktop

ls: cannot access /usr/share/xesssions: No such file or directory

The process was very benign and without incident...download iso and converted to live usb via Start up Disk Creator.......I have no hint of any lingering Mate elements. I may have run the usb through on the Desktop to see if it worked??

I imagine something must be linking the repositories.

---

### Post by vasa1 on 2016-06-21
Don't run those commands as root! Just plain user.

---

### Post by deadflowr on 2016-06-21
xsessions, not xesssions.
```
ls /usr/share/xsessions
```

---

### Post by Plumtreed on 2016-06-21
Yes, I have done both!

Attachment enclosed

---

### Post by vasa1 on 2016-06-21
> **deadflowr said:**
> xsessions, not xesssions.
```
ls /usr/share/xsessions
```
Thanks for catching that!

---

### Post by Plumtreed on 2016-06-21
Sry, had to chop some firewood,

ls /usr/share/xsessions

total 12
-rw-r--r-- 1 root root 216 Mar 27  2015 gnome.desktop
-rw-r--r-- 1 root root 198 Dec 22  2013 openbox.desktop
-rw-r--r-- 1 root root 213 Mar 27  2015 ubuntu.desktop

...stil nothing showing

---

### Post by vasa1 on 2016-06-21
> **Plumtreed said:**
> ...

I now get update advice via "Update Notifier" advising that there are upgrades available, ...
The next time they appear, open a terminal, run ```
sudo apt-get update
``` and post that information here so people can see what's exactly being suggested.

---

### Post by Plumtreed on 2016-06-21
I ran sudo apt-get update when the update notification arrived....

The following is the result that refers to Ubuntu-MATE, the remainder, correctly refers to Ubuntu inclusions. 

[sudo] password for plumtreed: 
Ign cdrom://Ubuntu-MATE 16.04 LTS _Xenial Xerus_ - Release i386 (20160420.1) xenial InRelease
Ign cdrom://Ubuntu-MATE 16.04 LTS _Xenial Xerus_ - Release i386 (20160420.1) xenial/main Translation-en_AU
Ign cdrom://Ubuntu-MATE 16.04 LTS _Xenial Xerus_ - Release i386 (20160420.1) xenial/main Translation-en
Ign cdrom://Ubuntu-MATE 16.04 LTS _Xenial Xerus_ - Release i386 (20160420.1) xenial/multiverse Translation-en_AU
Ign cdrom://Ubuntu-MATE 16.04 LTS _Xenial Xerus_ - Release i386 (20160420.1) xenial/multiverse Translation-en
Ign cdrom://Ubuntu-MATE 16.04 LTS _Xenial Xerus_ - Release i386 (20160420.1) xenial/restricted Translation-en_AU
Ign cdrom://Ubuntu-MATE 16.04 LTS _Xenial Xerus_ - Release i386 (20160420.1) xenial/restricted Translation-en
Ign cdrom://Ubuntu-MATE 16.04 LTS _Xenial Xerus_ - Release i386 (20160420.1) xenial/universe Translation-en_AU
Ign cdrom://Ubuntu-MATE 16.04 LTS _Xenial Xerus_ - Release i386 (20160420.1) xenial/universe Translation-en

It seems that I need to remove reference to Xenial Xerus in my ubuntu box.

---

### Post by vasa1 on 2016-06-21
One more piece of information please! The output of **/etc/apt/sources.list**

---

### Post by Plumtreed on 2016-06-21
I get a file not found response......ditto   sudo  /etc/apt/sources.list

---

### Post by vasa1 on 2016-06-21
What about **ls -R /etc/apt**? No need for sudo!

---

### Post by howefield on 2016-06-21
> **Plumtreed said:**
> I get a file not found response......ditto   sudo  /etc/apt/sources.list

Open the file manager and navigate to /etc/apt/sources.list and open the file in a text editor, you should then be able to copy/paste back here.

---

### Post by Plumtreed on 2016-06-21
I could see the direction you were guiding me towards and used the sources list gui that is included in the updater......I could see that it included some reference to Ubuntu MATE so I 'deselected' that part and did an update. I also did a apt-get update in the terminal and it shows that it is clear of MATE reference. So, with your patience & help it may be sorted......I intend to give it time to see if it happens again.

I don't know why it occurred and haven't had that happen before.....I have created live USBs many times previously....thanks to all and especially Vasa1

---

