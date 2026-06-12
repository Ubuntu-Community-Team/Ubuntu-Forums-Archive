---
title: "How to change Software Center repositories? (need to re-learn how to MAKE)"
date: 2013-06-05
forum: Installation &amp; Upgrades
---

### Post by pakopako on 2013-06-05
My brain really did hit empty. Forgot 11.04 Natty hit EOL.
I didn't know the repositories for Software Center would move, so my question is now "how to I tell Software Center where it's moved to?"

(Original post in quotes for those who want to skip it.)
> My AV gave an "engine needs upgrade, badly" sign so I went to the ClamTK website to DL the latest source (0.97.8)
[http://www.clamav.net/lang/en/download/sources/](http://www.clamav.net/lang/en/download/sources/)

They recommend removing your current version before compiling
[https://github.com/vrtadmin/clamav-faq/blob/master/faq/Upgrading.md](https://github.com/vrtadmin/clamav-faq/blob/master/faq/Upgrading.md)

So into Synaptic Package Manager I went, uninstalled (not completely remove) all the 0.97.6+dfsg-ubuntu0.11.04.1 files.
I go through the motions of downloading, unpacking, and compiling...
```
./configure  --sysconfdir=/etc
make
make check
```
... but it hangs (failed 2 out of six tests) and running "make install" does nothing.
[https://bugzilla.clamav.net/show_bug.cgi?id=7848](https://bugzilla.clamav.net/show_bug.cgi?id=7848)

So I try restoring 0.97.6 via Synaptic. 404.
Try re-installing from Software Center. 404.
[http://us.archive.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-freshclam_0.97.6+dfsg-1ubuntu0.11.04.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-freshclam_0.97.6+dfsg-1ubuntu0.11.04.1_i386.deb)
[http://security.ubuntu.com/ubuntu/pool/main/c/clamav/clamav_0.97.6+dfsg-1ubuntu0.11.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/clamav/clamav_0.97.6+dfsg-1ubuntu0.11.04.1_i386.deb)

I figure it was deleted from the repository, so I try and see if I can get the latest DEB.
[http://www.ubuntuupdates.org/package/core/natty/universe/proposed/clamav](http://www.ubuntuupdates.org/package/core/natty/universe/proposed/clamav)
```
software-center /tmp/clamav_0.97.8+dfsg-1ubuntu1.08.04.1_i386
dependency is not satisfiable: libclamav6 (>= 0.97.8+dfsg)
```

Tried Adding a new PPA (**ppa:ubuntu-clamav/ppa**), but it only offers PHP scripts, Anti-Virus Proxy, and Web filtering.
I went and downloaded the DEB files individually from Launchpad...
[https://launchpad.net/ubuntu/+archive/primary/+sourcepub/2713221/+listing-archive-extra](https://launchpad.net/ubuntu/+archive/primary/+sourcepub/2713221/+listing-archive-extra)
[https://launchpad.net/ubuntu/+source/clamav/0.97.6+dfsg-1ubuntu0.11.04.1/+build/3898306](https://launchpad.net/ubuntu/+source/clamav/0.97.6+dfsg-1ubuntu0.11.04.1/+build/3898306)

...when I click the install button (it gives me the "please install via your normal software channels" message), SC tries to download them (and runs into a 404). (The only package I managed to install this method was libclamav6_0.97.6+dfsg-1ubuntu0.11.04.1_i386)

I think my brain has hit empty. I'm pretty sure I'm overlooking some method. Help?
(Also, due to how old my PC is, upgrading beyond 11.04 is out of the question.)

---

### Post by ahallubuntu on 2013-06-05
~

---

### Post by pakopako on 2013-06-05
> **ahallubuntu said:**
> The repositories containing the last 11.04 updates have moved and you will need to change them to get any further updates.
How would I go about changing the repository information for my Software Center? (I would have to remove the current ones and find/add the 11.04, yes?)

Also, why wouldn't re-compiling clamav-0.97.6.tar.gz work? It keeps giving an error upon "make". Ditto with using dpkg:
```
sudo dpkg -i clamav_0.97.6+dfsg-1ubuntu0.11.04.1_i386
...
dependency problems prevent configuration of clamav
```

---

### Post by snowpine on 2013-06-05
You misunderstand, pakopako... there are no 11.04 updates. There will never be any more 11.04 updates. Third-party software such as ClamAV is no longer being developed with 11.04 compatibility in mind, because 11.04 is completely obsolete. You should probably back up your files/documents and do a fresh reinstall of a supported release (12.04 or newer). If your computer is too old/slow to run a currently-supported release, then use a "lightweight" distro or upgrade your hardware. I work in IT and recommend replacing your computer every 3-4 years.

---

### Post by pakopako on 2013-06-05
I get there are no updates, but I wonder about what would happen in this situation where I'm trying to re-install an older DEB file and it just isn't working.

I have totally understand what it means to keep up with things, but the reason I have 11.04 on this machine isn't so that it can play "keep up," and I'm not about to throw it away if it can still function.

It's an old machine, doing old tasks, with old software. I just want to be able to find said old software.

---

### Post by snowpine on 2013-06-05
**For educational purposes only; this is NOT a recommendation/endorsement!!!** you'll find that the repositories have moved to old-releases.ubuntu.com and you should change your /etc/apt/sources.list appropriately if you wish to use these repos for historical purposes, for example if you are writing an article on obsolete Linux releases.

---

### Post by Cheesehead on 2013-06-05
> **pakopako said:**
> I get there are no updates, but I wonder about what would happen in this situation where I'm trying to re-install an older DEB file and it just isn't working.

You would need to tell us the specific error of the older .deb. So far, you have told us about trying to install a new .deb into an old system.

End-of-life means no more **security updates**. Newly discovered vulnerabilities will not be fixed, and **your system is vulnerable**.
End-of-life means that you discover a bug, it will not be fixed (of course, it perhaps *has* been fixed in newer versions).
End-of-life means no more community support, no more software repositories.
Perhaps the LTS versions (like 12.04, which is supported until 2017) are better suited to your needs.

Why can't you use newer versions of Ubuntu? PAE-kernel? Too slow? There are ways to address those issues.

---

### Post by pakopako on 2013-06-05
***Very educational indeed!***

Although two questions now appear in my head. First, what did I do wrong with this code that I had to resort to using the USC:
```
sudo dpkg -i clamav_0.97.6+dfsg-1ubuntu0.11.04.1_i386
```
Second, how did this go wrong as well:
```
tar -zxvf [clamav_0.97.6+dfsg.orig.tar.gz]("https://launchpadlibrarian.net/119027425/clamav_0.97.6%2Bdfsg.orig.tar.gz")
cd /Downloads/clamav-0.97.6+dfsg
./configure --sysconfdir=/etc/clamav --localstatedir=/var --mandir=/usr/share/man
make
make install
```
I think I may have to go back to the beginner's class?

---

### Post by pakopako on 2013-06-05
> **Cheesehead said:**
> You would need to tell us the specific error of the older .deb. So far, you have told us about trying to install a new .deb into an old system.
I found out what my mistake was. The newer ClamAV library **libclamav6** requires a dependency to **libltdl3** (or libltdl3-dev) which 11.04 does not have. The closest would be libltdl-dev of which I have the latest build already. So yeah, new .deb, old system. (Likely this is why I couldn't "make install" the thing either.)

> **Cheesehead said:**
> Why can't you use newer versions of Ubuntu? PAE-kernel? Too slow? There are ways to address those issues.
Non-PAE would prevent me from installing Ubuntu 12.04 or higher, and the machine isn't quite robust enough to handle Xubuntu + Gnome.

I really like Gnome on this machine (I do run Xubuntu 12.04 on a slightly newer laptop) and the packages for Wacom pen use I hear is much improved over 11.10. The PHC kernel is also handy.

The only gripes I would say I have found exist with later versions of Ubuntu -- the lack of SD card drivers (because of Toshiba leaving it as closed) and the inability to have my Wacom and iR port functioning at once. (It requires a toggle and a reboot.)

---

