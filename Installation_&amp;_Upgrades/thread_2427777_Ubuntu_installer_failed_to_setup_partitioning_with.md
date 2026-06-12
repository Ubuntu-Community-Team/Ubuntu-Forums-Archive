---
title: "Ubuntu installer failed to setup partitioning with encrypted volumes"
date: 2019-09-26
forum: Installation &amp; Upgrades
---

### Post by mathieu-tarral on 2019-09-26
Hi,

I attempted to install Ubuntu 19.04 today, but it failed several times, at different stages:

First I had the **"An unsafe swap space has been detected"** issue, I had to manually remove the swap partition, otherwise the installer would complain.
Apparently this is a bug from **2013**, still not fixed today (!!!!)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1205397](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1205397)

The I had an config error, **"Configuration of encrypted volumes failed"** I rebooted to get a clean state and started the installer again.

Then I'm now blocked at **"The attempt to mount a file system ..."** which prevents me from finally installing Ubuntu.

see the attachments.

The installer seems like it is **full of bugs** when dealing with encrypted volumes !

Can you help me install Ubuntu with encrypted volume please ? (and how to report these bugs so they can actually get fixed)

Thanks

---

### Post by deadflowr on 2019-09-26
See: [https://ubuntuforums.org/showthread.php?t=2399092]("https://ubuntuforums.org/showthread.php?t=2399092")

---

### Post by Skaperen on 2019-09-26
do you have any data on that computer that you need to keep?  if yes, did you make a backup of it?

---

### Post by mathieu-tarral on 2019-09-26
Hi,

thanks for your replies.

About the Full Disk Encryption guide.
I notice 2 issues while following the guide:
- I have to download a user made script, from a Dropbox, as sudo
- it requires to use an internet connection, which I don't necessarly have 

"**You must be connected to the internet.** This installation will fail if you are not. 
Fill in the prompts as follows."

Basically I would like to put my trust in Ubuntu's official installer, and fix bugs upstreams if possible.



Yes, I made a backup of my home's data, fortunately.

I have more information about the last error I have, "**The attempt to mount ...**"

I took a look at **journalctl**, and this is what I got:


[IMG]https://i.ibb.co/pdXtfdY/mount-failed.png[/IMG]

---

