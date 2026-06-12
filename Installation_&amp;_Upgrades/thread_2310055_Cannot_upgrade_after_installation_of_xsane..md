---
title: "Cannot upgrade after installation of xsane."
date: 2016-01-15
forum: Installation &amp; Upgrades
---

### Post by Owen Thomas on 2016-01-15
Hello again Ubuntu community.

I recently installed the xsane package to assist me with scanning documents, and yesterday, I did some regular software upgrades since I installed the xsane software.

The installer got as far as saying that it was "Preconfiguring packages..." and then seemed to hang. I looked with my system monitor to see what activity was transpiring, and I could see that of my four CPUs, CPU's 1 and 2 were working at about 20% capacity each, and 3 and 4 were working at about 80% capacity each. Every 20 seconds or so this activity would swap, but this wouldn't last any longer than perhaps two seconds. Hence, I decided to let my laptop work overnight.

I wake up this morning, and the installer still said that it was preconfiguring packages, the same behaviour was still being witnessed by the CPUs but the physical and virtual memory space had almost been exhausted. Soon thereafter, my computer became unresponsive, and I had to perform a hard reset.

I had witnessed similar behaviour to this when I installed MySQL. I removed the package through the Software Centre and the problem "went away". I am now wondering that the problem will "go away" when I remove xsane. However, I want to keep xsane. Thus I have a dilemma.

Is there a way to keep xsane and allow my computer to upgrade?

Furthermore, I seem to have a general dilemma in that I cannot appear to install anything but standard Ubuntu bundled packages without seeing behaviour like this. Is anyone else having this problem?

I have an HP 250 G3 Notebook which is running Ubuntu 14.4 LTS. The xsane package says it is version 0.998.

Thanks for your help.

  Owen.

---

### Post by Owen Thomas on 2016-01-17
It has been about two days since I posted my question to the forum. I have received no assistance, and hence conclude the only action I can take is to uninstall xsane to be able to continue receiving and installing software updates.

If anyone who reads this might know what is going on, please respond because I don't really want to keep installing the xsane package, using my scanner, and then uninstalling xsane so I can process software updates. There must be a better way than this.

---

### Post by Irihapeti on 2016-01-17
Where did you get the xsane package? I'm not quite clear if you installed it from the Software Centre or got it somewhere else.

---

### Post by Owen Thomas on 2016-01-17
Thanks for your reply.

Although a version of xsane is given in the Software Centre, I didn't install it from there. I got the xsane software by following [this link]("http://gsusmonzon.blogspot.com.au/2015/06/canon-lide-220-in-ubuntu-1404.html"). I have removed the packages that I thought were responsible for my computer freezing when doing a software update, yet it appears to have frozen yet again.

I'm a bit dismayed.

---

### Post by Irihapeti on 2016-01-17
Presumably, you need a later version than what's in the Software Centre and installed a PPA. PPAs sometimes get in a tangle with existing software and cause problems.

I have to admit that I'm out of my depth here. I'd suggest contacting the author of the PPA [here]("https://launchpad.net/~rolfbensch"). I see that there are a couple of visible email addresses on the page, and you can see more if you log in.

To get your computer working for other things in the meantime, you could install ppa-purge and then do

```
sudo ppa-purge ppa:rolfbensch/sane-git
```

ppa-purge is recommended for making sure that your system has been cleaned up - it's easy to miss a package or two.

---

### Post by matt_symes on 2016-01-17
Hi

> **Owen Thomas said:**
> Although a version of xsane is given in the Software Centre, I didn't install it from there. I got the xsane software by following [this link]("http://gsusmonzon.blogspot.com.au/2015/06/canon-lide-220-in-ubuntu-1404.html").

Why did you install xsane from a PPA and not use the standard repositories ?

> I had witnessed similar behaviour to this when I installed MySQL. I removed the package through the Software Centre and the problem "went away". 

Did you also install MySQL from a PPA ?

Can you post the output of this command to. It lists your sources.

```
grep "^[^#]" /etc/apt/sources.list{,.d/*}
```

and the output of these commands as well please.

```
sudo apt-get check
sudo dpkg -C
```

Run ppapurge on the xsane package as suggested by Irihapeti.

Kind regards

---

### Post by Owen Thomas on 2016-01-18
Thank you to both of you for replying. I understand that trusting what people say is risky, and unfortunately I'm seeing these risks play out here. Although I'm a Java developer, I'm rather inept in matters that diverge away from my specific domain.

