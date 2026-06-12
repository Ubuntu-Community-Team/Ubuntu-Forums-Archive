---
title: "dpkg: dependency problems"
date: 2019-03-10
forum: Installation &amp; Upgrades
---

### Post by anderbuntu on 2019-03-10
Hi

I tried to install passwordSafe from deb pkg, because it is not in standard repositary..
However it is not possible  due to Package libxerces-c3.1 is not installed,  even newer 3.2 is installed.
Any idea ?


# dpkg -i passwordsafe-ubuntu16-1.07.0-BETA.amd64.deb 
Selecting previously unselected package passwordsafe.
(Reading database ... 222079 files and directories currently installed.)
Preparing to unpack passwordsafe-ubuntu16-1.07.0-BETA.amd64.deb ...
Unpacking passwordsafe (1.07.0-BETA) ...
dpkg: dependency problems prevent configuration of passwordsafe:
[B][COLOR=#ff0000] passwordsafe depends on libxerces-c3.1 (>= 3.1.0-1); however:
  Package libxerces-c3.1 is not installed.[/COLOR][/B]

dpkg: error processing package passwordsafe (--install):
 dependency problems - leaving unconfigured
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Errors were encountered while processing:
 passwordsafe



# apt list --installed|grep  libxerces
WARNING: apt does not have a stable CLI interface. Use with caution in scripts.
**[COLOR=#ff0000]libxerces-c3.2/bionic,now 3.2.0+debian-2 amd64 [installed][/COLOR]**


A.

---

### Post by TheFu on 2019-03-10
I would avoid using .deb files outside the repo.  Dependency issues, not just at install time but the dependencies which are already met will hold back updates to other packages. It is a security consideration.

This is where I'd look for a PPA.  If I can't find that, then a snap package or flatpak.
[https://www.omgubuntu.co.uk/2018/08/password-safe-keepass-linux-manager](https://www.omgubuntu.co.uk/2018/08/password-safe-keepass-linux-manager)

If you aren't tied to this specific software, I can say that KeePassXC is available and compatible. This is what I use on Linux.  I move the DB to different Linux systems, Android and 1 Windows system.

---

### Post by anderbuntu on 2019-03-11
Hmm, OK, so there is no workaround how to push this installation further ?
If there is already newer lib libxerces-c3.2 installed, I am surprised why is not working ?
Some workaround : symbolic link to missing lib or something...

A>

---

### Post by again? on 2019-03-11
I downloaded and installed the passwordsafe-ubuntu18-1.07.0-BETA.amd64.deb which works in ubuntu 18.04.
[https://sourceforge.net/projects/passwordsafe/files/Linux-BETA/1.07BETA/](https://sourceforge.net/projects/passwordsafe/files/Linux-BETA/1.07BETA/)
Don't know how the numbering works but as they're both beta releases with the same release date, I'm guessing "ubuntu18-1.07.0-BETA" is for bionic.

Install with apt using full path to downloaded deb.
eg
```
sudo apt install ~/Downloads/passwordsafe-ubuntu18-1.07.0-BETA.amd64.deb
```

---

### Post by TheFu on 2019-03-11
> **anderbuntu said:**
> Hmm, OK, so there is no workaround how to push this installation further ?
If there is already newer lib libxerces-c3.2 installed, I am surprised why is not working ?
Some workaround : symbolic link to missing lib or something...

A>

I provided 3 possible actions. If you don't understand, please ask.

Programs aren't always "forward compatible" with new libraries. The programs cannot know when/if a library will change the interfaces for any included calls.

---

### Post by anderbuntu on 2019-03-11
> **guber2 said:**
> I downloaded and installed the passwordsafe-ubuntu18-1.07.0-BETA.amd64.deb which works in ubuntu 18.04.
[https://sourceforge.net/projects/passwordsafe/files/Linux-BETA/1.07BETA/](https://sourceforge.net/projects/passwordsafe/files/Linux-BETA/1.07BETA/)
Don't know how the numbering works but as they're both beta releases with the same release date, I'm guessing "ubuntu18-1.07.0-BETA" is for bionic.

Install with apt using full path to downloaded deb.
eg
```
sudo apt install ~/Downloads/passwordsafe-ubuntu18-1.07.0-BETA.amd64.deb
```


Thanks its working this way :)

A.

---

