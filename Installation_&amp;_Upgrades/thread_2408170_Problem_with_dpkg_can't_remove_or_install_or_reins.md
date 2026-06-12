---
title: "Problem with dpkg can't remove or install or reinstall...."
date: 2018-12-14
forum: Installation &amp; Upgrades
---

### Post by sourceskyboxer on 2018-12-14
Hello everyone, I am new here
I am using Ubuntu 18.04 ( Very latest )
I would like to get fix if I have to install with mono runtime than it stopped because dpkg freezes.

How do I fix? 

I have searched but it looks like so close to same but nothing help..

```
dpkg: error processing package libnunit-util2.6.3-cil (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libnunit-core-interfaces2.6.3-cil
 libnunit-core2.6.3-cil
 libnunit-console-runner2.6.3-cil
 libnunit-util2.6.3-cil
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I am very disappointed - I have already tried sudo dpkg -r /var/caches/apt/archives/filename.deb 
No success

I am sorry - I am very hesitating because I want stay my Ubuntu 18.04 without re-installation.

That is why please explain how do I fix dpkg should be cool. ( Looks like dpkg shouldn't be aggressive or banned.

Thank you for help!

---

### Post by Impavidus on 2018-12-15
I see you're new. Welcome.

Let's have a look at the exact problem the package manager is running into:```
sudo apt install -f
```Show us the **complete** output of that command. It should contain a useful error message. Also try```
dpkg --list | egrep -v '^ii|^rc'
```That will produce a list of all packages not properly installed or removed.

---

