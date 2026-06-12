---
title: "Ned advice on 18.04 -&gt; 20.04 upgrade"
date: 2021-03-29
forum: Installation &amp; Upgrades
---

### Post by cscj01 on 2021-03-29
I have used Ubuntu for many years from version 7 to now. I have also tried differing methods of upgrading, i.e., upgrading in place, fresh install.  As the years have passed, I have added more applications to my install list.  As this occurred, the upgrade in place became a nightmare to clean up after the upgrade completed (if it did in fact complete.).  So I turned to doing fresh installs.  I created a list of installed apps using the following```
dpkg --get-selections | grep -v deinstall > software
```I used the following to reinstall all my apps after the clean install:```
sudo dpkg --set-selections <./software
apt-get -y update
apt-get dselect-upgrade
```I had a back of my home directory, so moving over my profiles for Firefox, Thunderbird, etc. was fairly simple.

This worked until I started using MySQL extensively.  When I upgraded from 16.04 to 18.04, I ran into a mess trying to get my authorizations straightened out.  This ranged from just logging in to MySQL to accessing my databases, to using my stored procedures, and on and on and on.

In an effort to avoid this with my upcoming upgrade, I would like some thoughts on what files located where I can save and restore to keep the same environment I had prior to the upgrade.  Any other thoughts or ideas also will be appreciated.

---

### Post by cscj01 on 2021-03-30
Bump

---

### Post by cscj01 on 2021-04-02
Bump

---

### Post by DuckHook on 2021-04-02
I don't have the knowledge to help you navigate the finer elements of databases, but I hope the following more general observations can provide at least some food for thought:

I used to run into the same issues that you've outlined. I would install so many apps that the chances were high that a network upgrade would choke and fail. For my first few years with Linux, I used exactly your strategy to do virgin installs and then back in my apps afterwards. In fact, it was the same two commands. We may even have read the same tutorial so many years ago. ;)

At any rate, I eventually ran into the same issue you are now facing: I don't recall the exact app (it may have been GnuCash) but backing in a list of newer apps did not pick up the configuration changes that had occurred in the interim. Since the app in question was mission&#8209;critical to me, this became a deal&#8209;breaker.

I solved my problem by approaching my setup using the opposite philosophy. Instead of loading my primary system with apps, I hived them off into VMs. Over the last two years these VMs have evolved into LXD containers which I find to be more versatile. The important thing is: my base system is left as close to its virgin state as possible. The only things I add are QEMU/KVM/Virtmanager, VirtualBox and LXD. These are needed to generate the VMs/containers into which everything else is installed.

Everything else runs in their own containers: ranging from databases, to cloud, to webservers, to browsers, to graphics/publishing, to you name it.

do-release-upgrades are now a breeze. I haven't had any major issues over the last four upgrade cycles. This is because, on my base system, there's nothing that's out of the ordinary. As far as the system is concerned, I'm going from one almost default install to another. The VMs/containers are upgraded independently, and since they are segregated into many smaller bite&#8209;sized pieces, there's far less that can go wrong there too. Fewer apps per container means fewer conflicts. This additionally gives me the freedom to hold back upgrades to some containers while going ahead with others. This enhanced granularity has been phenomenal: example—Chromium was deleted from the repos in Focal but remains in Bionic. By running Chromium in a Bionic container, I've managed to to avoid installing it as a snap or PPA for at least another two years. Some WINE apps run better in older version of WINE, going back to Trusty. Etc. Not least, the ability to roll back to an earlier working state has saved me on occasion after a borked app upgrade. So many advantages.

These days, my standard advice for overly complex installs is to simplify, simplify, simplify. Keep your base install as pristine as possible, control your messy stuff by segregating them in VMs/containers, then sit back and enjoy the newfound stability.

In your case, no more dickering around with awkward kludges and workarounds either.

---

### Post by cscj01 on 2021-04-06
Well, I accomplished the upgrade as follows:

[LIST=1]
[*]Uninstalled all sofware that I could easily re-install;
[*]I left MySQL installed;
[*]I updated using Software Updater to 20.04;
[*]I re-installed all sofware previously removed;
[*]I checked out software that had not been removed prior to upgrade - all was good;
[*]I checked out all software that had bveen removed and reinstalled - one issue.
[/LIST]
The only problem I now have is with Virtualbox.

I will change this thread as solved and enter my only problem.

---

