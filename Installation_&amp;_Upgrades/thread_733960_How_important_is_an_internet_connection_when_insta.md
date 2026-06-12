---
title: "How important is an internet connection when installing?"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by hackersmovie on 2008-03-24
I'm talking about the actual initial install. I've installed the 64bit version of Gutsy on my Macbook and am having trouble with the wireless and sound. I've read, re-read, tried and re-tried all the tips on getting them up an running. I guess my real question is:

Would I benefit or even solve some issues by re-installing Ubuntu with an internet connection?

From what I've read, apparently Ubuntu while installing searches repos for certain packages depending on your hardware. Is this correct?

Thanks in advance!

---

### Post by TheWizzard on 2008-03-24
> **hackersmovie said:**
> I'm talking about the actual initial install. I've installed the 64bit version of Gutsy on my Macbook and am having trouble with the wireless and sound. I've read, re-read, tried and re-tried all the tips on getting them up an running. I guess my real question is:

Would I benefit or even solve some issues by re-installing Ubuntu with an internet connection?

From what I've read, apparently Ubuntu while installing searches repos for certain packages depending on your hardware. Is this correct?

Thanks in advance!

having a wired internet connection during installations helps to get the sources list for the repos correct. i always have a wired connection when i install. 

i don't think a new installation is necessary. just enable the repos in synaptic.

---

### Post by muchas on 2008-03-24
I also tried that but some repos can't be enabled with just enabling them in synaptic or even shell. so the best thing is to reinstall the OS with a live internet connection. You may also download or enable some restricted hardware automatically.

---

### Post by zvacet on 2008-03-24
You can enable repositories 

1. system>software sources>check all under ubuntu software and update tab.Reload.

2. from terminal

```
gksudo gedit /etc/apt/sources.list
```

**remove # sign from all lines begin with deb**

save and close

```
sudo apt-get update
```

If you want to add repositories you can try with [this](http://easylinux.info/wiki/Ubuntu:Gutsy#Manual_Method_for_Adding_Repositories) one.

---

