---
title: "Missing initrd.img after installing Kubuntu 8.10"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by chrisvw on 2008-11-23
I seem to have missing files after installing Kubuntu 8.10 on the same hard drive as Kubuntu 8.04.

My current setup:

sda1 = swap
sda3 = Kubuntu 8.04
sda5 = Kubuntu 8.10

8.04 was running fine on its own.

During installation of 8.10 I said yes, create GRUB. Except that the installer did not add any reference to 8.10 to menu.lst

So I added it by hand. But judging by the 8.04 entry lines and other posts on this forum, there is a file missing in my /boot folder: **initrd.img-2.6.27-7-generic**

Contents of menu.lst
```

title           Ubuntu 8.10, kernel 2.6.27-7-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=5d058a32-e4ad-4820-ae45-26cd09032a75 ro quiet sp$
initrd          /boot/initrd.img-2.6.27-7-generic
quiet

title           Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=5d058a32-e4ad-4820-ae45-26cd09032a75 ro single
initrd          /boot/initrd.img-2.6.27-7-generic

### everything above this line I added myself

title           Ubuntu 8.04.1, kernel 2.6.24-21-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-21-generic root=UUID=a7af1ec9-2cf8-4b60-91ac-20a036e9e69a ro quiet s$
initrd          /boot/initrd.img-2.6.24-21-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-21-generic root=UUID=a7af1ec9-2cf8-4b60-91ac-20a036e9e69a ro single
initrd          /boot/initrd.img-2.6.24-21-generic

```

I were able to determine the UUID for my 8.10 partition.
I were able to determine the correct name for the vmlinuz file.
**But I can not find the missing initrd.img file in my /boot folder!**

Yes, I tried to comment it out and boot without, but Linux goes into a panic if I do. lol

```

root@k804ws1:/# mount /dev/sda5 /mnt/k810
root@k804ws1:/# ls /mnt/k810/boot
abi-2.6.27-7-generic     memtest86+.bin               vmcoreinfo-2.6.27-7-generic
config-2.6.27-7-generic  System.map-2.6.27-7-generic  vmlinuz-2.6.27-7-generic
root@k804ws1:/#

```

Where can I find this missing initrd.img file?

There is a red "initrd.img" file in /, but I can't seem to copy it to /boot.

```

root@k804ws1:/mnt/k810# cp initrd.img /mnt/k810/boot
cp: cannot stat `initrd.img': No such file or directory

