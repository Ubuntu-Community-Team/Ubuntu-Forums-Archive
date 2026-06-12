---
title: "Failed update/upgrade"
date: 2024-09-02
forum: Installation &amp; Upgrades
---

### Post by versss on 2024-09-02
Hello, I did a mistake trying to update to latest Ubuntu release. I was on 22.04 and tried to update to latest Ubuntu release after I received the notification about possible update. Update went through only partly, then problems started. 

I tried finishing the update/upgrade, did full-upgrade and also dist-upgrade. 
Was using ChatGPT to help me out navigate out of the mess I put myself into. Gave up and went to bed with my desktop up and running. Woke up to system booting only to terminal.  
Right now I’m in dead spot. I don’t know what to do next and also ChatGPT sucks. 

Outcome of —fix-broken install and —reinstall Ubuntu-desktop:

```
```
g g@gworkstation:~$ sudo apt --fix-broken install

A Reading package lists... Done a Building dependency tree... Done A Reading state information... Done
o 0 to upgrade, o to newly install, 0 to remove and 5 not to upgrade. 

g g@gworkstation: ^$ sudo apt-get install --reinstall ubuntu-desktop i 

Reading package lists... Done a Building dependency tree... Done &#1071; Reading state information... Done
2 Some packages could not be installed. This may mean that you have
1 requested an impossible situation or if you are using the unstable b distribution that some required packages have not yet been created o or been moved out of Incoming.
T The following information may help to resolve the situation:
I The following packages have unmet dependencies.
1ibpipewire-0.3-0t64 : Depends: 1ibspa-0.2-modules (= 1.0.5-1ubuntu1) but 1.0.7-3 ubuntu22.04 is to be installed
3E: Unable to correct problems, you have held broken packages. 

g gagworkstation: "$ sudo apt-get install --reinstall ubuntu-desktop

A Reading package lists... Done a Building dependency tree... Done
• Reading state information... Done
Some packages could not be installed. This may mean that you have 1 requested an impossible situation or if you are using the unstable b distribution that some required packages have not yet been created oor been moved out of Incoming.
The following information may help to resolve the situation:
T The following packages have unmet dependencies.
libpipewire-0.3-0t64 : Depends: 1ibspa-0.2-modules (= 1.0.5-1ubuntu1) but 1.0.7-3 ubuntu22.04 is to be installed
3E: Unable to correct problems, you have held broken packages.
```

Outcome of sudo apt-get updated:

```
g@gworkstation:^$ sudo apt-get update Ign: 1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble InRelease Ign:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble-updates InRelease Ign:3 [https://brave-browser-apt-release.s3.brave.com](https://brave-browser-apt-release.s3.brave.com) stable InRelease Ign:4 [https://repository.mullvad.net/deb/stable](https://repository.mullvad.net/deb/stable) jammy InRelease Ign:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble-backports InRelease Ign:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble-security InRelease Ign: 1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble InRelease Ign:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble-updates InRelease Ign:3 [https://brave-browser-apt-release.s3.brave.com](https://brave-browser-apt-release.s3.brave.com) stable InRelease Ign:4 [https://repository.mullvad.net/deb/stable](https://repository.mullvad.net/deb/stable) jammy InRelease Ign:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble-backports InRelease Ign:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble-security InRelease Ign: 1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble InRelease Ign:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble-updates InRelease Ign:3 [https://brave-browser-apt-release.s3.brave.com](https://brave-browser-apt-release.s3.brave.com) stable InRelease Ign:4 [https://repository.mullvad.net/deb/stable](https://repository.mullvad.net/deb/stable) jammy InRelease Ign:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble-backports InRelease Ign:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble-security InRelease
3 Err:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble InRelease
Temporary failure resolving
*archive.ubuntu.com'
3 Err:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble-updates InRelease
Temporary failure resolving
"archive.ubuntu.com"
1 Err:3 [https://brave-browser-apt-release.s3.brave.com](https://brave-browser-apt-release.s3.brave.com) stable InRelease
Temporary failure resolving
*brave-browser-apt-release.s3.brave.com'
3 Err:4 [https://repository.mullvad.net/deb/stable](https://repository.mullvad.net/deb/stable) jammy
InRelease
Temporary failure resolving
*repository.mullvad.net'
3 Err:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble-backports InRelease
Temporary failure resolving *archive.ubuntu.com"
3 Err:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble-security InRelease
Temporary failure resolving
*archive.ubuntu.com'
A Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/noble/InRelease](http://archive.ubuntu.com/ubuntu/dists/noble/InRelease)
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/noble-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/noble-updates/InRelease)
Release temporary rallure resolvive aunteubuntu. com
Temporary tallure resolving
W:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/noble-backports/InRelease](http://archive.ubuntu.com/ubuntu/dists/noble-backports/InRelease)
*archive.ubuntu.com*
W:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/noble-security/InRelease](http://archive.ubuntu.com/ubuntu/dists/noble-security/InRelease)
Temporary failure resolving
W: Failed to fetch [https://brave-browser-apt-release.s3.brave.com/dists/stable/InRelease](https://brave-browser-apt-release.s3.brave.com/dists/stable/InRelease)
Temporary failure resolving
W: Failed to fetch [https://repository.mullvad.net/deb/stable/dists/](https://repository.mullvad.net/deb/stable/dists/) jammy/InRelease
Temporary failure resolving repository.mullvad.net"
*brave-browser -apt-release.s3.brave.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.
```
```

I reached the end of possible solutions I could come up on my own. Tried booting to grub recovery mode, shift does nothing, when I repeatedly press ESC I access grub command line. No gui or anything, so I didn’t proceed with worry I could mess up further. I would be thankful for any possible advice what to do next here in order to avoid losing access to files I have on my desktop.

---

