---
title: "Can't get Ubuntu Back after fixmbr"
date: 2005-10-03
forum: Installation &amp; Upgrades
---

### Post by BarbiGirl8 on 2005-10-03
A little background...

Before I started farking with things, I had Ubuntu and Windows XP on the same hard drive, 2 different partitions. XP being the first, and Ubuntu being the second.

Then I got a second hard drive and decided to play around and installed debian on it. It loaded into the Grub without any problems. Well, here is where things got sticky.

After a week or so I decided that I was tired of playing around with straight debian, and while I was in windows, I reformatted my secondary hard drive. Which at the time I didn't think anything of it, until about a week later when I decided to reboot. (insert screams here)

When I rebooted, I got a grub error 17. So I pulled the hard drive and then I got a grub error 21.

After many attempts of trying to fix grub, I finally just booted with the Windows XP CD and went into recovery mode and did a FIXMBR

Well, now I can get into Windows XP just fine, but any attempts to get a dual boot back into Ubuntu have all failed.

My last attempt was as follows:

```

Boot from Live CD
Launch Root Console
grub
find/boot/grub/stage 1 * which was (hd0,1)*
root (hd0,1)
setup (hd0,1)
*It went through the setup no problems*
quit
reboot

```

So, I rebooted and it just went straight back into Windows.

Several months ago when I had first installed everything, I had fubared the Grub Loader, but that time it would only boot windows as well and I was looking though my ntoes and came across the following notes, but when I tried them from a Install CD, it didn't like it. 

```

Boot from Install CD
Ctrl + Alt + F2
Enter
mkdir /ubuntu
fdisk -l /dev/discs/disc0/disc *this is the line that it didn't like*
mount /dev/hda1/ubuntu
grub
>root (hd0,0)
>setup (hd0)
>exit
chroot /ubuntu

```

Any help would be appreciated. I've been working on this for 2 days now and I'm starting to get frustrated.

Thanks.

---

### Post by BarbiGirl8 on 2005-10-03
Nevermind.... 

I just attempted the boot from the install cd, fake out the partioner, and jump to Installing the GRUB and everything's honkey dorey.

Ok, I admit, I thought that idea was a little far fetched, but I aplogize to the person who posted it. And I bow in their presence.

---

