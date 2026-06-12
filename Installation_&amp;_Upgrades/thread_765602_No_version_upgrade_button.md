---
title: "No version upgrade button"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by Amiret on 2008-04-24
I clicked fetch updates and the version upgrade doesn't appear like it says here: [https://help.ubuntu.com/community/HardyUpgrades/Kubuntu](https://help.ubuntu.com/community/HardyUpgrades/Kubuntu)

Image attached

---

### Post by Verstege on 2008-05-09
I've got the same problem. Did you solve it without editing sources.list and some sudo apt-get dist-upgrade commands ?

Thanks.

---

### Post by Verstege on 2008-06-10
Problem: Sitting behind a proxy you don't get the Version Upgrade Button.
For a short time you see a window which says that a copy from
 [http://changelogs.ubuntu.com/meta-realease](http://changelogs.ubuntu.com/meta-realease) to /tmp/kde-root/whaterver.tmp
is in progress. This copy fails !

Solution: The copy-process doesn't use any proxy-settings, because it runs as root (/tmp/kde-root show that!). 
1. Open a konsole
2. type "xhost + <enter>"
3. become root (type "sudo su - <enter> yoursecretpassword <enter>")
4. type "export DISPLAY=:0.0"
5. type kcontrol <enter>
6. go to Internet & Network, then  proxy and make your proxy-settings as you did as normal user
Following the Upgrade Instructions at least I got the Version Upgrade button.

[https://bugs.launchpad.net/update-manager/+bug/127263/comments/47](https://bugs.launchpad.net/update-manager/+bug/127263/comments/47)
should also be solved.

Cheers
B

---

### Post by xavierh on 2008-06-13
I'm also sittign behind a proxy, but not using kubuntu, is htere a way of doing this with the regular ubuntu version?

---

