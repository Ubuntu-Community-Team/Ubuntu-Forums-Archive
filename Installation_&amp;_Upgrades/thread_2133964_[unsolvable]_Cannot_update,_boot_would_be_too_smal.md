---
title: "[unsolvable] Cannot update, /boot would be too small? Why is PAE installed"
date: 2013-04-09
forum: Installation &amp; Upgrades
---

### Post by kuifje09 on 2013-04-09
I just tried to do an update, but the updater say:

> 
The upgrade needs a total of 117 M free space on disk '/boot'. Please free at least an additional 82.2 M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.


Thats unusual, and /boot would only contain boot related files !  And secondly my space;

Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sdc3       23070676 16780024   5118712  77% /
/dev/sdc1         124427    84360     33643  72% /boot           ( 33 MB free )

What can cause this ugly error?

Its about  ubuntu 12.04

---

### Post by darkod on 2013-04-09
As it says, it wants 117MB free in /boot and you have only 33MB. That's why it's saying you need approx 82MB free more.

Depending how the upgrade process works, it can't replace all kernels in /boot. And I don't think it replaces any kernel at all, it leaves all old kernels and installs new ones. You made a very small /boot, only 124MB. Either leave it within / or if creating separate /boot make sure it has at least 300MB or better 500MB size.

---

### Post by kuifje09 on 2013-04-09
Okay, thats what I read too, but I have never had such huge new kernel. I usualy had 4 or 5 kernel versions.
That not needed, so i deleted then a few, kept 2 or 3 kernels at a time.

Only thing that can cause the problem...  Since I took Nvidia-96 driver in use, I now have a kernel and a sam kernel-pae.
That consumes twice the space.  Whats that pae kernel for, its build after the videodriver installation.

If I get 2 new kernels then I know why I would have just too less space in /boot but else I dont underrstand.
1 kernel comsumes about 25 MB  not 117 MB,  You understand my problem I hope...

---

### Post by TheFu on 2013-04-09
You have old kernels in /boot and not enough space for a new kernel. Remove some of the older kernels until there is enough space available.
This article might help: [http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt](http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt)
If you don't use encryption or special file systems, having / and /boot on the same file system might be a good alternative going forward.

---

### Post by kuifje09 on 2013-04-09
No its not solved. I have no clear answer why a new kernel would take up 117 MB  in   /boot.
Thats the space needed for normally 3 kernels !

I add 1 example 
```

 du -skc *3.0.0-31*
752     abi-3.0.0-31-generic
140     config-3.0.0-31-generic
13328   initrd.img-3.0.0-31-generic
2092    System.map-3.0.0-31-generic
4       vmcoreinfo-3.0.0-31-generic
4548    vmlinuz-3.0.0-31-generic
20864   totaal

```

---

### Post by kuifje09 on 2013-04-09
Noone else any suggestion?

The old 2.6 kernel only used 19MB in /boot

---

### Post by kuifje09 on 2013-04-09
Would a few of you post please the kernel sizes as I did in the post #5  but for the kernels 3.2.*  and 3.5.*  That would help me a lot.
Thanks in advance.

---

### Post by ajgreeny on 2013-04-09
Can you show the output of command ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
``` which will show us exactly how many kernels you have still installed.
I always remove old kernels using synaptic, but leaving the most recent plus the previous one as a backup.

The 3.2.0 kernels plus headers each use 180MB, the 3.5.0 use 188MB.

---

### Post by Bashing-om on 2013-04-09
kuifje09;
As per your request; Here is my output.
```
 du -skc *3.2.0-*
776    abi-3.2.0-32-generic
776    abi-3.2.0-33-generic
776    abi-3.2.0-34-generic
776    abi-3.2.0-35-generic
776    abi-3.2.0-36-generic
776    abi-3.2.0-37-generic
776    abi-3.2.0-38-generic
776    abi-3.2.0-39-generic
780    abi-3.2.0-40-generic
140    config-3.2.0-32-generic
140    config-3.2.0-33-generic
140    config-3.2.0-34-generic
140    config-3.2.0-35-generic
140    config-3.2.0-36-generic
140    config-3.2.0-37-generic
140    config-3.2.0-38-generic
140    config-3.2.0-39-generic
140    config-3.2.0-40-generic
13872    initrd.img-3.2.0-32-generic
13872    initrd.img-3.2.0-33-generic
13872    initrd.img-3.2.0-34-generic
13872    initrd.img-3.2.0-35-generic
13880    initrd.img-3.2.0-36-generic
13880    initrd.img-3.2.0-37-generic
13868    initrd.img-3.2.0-38-generic
13864    initrd.img-3.2.0-39-generic
13904    initrd.img-3.2.0-40-generic
2820    System.map-3.2.0-32-generic
2820    System.map-3.2.0-33-generic
2820    System.map-3.2.0-34-generic
2820    System.map-3.2.0-35-generic
2820    System.map-3.2.0-36-generic
2820    System.map-3.2.0-37-generic
2820    System.map-3.2.0-38-generic
2824    System.map-3.2.0-39-generic
2824    System.map-3.2.0-40-generic
4852    vmlinuz-3.2.0-32-generic
4852    vmlinuz-3.2.0-33-generic
4852    vmlinuz-3.2.0-34-generic
4852    vmlinuz-3.2.0-35-generic
4856    vmlinuz-3.2.0-36-generic
4856    vmlinuz-3.2.0-37-generic
4856    vmlinuz-3.2.0-38-generic
4856    vmlinuz-3.2.0-39-generic
4860    vmlinuz-3.2.0-40-generic
202212    total

