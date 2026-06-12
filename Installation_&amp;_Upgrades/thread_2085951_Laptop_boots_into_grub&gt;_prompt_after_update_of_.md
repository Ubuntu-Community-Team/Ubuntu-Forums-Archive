---
title: "Laptop boots into grub&gt; prompt after update of 12.10..."
date: 2012-11-19
forum: Installation &amp; Upgrades
---

### Post by SpiritFuzz on 2012-11-19
Hi all. I recently installed Ubuntu 12.10 (Quantal) on my laptop, and after the most recent update my system now boots into a black screen that reads: ```
GNU Grub version 2.00-7ubuntu11
Minimal BASH-like line editing is supported. For the first word, TAB lists 
possible command completions. Anywhere else TAB lists possible device 
or file completions.
grub>
``` I'm dual booting with Windows 7 only because I'm a student and most of my classes require Windows, otherwise I'm a devoted Ubuntu user. Please bear with me as I've been away from the Ubuntu scene for some time now, but once upon a time knew my way around it very well. 
Anyway, here's a general rundown of my situation: I did a fresh install of 12.10 a couple of weeks ago alongside Windows via USB. Now, as I stated, after the most recent update my system now boots into the screen above and I cannot access either Ubuntu or Windows. Luckily though, I'm still able to access the Internet with the Live CD on the USB stick. 
 Originally when I first ran the update the error message was something along the lines of: "Ubuntu encountered a problem with apt-daemon...", but I didn't think to write it down. After this I rebooted only to encounter the grub> prompt. I hit TAB and tried the command "boot", but it said that I needed to load the kernel first. After that I changed my boot priority, loaded the Live CD, studied the forums and found a similar problem, at which point I downloaded boot-repair. After running the default settings, it still boots into the grub> prompt. 
I'm still unable to find a solution and don't want to brick my machine, so a walk-through would probably be best. I have the day off at work so I'll be able to stay by my computer until this is solved. Thanks greatly in advance for any help.

---

### Post by oldfred on 2012-11-19
Welcome to the forums.

Not sure what error happened. But if kernel or init are damaged then grub could not update and then you cannot boot.

First lets see what this shows. 

       Post the link to the BootInfo report that this creates.

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
If kernel is missing  or damaged, we may be able to chroot into your system and repair update and install new kernel from chroot.

If you need to get to Windows quickly you can use Boot-Repair to install a Windows like boot loader and then reinstall grub2's boot loader later after repairs.

Or:
       How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by SpiritFuzz on 2012-11-19
Thanks for the reply. I'll get right on it and then post the link you requested.

---

### Post by SpiritFuzz on 2012-11-19
Okay, I ran the boot-repair again and still the same problem. Here's the link it generated:
[http://paste.ubuntu.com/1370762/](http://paste.ubuntu.com/1370762/)
Thanks again.

---

### Post by oldfred on 2012-11-19
Script cannot see sda5 partition, so that is why grub is having issue also. I suggest filechecks as most likely fix. Did system get shutdown abnormally as that is the most common reason for file issues?

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda5 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda5
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sda5

---

### Post by SpiritFuzz on 2012-11-19
Thanks oldfred. Sorry for the delay, I had to pick up my fiance from work. I'll try the codes you offered and get back with you promptly.

---

### Post by SpiritFuzz on 2012-11-19
Okay, I ran the codes you gave in the order specified, here is the result:
```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda5
/dev/sda5: recovering journal
/dev/sda5: Superblock needs_recovery flag is clear, but journal has data.
/dev/sda5: Run journal anyway

/dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda5
e2fsck 1.42.5 (29-Jul-2012)
/dev/sda5: recovering journal
Superblock needs_recovery flag is clear, but journal has data.
Run journal anyway? yes

e2fsck: unable to set superblock flags on /dev/sda5


/dev/sda5: ********** WARNING: Filesystem still has errors **********
```
I also read the man page as you recommended, but couldn't deduce anything else from it.

---

### Post by oldfred on 2012-11-19
We can try back up superblocks.
Info:

 [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)



example

#List backup superblocks:
sudo dumpe2fs /dev/sda5 | grep -i backup
#then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5

---

