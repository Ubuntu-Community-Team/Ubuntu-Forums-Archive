---
title: "Problem installing Opera Web Browser"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by randell6564 on 2008-05-22
Thank You in advance!
I recently installed 7.10, and UNcommented all repo's in my /etc/apt/sources.list. After 225 updates, I am good to go. (So I thought!)

I just tried to install Opera Web Browser and got the following message:
> bigboss@bigboss-desktop:~$ sudo apt-get install opera
[sudo] password for bigboss:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  opera: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but it is not going to be installed
E: Broken packages
I first attempted to install Opera, and all dependencies via Synaptic with no luck.  Thats when I opened a terminal and did a 'sudo apt-get install opera, but again, to no avail.
Any ideas?  Thanks again!

---

### Post by tamoneya on 2008-05-22
do a check to make sure that there arent any other broken packages causing this problem```
sudo apt-get update
sudo apt-get check
```

---

### Post by randell6564 on 2008-05-22
> **tamoneya said:**
> do a check to make sure that there arent any other broken packages causing this problem```
sudo apt-get update
sudo apt-get check
```
Thanks for the quick reply my friend!
"sudo apt-get check" returned:
> bigboss@bigboss-desktop:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
I'm sure that you don't want to see the results of "sudo apt-get update" as it went just fine. ( Or do you?) :)

---

### Post by tamoneya on 2008-05-22
well i want you to run update but i dont need to see it unless it did something unusual but from what you are saying it seems to be fine.  Does it install opera now?  I personally use opera but i installed the beta version by means of a deb file:[http://www.opera.com/download/?ver=9.50b2](http://www.opera.com/download/?ver=9.50b2)

---

### Post by randell6564 on 2008-05-22
sudo apt-get update does just fine, (no error messages), but I still get the same output as posted earlier when doing 'sudo apt-get install opera'.

It refers to broken packages:> The following packages have unmet dependencies:
opera: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but it is not going to be installed
E: **Broken packages**How do I check for broken packages in this situation?

---

### Post by randell6564 on 2008-05-22
Just took another look at my /etc/apt/sources.list.  Is this normal, or does it have something to do with my problem?
> # Line commented out by installer because it failed to verify:
This text appears throughout the sources.list file.

---

### Post by tamoneya on 2008-05-22
the apt-get check was supposed to check for the broken packages.  Try the deb file from the link above.

---

### Post by randell6564 on 2008-05-22
It had something to do with the following repo's that I failed to UNcomment.
> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
       deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
because it worked after correcting this. Strange.,never had this problem in the past.  Thanks for the help my friend!

---

### Post by zvacet on 2008-05-23
If you decide to use Opera from repos you will need older flash.You can find it > **SEMW said:**
> If version 9.0.115 (the current version) gives you a grey square in Opera, try version 9.0.48.  I've uploaded it [here]("http://home.btconnect.com/geoffwoolf/files/libflashplayer.so.tar.gz") since it's too big for the forums, and the [official Adobe package]("http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=1") contains every version for all OSes and takes aaages to download.  Just untargz that file into /usr/lib/opera/plugins, restart Opera, and go to Tools -> Preferences -> Advanced -> Downloads -> select Flash -> Edit -> and select the one from /usr/lib/opera/plugins.

---

### Post by randell6564 on 2008-05-23
> **zvacet said:**
> If you decide to use Opera from repos you will need older flash.You can find it
Thanks!

---

