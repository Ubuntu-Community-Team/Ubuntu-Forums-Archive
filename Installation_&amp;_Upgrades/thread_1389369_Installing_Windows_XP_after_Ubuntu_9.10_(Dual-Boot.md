---
title: "Installing Windows XP after Ubuntu 9.10 (Dual-Boot)"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by brokenrhythms on 2010-01-24
Hi Ubuntu Community-

There seems to be a lot threads on this topic, but I am having trouble finding the answers I exactly need. So, I decided to use this questions as my first Ubuntu Forum post.

I converted over to Ubuntu 9.10 and left about 60 gigs in my partition to leave for dual-booting Windows XP on a rainy day.

I want to move ahead and install Windows XP in the remaining 60 gigs.

Can somebody guide me through this? (It seems like installing xp first is recommended by i want to avoid re-doing my ubuntu setup. is there a safe way to install xp after ubuntu was already installed?)

I tried loading the Windows XP Home cd in startup and i get a blue screen error message saying windows setup cannot load.

I currently have Unbuntu 9.10 running w/ 60 gigs of unallocated space.

Thank you!

---

### Post by kansasnoob on 2010-01-24
Go to terminal in Ubuntu and post the output of:

```
grub-install -v
```

And:

```
sudo fdisk -l
```

BTW that's a lower case L.

---

### Post by brokenrhythms on 2010-01-24
hey kansasnoob: here is my output (thanks for your help) by the way, i am open to either vista or xp, if any is easier than the other. xp preferably though.

dekae@brokenrhythms:~$ grub-install -v
grub-install (GNU GRUB 1.97~beta4)
dekae@brokenrhythms:~$ sudo fdisk -l
[sudo] password for dekae: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x87b33479

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30151   242187876    5  Extended
/dev/sda5               1         243     1951834+  82  Linux swap / Solaris
/dev/sda6             244        1459     9767488+  83  Linux
/dev/sda7            1460       30151   230468458+  83  Linux

---

### Post by kansasnoob on 2010-01-24
I also need:

```
df -H
```

So I can tell the difference between sda6 and sda7.

BTW I like XP better too.

---

### Post by brokenrhythms on 2010-01-24
here it is:


dekae@brokenrhythms:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             9.2G  3.9G  4.9G  45% /
udev                  1.5G  300K  1.5G   1% /dev
none                  1.5G  456K  1.5G   1% /dev/shm
none                  1.5G  220K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/sda7             217G  112G   94G  55% /home

---

### Post by kansasnoob on 2010-01-24
> **brokenrhythms said:**
> here it is:


dekae@brokenrhythms:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             9.2G  3.9G  4.9G  45% /
udev                  1.5G  300K  1.5G   1% /dev
none                  1.5G  456K  1.5G   1% /dev/shm
none                  1.5G  220K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/sda7             217G  112G   94G  55% /home

OK sda6 is your Ubuntu root "/" partition and you're using grub2.

First look at only pages 3 and 4 here (ignore the rest because it's about legacy grub and you have grub2):

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=3](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=3)

You'll see they left the disc space where they're going to install XP unpartitioned and unformatted, then they just choose "Unpartitioned space" from the XP install program. That is the safest way to do this.

Then when the installation is complete you'll have to boot an Ubuntu Live CD and go to terminal and run:

```
sudo mount /dev/sda6 /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
grub-install /dev/sda
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

That will restore grub2 to the mbr of the drive.

You'll notice that Ubuntu just boots, no grub menu, on the first reboot. That's expected, so right after the initial boot into Ubuntu go to terminal and run:

```
sudo update-grub
```

Wait for it to say done.

Hopefully it will automagically find Windows.

---

### Post by brokenrhythms on 2010-01-24
Thanks for your all your time kansasnoob. really appreciate it.

i have one more question. i just tried rebooting into the windows xp setup with the windows xp home cd... i get the following error after it loads:

"A problem has been detected and windows has been shut down to prevent damage to your computer. 

If this is your first time you've seen this error screen, restart your computer. If this screen appears again, follow these steps:

Check for viruses on the computer.....etc.... etc...."

Any thoughts?

---

### Post by DnkAlex on 2010-01-24
hi! i got the exact same problem with the blue screen after xp setup loads, from what i have read the key to fixing this is to install xp first then ubuntu.
so to get rid of ubuntu i suppose i should format the ubuntu partitions from a ubuntu live cd, then install xp and the blue screen shouldn't appear again. i am reluctant this may work, so i hope someone will enlighten us.
cheers!

---

### Post by kansasnoob on 2010-01-24
> **brokenrhythms said:**
> Thanks for your all your time kansasnoob. really appreciate it.

i have one more question. i just tried rebooting into the windows xp setup with the windows xp home cd... i get the following error after it loads:

"A problem has been detected and windows has been shut down to prevent damage to your computer. 

If this is your first time you've seen this error screen, restart your computer. If this screen appears again, follow these steps:

Check for viruses on the computer.....etc.... etc...."

Any thoughts?

Assuming you can still boot Ubuntu install Gparted (if it's not already):

```
sudo apt-get install gparted
```

You'll then find it in System > Administration. Please post a screenshot of Gparted, the screenshot tool is in Applications > Accessories & you can attach it using the paper clip thingy at the top of the reply box.

Or you can do the same using the Live CD which already has Gparted installed by default.

---

### Post by kansasnoob on 2010-01-24
> **DnkAlex said:**
> hi! i got the exact same problem with the blue screen after xp setup loads, from what i have read the key to fixing this is to install xp first then ubuntu.
so to get rid of ubuntu i suppose i should format the ubuntu partitions from a ubuntu live cd, then install xp and the blue screen shouldn't appear again. i am reluctant this may work, so i hope someone will enlighten us.
cheers!

Are you sure you left the disc space for XP unpartitioned and unformatted? That's why I'm asking the OP for a screenshot of Gparted.

---

### Post by DnkAlex on 2010-01-24
> **kansasnoob said:**
> Are you sure you left the disc space for XP unpartitioned and unformatted? That's why I'm asking the OP for a screenshot of Gparted.
yes, i found out what the problem was.
my hard disk was set to ahci and now it's set to ide
i have another problem thought.. when i tried to install xp to the unpartitionted space it kept prompting me that i don't have a suitable partition for windows (something about mbr )
so i tried to boot back to ubuntu, afterwards my pc prompted me that it can't find a operating system. ok.. i thought the setup ****** up the grub, so i decided to delete the ubuntu's partitions from the xp setup, and now i wanted to backup my private data from a untouched partition and then format it too. but now ubuntu live cd can't mount the partition (message did not receive a reply (timeout by message bus))

what to do?

le: while i wait for your response i decided to create a ntfs partition from the live cd and try to install xp on it, will be back in 10-15 minutes with the outcome

even le:
ok.. so i managed to install xp and ubuntu 9.04, here is how i did it:
- set the hard drive to ide from ahci, this is were i got the blue screen error message when trying to install xp
- deleted the ubuntu partitions from the xp setup
- installed xp on the first partition, former ubuntu filesystem partition, other partitions wouldn't work including the one i created with gparted from the live cd
- installed ubuntu afterwards.

hope this helps to other ubuntu newbies like myself :)

---

### Post by canplaythegame on 2010-06-19
i had vista installed
and ran 9.10 off the cd
then decided to dual boot
and when it came to the option of partitioning the drive
the computer just hung up and froze while it was partitioning
so i had to turn off start again
at the same point it didnt give me the option second time round
only option was to delete windows drive and install ubuntu
which i did
but what do i do now to install vista afterwards

thanks

daniel d

---

### Post by wilee-nilee on 2010-06-19
> **canplaythegame said:**
> i had vista installed
and ran 9.10 off the cd
then decided to dual boot
and when it came to the option of partitioning the drive
the computer just hung up and froze while it was partitioning
so i had to turn off start again
at the same point it didnt give me the option second time round
only option was to delete windows drive and install ubuntu
which i did
but what do i do now to install vista afterwards

thanks

daniel d

You want to start your own thread for help, it is a easy job, so start your thread.;)

---

