---
title: "Not enough free space on boot for update"
date: 2017-03-10
forum: Installation &amp; Upgrades
---

### Post by Coriander Redgoat on 2017-03-10
I'm on 16.04. Whenever I try to update recently I get:

"The upgrade needs a total of 95.8 M free space on disk '/boot'. Please free at least an additional 29.7 M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."

I used to fix it with 

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' && sudo apt-get autoremove
```

but this is no longer working, or rather it is not longer sufficient.

I only have 246mb on '/boot' which strikes me as not a lot.

Can anyone help? Suggestions?

Thanks!

---

### Post by QIII on 2017-03-10
Hello!

Did you try what the warning message suggested?

You may also try

```
sudo apt autoremove
```

---

### Post by Impavidus on 2017-03-10
Maybe that long command should do the trick. The expressions are to complicated to verify quickly. But simply```
sudo apt autoremove
```should do it. Try it.

But that command (actually a variant of it) was already at the end of your big oneliner. Let's see what old packages you have installed:```
dpkg --list | grep 'linux-image*'
```

---

### Post by Coriander Redgoat on 2017-03-12
Running ```
dpkg --list | grep 'linux-image*'
```

gave

```
rc  linux-image-4.2.0-16-generic                                4.2.0-16.19                                   amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-23-generic                                4.2.0-23.28                                   amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-25-generic                                4.2.0-25.30                                   amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-27-generic                                4.2.0-27.32                                   amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-30-generic                                4.2.0-30.36                                   amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-35-generic                                4.2.0-35.40                                   amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-21-generic                                4.4.0-21.37                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-22-generic                                4.4.0-22.40                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-24-generic                                4.4.0-24.43                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-28-generic                                4.4.0-28.47                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-31-generic                                4.4.0-31.50                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-34-generic                                4.4.0-34.53                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-36-generic                                4.4.0-36.55                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-38-generic                                4.4.0-38.57                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-42-generic                                4.4.0-42.62                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-45-generic                                4.4.0-45.66                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-47-generic                                4.4.0-47.68                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-51-generic                                4.4.0-51.72                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-53-generic                                4.4.0-53.74                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-57-generic                                4.4.0-57.78                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-59-generic                                4.4.0-59.80                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-62-generic                                4.4.0-62.83                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-63-generic                                4.4.0-63.84                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-64-generic                                4.4.0-64.85                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-16-generic                          4.2.0-16.19                                   amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-23-generic                          4.2.0-23.28                                   amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-25-generic                          4.2.0-25.30                                   amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-27-generic                          4.2.0-27.32                                   amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-30-generic                          4.2.0-30.36                                   amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-35-generic                          4.2.0-35.40                                   amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-21-generic                          4.4.0-21.37                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-22-generic                          4.4.0-22.40                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-24-generic                          4.4.0-24.43                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-28-generic                          4.4.0-28.47                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-31-generic                          4.4.0-31.50                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-34-generic                          4.4.0-34.53                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-36-generic                          4.4.0-36.55                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-38-generic                          4.4.0-38.57                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-42-generic                          4.4.0-42.62                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-45-generic                          4.4.0-45.66                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-47-generic                          4.4.0-47.68                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-51-generic                          4.4.0-51.72                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-53-generic                          4.4.0-53.74                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-57-generic                          4.4.0-57.78                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-59-generic                          4.4.0-59.80                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-62-generic                          4.4.0-62.83                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-63-generic                          4.4.0-63.84                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-64-generic                          4.4.0-64.85                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic  

```

Seems like a lot I don't need

---

### Post by Bashing-om on 2017-03-12
Coriander Redgoat; Hello;

We can clean up and gain just a bit more space. The packages marked 'rc' where the 'rc' is (R)emoved but (C)onfig files remain .
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package with the following command.
```

dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P

```
Now what shows :
```

df -h
dpkg -l | grep linux-

```

//
> 
I only have 246mb on '/boot' which strikes me as not a lot.

True ! see:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by Coriander Redgoat on 2017-03-12
Boot still lacks space:

```
df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         1.9G     0  1.9G   0% /dev
tmpfs                        385M   40M  345M  11% /run
/dev/mapper/ubuntu--vg-root  436G  246G  169G  60% /
tmpfs                        1.9G  295M  1.6G  16% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        1.9G     0  1.9G   0% /sys/fs/cgroup
**/dev/sda1                    236M  161M   63M  72% /boot**
cgmfs                        100K     0  100K   0% /run/cgmanager/fs
tmpfs                        385M  120K  385M   1% /run/user/1000
/home/coriander/.Private     436G  246G  169G  60% /home/coriander
/dev/sdb1                    932G  447G  486G  48% /media/coriander/Seagate Expansion Drive

