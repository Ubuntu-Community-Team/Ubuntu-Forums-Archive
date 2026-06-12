---
title: "Unable to install any package after an aborted update from karmic to lucid"
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by v1v3k on 2011-01-31
Hi,

I have been using Ubuntu 9.10 for a while. When I noticed that the support for this version would end soon, I decided to upgrade to Ubuntu 10.04 (Lucid Lynx). So I started using the update manager (The GUI one). It was calculating changes for some time and then it showed a message that 1.9 GB of files need to be downloaded. Since I didn't have an unlimited data plan and with my connection , it could take a really long time, I aborted the process. After that I'm unable to install any package using apt-get or other wise. After a package has been downloaded, when apt tries to install it - I get the error:

```
E: Internal Error, Could not perform immediate configuration (2) on mountall
```I noticed that in the soures.list file, all the repositories were changed to lucid. I changed them all back to karmic and tried again. But I still get the same error when I try to install something.

Is there any work around for this?

---

### Post by garvinrick4 on 2011-01-31
> **v1v3k said:**
> Hi,

I have been using Ubuntu 9.10 for a while. When I noticed that the support for this version would end soon, I decided to upgrade to Ubuntu 10.04 (Lucid Lynx). So I started using the update manager (The GUI one). It was calculating changes for some time and then it showed a message that 1.9 GB of files need to be downloaded. Since I didn't have an unlimited data plan and with my connection , it could take a really long time, I aborted the process. After that I'm unable to install any package using apt-get or other wise. After a package has been downloaded, when apt tries to install it - I get the error:

```
E: Internal Error, Could not perform immediate configuration (2) on mountall
```I noticed that in the soures.list file, all the repositories were changed to lucid. I changed them all back to karmic and tried again. But I still get the same error when I try to install something.

Is there any work around for this? I believe this will get you in as root and change them and the update. Open terminal and copy and paste:
```
sudo sed -i 's/lucid/karmic/g' /etc/apt/sources.list && sudo apt-get update
```
Throw one of these in to make sure no dependency issues going on:
```
sudo dpkg --configure -a
```
and
```
sudo apt-get -f install
```

---

### Post by v1v3k on 2011-01-31
Thanks, It fixed the problem.

> **garvinrick4 said:**
> 
```
sudo dpkg --configure -a
```

Btw what does the above line of code do?

---

### Post by garvinrick4 on 2011-01-31
> **v1v3k said:**
> Thanks, It fixed the problem.



Btw what does the above line of code do? It changes the version in sources.list
saves them and updates them. In your case it is going backwards in version only because
you never upgraded your system just changed the sources.list other wise it is usually used
to go from one version to the next version. Add a && sudo apt-get dist-upgrade to it and you have upgraded your system to next version.

---

