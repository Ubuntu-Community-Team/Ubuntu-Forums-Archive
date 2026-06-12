---
title: "ubuntu-restricted-extras problem"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by splatterdash on 2010-04-21
Hi all,

I'm running Lucid beta 2 on my laptop (fresh install <24 hrs).

I wanted to install the ubuntu-restricted-extras package, so I ran:

```
sudo apt-get install ubuntu-restricted extras
```But in the middle of the installation, several of the packages which require additional download from different servers fail to install (I remember some of them: the flash plugin, some fonts .exe files). As a result, although the ubuntu-restricted-extras package is listed as successfully installed, those packages were not.

I think I've figured out why the download from other servers fail. You see, I'm currently behind a network proxy. I thought setting the proxy address and port from System-Administration-Network tools is enough to get things in line, since the download from the repos work. Turns out, I also need to edit /etc/bash.bashrc with several lines telling bash to use the proxy.

Now, what I want is to do a reinstall and reconfiguration as if the ubuntu-restricted-package wasn't installed in the first place. But I haven't been able to do that. I've tried these:

```
sudo apt-get autoremove ubuntu-restricted-extras
```then restarting the computer, then
```
sudo apt-get clean
sudo apt-get update
```then
```
sudo apt-get --reinstall install ubuntu-restricted-extras
```but the those packages (flash, etc) are still not installed. I've also tried various combinations of these:
```
sudo apt-get --reinstall install ubuntu-restricted-extras
sudo apt-get -f install ubuntu-restricted-extras
```Now I'm confused. What should I do to get the package installed properly?

---

### Post by prshah on 2010-04-21
> **splatterdash said:**
> 
```
sudo apt-get autoremove ubuntu-restricted-extras
```
What should I do to get the package installed properly?

```
sudo apt-get remove --purge ubuntu-restricted-extras
```
then```
sudo apt-get install ubuntu-restricted-extras
``` There is no need to restart inbetween these steps.

---

### Post by splatterdash on 2010-04-21
> **prshah said:**
> ```
sudo apt-get remove --purge ubuntu-restricted-extras
```then```
sudo apt-get install ubuntu-restricted-extras
``` There is no need to restart inbetween these steps.

Thanks for the info. I tried that as well, still the same :/.

I've somehow figure out a way, I think. I manually uninstalled the packages listed here:

[http://ubuntuforums.org/showthread.php?p=9152013](http://ubuntuforums.org/showthread.php?p=9152013)

And reinstall them again. It's messy but works for now (does anyone have a more elegant solution?), but I still experience the initial problem: the flash installer couldn't download the required filed. This is weird, since I tried opening the repo using Firefox and it works fine.

Anyway, thanks again.

---

### Post by jdbeyers on 2011-06-21
I managed to fix this issue by running aptitude, then searching for "ubuntu-restricted-extras" and then deselecting all the modules that come with it. Then I reinstall the modules, and it fixes up the files that were not downloaded.

---

