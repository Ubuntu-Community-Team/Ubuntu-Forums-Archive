---
title: "Linux 4.2.0-30-generic hang after update"
date: 2016-02-24
forum: Installation &amp; Upgrades
---

### Post by technutz1701 on 2016-02-24
I installed a brand new install of 15.10 from ISO to a VMware Fusion install 8.1.0. No issues at all.

I ran Software Updater and installed the latest updates and now on reboot it hangs with _ .

I can boot into 15.10 using the Linux 4.2.0-16-generic just fine via GRUB. 

I checked VMware and there are no new updates. So I do not know where to proceed from here. I will use (16) till I can other troubleshoot further?

I am not sure if this is a Vmware issue or a (30) issue?

Thanks!

---

### Post by lauwers on 2016-02-24
I have the same problem, as are lots of others:

[http://askubuntu.com/questions/738083/ubuntu-14-04-4-lts-hangs-on-boot-after-latest-dist-upgrade-in-vmware](http://askubuntu.com/questions/738083/ubuntu-14-04-4-lts-hangs-on-boot-after-latest-dist-upgrade-in-vmware)
[http://ubuntuforums.org/showthread.php?t=2314723](http://ubuntuforums.org/showthread.php?t=2314723)

I'd love to know if a fix is in the works?

---

### Post by peter-j-oconnell on 2016-02-25
Yep same here in vmware workstation..very frustrating..had to reinstall, take a snapshot, now I wait for a solution :)

---

### Post by technutz1701 on 2016-02-25
Well it appears to be a legit bug. Per these posts things seem good up to (27), then breaks after that. It looks like a fix is underway.

Here are other threads:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1548587](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1548587)

[http://askubuntu.com/questions/738045/ubuntu-15-10-stucks-before-login-screen-on-vm-workstation](http://askubuntu.com/questions/738045/ubuntu-15-10-stucks-before-login-screen-on-vm-workstation)

---