```

---

### Post by darkod on 2013-04-10
I think you are jumping to conclusions. The way I see it, it never said the new kernel will be 117MB so comparing it to current kernel sizes is pointless. It said it needs 117MB on /boot to do the upgrade. There is a lot more going on during the upgrade than simply copying the kernel. If it was like a simple copy, you would only need free size equal to the kernel size, but what about first downloading files, making temp files maybe, compiling, making the initrd image, etc.

At the end, the kernel will probably not be near 117MB but temporary it needs the space to finish the job. That's how I see it.

In your palce, instead of wasting my time I would start looking into option to free space on /boot. Sorry to say this, but it's your own fault you made it only 124MB.

After all, you have options. You have 5GB free on sdc3. Simply boot the machine in live mode with the ubuntu cd, make a boot folder on sdc3, copy the content of sdc1 making sure you keep ownership and permissions, modify fstab not to use sdc1 as /boot, and that's it. The boot folder will be integrated into / and it should boot fine.

Unless the reason to have separate /boot is that the computer can't boot from beyond 137GB on the disk and depending where sdc3 is exactly on the disk.

---

### Post by kuifje09 on 2013-04-10
Thanks for those reactions. And yes I know how to partition, thats not the point.  My problem is in Why the update process takes so much space in /boot.  It never happend before  and a boot of 128MB  ( mine just 124MB , okay... ) was always more then enough.
Now there is a sudden jump in used space needed....

And then, I don't think it is waste of time to try to understand what is going on.

I have been looking a bit further and I think I see a part of the problem. For some reason I realy cant get my finger on, the system has now instaled the generic and the generic-pae kernel.  I have a 32 bit system and no more then 1GB mem. So there is no point in having the pae on the system.
But when I try to remove it, it immediatly wants to install a new pae kernel.  Which doubles the space needed in /boot.

New kernels seems to be about 27MB (max) so at least I have then about 25MB short...  

[COLOR=#0000ff]So the question maby sould be    Why do I have a PAE kernel on my system.[/COLOR]

Reconfig of the harddrive is no problem I could even put both partitions together, even temporarily. Thats not the point.

Sorry, forgot the question of AJGREENY:
I have only these kernels on my system :
vmlinuz-2.6.38-16-generic
vmlinuz-3.2.0-39-generic
vmlinuz-3.2.0-39-generic-pae

And the header( and other kernel releted ) files are in /   not in /boot  I have them seperated.
Some years ago I had even more filesystems seperated, but sometimes it only means waste of space.

---

### Post by kuifje09 on 2013-04-10
Noone any idea.

---

### Post by kuifje09 on 2013-04-11
Meanwhile I renamed all the pae related files and dirs.  The system boots normal.
Why is the pae kernel put on my system !.  And why can't I remove it the normal way ?

When I start update and deselect all pae packages, the download starts and guess what ...

The pae packages are downloaded too.   Then I cancel, because I don't want them if I don't need them. At least I have no reason for.

So who is going to explain, who want to spread his/her knowlege.

Has it something to do with the nvidia-96 driver ????  As far I remember it is installed since I loaded that driver.

---

### Post by oldos2er on 2013-04-11
The PAE kernel is installed automatically if your system has more than 3GB RAM.

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by kuifje09 on 2013-04-12
Thanks Oldos2er, I have read that document and just because of whats written in it, I am very curious why the PAE kernel is on my system.
I have a 32 bit system with less then 1 Gb mem.  So it should not be nessecary to have it.
But I cannot even remove it, Update immediatly tries to install a new one even when I deselect it.
See my post number # 12  . 
Crippling the PAE fileset does not seem to harm the good working system. 
I still think it came on the system when I installed the Nvidia-96 package.

---

