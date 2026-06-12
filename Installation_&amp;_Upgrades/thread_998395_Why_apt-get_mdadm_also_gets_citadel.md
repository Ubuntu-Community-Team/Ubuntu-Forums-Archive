---
title: "Why apt-get mdadm also gets citadel??"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by celem on 2008-11-30
If I do an apt-get install mdadm citadel is also loaded, which I then have to remove. Why is citadel loaded?? I suspect some sort of error worthy of a bug report.

---

### Post by jpkotta on 2008-12-01
It is definately not a bug.  mdadm recommends an mta.
> $ aptitude show mdadm
Package: mdadm
State: installed
Automatically installed: no
Version: 2.6.7-3ubuntu8
Priority: optional
Section: admin
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 655k
Depends: libc6 (>= 2.8~20080505), debconf (>= 1.4.72), lsb-base (>= 3.1-6), udev (>= 113-0ubuntu1), initramfs-tools (>=
         0.85eubuntu24)
Recommends: **mail-transport-agent**, module-init-tools
Conflicts: mdctl (< 0.7.2), raidtools2 (< 1.00.3-12.1)
Replaces: mdctl
Description: tool to administer Linux MD arrays (software RAID)
 The mdadm utility can be used to create, manage, and monitor MD (multi-disk) arrays for software RAID or multipath I/O.
 
 This package automatically configures mdadm to assemble arrays during the system startup process. If not needed, this
 functionality can be disabled.
Homepage: [http://neil.brown.name/blog/mdadm](http://neil.brown.name/blog/mdadm)

citadel is apparently the default mta.  The reason it recommends an mta is that it mails you when the array fails.  You can disable installation of recommends by adding > APT::Install-Recommends "false"; to ~/.aptitude/config or using the -R option.  

I don't use apt-get, but there is a way to disable recommends there too.

---

### Post by celem on 2008-12-01
You are most probably right as /etc/mdadm/mdadm.conf does have a MAILADDR parameter that is defaulted to root. In my opinion, defaulting to load citadel is rather lame and quite an assumption. Thanks

---

### Post by russofris on 2008-12-06
> **celem said:**
> You are most probably right as /etc/mdadm/mdadm.conf does have a MAILADDR parameter that is defaulted to root. In my opinion, defaulting to load citadel is rather lame and quite an assumption. Thanks

I have to agree.  While citadel may be an MTA, it's also a full groupware solution.  What MTA would you feel is more appropriate?  Postfix/Sendmail, or something tiny/easy?

Frank

---

### Post by celem on 2008-12-06
I don't think that any email program should be automatically loaded with mdadm. Any Linux distribution would have some form of email, such as sendmail, already installed, and it is, in my opinion, inappropriate for a mdadm install to install another email program.

---

### Post by russofris on 2008-12-06
> **celem said:**
> I don't think that any email program should be automatically loaded with mdadm. Any Linux distribution would have some form of email, such as sendmail, already installed, and it is, in my opinion, inappropriate for a mdadm install to install another email program.

If the distro does not have a default MTA installed, do you feel that the default action should be to install Sendmail, or simply forgo the installation of an MTA?

Frank

---

### Post by celem on 2008-12-06
While email notification of a failed RAID is useful, it is not a dependency for operation. Consequentially, I would prefer mail to only be the configuration option in mdadm.conf and load nothing but what was requested - the mdadm package. The usefulness of configuring an email capability can be in a readme.

---

### Post by orzechowskid on 2008-12-26
> **celem said:**
> While email notification of a failed RAID is useful, it is not a dependency for operation. Consequentially, I would prefer mail to only be the configuration option in mdadm.conf and load nothing but what was requested - the mdadm package. The usefulness of configuring an email capability can be in a readme.

You're right when you say citadel (or any other MTA) isn't a requirement for mdadm; that's why it's under "Recommends" and not "Depends".  If you don't want recommended packages to be installed by default, jpkotta gave you the information you need at the bottom of his post.

---

