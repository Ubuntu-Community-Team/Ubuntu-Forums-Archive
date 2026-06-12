---
title: "Boot repair"
date: 2015-03-15
forum: Installation &amp; Upgrades
---

### Post by laura15 on 2015-03-15
Hello everyone!

A couple of days ago, while choosing the OS to load in the grub, my sister chose something other than Windows or Ubuntu (I am not sure what she did, sorry I cannot provide more details on that). She then saw a message like "grub recovery". She restarted the machine, but grub would not load and both Windows and Ubuntu were unreachable.

The only thing I could think of was to make a boot repair and you can see the result here:
[http://paste.ubuntu.com/10588884/](http://paste.ubuntu.com/10588884/)

After restarting the machine, it went directly to Windows. No grub, no Ubuntu. Any ideas?

Thanks!
Laura.

---

### Post by ajgreeny on 2015-03-15
You do not seem to have Ubuntu installed as there are no Linux partitions except for a swap, that is why it will not boot to Ubuntu.

From your description of what happened it is impossible to help, but what you have at present on disk is:-
```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   341964092   170878622+   7  HPFS/NTFS/exFAT
/dev/sda3       341964798   603408383   130721793    5  Extended
/dev/sda4       603408384   625139711    10865664    7  HPFS/NTFS/exFAT
/dev/sda5       597190656   603408383     3108864   82  Linux swap / Solaris
```
There should be at least one ext4 partition, unless you installed the ubuntu system using wubi, ie installed within a running Windows OS, which seems unlikely or you would not have a swap partition.

Can your sister have somehow deleted some partitions or done something she's not telling you, and then made some new ntfs partitions in place of Ubuntu?
Seems very unlikely, but something weird has happened here if you did have Ubuntu installed and running.

---

### Post by oldfred on 2015-03-15
I bet she started the entire system recovery. One of the first things that does is rewrite the partition table. And Windows does not 'see' Linux partitions so when it rewrote the partition table it left off the Linux partition. 

You have a large gap from the start of the extended partition to the start of the swap partition inside the extended partition. That is your Linux partition. 
Some users have been able to use testdisk and just restore that partition and have it work without even other repairs, depending on what else you may have done.

Testdisk is in repository, so you can use your Live installer in live mode and add testdisk. Many other Linux repair disks also have it as a standard application.

 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by laura15 on 2015-03-15
Thanks for your answers [COLOR=#000000]ajgreeny and [/COLOR][COLOR=#000000]oldfred!

ajgreeny, isn't the "Extended" partition the one where Ubuntu should be? I interpreted that as being the ext4 partition... I guess I was wrong. I did not install Ubuntu using wubi, I did a complete installation with different partitions. As that is not my computer and I did that installation a long time ago, I really do not remember how I structured the partitions. Do you think my sister just wiped-out the whole Ubuntu installation? [/COLOR]:confused: My mother is not going to be happy! And yes, it is very possible she did something she is not telling me. I do not think she did new partitions on purpose, I am pretty sure she does not even know what a partition is. I think she just did not know what she was doing, tried to fix whatever happened and ended up doing something very very very wrong.[COLOR=#000000]

oldfred, I will try the test-disk approach and let you know how it goes.

Thanks again!
Laura.[/COLOR]

---

### Post by ajgreeny on 2015-03-15
Yes, your whole ubuntu partition is gone and only the swap remains, so I think that is what your sister did.
Sorry I did not notice the start and end points of the partitions left a large space where your ubuntu partition used to be, partly because the partitions are not on disk in numerical order, which in itself is not a problem, it's just that I did not see the empty space.

I hope testdisk can restore the partition and all the files that were in it; I have never had a reason to use it so do not even know how easy it might be, nor how long it might take to do so.

The extended partition is not a Linux partition but just a wrapper within which you can make logical partitions.  Linux OSs can be fully installed and will boot from a logical partition but windows will not.  They are used when a machine uses legacy BIOS, which has a 4 partition limit but not with the modern UEFI.  Up to 128 logical partitions can be made within an extended partition I believe, certainly more than anyone is going to need or want.

I suspect, now that oldfred has drawn my attention to it, that the empty space was indeed your ubuntu OS partition but I wonder why the swap partition still exists and why the restore action carried out did not remove that as well as the OS partition.  I wonder also what the ~11GB partition at the end of the disc is, or was previously, and why it was there.

Strange happenings which perhaps we will never get to the bottom of.
Let's pray testdisk does its job nicely for you.

---

### Post by oldfred on 2015-03-15
The several users before that started recovery also kept the swap but not the Linux partition. Not sure what the Windows partition tool does. Yes it is strange.
But just points out why backups are important.

---

### Post by laura15 on 2015-03-25
Hello again everyone.

I read about testdisk and I have decided to give up and reinstall Ubuntu again. The main cause is that I am 400km away from the damaged computer and telling my mom or my sister how to do it over the phone is going to be a big pain that will make me cry with frustration, throw the telephone out the window and it may all end-up in family break-up. Well, maybe not family break-up, but tears are definitely expected! ;)

No, really, I think it is much easier to just reinstall. Fortunately, they had all the important information backed-up, so it will not be a big loss.

Thanks again everyone for your help!

Best,
Laura.

---

