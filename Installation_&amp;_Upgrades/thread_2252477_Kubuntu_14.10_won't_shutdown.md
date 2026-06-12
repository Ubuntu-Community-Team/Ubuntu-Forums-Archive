---
title: "Kubuntu 14.10 won't shutdown"
date: 2014-11-12
forum: Installation &amp; Upgrades
---

### Post by geoaraujo on 2014-11-12
Hello. I'm plagued by a [very similar (perhaps the same?) shutdown issue]("http://ubuntuforums.org/showthread.php?t=2251843") and following the moderator's advice, I've created a new thread. After upgrading from Kubuntu 14.04 to Kubuntu 14.10, my computer won't shutdown anymore. It hangs at Kubuntu logo and pressing one of arrow keys shows the message "wait-for-state stop/waiting". I would appreciate any help. Thanks in advance.

---

### Post by clepsdyrae on 2014-11-15
See thread-in-progress here: [https://www.kubuntuforums.net/showthread.php?66742-Kubuntu-14-10-does-not-shutdown](https://www.kubuntuforums.net/showthread.php?66742-Kubuntu-14-10-does-not-shutdown)

(no solutions yet, afaik)

---

### Post by geoaraujo on 2014-11-24
> **clepsdyrae said:**
> See thread-in-progress here: [https://www.kubuntuforums.net/showthread.php?66742-Kubuntu-14-10-does-not-shutdown](https://www.kubuntuforums.net/showthread.php?66742-Kubuntu-14-10-does-not-shutdown)

(no solutions yet, afaik)


I've created a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1395805").

---

### Post by geoaraujo on 2014-11-26
I was really getting mad but now I can shutdown again and I'm very happy! :D
I've changed this line at /etc/default/grub to look like this: **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash init=/lib/systemd/systemd"**


PS: Just hope this won't bring me any side effects...

---

### Post by geoaraujo on 2014-12-15
After the kernel update to 3.16.0-28-generic, I've removed the modification to test and it appears that the problem was solved for me.

---

### Post by ahhyes on 2014-12-31
I had this issue too after a 14.04 -> 14.10 upgrade. I am running a custom kernel. I had to do two things:


Add **init=/lib/systemd/systemd** to the kernel params.


I did this and the system booted but I still could not shut down/reboot via the KDE launcher menu. Simply selecting Shutdown/Reboot did nothing.


Once I added a new symlink for mtab (as per [https://wiki.ubuntu.com/systemd](https://wiki.ubuntu.com/systemd)) the system worked and I can now reboot/shutdown normally. No idea why that would fix it. I was getting the warning below [FONT=Verdana]during boot until I made the change.[/FONT]


**/etc/mtab is not a symlink or not pointing to /proc/self/mounts. This is not supported anymore. Please make sure to replace this file by a symlink to avoid incorrect or misleading mount(8) output.**

---

### Post by ahhyes on 2015-01-09
Well, it was working.... There were a bunch of updates yesterday, notably to systemd. now I have the same problem again.... Tired of this. Going back to LTS since nobody seems to have a clue.

> **ahhyes said:**
> I had this issue too after a 14.04 -> 14.10 upgrade. I am running a custom kernel. I had to do two things:


Add **init=/lib/systemd/systemd** to the kernel params.


I did this and the system booted but I still could not shut down/reboot via the KDE launcher menu. Simply selecting Shutdown/Reboot did nothing.


Once I added a new symlink for mtab (as per [https://wiki.ubuntu.com/systemd](https://wiki.ubuntu.com/systemd)) the system worked and I can now reboot/shutdown normally. No idea why that would fix it. I was getting the warning below [FONT=Verdana]during boot until I made the change.[/FONT]


**/etc/mtab is not a symlink or not pointing to /proc/self/mounts. This is not supported anymore. Please make sure to replace this file by a symlink to avoid incorrect or misleading mount(8) output.**

---

