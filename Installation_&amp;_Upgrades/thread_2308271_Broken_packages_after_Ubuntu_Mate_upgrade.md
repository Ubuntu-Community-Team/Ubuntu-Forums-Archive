---
title: "Broken packages after Ubuntu Mate upgrade"
date: 2016-01-01
forum: Installation &amp; Upgrades
---

### Post by charliewarlie on 2016-01-01
I've upgraded my Ubuntu Mate to the latest installation recently. I've tried reinstalling spotify, and keep getting told I have broken packages. 

> charlie@Stormageddon:~$ sudo apt-get install spotify-client
[sudo] password for charlie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 spotify-client : Depends: libssl0.9.8 but it is not installable
                  Recommends: libavcodec53 but it is not installable or
                              libavcodec52 but it is not installable or
                              libavcodec-extra-53 but it is not installable or
                              libavcodec-extra-52 but it is not installable
                  Recommends: libavformat53 but it is not installable or
                              libavformat52 but it is not installable or
                              libavformat-extra-53 but it is not installable or
                              libavformat-extra-52 but it is not installable
E: Unable to correct problems, you have held broken packages.
charlie@Stormageddon:~$ 

I tried to install the package and got this:

> charlie@Stormageddon:~$ sudo apt-get install libssl0.9.8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libssl0.9.8 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'libssl0.9.8' has no installation candidate

I found a version of the package here [http://packages.ubuntu.com/vivid/libssl0.9.8](http://packages.ubuntu.com/vivid/libssl0.9.8) and have extracted it to the desktop, but I don't know what to do next. I'm still pretty new to using terminal to sort things. Any help or advice would be greatly appreciated!

---

### Post by ian-weisser on 2016-01-01
DO NOT install the package you downloaded to the desktop. You are unlikely to succeed. If you do succeed, it is unlikely to help.

The system is trying to warn you that you have created a *version conflict*. The conflict must be resolved through the package manager.

A version conflict occurs when two sources provide different versions of the same package, and parts of your system depends upon package version A while other parts depend upon package version B. You told the system to install both parts, which is why the first error message said "you have requested an impossible situation".

The most frequent cause of a version conflict is PPAs and other non-Ubuntu sources. Since spotify-client is not in the Ubuntu repositories, that seems a likely cause here.

What source are you getting spotify-client from?
Are you following instructions from somplace? If so, a link to those instructions would be most helpful.
Is this your first try? Have you previously tried to install spotify-client or similar software some other way and failed (and didn't clean up)?

---

### Post by charliewarlie on 2016-01-03
> **ian-weisser said:**
> 

What source are you getting spotify-client from?
Are you following instructions from somplace? If so, a link to those instructions would be most helpful.
Is this your first try? Have you previously tried to install spotify-client or similar software some other way and failed (and didn't clean up)?

I followed the instructions here to download spotify: [https://www.spotify.com/uk/download/linux/](https://www.spotify.com/uk/download/linux/)

> # 1. Add the Spotify repository signing key to be able to verify download packages
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys BBEBDCB318AD50EC6865090613B00F1FD2C19886

# 2. Add the Spotify repository
echo deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free | sudo tee /etc/apt/sources.list.d/spotify.list

# 3. Update list of available packages
sudo apt-get update

# 4. Install Spotify 
sudo apt-get install spotify-client

I've tried a few times and it always says this. I guess there may be stuff that didn't get cleaned up - I did rm -f spotify-client but that's all - is there something else I should try? I tried the 'fix broken packages' in Synaptic Package Manager, but that did nothing.

---

### Post by charliewarlie on 2016-01-03
Ok, I've figured out the problem - I'm running 15.10, and the stable version only supports up to 14.05. I used the instructions on this page and installed the test repository to get it to work: [http://ubuntuhandbook.org/index.php/2015/09/install-spotify-client-ubuntu-15-10/](http://ubuntuhandbook.org/index.php/2015/09/install-spotify-client-ubuntu-15-10/)

Thank you for your help!

---

