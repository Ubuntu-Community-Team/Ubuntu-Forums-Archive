---
title: "How to exclude or exclude a directory during tar restore"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by sofasurfer on 2008-08-05
A while back I backed up my system using 'tar cvpzf backup.tgz --exclude=/proc/* --exclude=/lost+found/* --exclude=/backup.tgz --exclude=/mnt/* --exclude=/sys/* --exclude=/media/* /'

Now that I have screwed up my system I reinstalled off the alternate cd and to restore to the way it used to be I used ' tar  xvpzf backup.tgz -C /'

After running the restore I rebooted and the Ubuntu progress bar just goes back and forth for about 10 minutes and then I get a message about busybox.

So I'm thinking that if I restore everything EXCEPT /boot, (since I have it installed from the new install, maybe I will get a working system. By the way, during restore, I did get all my desktop icons back. So I know I'm on the right track.

How can I exclude /boot from the restore? Also, what if I just want to restore one directory at a time? How do I change my command line to accomplish this?

---

### Post by prshah on 2008-08-05
> **sofasurfer said:**
> 
How can I exclude /boot from the restore? 

Just a guess```
tar  xvpzf backup.tgz -C / --exclude=/boot/*
```?

---

### Post by coffeecat on 2008-08-05
I have backed-up, cloned, restored Linux systems many times with tar, and I have **never** bothered excluding directories such as /proc, /sys (or excluding anything for that matter), and it has always worked*...

SO LONG AS YOU....

... check and edit /boot/grub/menu.lst and /etc/fstab **before** you boot into the restored installation because of Ubuntu's obsession with UUIDs. You can do that from a live CD or another distro on another partition if you are multi-booting. Also, why are you excluding /media and /mnt? If you need different mountpoints after restore, you could do that when you are editing /etc/fstab. If you exclude them from the original tar, you will end up with a system with no /mnt or /media.

Of course, this doesn't help you now, but just something to think about for the future.

* with the exception of Fedora - of course. :roll:

---

### Post by sofasurfer on 2008-08-05
>>I have backed-up, cloned, restored Linux systems many times >with tar, and I have never bothered excluding directories such >as /proc, /sys (or excluding anything for that matter), and it >has always worked*...

I do not know why, in the 'heliode how to backup' they say to exclude various directories. I just do as I'm told. However, I do need to "--exclude=/media/*" since that is my backup drive.

>SO LONG AS YOU....
>... check and edit /boot/grub/menu.lst and /etc/fstab before >you boot into the restored installation because of Ubuntu's >obsession with UUIDs. 
>You can do that from a live CD or another distro on another >>partition if you are multi-booting. Also, why .are you >excluding /media and /mnt?

What am I checking for?
I have changed my fstab file to use '/dev/***' instead of 'uuid'.

I was told that using this format, "exclude=//mnt/*" instead of "exclude=/mnt" will keep my directories intact on restoration.

>Of course, this doesn't help you now, but just something to >think about for the future.

---

### Post by sofasurfer on 2008-08-05
P.S.
My subject tilte 'How to exclude or exclude a directory during tar restore' has a typo!!!

I meant to ask not only how to exclude a file or directory but how to restore ONLY ONE file or directory. Thus, the title should read 'How to include or exclude a single directory during tar restore'.

Thank you for your attention and I appreciate the help which so far has been interesting and informative.

---

