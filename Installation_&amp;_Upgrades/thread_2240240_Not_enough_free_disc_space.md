---
title: "Not enough free disc space"
date: 2014-08-18
forum: Installation &amp; Upgrades
---

### Post by laurietruluck on 2014-08-18
Hello!

I know this has been asked before quite often, but I'm quite new to Ubuntu and I always find it confusing trying to find solutions by looking at other threads.
I get this message when trying to udpate software: The upgrade needs a total of 81.4 M free space on disk '/boot'. Please free at least an additional 13.6 M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'
Please can someone explain how I can resolve this?

Many thanks,
Laurie

---

### Post by Bashing-om on 2014-08-18
laurietruluck; Hi ! Welcome to the forum.

The method of the 'fix' has changed in recent releases.
Now that begs the question, what release are you running ?
post back the out puts -Between Code Tags - of terminal commands:
```

lsb_release -a
uname -r
df -h
df -i

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

 And that tells us the release, and kernel you are running, and where the space is being consumed.

Once these are known, we can get detailed for the resolution.

[INDENT][INDENT]where there are solutions
[INDENT][INDENT][INDENT]there are no problems
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by laurietruluck on 2014-08-19
Hi Bashing-om

Thanks for your help. Here are the out-puts:

```
laurie@laurie-Vaio:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty
```

```
laurie@laurie-Vaio:~$ uname -r
3.13.0-30-generic
```

```
laurie@laurie-Vaio:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  455G   28G  404G   7% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         1.9G  4.0K  1.9G   1% /dev
tmpfs                        381M  1.2M  380M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         1.9G  512K  1.9G   1% /run/shm
none                         100M   40K  100M   1% /run/user
/dev/sda1                    236M  159M   65M  72% /boot
```

```
laurie@laurie-Vaio:~$ df -i
Filesystem                    Inodes  IUsed    IFree IUse% Mounted on
/dev/mapper/ubuntu--vg-root 30253056 297769 29955287    1% /
none                          487584      2   487582    1% /sys/fs/cgroup
udev                          483670    507   483163    1% /dev
tmpfs                         487584    536   487048    1% /run
none                          487584      4   487580    1% /run/lock
none                          487584     10   487574    1% /run/shm
none                          487584     26   487558    1% /run/user
/dev/sda1                      62248    316    61932    1% /boot
```


Thanks,
Laurie

---

### Post by ibjsb4 on 2014-08-19
Try this

Enter these commands one line at a time:

```
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get dist-upgrade
```

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by varunendra on 2014-08-19
ibjsb4,

Those commands will only free space on their root partition, while the /boot, where the cleanup is required, is clearly on a separate partition of 236 MB size -
> **laurietruluck said:**
> ```
laurie@laurie-Vaio:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  455G   28G  404G   7% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         1.9G  4.0K  1.9G   1% /dev
tmpfs                        381M  1.2M  380M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         1.9G  512K  1.9G   1% /run/shm
none                         100M   40K  100M   1% /run/user
[COLOR="#0000FF"]**/dev/sda1                    236M  159M   65M  72% /boot**[/COLOR]
```

I believe we need to see which other kernels are installed so we can be specific on what needs to be removed and how.


**@Laurie,**

Please also post the output of -
```
dpkg -l | egrep 'linux-(image|headers)'
```
You can copy-paste the above command from here to the terminal to avoid typo.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by ibjsb4 on 2014-08-19
Oops, didn't catch the partition.  :)

---

### Post by laurietruluck on 2014-08-19
```

laurie@laurie-Vaio:~$ dpkg -l | egrep 'linux-(image|headers)'
ii  linux-headers-3.13.0-24                               3.13.0-24.47                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                       3.13.0-24.47                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-27                               3.13.0-27.50                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-27-generic                       3.13.0-27.50                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-29                               3.13.0-29.53                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-29-generic                       3.13.0-29.53                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-30                               3.13.0-30.55                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-30-generic                       3.13.0-30.55                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.30.36                                        amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-24-generic                         3.13.0-24.47                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-27-generic                         3.13.0-27.50                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-29-generic                         3.13.0-29.53                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-30-generic                         3.13.0-30.55                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-27-generic                   3.13.0-27.50                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-29-generic                   3.13.0-29.53                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-30-generic                   3.13.0-30.55                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                   3.13.0.30.36                                        amd64        Generic Linux kernel image

