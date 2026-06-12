---
title: "How to install an application with the .rpm extension?"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by sshahir on 2007-11-17
Hello,

I am trying to install [[COLOR="Blue"]the debian application[/COLOR]]("http://ubuntuforums.org/showthread.php?t=608072") on my Ubuntu 6.0.6  using the following command:

sudo apt-get install ./vm-arm-se-1.0.6-15.debian3_1.i386.rpm

the installation stopped because a package couldn't be found.

> Reading package lists... Done
Building dependency tree... Done
[COLOR="Red"]E: Couldn't find package [/COLOR].

even when I try to install the .rpm application using the Synaptic Package Manager, I received the "Archive type not supported" error message(see the attached screenshot).

Any suggestion how I can install the application?

---

### Post by Frak on 2007-11-17
install alien
```
sudo aptitude install alien
```
then install it with
```
sudo alien -i /path/to/file.rpm
```

---

### Post by sshahir on 2007-11-27
Hello Frak,

Thank you for the provided information. I have been able to install the application successfully.

Cheers,
sshahir

---

