---
title: "Ubuntu 12.04 installing openssh from source"
date: 2013-11-26
forum: Installation &amp; Upgrades
---

### Post by erotavlas on 2013-11-26
Hi,

I have a trouble on installing the latest version of openssh on ubuntu 12.04. I downloaded the latest version openssh-6.4 since that ubuntu 12.04 provides an old version 5.9.
I installed succesfully with classic command ./configure make make install. Now if I type ssh -V from command line, the system recognizes the correct version. But if I try to use some applications that use ssh they still call the old version. I tried to remove the packages of openssh-client and openssh-server, but in this case also other applications are affected as freenx.
So what should I do to use the latest version of openssh from all applications?
Thank you

---

### Post by Lars Noodén on 2013-11-26
You'll have to remove or replace the old packages.  If you can't remove them you can replace them

One option would be to compile the new OpenSSH as a package and then install that homemade package.  That would solve the dependency problems.

---

### Post by erotavlas on 2013-11-26
Ok, can you tell me how to do or a link where it is explained how to make a package from source.
Thank

---

### Post by Lars Noodén on 2013-11-26
Here is the short HowTo:

[http://tldp.org/HOWTO/html_single/Debian-Binary-Package-Building-HOWTO/](http://tldp.org/HOWTO/html_single/Debian-Binary-Package-Building-HOWTO/)

It's not that many steps, though there are details to follow.  Debian and Ubuntu use the same packaging system even if they use different repositories and binaries.

---

### Post by Lars Noodén on 2013-11-26
Here's another one, but it works with the deb-src package in the repository.  In the middle, you'll want to substitute your new source code for the old source code and then update the control file etc.

[http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/](http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/)

I'm not finding a good, simple list of how to do what you are trying to do.  I used to have notes, but they are too old.

---

### Post by erotavlas on 2013-11-26
What about this [https://help.ubuntu.com/community/CompilingEasyHowTo?](https://help.ubuntu.com/community/CompilingEasyHowTo?)

---

### Post by Lars Noodén on 2013-11-26
Yes that looks ok, if you are not going to build a full package.   Step 4 is the important one, with checkinstall, in that it gets the package listed in the package manager.

---

### Post by erotavlas on 2013-11-26
Hi,

I tried with success it is no difficult, but I have not solved the original problem. In fact I'm able to install the code by source or by new package, but if I remove openssh-server and openssh-client it does not work. Otherwise if I maintain them I still have the old version. How could I do?

---

### Post by ian-weisser on 2013-11-26
We're assuming here that your use of 12.04 is for a considered reason.

Is that a valid assumption? Some users make extra work for themselves by using LTS releases for purposes they are not intended for (like latest software). Users who want the latest versions of software may find it easier to use 13.10, which does include openssh 6.4 in the Ubuntu repositories.

The next LTS 14.04, will also include openssh 6.4...and will include it for five years.

---

### Post by erotavlas on 2013-11-26
Yes, your are right. I need a stable LTS version because I have server. I need to install at least the version 6.3 of openssh because it implements new features and because I would try a patch of a project that enhance the performance for networks with high BDP.
Do you have any suggestion about how I can do?
Thank

---

### Post by erotavlas on 2013-11-26
Yes, your are right. I need a stable LTS version because I have server. I  need to install at least the version 6.3 of openssh because it  implements new features and because I would try a patch of a project  that enhance the performance for networks with high BDP.
Do you have any suggestion about how I can do?
Thank

---

### Post by Lars Noodén on 2013-11-26
Another option I just remembered is apt-pinning:
 
[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)
[https://wiki.debian.org/AptPreferences](https://wiki.debian.org/AptPreferences)

Unfortunately it looks like 6.4 is only in Trusty:

[http://packages.ubuntu.com/search?keywords=openssh-server](http://packages.ubuntu.com/search?keywords=openssh-server)

So pinning is probably not an option if you want to avoid messing up your LTS machine.

---

### Post by ian-weisser on 2013-11-26
Wait...are you going to install openssh 6.4 to experiment with the new features on your PRODUCTION system? You're taking on a lot of risk that way...and I thought you to avoid risk?

Do you have a testing system? 
If you are going to experiment with the new features, you could install the pre-release version of 14.04 (with openssh 6.4) onto your testing system...or into a VM on one of your other systems. Then experiment all you like with the new features.

After you migrate your production server from 12.04 to 14.04 sometime next year, you can begin to implement what you learned from the testing system.

---

### Post by jdeca57 on 2013-11-26
> **ian-weisser said:**
> Wait...are you going to install openssh 6.4 to experiment with the new features on your PRODUCTION system? You're taking on a lot of risk that way...and I thought you to avoid risk?



But isn't 6.4 the latest stable release of ssh?
```

Changes since OpenSSH 6.3
=========================

This release fixes a security bug:

```

---

### Post by Lars Noodén on 2013-11-26
There's a difference between patching and upgrading.  

Upgrading, you go to a new version with possibly different functionality and maybe even different licensing.  Adding, removing, or changing functionality can break things and is undesireable in a production system.  Patching, on the other hand, fixes a specific problem and (ideally) introduces no additional changes beyond the one item being fixed.  

So it's possible to run 6.2, if it's patched.

---

### Post by Lars Noodén on 2013-11-26
I looked at apt-pinning on 12.04 and to get openssh 6.4 you have to go all the way up to trusty tahr:
[https://launchpad.net/ubuntu/+source/openssh](https://launchpad.net/ubuntu/+source/openssh)

Unfortunately that deb package depends on libc6 >= 2.17 and precise only has 2.15.  So you'd have to get into upgrading too many other pieces and things would break.  If possible, it would be best to wait the few extra months for trusty (14.04).

What feature in 6.4 was desired?  Maybe there is a work-around.

---

### Post by erotavlas on 2013-11-26
Ok, I'm interested about trying this project [http://www.psc.edu/index.php/hpn-ssh](http://www.psc.edu/index.php/hpn-ssh). I need to improve the speed of my connection. I can install version 6.3 or 6.2 of openssh.

---

### Post by ian-weisser on 2013-11-26
That looks like building from source.
If you're going to do that, you may as well build openssh from source, too.

---

### Post by erotavlas on 2013-11-27
Yes, it is exactly what I have done. I installed openssh version 6.4 or 6.3 or 6.2 from source with classic command ./configure make make  install. I learned also to make .deb package. Now if I type ssh -V from command line, the system recognizes  the correct version. But if I try to use some applications that use ssh  they still call the old version. I tried to remove the packages of  openssh-client and openssh-server, but in this case also other  applications are affected as freenx.
My problem is: how should I do to use the latest version of openssh from all applications?

---

### Post by Lars Noodén on 2013-11-27
The classic ./configure, make will give you two versions of openssh.  One is probably in /usr/local/bin, which is the first one in your $PATH.  The original one is in /usr/bin which is where other programs know to look for it.  checkinstall might: help with that.r

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

Though I'm not sure how it works to replace an existing package.  Nor am I sure if it is safe to just swap binaries in to /usr/bin and /usr/sbin by hand.

Making a package as suggested earlier above should avoid having two versions might be your last option.

About apt-pinning, I've tried apt-pinning with either binaries or source.  The source package 6.2 does not build on 12.04, due to dependencies nor will the binary for the server install for the same reason.  

You'll want to do all your building on another machine, not the production machine.  Building will clutter it with unnecessary packages, such as build tools, build dependencies and such.

---

### Post by erotavlas on 2013-12-01
Hi,
I replicated my system in a virtual machine and I installed openssh from source. After I copied the file in /usr/local/bin inside /usr/bin. Now all the executables related to ssh are updated to the latest version. The problem is not disappeared: in fact, if I try to remove the package openssh-server I cannot connect to the server using ssh. So it seems that ubuntu needs the openssh-server package, I don't know why. If I search files related to openssh-server I can find only these /etc/network/if-up.d/openssh-server, /etc/ufw/applications.d/openssh-server. Do you have any idea?
```

/usr/local/bin/ssh
/usr/local/bin/ssh-add
/usr/local/bin/ssh-agent
/usr/local/bin/ssh-keygen
/usr/local/bin/ssh-keyscan
/usr/local/bin/sshfs

```

---

### Post by Lars Noodén on 2013-12-01
That's part of why I suggested trying to build your own package, even if it is a lot of fiddle up front.  

Just compiling openssh on its own from the upstream source files won't set up the upstart script that is needed to get sshd going on Ubuntu upon start up and to keep it running should it stop.  If you've manually compiled, instead of making a package, you can manually set up the upstart scripts by copying the ones from the official package and putting them back after uninstalling the officially packaged version.  Or else if you're fine with manually starting sshd everytime you start the server, you can do that, too.  But I would recommend upstart.

/etc/init/ssh.conf should be the one

---

### Post by erotavlas on 2013-12-01
Ok, I tried with sudo checkinstall and it works but it install all under /usr/local/sbin and the package openssh-server is still necessary. With sudo checkinstall --install /usr/bin/ does not work.

---

