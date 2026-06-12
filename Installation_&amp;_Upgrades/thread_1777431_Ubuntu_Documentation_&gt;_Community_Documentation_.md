---
title: "Ubuntu Documentation &gt; Community Documentation &gt; AptGetOfflineRepository"
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by mmaru on 2011-06-07
I would appreciate if someone can help me clarify the following which is contained in [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository).

1) "Now, you have to store the files in your local Ubuntu repository in the same order. For example:

    * In /home/repository/dists/karmic you would have the files: Contents-i386.gz , Release and Release.gpg
    * And in /home/repository/dists/karmic/main/binary-i386 the files: Packages.bz2 , Packages.gz and Release "

I am not sure whether I have to create the above two directories specific to the version of Ubuntu I am using e.g. /home/repository/dists/lucid

2) "Use Applications -> Add/Remove as explained in Repositories/Ubuntu to add the offline repository, stored in the /home/repository directory :

deb file:///home/repository SuiteCodename main restricted universe multiverse "

I could not find Applications -> Add/Remove on Lucid.

Regards

Maru

---

### Post by wildmanne39 on 2011-06-07
> **mmaru said:**
> I would appreciate if someone can help me clarify the following which is contained in [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository).

1) "Now, you have to store the files in your local Ubuntu repository in the same order. For example:

    * In /home/repository/dists/karmic you would have the files: Contents-i386.gz , Release and Release.gpg
    * And in /home/repository/dists/karmic/main/binary-i386 the files: Packages.bz2 , Packages.gz and Release "

I am not sure whether I have to create the above two directories specific to the version of Ubuntu I am using e.g. /home/repository/dists/lucid

2) "Use Applications -> Add/Remove as explained in Repositories/Ubuntu to add the offline repository, stored in the /home/repository directory :

deb file:///home/repository SuiteCodename main restricted universe multiverse "

I could not find Applications -> Add/Remove on Lucid.

Regards

MaruHi, you add and remove through synaptic package manager, I am not sure about the rest you are trying to do, are you trying to install apps with out a internet connection, if not just use synaptic to install and remove packages, you do not need to mess with coping files from one place to another.

---

### Post by mmaru on 2011-06-07
Thank you for your response. However, I was trying to get clarification on a community documentation. The document instructs you on how to use external repository. Please refer to the document which I have provided a link.

Regards,

Maru

---

### Post by wildmanne39 on 2011-06-07
> **mmaru said:**
> Thank you for your response. However, I was trying to get clarification on a community documentation. The document instructs you on how to use external repository. Please refer to the document which I have provided a link.

Regards,

MaruHi, again that said it is an offline repository, is that what you want, what program are you trying to install and from where? You can add ppa's to synaptic package manager, if you find one you want it should give the instructions how to add the ppa,and that only takes a minute to do and then you can install any software in that ppa which is a server with a particular software on it or could be many.

---

### Post by mmaru on 2011-06-08
Thank you again. Please see this documentation:

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

What does the following two instruction mean in the documentation:

1) Now, you have to store the files in your local Ubuntu repository in the same order. For example:

    * In /home/repository/dists/karmic you would have the files: Contents-i386.gz , Release and Release.gpg
    * And in /home/repository/dists/karmic/main/binary-i386 the files: Packages.bz2 , Packages.gz and Release "

2) Use Applications -> Add/Remove as explained in Repositories/Ubuntu to add the offline repository, stored in the /home/repository directory :

deb file:///home/repository SuiteCodename main restricted universe multiverse "

Regards,

Maru

---

### Post by wildmanne39 on 2011-06-08
> **mmaru said:**
> Thank you again. Please see this documentation:

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

What does the following two instruction mean in the documentation:

1) Now, you have to store the files in your local Ubuntu repository in the same order. For example:

    * In /home/repository/dists/karmic you would have the files: Contents-i386.gz , Release and Release.gpg
    * And in /home/repository/dists/karmic/main/binary-i386 the files: Packages.bz2 , Packages.gz and Release "

2) Use Applications -> Add/Remove as explained in Repositories/Ubuntu to add the offline repository, stored in the /home/repository directory :

deb file:///home/repository SuiteCodename main restricted universe multiverse "

Regards,

Maru
Hi, I am have never done what you are trying to do, so I hope someone else will answer your question, here is a guide for installing software hopefully it will help until someone comes to help. 
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

### Post by mmaru on 2011-06-08
Thank you. What I am trying to do is to use off-line repository. I will be going to an area where there is no Internet access.

Regards,

Maru

---

### Post by linuxinstalledfromhdd on 2011-06-08
You can create a backup system you can use to reinstall everything if you want, simply by creating a clone of your installed system, and then copying it to a disc for later, in case you need to reinstall it to a different system.  You won't need internet to install it again after you use a custom remastersys disc clone of your system.  It's like a resque disc that installs everything you want without internet.   Why would you want your own repositories when you can simply do that instead? 

Example:

[http://cinderbox.net/2011/06/02/creating-custom-ubuntu-live-usb-with-remastersys/](http://cinderbox.net/2011/06/02/creating-custom-ubuntu-live-usb-with-remastersys/)

As long as you stick with a 32-bit system, you can install it to most PC hardware.

---

### Post by wildmanne39 on 2011-06-09
> **mmaru said:**
> Thank you. What I am trying to do is to use off-line repository. I will be going to an area where there is no Internet access.

Regards,

Maru
Hi, I found this link with a program and instructions that is suppose to make what you are trying to do easy. I hope this helps.
[http://keryxproject.org/](http://keryxproject.org/)

---

