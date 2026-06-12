---
title: "Getting very frustrated with Bandwidthd"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by ayoalex on 2010-11-07
Ok, i am getting extremely annoyed by this, and i do not want to have to reinstall ubuntu to fix this because I feel as though this problem that I am having is getting fixed. I have tried to post this before on this forum but have only received minimal help, and when people do start helping me they just stop writing to me. 

Now that I am done ranting and venting i am now going to tell AGAIN, what my problem is.

Bandwidthd will not update. it refuses to. it says that i need to reinstall it but it won't let me. 
i have tried removing it but it says i need to reinstall it. can someone please help me i am very lost! thank you again.


When i try to update it this is what happens 

E: /var/cache/apt/archives/bandwidthd_2.0.1+cvs20090917-3_i386.deb: subprocess new pre-removal script returned error exit status 2

---

### Post by Cheesehead on 2010-11-07
Ok, the error message says that there is a syntax error in the pre-removal script.

Please attach the script to this thread so we can see it.

You should find it on your system at: /var/lib/dpkg/info/bandwidthd.prerm (or something close to that).

---

### Post by ayoalex on 2010-11-07
Thank you Cheeshead for answering me...

I checked in the info and found the .prerm file and this was what is inside of it. 


#!/bin/sh

set -e

if [ "$BANDWIDTHD_PACKAGE_DEBUG" != "" ]; then
    echo "bandwidthd.prerm: $*"
fi


if [ -x "/etc/init.d/bandwidthd" ]; then
    if [ -x /usr/sbin/invoke-rc.d ] ; then
        invoke-rc.d bandwidthd stop
    else
        /etc/init.d/bandwidthd stop
    fi
fi

---

### Post by Cheesehead on 2010-11-08
It's a bit of a hack, but one way to get past this is:

1) Make SURE bandwidthd is not running. You can check from the command line, or from System Monitor. It it's running, even sleeping, kill it.

2) In the .prerm script, on the empty line 2 add:
```
exit 0
```
(You must use sudo to open the file)
Save and try removing it again.


It's not the best way. But it will work.
The best way would be for you to run all those script commands manually, identify the failure, and then correct the failure if it's your fault or file a bug report if it's the package's fault.

---

