---
title: "Which download version?"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by cthulhuxxx on 2010-01-31
I need to know which Ubuntu to download for a 64bit machine, and will also be able to recognise the RAID 0 setup as 1 drive instead of 2.

I will use partitioning software to resize the RAID 0 partition. Once I do, I need Ubuntu to see it as a single drive.

Could someone link me to the correct one, please.

Appreciated,
Thanks

---

### Post by x33a on 2010-01-31
download the latest stable ubuntu (karmic koala/9.10) 64-bit from here:

[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

as for raid, search the forums, and also take a look here:

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by yogesh.girikumar on 2010-02-02
Hi,

You can download the 64Bit ISO files from the ubuntu repository or from any one of its mirrors. Here is the official download site.


       [http://releases.ubuntu.com]("http://releases.ubuntu.com/")
[URL="http://releases.ubuntu.com/"]
[/URL]
       Select the version you want to install and download the 64Bit version. You can configure RAID during installation if you're using a server edition. Alternatively, you can also install Ubuntu without any RAID configuration and later use the 'mdadm' command to configure RAID as you desire.
   ```
man mdadm
```      You might have to install mdadm as it is not installed by default. Be sure to do a package repo update.
   ```
$ sudo apt-get update && apt-get install mdadm
```      HTH,
Yogesh.

---

