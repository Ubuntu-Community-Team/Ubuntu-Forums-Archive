---
title: "update ubuntu 7.04 to 7.10"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by sandipan on 2007-10-24
Hi 
    I am trying to update ubuntu 7.04 to 7.10 using cd. i downloaded the cd from ubuntu site and it's worked as live cd and i installed the same in other pc.  then i went to update the ubuntu into my pc, so i did
1. go to update manager and check is my ubuntu 7.04 is updated
it says no and gave some list of update to install.
2. i install all the update
3.restart the system
4. insrt the cd and it's auto mounted, but nothing happen, no package manager came to ask for update. ( this came when i first put the cd just for test)
5. i try from the terminal ( code i got from ubuntu site) nothing
so i went to package manager and try from source by manually check for update then it's says some missing dependency file
but when i try from update manager nothing is coming for update/install missing dependency.
here i do got the option   to upgrade 7.10 but i can't as i am using little slow internet connection.
can anyone help me how i can update it using cd.
thanks
sandipan

---

### Post by logos34 on 2007-10-24
need to use the Alternate desktop cd.

[https://help.ubuntu.com/community/GutsyUpgrades#head-93ac2e597b9e0c5ff78111d4fd2bbe34a35799c7](https://help.ubuntu.com/community/GutsyUpgrades#head-93ac2e597b9e0c5ff78111d4fd2bbe34a35799c7)

---

### Post by sandipan on 2007-10-25
Hi 
THanks, But i already try that one and it's not worked. nothing happen
any other option we have?
:(

---

### Post by jenhsun on 2007-10-25
> **sandipan said:**
> Hi 
THanks, But i already try that one and it's not worked. nothing happen
any other option we have?
:(

sandipan
I don't recommend you upgrade to 7.10 now because of your internet condition. Currently the 7.10 got lots of complain about the performance issue. I hope you can wait a little bit a month, then download the improved iso.

---

### Post by PointyWombat on 2007-10-25
if you already downloaded the CD; System -> Administration -> Synaptic -> Settings ->Repositories, there's something there which I believe will allow you to use your CD as the upgrade source.

Good Luck.

---

### Post by emmerc on 2007-10-25
Hello jenhsun I did an upgrade without any trouble following this procedure: everything is working perfectly: I hope it might be useful for you.
   1. Open a terminal window and run the following command:  sudo nano /var/lib/update-manager/meta-release 
   2.  Scroll to the bottom of the file and add the following to the end:

Dist: gutsy
Name: Gutsy Gibbon
Version: 7.10
Date: Thu, 18 Oct 2007 12:00:00 UTC
Supported: 0
Description: This is the 7.10 release
Release-File: [http://archive.ubuntu.com/ubuntu/dists/gutsy/Release](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release)
ReleaseNotes: [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/ReleaseAnnouncement](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/ReleaseAnnouncement)
UpgradeTool: [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz)
UpgradeToolSignature: [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz.gpg)

   1.     Press Ctrl + O
   2.       This will prompt you to write out the file. Press the Enter key
   3.       Press Ctrl + X to exit nano
   4.       Issue the following two commands:

sudo apt-get update
gksudo "update-manager -c -d"

This should bring the Update Manager back up, allowing you to Upgrade to Gusty.

---

### Post by jenhsun on 2007-10-25
> **emmerc said:**
> Hello jenhsun I did an upgrade without any trouble following this procedure: everything is working perfectly: I hope it might be useful for you.
   1. Open a terminal window and run the following command:  sudo nano /var/lib/update-manager/meta-release 
   2.  Scroll to the bottom of the file and add the following to the end:

Dist: gutsy
Name: Gutsy Gibbon
Version: 7.10
Date: Thu, 18 Oct 2007 12:00:00 UTC
Supported: 0
Description: This is the 7.10 release
Release-File: [http://archive.ubuntu.com/ubuntu/dists/gutsy/Release](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release)
ReleaseNotes: [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/ReleaseAnnouncement](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/ReleaseAnnouncement)
UpgradeTool: [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz)
UpgradeToolSignature: [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz.gpg)

   1.     Press Ctrl + O
   2.       This will prompt you to write out the file. Press the Enter key
   3.       Press Ctrl + X to exit nano
   4.       Issue the following two commands:

sudo apt-get update
gksudo "update-manager -c -d"

This should bring the Update Manager back up, allowing you to Upgrade to Gusty.

Thanks emmerc. i just try to answer the other guys problem based on his/her own slow internet connection to acquire the Gutsy version.

---

### Post by sandipan on 2007-10-25
Hi jenhsun /emmerc  
Thanks a lot. 
Emmerc I will try to update through your process. But I am thinking Jenhsun told that 7.10 have lots of issue. i checked in net it's look like true.
What you both suggest. I am upgrading because it's look good and othe new feature.
But in 7.04 what i have right now, all of my stuff work there - sound card, usb modem, tv, movie etc.
So i am little confused about upgrade!
Thaks
SAndipan

---

### Post by jenhsun on 2007-10-25
> **sandipan said:**
> Hi jenhsun /emmerc  
Thanks a lot. 
Emmerc I will try to update through your process. But I am thinking Jenhsun told that 7.10 have lots of issue. i checked in net it's look like true.
What you both suggest. I am upgrading because it's look good and othe new feature.
But in 7.04 what i have right now, all of my stuff work there - sound card, usb modem, tv, movie etc.
So i am little confused about upgrade!
Thaks
SAndipan

Wait and be patient. The new features in 7.10 aren't attract me at all.
By the way, save some frustrated time on solving some 7.10 new-bug finding instead of go out and have fun with your friends might be much better.

---

### Post by emmerc on 2007-11-03
Sorry you are having troubles with 7.10. 

Really I upgraded my box from 7.04 to 7.10 and is working wonderfully. But you are right I had a LAN broadband to do the whole thing. Previously I had tried downloading the ISO and it had problems so it did not work. I really hope Ubuntu might fix these details soon. I had never before heard about this kind of issues. I downloaded 5.10, 6.10 and 7.04 in their times and all of them worked very well. Anyhow all the best.

---