I have installed and run ppa-purge as instructed Irihapeti, and get the tollowing output:
```
owen@owen-HP-250-G3-Notebook-PC:~$ sudo ppa-purge ppa:rolfbensch/sane-git
Updating packages lists
PPA to be removed: rolfbensch sane-git
Package revert list generated:
 libsane:amd64/trusty libsane-common/trusty libsane-dev/trusty sane-utils/trusty

Disabling rolfbensch PPA from 
/etc/apt/sources.list.d/rolfbensch-sane-git-trusty.list
Updating packages lists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sane-utils is already the newest version.
Selected version '1.0.23-3ubuntu3.1' (Ubuntu:14.04/trusty-updates [amd64]) for 'libsane'
Selected version '1.0.23-3ubuntu3.1' (Ubuntu:14.04/trusty-updates [amd64]) for 'libsane-common'
Selected version '1.0.23-3ubuntu3.1' (Ubuntu:14.04/trusty-updates [amd64]) for 'libsane-dev'
Selected version '1.0.23-3ubuntu3.1' (Ubuntu:14.04/trusty-updates [amd64]) for 'sane-utils'
The following packages were automatically installed and are no longer required:
  gimp gimp-data libamd2.3.1 libbabl-0.1-0 libblas3 libcamd2.3.1
  libccolamd2.8.0 libcholmod2.1.2 libgegl-0.2-0 libgfortran3 libgimp2.0
  libilmbase6 libjavascriptcoregtk-1.0-0 liblapack3 liblcms1 libmng2
  libopenexr6 libsdl1.2debian libumfpack5.6.2 libwebkitgtk-1.0-0
  libwebkitgtk-1.0-common linux-headers-3.13.0-32
  linux-headers-3.13.0-32-generic linux-headers-3.13.0-39
  linux-headers-3.13.0-39-generic linux-image-3.13.0-32-generic
  linux-image-3.13.0-39-generic linux-image-extra-3.13.0-32-generic
  linux-image-extra-3.13.0-39-generic linux-signed-image-3.13.0-39-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  hpoj libsane-extras-dev
The following packages will be DOWNGRADED:
  libsane libsane-common libsane-dev
0 to upgrade, 0 to newly install, 3 to downgrade, 0 to remove and 88 not to upgrade.
Need to get 4,481 kB of archives.
After this operation, 2,256 kB disk space will be freed.
Do you want to continue? [Y/n] 
Get:1 http://au.archive.ubuntu.com/ubuntu/ trusty-updates/main libsane-dev amd64 1.0.23-3ubuntu3.1 [2,100 kB]
Get:2 http://au.archive.ubuntu.com/ubuntu/ trusty-updates/main libsane amd64 1.0.23-3ubuntu3.1 [1,929 kB]
Get:3 http://au.archive.ubuntu.com/ubuntu/ trusty-updates/main libsane-common amd64 1.0.23-3ubuntu3.1 [451 kB]
Fetched 4,481 kB in 7s (608 kB/s)                                              
dpkg: warning: downgrading libsane-dev from 1.0.26-git20160103-trusty0 to 1.0.23-3ubuntu3.1
(Reading database ... 850840 files and directories currently installed.)
Preparing to unpack .../libsane-dev_1.0.23-3ubuntu3.1_amd64.deb ...
Unpacking libsane-dev (1.0.23-3ubuntu3.1) over (1.0.26-git20160103-trusty0) ...
dpkg: warning: downgrading libsane:amd64 from 1.0.26-git20160103-trusty0 to 1.0.23-3ubuntu3.1
Preparing to unpack .../libsane_1.0.23-3ubuntu3.1_amd64.deb ...
Unpacking libsane:amd64 (1.0.23-3ubuntu3.1) over (1.0.26-git20160103-trusty0) ...
dpkg: warning: downgrading libsane-common from 1.0.26-git20160103-trusty0 to 1.0.23-3ubuntu3.1
Preparing to unpack .../libsane-common_1.0.23-3ubuntu3.1_amd64.deb ...
Unpacking libsane-common (1.0.23-3ubuntu3.1) over (1.0.26-git20160103-trusty0) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for doc-base (0.10.5) ...
Processing 1 changed doc-base file...
Setting up libsane-common (1.0.23-3ubuntu3.1) ...
Setting up libsane:amd64 (1.0.23-3ubuntu3.1) ...
Installing new version of config file /etc/sane.d/xerox_mfp.conf ...
Installing new version of config file /etc/sane.d/genesys.conf ...
Installing new version of config file /etc/sane.d/cardscan.conf ...
Installing new version of config file /etc/sane.d/dll.conf ...
Installing new version of config file /etc/sane.d/epson2.conf ...
Installing new version of config file /etc/sane.d/gt68xx.conf ...
Installing new version of config file /etc/sane.d/kodakaio.conf ...
Installing new version of config file /etc/sane.d/canon_dr.conf ...
Installing new version of config file /etc/sane.d/epjitsu.conf ...
Installing new version of config file /etc/sane.d/fujitsu.conf ...
Setting up libsane-dev (1.0.23-3ubuntu3.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
PPA purged successfully
```
However, alas, my computer still appears to be hanging after displaying "Preconfiguring packages..." in the Software Updater console.