```

---

### Post by coffeecat on 2014-08-19
@laurietruluck, I won't interfere with excellent the help you are getting in removing unwanted kernels, but please would you do something for the community? You installed Ubuntu specifying a whole disc LVM installation either with or without encryption. That is why the installer set up a separate /boot partition. Unfortunately, the default and only size for the boot partition is a little under 256MB, which is far too small. Please mark this bug as affecting you:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)

You need a launchpad account which is easy to set up. Once you have logged into LP, you can click the link to say it affects you, which will help raise the heat on the bug and hopefully lead to serious attention. Please don't post any comment on the bug thread unless you really need to - let's try to keep this bug free of unnecessary background noise.

@everyone helping: please bookmark this bug and get others you help who are in the same situation marking it as affecting them too. Thanks.

---

### Post by laurietruluck on 2014-08-19
@coffeecat -  I've now done what you've advised, thanks for your help.

---

### Post by kansasnoob on 2014-08-19
> **coffeecat said:**
> @laurietruluck, I won't interfere with excellent the help you are getting in removing unwanted kernels, but please would you do something for the community? You installed Ubuntu specifying a whole disc LVM installation either with or without encryption. That is why the installer set up a separate /boot partition. Unfortunately, the default and only size for the boot partition is a little under 256MB, which is far too small. Please mark this bug as affecting you:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)

You need a launchpad account which is easy to set up. Once you have logged into LP, you can click the link to say it affects you, which will help raise the heat on the bug and hopefully lead to serious attention. Please don't post any comment on the bug thread unless you really need to - let's try to keep this bug free of unnecessary background noise.

@everyone helping: please bookmark this bug and get others you help who are in the same situation marking it as affecting them too. Thanks.

I "me too'ed" that also, and subscribed. That's a ridiculous design flaw :(

At best a default LVM/encrypted install would be good for maybe three kernel updates ................ what were they thinking?

---

### Post by varunendra on 2014-08-19
> **coffeecat said:**
> @everyone helping: please bookmark this bug and get others you help who are in the same situation marking it as affecting them too. Thanks.

Done! Thanks for the pointer coffeecat. I was just about to ask the OP - "Why did you choose such a small size for /boot?". Thankfully, you posted above before I could successfully confuse them :p


**@Laurie,**

Please run the following command to get rid of some older kernels (copy-paste it to avoid typo) -
```
sudo apt-get purge linux-{headers,image}-3.13.0-{24,27}-generic linux-headers-3.13.0-{24,27} linux-image-extra-3.13.0-{24,27}-generic
```
If you get any error, please report back what it is. Although there should be none.

I am leaving one older kernel (3.13.0-29) which is always recommended. You are almost certainly going to receive another kernel upgrade during the update you were originally trying. If that works fine after a reboot, you can also purge (remove) the older kernel (...29) to claim the space it occupies.

It is recommended to keep at least one older kernel so that you can get a working system in case some problem occurs with the currently running one.

---

### Post by laurietruluck on 2014-08-19
Seems to be sorted now. Thanks all for your help.
 
 Is there a way to prevent this is in the future without continually having to delete old kernels?

---

### Post by varunendra on 2014-08-19
Kernel upgrade is a continuous and recommended process, and deleting older kernels is NOT part of that process for some valid reasons. It has to be done manually, although there are nice GUI tools like "Ubuntu Tweak" to do that easily. You may search on how to install it on Ubuntu.

The best solution is to make the /boot partition large enough (2-3 GB) so that you don't have to worry for a couple of years or more! But as per the bug coffeecat linked to - that was not your choice at all. And I am not sure how easy (or difficult) resizing partitions on LVM disks is.

If you need help with installing Ubuntu Tweak or resizing partitions, please start a different thread with a suitable title, and in a suitable section (could be "General Help"). You should mark this one as [SOLVED] now, using "Thread Tools" link above the top post.

---

