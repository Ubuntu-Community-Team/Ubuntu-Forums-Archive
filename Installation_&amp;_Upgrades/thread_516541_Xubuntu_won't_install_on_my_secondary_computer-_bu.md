---
title: "Xubuntu won't install on my secondary computer- but I JUST installed Ubuntu. whaa??"
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by Protagonistics on 2007-08-03
I'm playing around with my secondary compy. I installed Ubuntu FF. great. Then, as it is a slower puter than my main one, thought Xubuntu might be better suited for it. After going all the way up through the installation windows, I choose the complete install of Xubuntu over all other harddrive OS's. When I start the operation to install, I get this error message:

"Failed to create a file system."
"The ext3 file system creation in partition #1 of IDE2 master (hdc) failed."

But how can this be going awry unless my CD is bad? I JUST installed Ubuntu an hour before. My compy is fine. What do I do?

Thanks.

---

### Post by Protagonistics on 2007-08-03
Addendum:

How do I format the disk if I wanted to? I tried using GParted but I didn't have access or something to format the old girl.

---

### Post by forestpixie on 2007-08-03
you could just install Xubuntu and run that instaed of Ubuntu, change the session to Xubuntu

[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

---

### Post by Gremlinzzz on 2007-08-03
To do a complete cleaning of the hard drive use [http://dban.sourceforge.net/](http://dban.sourceforge.net/)
i download the cd version and burn the small image//iso file to a cd.the program gives a list of commands like quick or autonuke you'll see it.good program to have on hand.
as for using a linux system for older computer i would try [http://distrowatch.com/?newsid=04341](http://distrowatch.com/?newsid=04341)
just because of what i read i never used it.
:guitar:

---

### Post by ryangoff on 2007-09-11
I was getting the same errors. I already had Ubuntu 7.04 installed, found out my system couldn't really hack it (it's an old system), and then tried to install Xubuntu 7.04. I'd get 5% into disk partitioning (I was doing a full partition) and I'd get the "Xubuntu failed to create a file system" error message. I found a bug report that says basically "We're sorry. We couldn't fix it in time for the release. Here's the work around:"

  ```
Boot the desktop CD.
  Go to Applications -> Settings -> Settings Manager.
  Select "File Manager".
  Switch to the "Advanced" tab.
  Click on the "Configure" link ("Configure the management of removable drives and media ...").
  Uncheck "Mount removable drives when hot-plugged" and "Mount removable media when inserted".
  Close all the windows just opened, and start the installer.
```

Here's the full link: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107259]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107259")

Seems to be working...

---