```

```
dpkg -l | grep linux-
ii  linux-base                                                  4.0ubuntu1                                    all          Linux image base package
ii  linux-firmware                                              1.157.8                                       all          Firmware for Linux kernel drivers
ii  linux-generic                                               4.4.0.64.68                                   amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-62                                      4.4.0-62.83                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-62-generic                              4.4.0-62.83                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-63                                      4.4.0-63.84                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-63-generic                              4.4.0-63.84                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-64                                      4.4.0-64.85                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-64-generic                              4.4.0-64.85                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       4.4.0.64.68                                   amd64        Generic Linux kernel headers
ii  linux-image-4.4.0-62-generic                                4.4.0-62.83                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-63-generic                                4.4.0-63.84                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-64-generic                                4.4.0-64.85                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-62-generic                          4.4.0-62.83                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-63-generic                          4.4.0-63.84                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-64-generic                          4.4.0-64.85                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                                         4.4.0.64.68                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        4.4.0-64.85                                   amd64        Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu5                          all          base package for ALSA and OSS sound systems
ii  linux-tools-4.4.0-62                                        4.4.0-62.83                                   amd64        Linux kernel version specific tools for version 4.4.0-62
ii  linux-tools-4.4.0-62-generic                                4.4.0-62.83                                   amd64        Linux kernel version specific tools for version 4.4.0-62
ii  linux-tools-4.4.0-63                                        4.4.0-63.84                                   amd64        Linux kernel version specific tools for version 4.4.0-63
ii  linux-tools-4.4.0-63-generic                                4.4.0-63.84                                   amd64        Linux kernel version specific tools for version 4.4.0-63
ii  linux-tools-4.4.0-64                                        4.4.0-64.85                                   amd64        Linux kernel version specific tools for version 4.4.0-64
ii  linux-tools-4.4.0-64-generic                                4.4.0-64.85                                   amd64        Linux kernel version specific tools for version 4.4.0-64
ii  linux-tools-common                                          4.4.0-64.85                                   all          Linux kernel version specific tools for version 4.4.0
ii  linux-tools-virtual                                         4.4.0.64.68                                   amd64        This package will always depend on the latest minimal generic kernel tools.
ii  syslinux-common                                             3:6.03+dfsg-11ubuntu1                         all          collection of bootloaders (common)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu8                          amd64        Bootloader for Linux/i386 using MS-DOS floppies



```

---

### Post by Bashing-om on 2017-03-12
Coriander Redgoat; Well ..

Better .. but not good 'nuf .

Still with an that extra -62 kernel installed.
What now:
```

sudo apt autoremove

```

Looks as if autoremove should run . else --- well I guess we manually intervene .
Short of a risky re-sizing of partitions I have no ready solution . Get the installed kernels down to the minimum 2 and keep it there when a new kernel is installed , is in my opinion, the better option .

[INDENT][INDENT]there is a way
[/INDENT][/INDENT]

---

### Post by Coriander Redgoat on 2017-03-12
```
sudo apt autoremoveReading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

```

How do I get my kernels down to 2 safely?

---

### Post by Bashing-om on 2017-03-12
Coriander Redgoat; Well ....

> 
How do I get my kernels down to 2 safely? 

for starters show what kernel you are booting currently:
```

uname -r

```

And if not that -62 kernel we remove it with apt . THEN get this system fully updated .

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by Coriander Redgoat on 2017-03-12
```
uname -r
4.4.0-64-generic

```

---

### Post by Bashing-om on 2017-03-12
Coriander Redgoat; Ho Kay !

Let's run:
```

sudo apt purge linux-{headers,image}-4.4.0-62-generic linux-headers-4.4.0-62 linux-image-extra-4.4.0-62-generic

```
If that runs clean and proper:
update the system:
```

sudo apt update
sudo apt full-upgrade
sudo apt -f install

