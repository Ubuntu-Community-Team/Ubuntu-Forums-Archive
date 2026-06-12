---
title: "install ubuntu from ubuntu"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by gcbzzzz on 2010-11-03
i just added a new storage disk, and i can still boot the old one with ubuntu 10.10.

 I want to install ubuntu on the new disk using the existing install.

Don't want to burn a CD or go hunt for a pen drive.


am i a lucky punk?

---

### Post by tommcd on 2010-11-04
> **gcbzzzz said:**
> i just added a new storage disk, and i can still boot the old one with ubuntu 10.10.
 I want to install ubuntu on the new disk using the existing install.
am i a lucky punk?
I believe the correct (*Dirty Harry*) quote is: "*Do you feel lucky, PUNK???*".
Anyway,
Since you can boot Ubuntu 10.10 from the "old" drive, and since the new drive is added for storage, why not just continue to use the existing Ubuntu 10.10 and just add the second hard drive to the existing Ubuntu install:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
Yo can use GParted to partition the hard drive. Then just make a mount point for the new drive, and add the new drive to /etc/fstab and you should be good to go.

If you want to copy your existing 10.10 install to the new hard drive, the easiest way I can think of is to use a **Clonezilla** live CD:
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by gcbzzzz on 2010-11-04
> **tommcd said:**
> I believe the correct (*Dirty Harry*) quote is: "*Do you feel lucky, PUNK???*".
Anyway,
Since you can boot Ubuntu 10.10 from the "old" drive, and since the new drive is added for storage, why not just continue to use the existing Ubuntu 10.10 and just add the second hard drive to the existing Ubuntu install:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
Yo can use GParted to partition the hard drive. Then just make a mount point for the new drive, and add the new drive to /etc/fstab and you should be good to go.

If you want to copy your existing 10.10 install to the new hard drive, the easiest way I can think of is to use a **Clonezilla** live CD:
[http://clonezilla.org/](http://clonezilla.org/)

It was a lame attempt to convert the phrase into a question :)


So, the main point is that the new drive is 3x faster. using the install on the actual drive would defeat the purpose.


What the install image has that the desktop image doesn't? can't i simply apt-get install ubuntu-installer?

...just need to know how the installer app is called and i can give it a try. i mean, don't need to be in a package, i can download the source and compile... i just really want to avoid burning a disc or go out for a pendrive...

---

### Post by linux18 on 2010-11-04
here is what your looking for:

[https://help.ubuntu.com/6.10/ubuntu/installation-guide/hppa/linux-upgrade.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/hppa/linux-upgrade.html)

it's how I fine-tune my ubuntu remixes, since you could even turn that into a live cd after your done

---

