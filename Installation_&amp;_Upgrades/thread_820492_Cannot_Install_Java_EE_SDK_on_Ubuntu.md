---
title: "Cannot Install Java EE SDK on Ubuntu"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by I3ritnay on 2008-06-06
Hi,

I have an Ubuntu linux machine, and am trying to install the Java EE SDK.  I don't have gnome on this machine, so to get the SDK on there I used two methods: ftp and flash drive.

I put the bin file (from the download) in the usr/local folder just because.  In that directory, I tried the following ways to run/execute the bin file:

(Before hand, I chomod +x the file)

1) ./path/to/java/ee/sdk

Error: Unable to execute ./path/to/java/ee/sdk: No such file or directory
(makes no sense because I can ls in that directory and I see the bin file)

2) sh ./path/to/java/ee/sdk

Error: Syntax error: "(" unexpected

3) /path/to/java/ee/sdk
(just typing filename)

Error: Command not found

4) /usr/local/path/to/java/ee/sdk

Error: Command not found

------

I tried many other things, that I can't remember or list.  I cannot apt-get install the file because the java_ee_sdk is not in the repository.  Maybe there is a way to add it or find a source?  So, I had to get it off java.sun.com on another computer.  I've tried this on two different machines, with two different versions of Ubuntu Linux, and received the same error, so I am not really sure what is going on here.

---

### Post by I3ritnay on 2008-06-06
Sorry,

I meant chmod and the 2nd command should be:

2) sh path/to/java/ee/sdk

Thanks.

---

### Post by jamesstansell on 2008-06-08
Hi,

A lot of the parts of the SDK are available in the ubuntu repositories, but it's good for a developer to be able to make use of the packaging and installation instructions from Sun too.

You say that you did a chmod +x on the file, but I don't see that you ever mentioned the filename.  Sun mostly names their files either .bin or .sh.

[http://java.sun.com/javaee/downloads/index.jsp](http://java.sun.com/javaee/downloads/index.jsp) lists a bunch of different downloads.  The one I'll look at is the plain one that showed on this page when I clicked the download button:

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=java_ee_sdk-5_05-nojdk-oth-JPR@CDS-CDS_Developer](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=java_ee_sdk-5_05-nojdk-oth-JPR@CDS-CDS_Developer)

The downloade filename for this is java_ee_sdk-5_05-linux-nojdk.bin but it's curious that I'm not seeing any installation instructions on Sun's JavaEE pages.

I would try creating a new directory to install the SDK to, putting the file in it and then running these commands:
```
$ cd /path/to/directory
$ /bin/sh ./java_ee_sdk-5_05-linux-nojdk.bin
```

You will likely need to have Java already installed first.  If you have one of the other downloads you should substitue the name of the file above.

---

### Post by Quique67 on 2009-05-28
I have a similar problem.

I receive the following error

root@enrique-desktop:~# ./java_ee_sdk-5_07-linux-ml.bin
./java_ee_sdk-5_07-linux-ml.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
root@enrique-desktop:~# 

What is this error?

---

### Post by eugen_nicoara on 2009-11-09
Hi,

This one worked for me:
```

cd /usr/lib
ln -s libstdc++.so.6.0.8 libstdc++.so.5

```
[http://forums.sun.com/thread.jspa?forumID=136&threadID=5295337]("http://forums.sun.com/thread.jspa?forumID=136&threadID=5295337")

Cheers!

---

