---
title: "Dead computer after terminal command - help"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by krklabunde on 2007-11-06
I just entered these commands ( [http://ubuntuforums.org/showthread.php?t=604326](http://ubuntuforums.org/showthread.php?t=604326) ) and it ruined my computer.  Here is the problem:
I just installed Ubuntu last night on a new slave hard drive.  Windows XP is on the master drive.
All worked fine except the splash screen as described here, and the fact that my keyboard didn't work (logitech wireless) during the screen where I select the OS to boot from.  However, the keyboard works fine before this point (in the bios).  No big deal since Ubuntu defaulted as the OS in 10 seconds.  Once Ubuntu is running, the keyboard and mouse work fine.  I will need to fix this soon since I can't select Ubuntu troubleshooting mode or Windows to boot without the keyboard being recognized.
Now that I fixed the splash screen with the commands provided in this post, I get the following error right after Ubuntu begins to load:
[INDENT]Starting up ...   [   23.991011] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)[/INDENT]
This never happened until the moment I rebooted after enter the commands for the splash screen.
I have no idea how to fix this.

---

### Post by frodon on 2007-11-06
Look at these similar bug reports :
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/138325](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/138325)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/149565](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/149565)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/151146](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/151146)

I would try to boot the failsafe kernel or another bootable kernel and run the following command as it looks like (in my opinin) an initramfs problem :
```
sudo update-initramfs -k all -u
```

---

### Post by krklabunde on 2007-11-06
Sorry, I don't understand anything you just said, or what is posted on these other bug threads.  My computer will now only boot from the Ubuntu Live CD.  So I'm looking at the Ubuntu desktop from the CD...now what do I do?

---

### Post by frodon on 2007-11-06
if you don't have a bootable kernel, you can do chrooting using livecd. chroot mean that you are kind of loading your ubuntu partition environment

While in livecd, open a terminal and use fdisk to find out your gutsy root partition

```
sudo fdisk -l
```

For example, if your gutsy root partition is /dev/sda1 type :

```
sudo mount /dev/sda1 /mnt
sudo mount -t proc proc /mnt/proc
sudo chroot /mnt
update-initramfs -k all -u
```

then reboot.

---

### Post by krklabunde on 2007-11-06
I have no idea what you just had me do, but it worked...THANK YOU!

---

### Post by frodon on 2007-11-06
It's our purpose to help users especially when they don't know much about linux so you're welcome ;)

---

### Post by krklabunde on 2007-11-06
Splash screen works, you fixed my boot problem - can you fix my keyboard and mouse too?  They work while the bios is loading, but stop during the OS selection screen.  Once Ubuntu is loaded, the keyboard and mouse work again.  This is a Logitech wireless keyboard and mouse...Thanks!

---

### Post by frodon on 2007-11-06
For your keyboard problem i think it's not related to ubuntu but to your BIOS setting. So look in your BIOS setting and try to find the option which enable USB keyboard support, once found and enabled reboot and it should be good.

---

### Post by krklabunde on 2007-11-06
Worked...You're good!  Thanks...have a great day!

---

### Post by frodon on 2007-11-06
you too and enjoy ubuntu :)

---

