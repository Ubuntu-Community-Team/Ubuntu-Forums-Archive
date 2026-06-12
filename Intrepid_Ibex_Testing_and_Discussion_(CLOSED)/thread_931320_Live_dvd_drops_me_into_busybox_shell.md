---
title: "Live dvd drops me into busybox shell"
date: 2008-09-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by khiraly on 2008-09-27
Hi!

I downloaded the live DVD iso image from here:
[http://cdimage.ubuntu.com/releases/intrepid/alpha-6/intrepid-dvd-i386.iso](http://cdimage.ubuntu.com/releases/intrepid/alpha-6/intrepid-dvd-i386.iso)

Checked the md5sums, and burn it to a dvd.

If I choose try ubuntu without installing or check the CD for defects (didnt tried the other options), it always drop me into busybox shell.

In the check CD option, I type into the busybox shell an exit command, I get rebooted.

In the 'try ubuntu without installing' option, I type exit, after some minutes it drops me again into the busybox shell.
I see this message on the console:
```

cp: cannot create /root/var/log/: nosuch file or directory
mount: mounting /root/dev on /dev/.static/dev failed: no such
mount: mounting /sys on /root/sys failed: no such
mount: mounting /proc on /root/proc fail
target filesystem doesnt have /sbin/init
no init found try passing init= bootarg

```

When I type this time an 'exit', I get a kernel panic:
```

/init: line 231: cannot open /root/dev/console: no such file or directory
[   ...] Kernel panic - not syncing: Attempted to kill init!
and capslock is blinking.

```

I attached dmesg's to this message:
dmesg-intrepid_livecd_alpha6.txt.zip: dmesg typed to the first busybox shell

dmesg_intrepid_after_exit.txt.zip: dmesg typed into the second busybox shell.

In busybox shell I successfully mounted my normal root filesystem (/dev/sda2)

My hardware details:

I have an Compaq-hp nx9105 notebook. It has an IDE hard drive.

My dmesg on my normal system (ubuntu 8.04 upgraded from 7.10):

dmesg:
dmesg.txt.zip

lspci -vnnn:
lspci-vnnn.txt

uname -a:
Linux buza 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux


If you need more information please just ask for it.

Best regards, 
 Khiraly

---

### Post by Kosimo on 2008-09-27
> **khiraly said:**
> Hi!

I downloaded the live DVD iso image from here:
[http://cdimage.ubuntu.com/releases/intrepid/alpha-6/intrepid-dvd-i386.iso](http://cdimage.ubuntu.com/releases/intrepid/alpha-6/intrepid-dvd-i386.iso)

Checked the md5sums, and burn it to a dvd.

If I choose try ubuntu without installing or check the CD for defects (didnt tried the other options), it always drop me into busybox shell.

In the check CD option, I type into the busybox shell an exit command, I get rebooted.

In the 'try ubuntu without installing' option, I type exit, after some minutes it drops me again into the busybox shell.
I see this message on the console:
```

cp: cannot create /root/var/log/: nosuch file or directory
mount: mounting /root/dev on /dev/.static/dev failed: no such
mount: mounting /sys on /root/sys failed: no such
mount: mounting /proc on /root/proc fail
target filesystem doesnt have /sbin/init
no init found try passing init= bootarg

```

When I type this time an 'exit', I get a kernel panic:
```

/init: line 231: cannot open /root/dev/console: no such file or directory
[   ...] Kernel panic - not syncing: Attempted to kill init!
and capslock is blinking.

```

I attached dmesg's to this message:
dmesg-intrepid_livecd_alpha6.txt.zip: dmesg typed to the first busybox shell

dmesg_intrepid_after_exit.txt.zip: dmesg typed into the second busybox shell.

In busybox shell I successfully mounted my normal root filesystem (/dev/sda2)

My hardware details:

I have an Compaq-hp nx9105 notebook. It has an IDE hard drive.

My dmesg on my normal system (ubuntu 8.04 upgraded from 7.10):

dmesg:
dmesg.txt.zip

lspci -vnnn:
lspci-vnnn.txt

uname -a:
Linux buza 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux


If you need more information please just ask for it.

Best regards, 
 Khiraly

Just a quick question:
Are you may using a nvidia card?
I think you're experiencing the same bug that has been discussed on [this]("http://ubuntuforums.org/showthread.php?t=924202") topic. (If yes, you can may help giving this information in the submitted bug on launchpad, [here]("https://bugs.launchpad.net/ubuntu/+bug/272155"))
Thank you

---

### Post by UbuWu on 2008-09-27
It might be due to this bug, for which a fix has just been released: [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/274076](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/274076)

If you download the latest daily livecd in some days you can see if that fixed it.

---

### Post by khiraly on 2008-09-28
> **Kosimo said:**
> Just a quick question:
Are you may using a nvidia card?


Yes, I use nvidia card. I have an nforce3 motherboard inside my laptop with a geforce4 420 go video card)

I tried what is in the bugreport (boot with extra parameter break=mount wait a little and type 'exit' in busybox), but resulted the same screen as in this topic:
[http://ubuntuforums.org/showthread.php?t=924202](http://ubuntuforums.org/showthread.php?t=924202)

Anyway, thank you for your responses, at least there are relevant bugreports.

I upgraded with apt-get finally.
But for what I upgraded dont work on this kernel either.:(
(I have an usb thumbdrive, and always have a descriptor read error -110 message. It works under windows, and works on 3 different computer (under windows) but not under linux).
For this reason I downloaded the live dvd, to be able test on different computer. The thumbdrive is a 16GB model from Adata.

Best regards, 
 Khiraly

---

### Post by khiraly on 2008-09-28
> **UbuWu said:**
> 
If you download the latest daily livecd in some days you can see if that fixed it.

When alpha7 will come out, I will download and retest, because I dont think it is fixed. (if it is the same problem (need more than 20sec to recognize the cdrom), it should work the mount=break kernel option. Which does not work in my case)

Thanks.

---

