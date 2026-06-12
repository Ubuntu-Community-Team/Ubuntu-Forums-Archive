---
title: "do-dist-upgrade broke my machine because of libgpg error"
date: 2018-06-21
forum: Installation &amp; Upgrades
---

### Post by vob2 on 2018-06-21
Hello,

Before you read this let me point out that I have already repaired my system. I place this here in lieu of a bug-report as I am not sure if and where to report it. I had trouble for example with my mountpoints, because /var is on a different drive. (I wanted to spare my ssd constant writing to /var). I also had other issued with 17.10 today just before upgrading, and although I think they are unrelated, I am not sure a bug report would do any good. I place this here in case someone else gets/has this problem.

I had just finished repairing my kernel from my old 17.10 build (something to do with the nvidia drivers, I have had earler issues with those), when I decided to upgrade to 18.04 from the command line. When I did, it crashed somewhere reporting that it could not find libgpg-error in some libgpg library. It was called a relocation error(whatever that is). After it crashed many programs failed to run, including firefox, reporting the same error(gnome terminal was used to start the programs). After reboot, only one kernel was still working, and not even in recovery mode, but in some sort of initramfs mode.

Trying to fix the initramfs files resulted in even worse problems. (Apparently update-initramfs still worked, but it broke even more) I used a boot-repair usb drive from which I went to chroot, with a couple of extra mount commands beforehand and editing mtab after, in order to try to repair the system. It turned out that after some messing with apt, that /usr/local/lib contained another older version of libgpg. Moving that to a backup folder resolved the problems, after which I could start repairing the damage I did (I messed somewhat with apt remove because one package could not be fixed.). I had to reinstall kernel drivers manually from an usb drive to get internet working. After which I am running updates and trying to check if my desktop got any other problems from this issue. (I already noticed my two monitor setup stopped working with both monitors, but that might be the nvidia driver.)

In short, one outdated crypto lib in /usr/local/lib pulled my entire system down. (My system is not encrypted btw, so it should not be needed to decrypt file systems.) Because of the severity of the problem, and to document it for any future victims, I decided to post it here.

---

### Post by oldos2er on 2018-06-22
See [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