This is the output from grep "^[^#]" /etc/apt/sources.list{,.d/*}:
```
owen@owen-HP-250-G3-Notebook-PC:~$ grep "^[^#]" /etc/apt/sources.list{,.d/*}
/etc/apt/sources.list:deb http://au.archive.ubuntu.com/ubuntu/ trusty main restricted
/etc/apt/sources.list:deb-src http://au.archive.ubuntu.com/ubuntu/ trusty main restricted
/etc/apt/sources.list:deb http://au.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
/etc/apt/sources.list:deb-src http://au.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
/etc/apt/sources.list:deb http://au.archive.ubuntu.com/ubuntu/ trusty universe
/etc/apt/sources.list:deb-src http://au.archive.ubuntu.com/ubuntu/ trusty universe
/etc/apt/sources.list:deb http://au.archive.ubuntu.com/ubuntu/ trusty-updates universe
/etc/apt/sources.list:deb-src http://au.archive.ubuntu.com/ubuntu/ trusty-updates universe
/etc/apt/sources.list:deb http://au.archive.ubuntu.com/ubuntu/ trusty multiverse
/etc/apt/sources.list:deb-src http://au.archive.ubuntu.com/ubuntu/ trusty multiverse
/etc/apt/sources.list:deb http://au.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
/etc/apt/sources.list:deb-src http://au.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
/etc/apt/sources.list:deb http://au.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src http://au.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu trusty-security main restricted
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu trusty-security universe
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu trusty-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu trusty-security multiverse
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
/etc/apt/sources.list:deb http://extras.ubuntu.com/ubuntu trusty main
/etc/apt/sources.list:deb-src http://extras.ubuntu.com/ubuntu trusty main
/etc/apt/sources.list.d/mysql.list:deb http://repo.mysql.com/apt/ubuntu/ trusty mysql-apt-config
/etc/apt/sources.list.d/mysql.list.save:deb http://repo.mysql.com/apt/ubuntu/ trusty mysql-apt-config
```
Running sudo apt-get check gives me the following:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```
Running sudo dpkg -C produces no output.

Being that I've never familiarised myself with the Ubuntu Software Centre, I appear to have opened myself up to making mistakes that cause the Software Updater to hang. As I stated above, the Software Updater is still hanging even after I have done what Irihapeti has suggested. I'll make a mental note that maybe in the future I should try to install the Software Centre versions of the packages before I go searching for unsolicited advice.

Further help on getting the Software Updater to work would be greatly received. I note that CPU activity picks up when I attempt to update software, and this activity does not stop even after I cancel the update. I have to restart my computer to make my CPUs settle down.

Thanks,

  Owen,

---

### Post by Irihapeti on 2016-01-19
You could try installing Synaptic package manager
```
sudo apt-get install synaptic
```
to use in place of the Software Centre. I have the Software Centre installed (by default) but almost never use it, since I much prefer Synaptic. For me, the Software Centre is slow and laggy.

I'd suggest giving Synaptic a go and seeing if that helps.


I see you also have a mysql ppa. That may also be causing a few issues.

For the record, I use PPAs myself. They are great when they work, but that's not always guaranteed, unfortunately.

---

### Post by Owen Thomas on 2016-01-20
Hello again.
> **Irihapeti said:**
> You could try installing Synaptic package manager
```
sudo apt-get install synaptic
```
to use in place of the Software Centre. I have the Software Centre installed (by default) but almost never use it, since I much prefer Synaptic. For me, the Software Centre is slow and laggy.

I'd suggest giving Synaptic a go and seeing if that helps.
Thank you Irihapeti for your ongoing assistance. It acknowledge your comments about Synaptic, but I'd rather just prefer to have things back to what they were before I tried to turn my hand to hacking. I think there's a lesson for me in that I should, unless it is impractical, stick to the Ubuntu Software Centre.
> **Irihapeti said:**
>  I see you also have a mysql ppa. That may also be causing a few issues.

For the record, I use PPAs myself. They are great when they work, but that's not always guaranteed, unfortunately.
I uninstalled MySQL when I found that the Software Updater was hanging before. Maybe, somehow, something about installing xsane (which has now been uninstalled and the PPAs removed with your assistance) has caused the MySQL PPA's to affect the Software Updater. I'd like everything back to normal so I can just update my Ubuntu whenever updates are due.

How do I reset everything so the Software Updater doesn't hang? Do I just get rid of these MySQL PPAs? If so, how do I do this cleanly?

---

### Post by Irihapeti on 2016-01-20
The mysql repository isn't a standard PPA, so I don't know if PPA-purge would work. I need to leave that to someone else who's more knowledgeable on that score.

Something else I notice: you have a lot of "deb-src" entries. You could disable / remove those and see if that reduces the load on the software updater.

---

### Post by Owen Thomas on 2016-01-22
I ended up reinstalling 14.4 from a USB. The problem appears to have gone away; the inconvenience has perhaps underscored to me the importance of making use of the official installation channels offered through the Software Centre before going in like a bull in a china shop, and I hope doing so will help avoid the recurrence of situations like these.

Thanks for your help.

---

