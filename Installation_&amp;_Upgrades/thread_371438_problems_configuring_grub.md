---
title: "problems configuring grub"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by 999alfred on 2007-02-26
I installed Ubuntu on drive hda1 and I have a Slackware install on hdb2. I want to be able to bott either but I can not seem to get grub configured correctly. I have always used lilo.
Here is my grub entry for the Slackware entry

title           Slackware
root            (hd1,1)
kernel          (hd1,1)/boot/bzImage.scsicd ro single hdc=ide-scsi hdd=ide-scsi
boot
 
Now when I boot I select Slack and it starts, but It kernel panics. From the messages:

sh-2021 reiserfs_read_super: can not find reiserfs on ide0(3,2)
Kernel Panic: VFS: Unable to mount root fs on 03:02

The fstab on the slackware partion has /dev/hdb2 as root and /dev/hdb3 as swap.

Again, this is my first experience with grub. So what am I doing wrong?

tj

---

### Post by tgalati4 on 2007-02-27
Welcome to the forums!

You have the title wrong.  It should be Slackware Rocks!

My Ubuntu stanza looks like:
title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

I don't have Slackwareinstalled as dual boot so I can't answer your specific question.  Perhaps you are missing the initrd line?  This initializes the ramdisk to allow the boot to continue.  I don't remember how Slackware goes through it's boot process.

But Slackware rocks regardless.

Good luck.

---

### Post by Herman on 2007-02-27
Hello 999alfred,
I don't know why, but a quick look around in Slackware's forum makes it look like no-one uses Grub there. Maybe it isn't even possible to boot Slackware with grub directly (easily).
If you installed Slackware's Lilo to the first sector of the slackware partition as well as to MBR, you can always chainload it from grub. (Add a boot entry like this in Ubuntu's /boot/grub/menu.lst
```
 root (hdX,0)
chainloader +1
boot
```If you have not installed Lilo to your slackware partition, and you can't boot slackware to so so, then perhaps installing Lilo in Ubuntu will solve your problem         [Install Lilo with apt-get from terminal]("http://users.bigpond.net.au/hermanzone/p4.html#Install_Lilo_from_terminal") 
Then  [Run Liloconfig]("http://users.bigpond.net.au/hermanzone/p4.html#Run_Liloconfig") and install Lilo to your Ubuntu partition's first sector instead. Chainload your Ubuntu partition from grub  to start Lilo. Then select Slackware from the Lilo menu.
There is no reason why we can't have both bootloaders in Ubuntu. I use Grub from MBR and  have Lilo in the bootsector as well, I do it all the time. I am hoping that boot entries for your slackware installation will automatically be added to your new Lilo menu in Ubuntu, I know Windows boot entries will be normally. If it isn't, you can probably add one manually. Just take a look at your Slackware's lilo.conf file and copy the boot entry from it. Paste it to your Ubuntu /etc/lilo.conf
Normally other filesystems (partitions are automatically mounted in /media in Ubuntu, if not, then this link might help, [Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm")

Regards, Herman :)

---

### Post by tgalati4 on 2007-02-27
Great reply.  I had a similar setup with lilo and grub when I pulled a drive out of another machine with a lilo-bootstrapped distro on it and put it into a grub machine.  It worked.  Although it wasn't slackware so I can't verify that, but it should work in principle.

---

