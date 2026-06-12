---
title: "dpkg --configure python3: bad inconsistent state"
date: 2019-04-07
forum: Installation &amp; Upgrades
---

### Post by franknfurter2 on 2019-04-07
Hallo,

some days ago update manager showed up and said, that it could only do a partial update. I clicked "Yes" to do the partial update.

Update process stopped telling that python is in a bad state. Since then, no upgrade or install process via apt-get or dpkg will work anymore.

Finally I tried to installed python3 from sourcecode. Configure and make were running fine. But sudo make install failed with an error that meant that lsb_release -a has got failure.

And yes. lsb_release -a has got a python3 error. So I got stuck.

After installing python-minimal from .deb package lsb_release does work again and "sudo make install" of python3 worked.

But still: Each upgrade or install process via dpkg or apt-get fails. dpkg --configure python3 still returns

dpkg: error while editing the package python3 (--configure):
  Package is in a very bad inconsistent state - you should
  reinstall before attempting the configuration.
Errors occurred while editing:
  python3 

Should I do: 
sudo dpkg --remove --force-remove-reinstreq python3

Regards

Frank

---

### Post by huff2 on 2019-04-07
Was the error after updating or upgrading? If you can update with sudo apt-get update, then try sudo apt-get dist-upgrade. **dist-upgrade **will install and/or remove packages as necessary to complete the upgrade (upgrade will not). 

Otherwise:

Yes, the command you asked about will work. You will need to reinstall python3. I recommend using apt to perform these tasks. The following link is recommended and is easy to follow regarding python3. Be sure to have the correct/recommended repository, the adding of which is detailed in this link as well: [https://docs.python-guide.org/starting/install3/linux/](https://docs.python-guide.org/starting/install3/linux/)

Be sure to do an update and upgrade after the package removal, then do the reinstall.

---

### Post by franknfurter2 on 2019-04-08
Dear huff2,

thanks for your answer, but it does not lead to a solution. apt-get update is working but each upgrade will not. As I wrote, it is because the package python3 is in a bad state and so could not be configured in dpkg which is called by apt-get.

I added the output of sudo apt-get dist-upgrade to this post.

It's like a circle I am arrested in. Installing / fixing python 3 needs a working dpkg. dpkg needs a working python3. So what can one do?

HELP!!

Regards

Frank

---

### Post by huff2 on 2019-04-08
Try sudo apt-get install -f 

What is the output?

---

### Post by franknfurter2 on 2019-04-09
Dear huff2,

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apport-symptoms dc dh-translations gimp-help-common 

....... package list ......

Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
62 not fully installed or removed.
Need to get 0 B/598 kB of archives.
After this operation, 0 B of additional disk space will be used.
Setting up qgis-providers (1:3.6.1+28bionic) ...
Setting up libpam-systemd:amd64 (237-3ubuntu10.19) ...
dpkg: error processing package python3 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
Setting up libqgisgrass7-3.6.1 (1:3.6.1+28bionic) ...
dpkg: dependency problems prevent configuration of catfish:
 catfish depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

... and so on, see my last post.

---

### Post by rsteinmetz70112 on 2019-04-09
Have you tried ```
# apt install --reinstall python3
```
That should install the package over the existing install.
Then:
```
# dpkg --configure -a
# apt install -f

```

---

### Post by franknfurter2 on 2019-04-09
Dear rsteinmetz70112,

thank you so much. The apt install --reinstall python3 did the trick. I had tried apt-get install --reinstall before some days ago, before I posted the problem, but it had not worked. So there seems to be a difference between apt and apt-get.

dpkg --configure -a worked as well. On the fly I updated update-manager as well and did a update-manager run. It has installed some updates now. So it seem to work again.

Thanks a lot.

Regards

Frank

---

### Post by rsteinmetz70112 on 2019-04-10
> **franknfurter2 said:**
> Dear rsteinmetz70112,

thank you so much. The apt install --reinstall python3 did the trick. I had tried apt-get install --reinstall before some days ago, before I posted the problem, but it had not worked. So there seems to be a difference between apt and apt-get.



Glad it worked for you. 

I don't quite understand why ```
apt --reinstall
``` worked and ```
apt-get --reinstall
``` didn't work. 

My understanding is they both do the same thing as apt is simply a different interface to dpkg than apt-get and some other commands.

Just to be sure you might want to run ```
apt install -f 
```to pick up any looses ends.

---

### Post by #&amp;thj^% on 2019-04-10
> **franknfurter2 said:**
> Dear rsteinmetz70112,

thank you so much. The apt install --reinstall python3 did the trick. I had tried apt-get install --reinstall before some days ago, before I posted the problem, but it had not worked. So there seems to be a difference between apt and apt-get.

dpkg --configure -a worked as well. On the fly I updated update-manager as well and did a update-manager run. It has installed some updates now. So it seem to work again.

Thanks a lot.

Regards

Frank

what is the difference between apt --reinstal and apt-get --reinstal


apt is a new command that supposed to merge several functions from apt-get and apt-cache into one command. It's still a little rough around the edges but here's the command listing from --help:

[list]Basic commands: 
 [*]list - list packages based on package names
[*]search - search in package descriptions
 [*]show - show package details

 [*]update - update list of available packages

 [*]install - install packages
 [*]remove  - remove packages

 [*]upgrade - upgrade the system by installing/upgrading packages
 [*]full-upgrade - upgrade the system by removing/installing/upgrading packages

 [*]edit-sources - edit the source information file

also  DIFFERENCES TO APT-GET(8) section in the man apt page that's interesting:
> 
   The apt command is meant to be pleasant for end users and does
   not need to be backward compatible like apt-get(8). Therefore
   some options are different:

   ·   The option DPkgPM::  Progress-Fancy is enabled.

   ·   The option APT::Color is enabled.

   ·   A new list command is available similar to dpkg --list.

   ·   The option upgrade has --with-new-pkgs enabled by default.

[/list]


As far as I know, apt, aptitude and apt-get/cache use the same repository configurations. Therefore, there is no difference in installations from any of them.
The main point to take note of is that these tools are front-ends, so you can use them interchangeably. The difference being their functionality and ease of use.

**Essentially apt-get is "older" and apt is "newer" but both have largely the same functionality, **that being they download, install, update, upgrade, and manage all your packages on your Debian install. They are interchangeable outside of a few edge cases.

---