```

I booted from the Kubuntu 8.10 LiveCD in the hope that I can find the file in the CD's /boot folder, but it's not there either.

---

### Post by chrisvw on 2008-11-25
I just discovered that my Kubuntu 8.10 installation is in partition sda5, which is **inside** sda4, which is an extended partition. Is that maybe the reason why Kubuntu 8.10 were not added to /boot/menu.lst?

With other words: Should all bootable partitions only exist in primary (non-extended) partitions?

---

### Post by chrisvw on 2008-11-26
Nobody knows?

Guess it's up to me to experiment. Busy making space in the primary partition with the intent to reinstall Kubuntu 8.10. I sadly doubt that reinstalling the OS is going to make a difference. I expect to sit with the same problem afterwards.

*sighs*

---

### Post by dnoyeb on 2008-12-13
Im having the same problem.  I am however installing to /dev/sda1 which is not an extended partition or logical partition.  Also, the initrd you see in '/' is not a file but a link to a file that should be in /boot/.  Do an ls -la and you should see what the link points too.  Its a broken link.  makes me think the file was there then erased.

---

### Post by tomthumb99 on 2008-12-28
Folks any further info on this problem? I have been working with GRUB for three weeks now, it looks to be working for me (win XP boots, mem test fine). I am getting good a modifying menu.lst over this tough period.  I do not want to re-install grub if possible.

 Best I can figure is that this is a missing ubuntu file. {How can one of three core ubuntu boot files be missing off the 8.10 release???}

---

### Post by akhenax on 2008-12-30
Wow, after hours and hours of searching, I think this thread will save my sanity. This thread is my 44th attempt at Google to find an answer.

When my system attempts to boot, I get a kernel panic, unable to sync (hd0,0) unknown block, or something like that.  Looking at Grub menu.lst everything looked fine at first: There's the Title, there's the uuid, there's my kernel with the options, ending with "quiet".  Ok, things look ok I think.  What am I missing? After reinstalling the OS a few times, then reinstalling Grub a few times, I look at other postings, and noticed that they made reference to the initrd.img file, but I'm thinking Ubuntu 8.10 doesn't need it because this is a new install, and it didn't provide one so I must not need one...right ? Wrong! I booted up the Ubuntu Live CD and was able to mount to my boot fs and my root fs.  Looking around, I noticed that I DON'T HAVE AN INITRD.IMG FILE in my /boot partition or anywhere.  Why?  I am a RedHat user, and occasionally use SUSE.  I wanted to try Ubuntu because I've heard great things about it, but this is a huge bug.  I guess I'll try 8.04 to see if the problem disappears in older distros of Ubuntu.

---

### Post by sunnyDev on 2009-01-24
I have exaclty the same problem installing Ubuntu 8.10 64 bit! I have made a lot of try without success. During several installation, I examined any information during the installing processor, but thre was no signs of errors.

I kept my old Ubuntu 8.04.1 32 bit, and there was already a grub installed.The partition I used to install the 8.10 64 bit version is also an extended partition. 

I tried to add entry to exisiting menu.lst, the same with akhenax, I could not find "/boot/initrd.img-2.6.27-7-generic" file in my installation, nor can I find it in live CD. 

Following this advice:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
I aslo tried to install grub in the partition of the newly installed system, but still failed.  I got: "Could not find device for /boot: Not found or not a block device."

I think there must be someone has successfully installed Ubuntu 8.10 64 bit together with Grub? (There would be a little weird if otherwise) So I'm wordering what's wrong in my case? Could that be hardware incompatible? But the live CD worked. I tried two mirrors from offical site, they bothe missing .img file. Does the missing file cause the problem?

---

### Post by Tido on 2009-01-24
Hi 

I have the same error, so I google: 8.10 initrd.img and found following which I have not tested yet:

I was looking around at other bug reports here and
I learned that "ubiquity" may be run manually.

So this time I booted ubuntu-8.10-desktop-i386 but chose to go into the live session, 
rather than the "Install Ubuntu" option. Then I started up an xterm and issued the following command, as a response to another bug report had suggested:
```
ubiquity --no-migration-assistant
```

[URL="https://bugs.launchpad.net/ubuntu/+bug/309748"]Bug #309748:
[/URL]

hope that helps.

Br,
Tido

---

### Post by sunnyDev on 2009-02-08
Hope the following information helps. 

I downloaded a new Ubuntu 8.10 64 bit installation disk image yesterday and installed it on a new PRIMARY partition successfully! I already have windows and Ubuntu 8.04 on another two primary partitions. Grub was successfully installed too! Under the same computer with windows XP and Ubuntu 8.04 pre-installed,  I have tried to install Ubuntu 8.10 64 bit on an extended partition without success, but have installed Ubuntu 8.10 32 bit on the extended partition successfully. Maybe Ubuntu 8.10 64 bit could not be installed successfully with Grub on an extended partition, but should be installed on a primary partition?

---

### Post by DaveAtFraud on 2009-02-22
> **Tido said:**
> Hi 

I have the same error, so I google: 8.10 initrd.img and found following which I have not tested yet:

I was looking around at other bug reports here and
I learned that "ubiquity" may be run manually.

So this time I booted ubuntu-8.10-desktop-i386 but chose to go into the live session, 
rather than the "Install Ubuntu" option. Then I started up an xterm and issued the following command, as a response to another bug report had suggested:
```
ubiquity --no-migration-assistant
```

[URL="https://bugs.launchpad.net/ubuntu/+bug/309748"]Bug #309748:
[/URL]

hope that helps.

Br,
Tido
This approach still didn't work for me.  I was attempting to install Ubuntu on an external (USB) hard drive and ubiquity only showed the internal drive in the partitioning step.

Never one to give up and especially since I already had Fedora 10 running from the external drive I decided to persevere.  I'm an old Red Hat geek so I'm used to making the initrd when the kernel is built.  I didn't know Ubuntu built an initrd on the fly until I read this thread and only after spending quite a bit of time trying to find an initrd file on the installation image.  Grrrr.

Once I realized that the initrd was to be constructed I went through the following steps:

0) Go ahead and install however you want to and discover that the initrd image is missing.
1) Boot from the live CD in the "just try it" mode.
2) The live CD will mount your existing installation.  Depending on how you partitioned the target drive, change to the real /boot directory (I always create a separate partition for /boot to keep it clean in case of a crash).
3) run mkinitramfs -o initrd-<kernel version> (or whatever you like to call your initrd).
4) reboot

From what I can tell, grub gets installed but I can't find any sort of grub.conf or menu.lst file so configuring it is probably borked also.  I added the right entries to the grub.conf on my internal hard disk so it can now manage booting Ubuntu.  If you want a grub.conf/menu.lst file that configures grub under Ubuntu, you'll still need to look into how to set that up (create a grub.conf/menu.lst file in /boot/grub that has the configuration stuff you need and do a setup from within grub and a grub-install, I think).

Cheers,
Dave

---

### Post by purijatin on 2011-08-05
I had the same problem, but finally found the solution.
after installation, that is *make install* , to get the initramfc.img file execute the following
*sudo update-initramfs -c -k 2.6.32.11* where you should replace your version with *2.6.32.11*

---