```

[INDENT][INDENT]done all we can do ?
[/INDENT][/INDENT]

---

### Post by deadflowr on 2017-03-12
Try this one-liner:
```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | xargs sudo apt-get --dry-run remove
```
this runs a simulation of what would happen, and if it properly lists all kernels except the -64 kernel and all else looks good, run it again properly with
```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | xargs sudo apt-get purge -y
```
the run the updater to get the newest kernel -66.

The original command you posted seems like all it did was print a bunch of kernels and then ran a completely different command with the autoremove, inconsequential to the listed kernels.
fwiw

---

### Post by Coriander Redgoat on 2017-03-12
```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | xargs sudo apt-get --dry-run remove[sudo] password for coriander: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-4.4.0-62 linux-headers-4.4.0-62-generic linux-headers-4.4.0-63 linux-headers-4.4.0-63-generic linux-image-4.4.0-62-generic
  linux-image-4.4.0-63-generic linux-image-extra-4.4.0-62-generic linux-image-extra-4.4.0-63-generic
0 upgraded, 0 newly installed, 8 to remove and 4 not upgraded.
Remv linux-headers-4.4.0-62-generic [4.4.0-62.83]
Remv linux-headers-4.4.0-62 [4.4.0-62.83]
Remv linux-headers-4.4.0-63-generic [4.4.0-63.84]
Remv linux-headers-4.4.0-63 [4.4.0-63.84]
Remv linux-image-extra-4.4.0-62-generic [4.4.0-62.83]
Remv linux-image-4.4.0-62-generic [4.4.0-62.83]
Remv linux-image-extra-4.4.0-63-generic [4.4.0-63.84]
Remv linux-image-4.4.0-63-generic [4.4.0-63.84]



