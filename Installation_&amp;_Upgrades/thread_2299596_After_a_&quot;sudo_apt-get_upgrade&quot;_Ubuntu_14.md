---
title: "After a &quot;sudo apt-get upgrade&quot; Ubuntu 14.04 doesn't boot and I just get an initramfs"
date: 2015-10-19
forum: Installation &amp; Upgrades
---

### Post by blau2 on 2015-10-19
Hi everyone,

First of all, thank you for reading this and giving my trouble a thought. I've been reading around a lot about this issue, but nothing has solved it so far. I summarize the situation following.

After executing "sudo apt-get upgrade" in Ubuntu 14.04 everything runs without major issues, but the next time I boot, Ubuntu doen't start and I just get an initramfs busybox prompt.

I have reinstalled several times, always with the same result once that I execute again the upgrade.

To try to solve the initramfs prompt, I have executed fsck, but the problem wasn't solved.

I have also burned a Live CD with Rescatux on it, amd I executed its tools for repairing installations; it didn't work either.

I've searched hard for a solution to this problem, but I'm surprised not to have found anything on this: the trouble is caused on a clean installation of Ubuntu 14.04, always after just executing the upgrade (which I assume is a pretty usual operation).

Thanks beforehand for your help.

Blau.

---

### Post by ian-weisser on 2015-10-20
Are any other OS installed on the same machine?
How old is the hard drive?

During boot, a few things happen in order.
1) The BIOS/EFI finds the correct (read-only) drive to boot from
2) The BIOS/EFI reads GRUB from the correct drive, which explains the correct partition and file to discover the kernel and initramfs.
3) The BIOS/EFI loads the kernel and initramfs into RAM, and (effectively) turns control over to the bootstrap 'init' program in initramfs.
4) Bootstrap Init unmounts all (read-only) drives, creates the filesystem, remounts all drives read-write, and turns control over to the real /sbin/init.
5) /sbin/init begins probing hardware and starting the system we know.

Usually, a busybox prompt means that steps 1-3 were successful, but something in step 4 has failed. It may be unrelated to fsck or anything boot-repair can fix.
For example, a different OS on the same system may have overwritten /sbin/init. Or The hard rive may be failing. Or many other possible causes.
Are there any error messages?

---

### Post by efflandt on 2015-10-20
Of course you should first do "sudo apt-get update" to make sure that you have most recent package lists.

Also note that "sudo apt-get upgrade" may skip packages if they involve installing something that you do not already have a version of on your computer. So it may skip packages that have changing dependencies which may break other packages. So I am wondering if you would have better results trying "sudo apt-get dist-upgrade" which is smarter about installing any necessary changing dependencies.

Read **man apt-get** in a terminal to see the difference between **upgrade** and **dist-upgrade** (which contrary to what you might think, does NOT automatically upgrade to a newer Ubuntu version).

---

### Post by blau2 on 2015-11-21
Hi guys, 

Thank you both for your responses, and sorry for the late answer, but I just haven't got much time left for my techie issues. 

I'm sorry to say that I tried the dist-upgrade and unluckily the problem persists. 

Anyway, I have some more information that I hope will help you to lend me a hand:
1) during the dist-upgrade process I get the following message several times: "Update initramfs: deferring update (trigger activated)" 
2) after completing the dist-upgrade process, the next time I start Ubuntu up, I get again the Initramfs prompt after the following message: "No caching mode page found. Assuming drive cache: write through" 

Let's see if we can solve this issue that doesn't let me to keep my Ubuntu up and running. Thanks beforehand for your help. 

Regards, 

Blau.

---

### Post by Bucky Ball on 2015-11-21
Welcome. Maybe you missed this. ALWAYS run 'sudo apt-get update' first. Thus:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

In that order.

---

### Post by kansasnoob on 2015-11-21
I've only seen that if installing to a USB drive. For some general info read:

[http://askubuntu.com/questions/167343/what-is-a-asking-for-cache-data-failed-warning](http://askubuntu.com/questions/167343/what-is-a-asking-for-cache-data-failed-warning)

I see that others have encountered that using an SSD and indicate that this is a workaround:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/925760/comments/70](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/925760/comments/70)

But this is all just general info. Your mileage will vary depending on the specific installation type and hardware.

---

### Post by blau2 on 2015-11-21
Yes, that's exactly what I've done, and the problem persists. I just can't understand how such a standard OS maintenance operation can be such a headache. Any other clue, guys? Thx.

---

### Post by blau2 on 2015-11-21
Sorry Kansasnoob, in my previous answer I was answering to Bucky Ball. You've hit the nail on the head: I'm working on a live USB installation. Sorry for missing this detail, but I didn't think this made a difference. I'm going to have a look at your links and come back to you later on with the result. Thx.

---

### Post by Bucky Ball on 2015-11-21
A Live USB or you've installed Ubuntu to a USB using persistence? If the former, no point updating as all will be lost on reboot.

---

### Post by blau2 on 2016-01-09
Yes, the problem arises on an USB pendrive with persistence. Does this configuration involve specific troubles which don't apply to a standard installation? Any solution? Thx.

---

