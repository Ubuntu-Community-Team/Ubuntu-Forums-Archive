---
title: "Why is Aptitude holding some packages at current version?"
date: 2013-10-14
forum: Installation &amp; Upgrades
---

### Post by spookybathtub on 2013-10-14
In the past, I've always updated my system using the GUI or with "sudo aptitude safe-upgrade".  Recently I discovered the interactive CLI mode of aptitude, and started playing with it.  I notice that a few packages have the status "held at current version.  Can anyone shed some light as to why these packages are being held?  I never chose that intentionally.  Maybe I did it by mistake.  These are the packages:
[FONT=courier new]
[/FONT][TABLE="width: 300"]
[TR]
[TD][FONT=courier new]apparmor[/FONT][/TD]
[TD][FONT=courier new]2.7.102-0ubunt[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=courier new]apt[/FONT][/TD]
[TD][FONT=courier new]0.8.16~exp12ub[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=courier new]apt-transport-https[/FONT][/TD]
[TD][FONT=courier new]0.8.16~exp12ub[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=courier new]apt-utils[/FONT][/TD]
[TD][FONT=courier new]0.8.16~exp12ub[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=courier new]libapt-inst1.4[/FONT][/TD]
[TD][FONT=courier new]0.8.16~exp12ub[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=courier new]libapt-pkg4.12[/FONT][/TD]
[TD][FONT=courier new]0.8.16~exp12ub[/FONT][/TD]
[/TR]
[/TABLE]
[FONT=courier new]
[/FONT]

---

### Post by sudodus on 2013-10-15
I usually update/upgrade with apt-get, which is similar to aptitude. Sometimes I let the auto-started GUI interface do the job.

Read the detailed description in ```
man apt-get
``` and ```
man aptitude
```

```
sudo apt-get update
sudo apt-get upgrade         # install most packages
sudo apt-get dist-upgrade    # try to install packages held back by upgrade
```

Try this and report back

---

### Post by spookybathtub on 2013-10-15
I'm reluctant to use apt-get because everything I've read says aptitude is the newer, better version.
I ran aptitude dist-upgrade and most packages were installed, except one. Details:

```
$aptitude show apparmor
Package: apparmor
State: installed [held]
Automatically installed: no
Version: 2.7.102-0ubuntu3.7
Priority: standard
Section: admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Uncompressed Size: 1,081 k
Depends: libc6 (>= 2.14), debconf (>= 0.5) | debconf-2.0, python, lsb-base,
         initramfs-tools, debconf
PreDepends: dpkg (>= 1.15.7.2)
Suggests: apparmor-profiles, apparmor-docs, apparmor-utils
Conflicts: apparmor
Breaks: apparmor-utils (< 2.6.1-4ubuntu1), apparmor-utils (< 2.6.1-4ubuntu1),
        libapache2-mod-apparmor (< 2.5.1-0ubuntu3), libapache2-mod-apparmor (<
        2.5.1-0ubuntu3)
Replaces: apparmor-parser, apparmor-parser, apparmor-utils (< 2.6.1-4ubuntu1),
          apparmor-utils (< 2.6.1-4ubuntu1), libapache2-mod-apparmor (<
          2.5.1-0ubuntu3), libapache2-mod-apparmor (< 2.5.1-0ubuntu3)
Description: User-space parser utility for AppArmor
 This provides the system initialization scripts needed to use the AppArmor
 Mandatory Access Control system, including the AppArmor Parser which is
 required to convert AppArmor text profiles into machine-readable policies that
 are loaded into the kernel for use with the AppArmor Linux Security Module.
Homepage: http://apparmor.net/

```

---

### Post by sudodus on 2013-10-15
Maybe apparmor is not ready to upgrade because it is waiting for some library, that must be upgraded too. But I am not used to aptitude, so I am not good at decrypting its messages.

---

