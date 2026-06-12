---
title: "Dependency Issues in Kubuntu, behaving weird....."
date: 2015-10-23
forum: Installation &amp; Upgrades
---

### Post by amantripathi4u on 2015-10-23
Hello Community. I was using Ubuntu 14.04, and upgraded it to Kubuntu 15.04 few days ago. It was working flawlessly. Then one day I used "sudo apt-get autoremove" command, I thought it would save me some memory. But when auto-remove process was running I noticed it was removing some important packages like upstart related packages, KDE environment programs, dependencies and all. I thought it was a part of process, as I am new to Linux. But when I rebooted the system I was unable to boot into GUI, only shell was working, from there I reinstalled Ubuntu-default and KDE environment,display managers, xserver and window managers after which I succeeded to reach login screen, but could not boot into complete desktop. 


I tried tried nearly everything (including suggestions from different forums), but was unable to boot into complete desktop experience. Then out nowhere I decided to boot with previous kernel (i.e. 3.13.x.x) and it booted to desktop. That's fine, but it was not complete, I mean some of the essential programs were missing like Dolphin, Konsole, Kmail and many more. From here I am explaining series of incidents step by step: 

[LIST]
[*]Rebooted the machine with default kernel (i.e. 3.19.x.x) and it worked too. But still there were programs missing.
[*]Reinstalled KDE with "sudo apt-get install --reinstall kubuntu-desktop", most of the programs appeared, but some modules were still not working, like there was Dolphin plugins, some widgets, Amarok.
[*]When I try to install some packages like Yakuake, it gives error "yakuake : Depends: konsole4-kpart but it is not going to be installed". And this problem occurs for many packages.
[/LIST]

[LIST]
[*]Now for these dependency related issues I used nearly every method like : running ```
sudo apt-get clean
``` ```
sudo apt-get install -f
```, and others which are available in may every forum in the world.
[*]Used synaptic but it says something like "unable to correct problems, you have held broken packages.", also Synaptic is not listing any package in "Broken" tab.
[*]When I try build-dep, for a particular package, it installs dependencies for that particular packages but removes many of the other packages, and then I need to install them either manually or reinstall the KDE again.
[*]Using aptitude also does this.
[/LIST]
Now, yesterday Ubuntu 15.10 was released, I thought upgrading the system might solve the problem, so today I upgraded the system to 15.10, update went fine, but problems are still there.

[LIST]
[*]Few minutes back I rebooted the system, and it got stuck at kubuntu splash screen, even shell wasn't opening.
[/LIST]
I changed the kernel to 3.19  and it booted. And here I am writing this post.

[LIST]
[*]When I try to boot with kernel 4.2, it hangs after splash screen, only black screen, and then I need to force shutdown to restart the machine with old kernel.
[/LIST]
Kindly tell me how to solve these problems. I don't want to reinstall the complete system as it not possible for some reasons. 
 
P.S. Sorry for long post and awful English, I tried to make it as concise as possible.


Thanks and Regards.

---

### Post by Bucky Ball on 2015-10-24
How did you upgrade to Kubuntu 15.04? Clean install or did you manage to upgrade to Ubuntu 14.10 then to 15.04 and added kubuntu-desktop? Not a great move either way as you have gone from a long-term support release, supported for five years until 2019 and upgradeable directly to the next LTS release, 16.04 LTS in April 2016 or anytime after that, to an interim release which is supported until January when you are going to need to upgrade to 15.10 anyway. 

First off, though, how did you upgrade and please post any errors you might get when you run these commands, one after the other.

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Use code tags for output if you post any here (see last link in my signature).

---

### Post by SeijiSensei on 2015-10-24
Check to make sure that the permissions on your home directory, particularly those for $HOME/.kde provide full access by your username. Mine look like this:
```

lrwxrwxrwx 1 seiji seiji   12 Feb 12  2015 tmp-linux-tv -> /tmp/kde-seiji
lrwxrwxrwx 1 seiji seiji   16 Feb 12  2015 socket-linux-tv -> /tmp/ksocket-seiji
lrwxrwxrwx 1 seiji seiji   21 Feb 12  2015 cache-linux-tv -> /var/tmp/kdecache-seiji
drwxr-xr-x 6 seiji seiji 4096 Feb 12  2015 share
drwxrwxr-x 2 seiji seiji 4096 Feb 12  2015 Autostart
seiji@linux-tv:~$ ls .kde/share -ltr
total 16
drwx------  3 seiji seiji 4096 Feb 12  2015 kde4
drwx------  2 seiji seiji 4096 Feb 12  2015 autostart
drwxr-xr-x 40 seiji seiji 4096 Oct 20 15:11 apps
drwx------  4 seiji seiji 4096 Oct 24 08:48 config

```
All the files below these directories are owned by seiji:seiji.

---

