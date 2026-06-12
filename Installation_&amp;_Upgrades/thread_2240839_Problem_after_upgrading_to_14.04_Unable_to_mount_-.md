---
title: "Problem after upgrading to 14.04: Unable to mount - Not authorized [SOLVED]"
date: 2014-08-22
forum: Installation &amp; Upgrades
---

### Post by elisa3 on 2014-08-22
Hello:
This is the first time I ever post on this forum. I have used ubuntu for 7 years, and everytime I've had a problem, I have browsed the web and I have been able to solve it thanks to the help given on forums to other users experiencing the same issues (I do not have technical knowledge on ubuntu). This time, I've spent hours reading forums and typing commands and nothing helps. I am exhausted.
Upgrading to 14.04 has proved itself a mistake. Many things won't work anymore. But the one which worries me right now is external media not automounting anymore. I know other people have had the same issue and I have carefully read their threads, but nothing helps!!

---

### Post by Bashing-om on 2014-08-22
elisa3; Hi (again)

1st things first. Let's get ya booting to a terminal:
as per your thread:
[http://ubuntuforums.org/showthread.php?t=2240849](http://ubuntuforums.org/showthread.php?t=2240849)

Can't do much
[INDENT][INDENT][INDENT]when you can't reach a terminal
[/INDENT][/INDENT][/INDENT]

---

### Post by elisa3 on 2014-08-22
The issue on the other thread was solved, thank you very much! Now I can use ubuntu normally. I still can't automount, though.

---

### Post by Bashing-om on 2014-08-22
elisa3; Ok ..
Moving right on along.

When you say "automount, what is your conception of that term ?
-mine is an added entry in the "/etc/fstab" file so the system mounts that file system at boot-
Yours maybe that it is to be mounted on-demand and from the file manager.

Presently we need to know what we are working with:
Post back the outputs -Between code tags, please -  of terminal commands:
```

sudo fdisk -lu
sudo parted -l
ls -l /dev/sd*
sudo blkid
cat /etc/fstab

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
And we see what is and where we go from there.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by elisa3 on 2014-08-22
I was feeling very anxious, so I asked for help on the #ubuntu IRC chat channel, and a smart fellow found the bug I had: [https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/1240336](https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/1240336)
I followed solution #19 and it worked, it solved all my issues
I am sorry for the inconveniences and thank you very much

---

### Post by Bashing-om on 2014-08-22
elisa3; Like this :

It is not an "inconvenience"; We are here to help, and your response may help another seeking your same solution.
You add to the sum total of knowledge.

make it known by ->
Marking your thread solved.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

