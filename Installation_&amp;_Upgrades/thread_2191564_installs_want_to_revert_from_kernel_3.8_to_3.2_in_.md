---
title: "installs want to revert from kernel 3.8 to 3.2 in 12.04.3 LTS"
date: 2013-12-03
forum: Installation &amp; Upgrades
---

### Post by keller.ee on 2013-12-03
I recently installed 12.04.3 AMD 64 on my system after having some issues with the previous install caused by careless use of apt-get remove.  I don't recall the version I installed on top of, it was 12.04.x  Since the problems I was having with the previous install weren't stopping the system from booting, I didn't format the partitions I am using.  So random things are left over from the previous install.  Apparently, one of those things is the updated kernel, 

uname -a reports: Linux eric-desktop 3.8.0-34-generic #49~precise1-Ubuntu SMP Wed Nov 13 18:05:00 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Today, I got the first notification of updates, it wanted to install kernel 3.2 generic. Is the update manager actually going to catch up to my system?  Does this really make sense in this context?

---

### Post by philinux on 2013-12-03
Post back the output of this.

```
apt-cache policy linux-generic
```

---

### Post by keller.ee on 2013-12-03
here:
> 
eric@eric-desktop:~$ sudo apt-cache policy linux-generic
linux-generic:
  Installed: (none)
  Candidate: 3.2.0.57.68
  Version table:
     3.2.0.57.68 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main amd64 Packages
     3.2.0.23.25 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main amd64 Packages



---

### Post by philinux on 2013-12-03
That package always points to the latest kernel. So.

```
sudo apt-get install linux-generic
```

then

```
sudo apt-get update ; sudo apt-get dist-upgrade
```

You'll then be able to use update manager from then on.

---

### Post by ian-weisser on 2013-12-03
> **keller.ee said:**
> Is the update manager actually going to catch up to my system?  Does this really make sense in this context?

The answer to your first question is "probably not"
You seem to be wondering if your 3.2x kernel (12.04) will someday automatically update back to a 3.8x kernel (13.04).
No.  It won't. Your system will stick with the older kernel because you told  it so by installing the older repositories in /etc/apt/sources* when you installed the older release.
You can update to a newer release anytime you wish...or not, of course. 12.04 will be supported until Spring 2017.

The answer to your second question is "yes"

---

### Post by keller.ee on 2013-12-03
I actually went forward from 12.04.x where something less than 3 to 12.04.3  The 3.8 kernel I'm using was installed on a 12.04.x system by automatic updates.  A quick search didn't tell me what kernel version I should expect to see on my system.

---

