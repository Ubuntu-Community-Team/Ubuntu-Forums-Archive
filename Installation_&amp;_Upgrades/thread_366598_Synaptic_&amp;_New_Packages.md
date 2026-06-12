---
title: "Synaptic &amp; New Packages"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by Apoorv on 2007-02-21
Yesterday, I downloaded Skype from it's website and tried to install it . It was a deb package and I tried to install it with GDebi Package Installer. The installation went smooth, but during the final stage of installation, the installer crashed. I tried to install it, but the installer crashed again. I chose to send a bug report, but the bug reporter crashed too. Next, I downloaded Opera, which was a deb package too. I can't install that too.

Worst, I now can't even open Synaptic Package Manager. I can't even get packages from the terminal now. I get an error each time I try to sudo apt-get install anything. It says - "Segmentation Fault (Core Dumped)."

Any ideas?

---

### Post by louis_nichols on 2007-02-21
That sounds quite bad. How about downloading the apt-get deb package directly from the repository and then re-installing it with dpkg? you can visit [http://packages.ubuntu.com]("http://packages.ubuntu.com") and download it from there.

Then you can try to run *apt-get -f install*. And then, in theory, you should be back on track.

Just an idea.

---

### Post by Apoorv on 2007-02-21
How do I install it with dpkg? And what's the use of redownloading it, when I already have them on my hard disk? 

Plus what does the -f do?

---

### Post by Apoorv on 2007-02-21
Is there no solution except re-installation?

---

### Post by louis_nichols on 2007-02-21
There may be. But I think this a simple enough solution. The whole apt package can be downloaded easily. You can also try using aptitude to reinstall apt, like this:

```
sudo aptitude reinstall apt
```

Otherwise, you can do as I wrote above. download a package in a folder and use dpkg to reinstall it from that folder. so what you should is this:

```
 wget http://mirrors.kernel.org/ubuntu/pool/main/a/apt/apt_0.6.45ubuntu14_i386.deb
sudo dpkg -i apt_0.6.45ubuntu14_i386.deb

```
all this takes less than 5 seconds, depending on your internet connection. And then everything should be back to normal.

You should run after this an ```
apt-get -f install
``` which fixes installations.

---

### Post by Apoorv on 2007-02-21
Ahh. Fixed. Thanks a lot. Would you care to explain the problem, what had happened, and how doing this fixed it?

---

### Post by louis_nichols on 2007-02-21
There is no real way to tell the exact problem, especially after it's fixed. I never did know the source. It's just that a segmentation fault all of a sudden, while running a program, suggests there's something wrong with the installation. I was actually never sure it would work, but it was a simple enough solution to try even if doesn't solve the problem. We're sure it can't make things works, anyway.

Sometimes, solving something is a matter of trial and error.

---

