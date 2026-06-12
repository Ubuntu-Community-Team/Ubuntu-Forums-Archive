---
title: "Upgrade error BusyBox wont boot"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by egregory on 2008-11-01
Guys,

Need your help, my upgrade has gone very very wrong, and i think i am on the verge of a meltdown!!

while trying to upgrade 8.04 to 8.10 (Ubuntu Gnome) everyhig went well until cleaning up stage where it asked me to remove just over 600 applications, at first i thought this was rather strange, however i did a quick scan on upgrade guides and all of which reccommended that i followed on with REMOVE so i removed and clicked restart.

After that my compter has gone tits up and it wont boot - i have an error message saying:

BusyBox V.1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in Shell (ash)
Ente "help" for a list of built-in commands
(initramfs)_

After i typed help none of the commands or options work i am stuck!

what the hell is all this mambo-jumbo?

please somebody help me!! I am scared i may have completely removed my hard drive and have lost all my data!!

Help Help Help!!

---

### Post by steveydoteu on 2008-11-01
Your data is there, someplace. It would not even get as far as it had without anything on the disk.

What does it actually tell you if you enter help.

---

### Post by egregory on 2008-11-01
Hi there, thanks for a quick reply!

well it gives me the full list of buil in commands

.: alias break cd chdir comman continue echo eval exec exit export false getopts hash help let local pwd read readonly return set shift times trap true type ulimit umask unalias unset wait [ [[ ash awk basename busybox cat chmod chroot chvt celar cmp cp cut deallcovt dumpkmap echo egrep env expr gfalse fbset fdflush fgrep grep hostname ifconfig ip kill in loadfont loadkmap is mkdir mkfifo mknod mkswap mktemp more mount mv openvt pidof printf ps pwd readlink rset rm rmfir sed setkeycodes sh sleep sort stat sync tail tee test touch tr tue tty umount uname uniq wget

jesus that was painful, so after i typed the logical commands, i.e. exit, nothing happens!!

---

### Post by steveydoteu on 2008-11-01
Having had a dig around try this:

Boot into a LiveCD and mount your root filesystem:

```
mkdir ~/Desktop/harddrive
sudo mount -rw /dev/hda1 ~/Desktop/harddrive

```This is presuming your drive is located at hda1. Failing that you can unmout using

```
 unmount /dev/hda1
```And repeat the above with different combinations. Another to try would be /dev/sda.

Once you have managed to mount your root to the desktop of the live environment:

```
sudo chroot ~/Desktop/harddrive
sudo aptitude reinstall ubuntu-minimal
```

Then see what happens when you try to boot your system this time.

---

### Post by ramitsingal on 2009-03-23
> **egregory said:**
> Hi there, thanks for a quick reply!

well it gives me the full list of buil in commands

.: alias break cd chdir comman continue echo eval exec exit export false getopts hash help let local pwd read readonly return set shift times trap true type ulimit umask unalias unset wait [ [[ ash awk basename busybox cat chmod chroot chvt celar cmp cp cut deallcovt dumpkmap echo egrep env expr gfalse fbset fdflush fgrep grep hostname ifconfig ip kill in loadfont loadkmap is mkdir mkfifo mknod mkswap mktemp more mount mv openvt pidof printf ps pwd readlink rset rm rmfir sed setkeycodes sh sleep sort stat sync tail tee test touch tr tue tty umount uname uniq wget

jesus that was painful, so after i typed the logical commands, i.e. exit, nothing happens!!


Did you say nothing happens? I'm stuck with the same problem, and this is what I get when I type exit:

(initramfs) exit

cp: cannot create '/root/var/log/' : No such file or directory
mount: mounting root/dev on /dev/.static/dev failed : No such file or directory
mount: mounting /sys on /root/sys failed : No such file or directory
mount: mounting /proc on /root/proc failed : No such file or directory
Target filesystem doesn't have /sbin/init
No init found. Try passing init=bootary

***

And then it starts over again.

---

### Post by egregory on 2009-03-25
Hi,

I am sorry to hear that you are having the same problem, unfortunately i could not fix my problem, nor was i able to find any valuable info on the web to help with my troubles, so the only thing that i did was to delete my ubuntu OS and reinstall it, i.e. deleted the partition from wndows and did the whole thing over again thereby losing all my data. Sorry I cant help you. good luck. p.s. since then i decided to part ways with both Linux and Microsoft!, and bought myself  a mac!

---

