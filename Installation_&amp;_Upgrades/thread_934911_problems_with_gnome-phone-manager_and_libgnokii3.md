---
title: "problems with gnome-phone-manager and libgnokii3"
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by fritsmartfu on 2008-10-01
Hi,
I have problems with Ubuntu 8.04.
I installed it a couple of days ago and found some problems with Gnokii what disturbed my whole Synaptic. Because of my system is Dutch, I translate the most important messages as good as possible. I tried to use the Dutch Forum, but despite of a lot great help, my problems remain as before:

Dpkg: requirement problems makes it impossible to configure libgnokii3. Libgnokii3 depends on Gnokii common (=06.6.22.dfsg-3); but: Gnokii-common package is not installed. 

Dpkg: failure to settle libgnokii3 (--configure)
requirements problem - remain unconfigured

Dpkg: Requirement problem makes it impossible to configure the gnome-phone-manager: gnome-phone-manager depends on libgnokii3; but: package libgnokii3 is still not configured.

Dpkg: failure with settle of gnome-phone-manager (--configure): requirement problems - remain unconfigured.

Failures found during the treatment of 
   libgnokii3
   gnome-phone-manager

What can I do to use the Synaptic package manager as before and to install new packages, and to upgrade and to update my Ubuntu 8.04?

Thanks!

---

### Post by fballem on 2008-10-01
If I'm understanding the problem correctly, then you are trying to install gnokii and running into problems because of dependencies. I don't speak Dutch and my system is set to English.

I don't know if you have tried the following, but I hope that it helps:

1. Open Synaptic (System > Administration > Synaptic Package Manager). This will open Synaptic.
2. Use the Search button and search for gnokii. This will give you a list of applications. It should be similar to the list shown in the attached screenshot.
3. Right click on the entry for gnokii and select 'Mark for Install'. This should result in a second list being shown saying that Mark Additional Required Changes?. Select OK (screenshot is attached).
4. The Synaptic panel should now look like my screenshot.
5. If you select Apply, this should install gnokii and all of the required dependencies.

Hope this helps,

---

### Post by fritsmartfu on 2008-10-01
Thank you fballem for your suggestion, 
I tried all your suggestions with help of the Dutch forum several times without succes. I couldn't repair broken files in Synaptic, Synaptic is downloading new files, but can't work up those files, because files are broken.
It seems, as if files are waiting for each other in a virtual circle: libgnokii3 couldn't configured, because of gnokii-common is missing;
gnokii-common can'nt be installed because of libgnoki3 isn't configured.
And because of there is a failure, Synaptic is not able install anything: no applications, no updates, no upgrades.

The result from of the last suggestions at the Dutch forum was:

> frits@frits:~$ ls /var/lib/dpkg/info/gnok*
/var/lib/dpkg/info/gnokii.conffiles  /var/lib/dpkg/info/gnokii.postinst
/var/lib/dpkg/info/gnokii.list       /var/lib/dpkg/info/gnokii.postrm
/var/lib/dpkg/info/gnokii.md5sums    /var/lib/dpkg/info/gnokii.preinst

frits@frits:~$ ls /var/cache/apt/archives/gnok*
/var/cache/apt/archives/gnokii_0.6.22.dfsg-3_all.deb
/var/cache/apt/archives/gnokii-cli_0.6.22.dfsg-3_i386.deb
/var/cache/apt/archives/gnokii-common_0.6.22.dfsg-3_all.deb
frits@frits:~$ cat /var/lib/dpkg/info/gnokii.list
/etc
/etc/gnokiirc

In this message, the second parts of the three "anwer" lines for the first command are in green, and the whole "answer" at the second command is red coloured. I do'nt know what it means, but perhaps it could help you, to help me.
If you looks for the whole Dutch discussion the partially Dutch terminal-window you can find them at [http://forum.ubuntu-nl.org/topic/32180](http://forum.ubuntu-nl.org/topic/32180).

The most terible thing is, that I don't need gnokki anymore, because I use Samsung now!

Thank you again!

---

