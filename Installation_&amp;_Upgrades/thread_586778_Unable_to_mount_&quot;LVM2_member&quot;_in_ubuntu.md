---
title: "Unable to mount &quot;LVM2_member&quot; in ubuntu"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by Swiftfeet8 on 2007-10-22
I have searched around on the forums here and haven't really found anything the ties directly to the issue I am having.  I will explain my predicament below.

I originally had a server at my house running Fedora (unsure of the version) that was used as an archives server for storing all of our pictures and information.  During the initial install of the system a few years ago I setup an LVM volume across two hard drives...something the ends up coming back to haunt me.  Over this past weekend I was going to experiment around with Mythbuntu.  I had forgotten that I had setup the LVM during the fedora upgrade, and I had assumed that I had two separately partitioned drives.  I went through the installation and installed Mythbuntu on my first drive, thinking that my archived files were on the second drive.  Once I started up Mybuntu I noticed that my second drive was recognized for some reason.  When I tried to mount the drive I got an error back stating "unable to mount drive of type LVM2_member".  I have searched online to see how I can mount this drive.  I took the drive out of the server to stop any potential changes from happening that could harm the data on the drive.  I removed Mythbuntu and installed ubuntu 6.10 on my server.  This brings me to my question.

I need to find a way to extract the data from my second drive that is an "LVM2_member"!  I have not tried much, because I wanted to get some advice first.  Any help is greatly appreciated!  Sorry if this post is long, but I need NEED to recover the data from that drive!  I realize that some of the data might be lost since the first drive was formatted, but I am hoping that some of the data is still on the second drive.  My primary drive was 20GB and my second drive is 200GB, and I had about 90GB of data being stored on the server.

Thank you for the help.

-Swiftfeet

---

### Post by asridhar on 2007-12-11
This link should solve you problem:

[http://www.linux-sxs.org/storage/fedora2ubuntu.html](http://www.linux-sxs.org/storage/fedora2ubuntu.html)

---

