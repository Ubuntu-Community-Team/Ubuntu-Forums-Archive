---
title: "Grub error 22"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by chejose on 2007-08-16
I had a dual system, Windows with Ubuntu. For varios reasons I decided to remove Windows.

I did the HD into 3 partitions, and installed using the Feisty CD.

when finished, and I tried to boot into Ubuntu, I got a message:

GRUB loading stage 1.5
Error 22

Thanks for help to solve this.

José

---

### Post by merlinus on 2007-08-16
Grub error [FONT=Helvetica,Arial,sans-serif] 22 : No such partition
This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.

Did you completely erase both windows and ubuntu, or reinstall?

Maybe this will help:

[/FONT]Boot from live cd, and post results of this:

```

sudo fdisk -l
blkid

```

Also, you can mount your linux partitions manually:

[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_a_reiserfs_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_a_reiserfs_filesystem)

Then navigate to the mount point for / and post /etc/fstab and /boot/grub/menu.lst.

Also, you might try reinstalling grub first.
```

sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hdx)
quit

```
Substitute results from find for (hdx,x).

-merlin

---

### Post by chejose on 2007-08-17
Merlinus

Thanks for your suggestions. What I wanted was a clean installation of Linux. So what I finally did was erase all partitions and format the drive. With that the installation stuck.

Many thannks,

Jose

---

### Post by ryanawall on 2007-08-25
I am having a similar problem. I was running Ubuntu and  Vista on the same computer.  I tried to get rid of Windows Vista and when I restarted my computer I got  Grub error 22. So I poped in the Ubuntu live cd thinking I could just reinstall. It gets to a point where it asks for my username and password. I entered them and it doesn't even recognize them. What can I do to get Ubuntu back up?

---

### Post by Pumalite on 2007-08-25
Follow all of merlinus suggestions. If you continue to have problems; post back.

---

### Post by ryanawall on 2007-08-25
I can't even get into the terminal to type in those commands. Is there another way to get there?

---

### Post by Pumalite on 2007-08-25
Can you boot a Live CD?

---

### Post by ryanawall on 2007-08-25
Yes, I get the main screen and I click on run/install Ubuntu then I get a screen asking for username and password (they won't work anymore).

---

### Post by Pumalite on 2007-08-25
Besides downloading a new iso, doing md5sum, burning at 4x, etc; if it doesn't work, then start afresh. Use DBan: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)
Then Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) and then install again; this time without Vista. By now you see the problem that it represents. Did you try to re-install Grub? I'm sure you could boot it: Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by ryanawall on 2007-08-26
Thanks a lot. Finally got it up and running (with no windows!) Couldn't have done it without you.

---

### Post by Pumalite on 2007-08-26
Glad it worked for you!.

---