```

This looks good. Just wanted to post it for a sanity check before I run the next command from above.

---

### Post by Bashing-om on 2017-03-12
Coriander Redgoat; Well ..

That removes the backup kernel -63 also . Maybe fine IF on the updates the -66 kernel is installed . - will save a step -
Be interesting to "see" what happens .

Do you feel lucky ?


[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by deadflowr on 2017-03-12
Looks good.
You can add additional pipe(s) to exclude more kernels, but my thinking was that since the purpose of this thread was to clean out enough space to run the updater, you're gonna get the newer kernel anyway, which would provide a secondary kernel to boot, in this case the current kernel.
If that makes sense.

---

### Post by Coriander Redgoat on 2017-03-12
I don't feel lucky, or rather, I'm risk averse :)

What command will leave me with a backup?

Thanks!

---

### Post by deadflowr on 2017-03-12
> **Coriander Redgoat said:**
> I don't feel lucky, or rather, I'm risk averse :)

What command will leave me with a backup?

Thanks!

Not sure why, but simply add another pipe like grep -v -e -4.4.0-63
```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" **| grep -v -e -4.4.0-63** | xargs sudo apt-get --dry-run remove
```
you should now see that the -63 version is excluded from the removal list.

---

### Post by Coriander Redgoat on 2017-03-12
Ran ```
[COLOR=#000000][FONT=&quot]dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | xargs sudo apt-get purge -y[/FONT][/COLOR]
```

It worked. I then updated with no problem. I guess I will be good until I have to do this again.

Thanks for the help!

---

### Post by Bashing-om on 2017-03-12
Coriander Redgoat; Hey ...

```

sudo apt update
sudo apt full-upgrade
sudo apt -f install

```
and the -66 kernel installed ?
Do you now need to trim some space ?
```

df -h 

```
As enough overhead is needed for the next kernel install .

[INDENT][INDENT]Prior Prudent Planning
[/INDENT][/INDENT]

---

### Post by Coriander Redgoat on 2017-03-13
```

Filesystem                 Size   Used   Avail Use% Mounted on
...
/dev/sda1                  236M   110M   114M 50% /boot

```

More space than last time. I did get Kernel -66.

```
uname -r
4.4.0-66-generic

```

I certainly wouldn't mind more space

---

### Post by Bashing-om on 2017-03-13
Coriander Redgoat; Hey ..

Not looking real shabby now ,
As to "I certainly wouldn't mind more space" : the only way to do that is resize the partitions - risky risky, but can be done . That however only prolongs the need for house keeping . One can help on the house keeping by invoking 'autoremove' automatically .

What now is the current situation ?
```

df -h
dpkg -l | grep linux-

```

[INDENT]done with what we can ?
[/INDENT]

---

### Post by Nico_Janow on 2017-03-14
I'm having the same problem with Ubuntu-Mate 16.04 on a Raspberry pi3.  Update asks for 48.2 M.  It doesn't look like there are any old kernels to delete.  Is there a simple way to increase the size of /boot?  I've been using Ubuntu 14.04 on my main computer for a few years, but I'm by no means knowledgeable about linux commands.

The linux community wants people to give linux a try.  Hassles like this are certainly likely to make a Windows user say "Nope, too buggy/difficult."  I should also point out that I was lucky to notice the update notice on the bottom of the screen when my computer suddenly froze up.  The 'auto-update' feature might as well be called 'mysterious auto-crash' to anyone who didn't notice.  I've now turned updates to 'manual'.

nico@nico-desktop:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/root        15G  4.2G   11G  29% /
devtmpfs        459M     0  459M   0% /dev
tmpfs           463M   18M  446M   4% /dev/shm
tmpfs           463M   13M  451M   3% /run
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           463M     0  463M   0% /sys/fs/cgroup
/dev/mmcblk0p1   63M   21M   43M  34% /boot
tmpfs            93M   52K   93M   1% /run/user/1000
/dev/sda1       7.5G  2.4G  5.2G  32% /media/nico/B33D-4A60

nico@nico-desktop:~$ dpkg -l | grep linux-
ii  linux-base                             4.0ubuntu1                                 all          Linux image base package
ii  linux-firmware                         1.157.8                                    all          Firmware for Linux kernel drivers
ii  linux-libc-dev:armhf                   4.4.0-64.85                                armhf        Linux Kernel Headers for development
ii  linux-sound-base                       1.0.25+dfsg-0ubuntu5                       all          base package for ALSA and OSS sound systems



Okay, I found more info on the ubuntu-mate community forum.  The Raspberry Pi has a non-standard boot format which causes a problem with updating.  I'll wait for the Raspberry Pi software engineers to fix the problem.

---

### Post by Coriander Redgoat on 2017-03-15
Hey, the current situation:

```
df -hFilesystem                   Size  Used Avail Use% Mounted on
udev                         1.9G     0  1.9G   0% /dev
tmpfs                        385M   31M  355M   8% /run
/dev/mapper/ubuntu--vg-root  436G  246G  169G  60% /
tmpfs                        1.9G   35M  1.9G   2% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        1.9G     0  1.9G   0% /sys/fs/cgroup
**/dev/sda1                    236M  110M  114M  50% /boot**
cgmfs                        100K     0  100K   0% /run/cgmanager/fs
tmpfs                        385M   88K  385M   1% /run/user/1000
/home/coriander/.Private     436G  246G  169G  60% /home/coriander
/dev/sdb1                    932G  447G  486G  48% /media/coriander/Seagate Expansion Drive



```

```
dpkg -l | grep linux-ii  linux-base                                                  4.0ubuntu1                                    all          Linux image base package
ii  linux-firmware                                              1.157.8                                       all          Firmware for Linux kernel drivers
ii  linux-generic                                               4.4.0.66.70                                   amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-64                                      4.4.0-64.85                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-64-generic                              4.4.0-64.85                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-66                                      4.4.0-66.87                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-66-generic                              4.4.0-66.87                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       4.4.0.66.70                                   amd64        Generic Linux kernel headers
ii  linux-image-4.4.0-64-generic                                4.4.0-64.85                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-66-generic                                4.4.0-66.87                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-64-generic                          4.4.0-64.85                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-66-generic                          4.4.0-66.87                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                                         4.4.0.66.70                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        4.4.0-66.87                                   amd64        Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu5                          all          base package for ALSA and OSS sound systems
ii  linux-tools-4.4.0-64                                        4.4.0-64.85                                   amd64        Linux kernel version specific tools for version 4.4.0-64
ii  linux-tools-4.4.0-64-generic                                4.4.0-64.85                                   amd64        Linux kernel version specific tools for version 4.4.0-64
ii  linux-tools-4.4.0-66                                        4.4.0-66.87                                   amd64        Linux kernel version specific tools for version 4.4.0-66
ii  linux-tools-4.4.0-66-generic                                4.4.0-66.87                                   amd64        Linux kernel version specific tools for version 4.4.0-66
ii  linux-tools-common                                          4.4.0-66.87                                   all          Linux kernel version specific tools for version 4.4.0
ii  linux-tools-virtual                                         4.4.0.66.70                                   amd64        This package will always depend on the latest minimal generic kernel tools.
ii  syslinux-common                                             3:6.03+dfsg-11ubuntu1                         all          collection of bootloaders (common)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu8                          amd64        Bootloader for Linux/i386 using MS-DOS floppies



```

---

### Post by Bashing-om on 2017-03-15
Coriander Redgoat; Uh HuH ;

Looks golden to me .
Now, if you are comfortable with the system taking control:
Use the unattended-upgrades package to regularly run autoremove for you. Edit the autoremove setting in /etc/apt/apt.conf.d/50unattended-upgrades from 'false' to 'true' .

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

