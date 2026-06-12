---
title: "[SOLVED] freepopsd libgnutls13 and 8.10"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by Spyros_Gre on 2008-11-02
Hello! I made a clean installation of Ubuntu 8.10 last night. I used to use freepopsd in order to receive hotmail in mozilla thunderbird. I tried to install it again but it said it needed libgnutls13.
I searched for it in synaptic but found nothing. I found this link [http://packages.ubuntu.com/feisty/i386/libgnutls13/download](http://packages.ubuntu.com/feisty/i386/libgnutls13/download) but apparently it's for feisty. 
Does anybody know why this package is no longer available?
Does it have a substitute? Is there any other way to install freepopsd in Ubuntu 8.10??
Thank you!

is this relevant? [http://ubuntuforums.org/showpost.php?p=6085954&postcount=343](http://ubuntuforums.org/showpost.php?p=6085954&postcount=343)

---

### Post by Partyboi2 on 2008-11-02
That link is to compile freepops from source, but freepops is in the ubuntu repo's and can be install by synaptic or 
```
sudo apt-get install freepops
```
What is the difference between freepopsd and freepops?

---

### Post by Spyros_Gre on 2008-11-02
Yes indeed it is in the repositories but it is not the last one and for me has a problem with hotmail. I think the one ending in d is a daemon? :-)

---

### Post by Partyboi2 on 2008-11-02
You could compile the 2.8 version from source, as mentioned in that link which is a later version then what is in the repos.> 
I searched for it in synaptic but found nothing. I found this link [http://packages.ubuntu.com/feisty/i3...tls13/download]("http://packages.ubuntu.com/feisty/i386/libgnutls13/download") but apparently it's for feisty. Try downloading and installing libgnutls13 from the hardy repos and see how you go.
[http://packages.ubuntu.com/hardy-updates/libgnutls13](http://packages.ubuntu.com/hardy-updates/libgnutls13)

---

### Post by Spyros_Gre on 2008-11-02
libgnutls for 8.04 needs libopencdk10 which is also not found in the repositories of 8.10... Either way would it be safe to install from older repositories in a newer release? In general. 
Thank you!

---

### Post by Partyboi2 on 2008-11-02
> Either way would it be safe to install from older repositories in a newer release? In general.  Sometimes manually you can install packages from an older release (not to old a release) as long as you can satisfy the dependencies for. 
Have you tried downloading the source (freepops) and compiling it?

---

### Post by netof_100 on 2008-11-04
I'm having the same issue, and it all began after I did a clean ubuntu 8.10 installation.
but I don't have any solution yet, I'll keep doing my research

---

### Post by Spyros_Gre on 2008-11-04
Hello!
I tried to install from source and that was where I needed libgutls13 after all. I am currently waiting for the .deb package from the author of freepops. My main problem is that I cannot access hotmail with the old freepops. Either way thank you very much!):P):P

---

### Post by Partyboi2 on 2008-11-04
maybe try installing libgnutls-dev package
```
sudo apt-get install libgnutls-dev
```
I did have a play around with it and successfully installed it from source.

---

### Post by netof_100 on 2008-11-08
> **Partyboi2 said:**
> maybe try installing libgnutls-dev package
```
sudo apt-get install libgnutls-dev
```
I did have a play around with it and successfully installed it from source.
I tried that but still is not working I hate to check emails in the webpage

---

### Post by Partyboi2 on 2008-11-09
Has anyone tried installing the debs from [[COLOR=Blue]this[/COLOR]]("http://cybertech.altervista.org/en/freepops.php") page?

---

### Post by Spyros_Gre on 2008-11-14
Ok new deb package at this site [http://cybertech.altervista.org/en/freepops.php](http://cybertech.altervista.org/en/freepops.php).
(link provided by [http://www.freepops.org/en/download-linux.shtml](http://www.freepops.org/en/download-linux.shtml))
I think the thread should close?

---

