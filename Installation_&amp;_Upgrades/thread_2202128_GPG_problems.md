---
title: "GPG problems"
date: 2014-01-27
forum: Installation &amp; Upgrades
---

### Post by brichert on 2014-01-27
Howdy all. I'm running 12.04 on a Dell Optiplex 7010, dual booting, and having two problems, one major and one minor. I've been hashing through the major networking problem in another thread [ http://ubuntuforums.org/showthread.php?t=2183423]("http:// http://ubuntuforums.org/showthread.php?t=2183423"), and if anyone has any advice there I would really appreciate it (for a bit I've been having a conversation with myself there).

In any event, I also have the GPG errors. When I run update-manager and try to install updates I get the usual : this would require installation of untrusted packages. After looking around on the forums, I did the following:

sudo apt-get clean
sudo rm -r /var/lib/apt/lists/*
sudo touch /var/lib/apt/lists/lock
sudo mkdir /var/lib/apt/lists/partial
sudo apt-get clean
sudo apt-get update

which works like a charm (though I confess to not being totally sure what it is doing ... presumably removing the authentication keys, but what does the time stamp have to do with it?). In any event, after running this, update-manager works with no problem. The trouble is, a day or so goes by, and I try to run update-manager again, and get the error back again! The same fix still works, but there must be something deeper going on here. Any ideas? Thanks.

---

### Post by Old_Grey_Wolf on 2014-01-27
The link to your other thread has an error, an http:// followed by http. The link should be [http://ubuntuforums.org/showthread.php?t=2183423](http://ubuntuforums.org/showthread.php?t=2183423)

Edit: I suspect that fixing the network problem will fix the update/upgrade problem.

---

### Post by Old_Grey_Wolf on 2014-01-27
I seem to remember that there is a problem using the e1000e driver for Kernels after 2.6.x. Although I was using VMWare at the time.

---

### Post by brichert on 2014-01-28
Thanks, I'll look into the e1000e driver problem.

---

### Post by brichert on 2014-05-14
Upgrading to 14.04 seems to have fixed this problem, although the (possibly related) ethernet problem, alas, remains.

---

