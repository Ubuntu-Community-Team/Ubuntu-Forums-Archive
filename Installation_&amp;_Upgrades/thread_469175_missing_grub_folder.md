---
title: "missing grub folder"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by f3nol on 2007-06-09
Hello everybody!

I've recently installed Xubuntu Feisty and after rebooting I'm getting grub error 15. After running from LiveCD I've noticed that there's no 'grub' folder in my /boot folder.
When I'm trying 'sudo grub-install /dev/hda1' or /dev/hda I'm getting this error: Could not find device for /boot: Not found or not a block device.
And this is fdisk -l output:

Disk /dev/hda: 2111 MB, 2111864832 bytes
255 heads, 63 sectors/track, 256 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         237     1903671   83  Linux
/dev/hda2             238         256      152617+   5  Extended
/dev/hda5             238         256      152586   82  Linux swap / Solaris

Could anyone help me install Grub properly without reinstalling the system?
Thanks in advance for any help :)

---

### Post by merlinus on 2007-06-09
You might try this:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Another thing is that you may be looking at /boot of the live cd, not /boot of your ubuntu partition.

-merlin

---

### Post by f3nol on 2007-06-09
Hey  merlinus!
thanks for the link, I'll try it as soon as I'll have a chance.

> Another thing is that you may be looking at /boot of the live cd, not /boot of your ubuntu partition.

I'm looking at my mounted ubuntu partition. There actually is /boot/grub/ on live cd, unfortunatelly not on my partition 
Thanks again :)

f3nol

---

### Post by taurus on 2007-06-09
What's the output of the third command from a terminal while in LiveCD?

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
ls -la /mnt/ubuntu/boot/grub
```

---

### Post by Pumalite on 2007-06-09
> **f3nol said:**
> Hey  merlinus!
thanks for the link, I'll try it as soon as I'll have a chance.

I'm looking at my mounted ubuntu partition. There actually is /boot/grub/ on live cd, unfortunatelly not on my partition 
Thanks again :)

f3nol

You might try a Knoppix Live CD with this recipe:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Good luck.

---

### Post by f3nol on 2007-06-10
Thanks everyone for your replies,
I didn't try suber grub cd yet and am about to try the Knoppix cd too. I'll let you know how it went. And that's what happens when I type what taurus posted
> ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
ubuntu@ubuntu:~$ ls -la /mnt/ubuntu/boot/grub
ls: /mnt/ubuntu/boot/grub: No such file or directory

f3nol

---

### Post by f3nol on 2007-06-15
ok, it's solved now.
It wasn't just a grub problem but looks like some bug in the installer. After installing my Xubuntu Feisty few times with different partition settings and diffrent grub localizations I realised that it wasn't only /boot/grub/ catalog missing but my /home catalog was empty too after each installation. It looked like the installer was installing only the base system and was quitting the installation. The process was suspicoously quick (about 5mins.) and after the installation it didn't ask to reboot or anything.
So finally I burned alternate cd and installed my system from it without any problems.
Thanks again for all your help.

---

