---
title: "[SOLVED] Internet filter blocking 'sexy' updates"
date: 2008-10-13
forum: Installation &amp; Upgrades
---

### Post by kuitems on 2008-10-13
I am trying to install the last of 1200+ upgrades to an older version of Ubuntu using update manager. The computer was installed with Ubuntu 6.06 from a live CD and the updated accordingly using the update manager. All was going well except for this last step. Error message reads:

Could not download the upgrades

The upgrade aborts now. Please check your Internet connection or installation media and try again.

[http://ua.archive.ubuntu.com/ubuntu/pool/main/libs/libsexy/libsexy2_0.1.11-2_i386.deb](http://ua.archive.ubuntu.com/ubuntu/pool/main/libs/libsexy/libsexy2_0.1.11-2_i386.deb)
[http://ua.archive.ubuntu.com/ubuntu/pool/main/s/sexy-python/python-sexy_0.1.9-1ubuntu1_i386.deb](http://ua.archive.ubuntu.com/ubuntu/pool/main/s/sexy-python/python-sexy_0.1.9-1ubuntu1_i386.deb)

I posted a help request on Friday but got no response. Searching for the files causes my school's internet filter to block results.](*,)  The same filter is probably blocking the update manager from getting these updates. I don't have permission to turn off the filter, so please help me with a workaround.

---

### Post by Elfy on 2008-10-13
If you can get to another machine - download the files from here

[http://packages.ubuntu.com/hardy/python-sexy](http://packages.ubuntu.com/hardy/python-sexy)
[http://packages.ubuntu.com/hardy/libsexy2](http://packages.ubuntu.com/hardy/libsexy2)

Then copy them to your apt cache and update apt-get, then when it tries to do the update the files will be there and it won't need to get them.

I assumed you were updating to hardy 8.04 as libsexy isn't available from packages for dapper

---

### Post by kuitems on 2008-10-13
Thanks for the advice. I'm working overseas as a volunteer and finding a different Internet connection means travel to a neighboring town.  Can someone host these two packages somewhere in a place that doesn't contain 'sexy' in the html code.  I could probably download a zip file or a torrent if they were packaged that way.

I'm not sure if these packages are important for the update, but I could imagine other people getting stuck at this step.

---

### Post by Fredzz on 2008-10-13
Because its just an easy request to download those 2 files, zip them and upload them, here is the link for the 2 requested files: [http://rapidshare.com/files/153647620/lib_python-seyy.rar]("http://rapidshare.com/files/153647620/lib_python-seyy.rar")

Greetings,

Fred

---

### Post by Elfy on 2008-10-13
Once you have the file unzipped - copy them to /var/cache/apt/archives with ```
gksudo nautilus
```

Do an update ```
sudo apt-get update
``` and you should be good to go for the upgrade.

---

### Post by kuitems on 2008-10-14
Success!  The update found those files after I downloaded them and placed them in the folder described.  Thanks Fredzz and forestpixie for the help and advice.

Problem solved.

---

### Post by Elfy on 2008-10-14
welcome - I think there was someone else a while back with the same problem - maybe the name should change lol

---

