---
title: "Nvidia forgot the registry key,"
date: 2020-01-21
forum: Installation &amp; Upgrades
---

### Post by cedara2 on 2020-01-21
System: Ubuntu 18.04
graphic card: nvidia 750Ti (-390 driver)

Last Sunday after booting first on that day, my nvidia graphic card wasn't recognised anymore and also not the monitor. Looking into the graphical part of nvidia settings, I saw that there was no profile listed. When I put in nvidia-settings into the terminal, I got an error message in the terminal, that told me that the registry key could not be found. Lacking the in-depth knowledge, I purged all things nvidia due to advice I got via Mastodon (federated social network) and went back to noveau, the standard driver, for now.

Making sure I didn't have a hardware problem, I tested my drives and they all came out fine, without any errors. Therefore I conclude that it has to be a software issue. However I need the proprietary driver for some games at some point, so I do wonder if the same happens when I again install the drivers from the packages (additional drivers). Should I just try or wait a few days, as I saw in a German forum that other people had likely problems?

---

### Post by webaake on 2020-01-21
I'm running 390-* as well, from the repo [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu). No problem here with kernel 5.05 and since a couple of weeks kernel 5.3.18. From where du you install your 390* driver?

And your not on kernel 5.4.x are you? There seems to be no compatible 390-driver from the repos for kernel 5.4.x yet.

I'd just try to reinstall from repo (like the one above)

Foot note: "From the repos" as opposed to nivida .run installation files downloaded directly from Nvidia.

---

### Post by webaake on 2020-01-21
Ahh, double checked! You should be able to run the 440* driver as your card has a newer chip than my GT610.

Did you try the 440* driver?

---

### Post by cedara2 on 2020-01-21
> **webaake said:**
> Ahh, double checked! You should be able to run the 440* driver as your card has a newer chip than my GT610.

Did you try the 440* driver?

Err, there is no 440 listed in the additional drivers. Also, the 390 ran fine before without any problems (installed it from there). Why do you think I should try another? Got a link where I can read up what driver goes for which card?

I have a metapackage - with 435, a binary with 340.107, a metapackage with 430 and a metapackage with 390 - aside from the nouveau that I use right now.

---

### Post by webaake on 2020-01-21
I've got the 440* listed on 18.04.xx

Do you have the repo [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) activated?

---

### Post by cedara2 on 2020-01-21
I installed my drivers via the additional drivers section, from the repos.

Your question/post made me search a bit more and I found this: [https://askubuntu.com/questions/1204165/ubuntu-18-04-3-lts-and-nvidia-card-low-resolution/1204640#1204640](https://askubuntu.com/questions/1204165/ubuntu-18-04-3-lts-and-nvidia-card-low-resolution/1204640#1204640)

The fellow concludes that the 390 is incompatible with the 5.3. kernel.

---

### Post by webaake on 2020-01-21
390 works fine here on 5.x kernels. Not on 5.4 kernels yet, I've tested. But that's not the issue.

I think that you would get the 440 driver available via the repo [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu)

Here's how to add the repo: (a bit down the page)

[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

---

### Post by cedara2 on 2020-01-21
> **webaake said:**
> 390 works fine here on 5.x kernels. Not on 5.4 kernels yet, I've tested. But that's not the issue.

I think that you would get the 440 driver available via the repo [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu)

Here's how to add the repo: (a bit down the page)

[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)


Hmmm... I'm very cautious on adding drivers with a ppa. I'd be more likely to add the -435(tested). 

I can see however why you think it might be worth it, as it's the one suggested on the nvidia page: 
[https://www.nvidia.com/Download/driverResults.aspx/156086/en-us](https://www.nvidia.com/Download/driverResults.aspx/156086/en-us)

---

### Post by webaake on 2020-01-21
I've used that ppa for years. No problem.

---

### Post by CatKiller on 2020-01-21
> **cedara2 said:**
>  However I need the proprietary driver for some games at some point, so I do wonder if the same happens when I again install the drivers from the packages (additional drivers). 

The Additional Drivers tool is brilliant for discoverability but, because it's been so simplified, it doesn't give a lot of feedback if there are any problems. 

It has the handy hardware scanner to identify candidates for likely packages to install but the behind-the-scenes installation is just installing a package through the package manager. Installing the package that you're after through the command line instead will give you useful information on where, if anywhere, the problem lies.

---

### Post by cedara2 on 2020-01-21
> **CatKiller said:**
> The Additional Drivers tool is brilliant for discoverability but, because it's been so simplified, it doesn't give a lot of feedback if there are any problems. 

It has the handy hardware scanner to identify candidates for likely packages to install but the behind-the-scenes installation is just installing a package through the package manager. Installing the package that you're after through the command line instead will give you useful information on where, if anywhere, the problem lies.

True, which is why I suspect I might be fine with the -435 as it said "tested". 

ETA: That said, the German wiki site says the nouveau has to be used for Geforce 7 now --- link: [https://wiki.ubuntuusers.de/Grafikkarten/Nvidia/](https://wiki.ubuntuusers.de/Grafikkarten/Nvidia/)

---

### Post by cedara2 on 2020-01-24
Turns out my problem isn't just mine, but also someone else's - it's a bug:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1851162](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1851162)

I'm waiting for the fix to show up in the repos.

---

