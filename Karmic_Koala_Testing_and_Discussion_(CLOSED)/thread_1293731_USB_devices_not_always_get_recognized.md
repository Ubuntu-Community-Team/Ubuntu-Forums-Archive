---
title: "USB devices not always get recognized"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by francsal on 2009-10-17
Here´s the thing. I have a ZTE MF626 3G modem, and I can say that it works perfectly with 9.10... IF it gets recognized when I plug it.

Sometimes, whenever I plug the modem, even though the lights turn on, it doesn´t get recognized. I thought that it was a modem problem, so switched back to XP, and it works without a problem there. SO, back in karmic, tried it again, and no joy. When I was doing that, i needed some files from my usb memory stick, so I plugged it, and it didn´t got recognized, either! Obviously, I didn´t had this problems in 9.04

After rebboting several times, it finally got recognized again, and everything works ok. But, the moment I restart/reboot, the problem arises again, requiring some other boots, to make it work.

And it´s not that I don want to reboot or anything, but, also, whenever I try to reboot or restart, the system hangs, so, it´s a bit tedious to keep doing it.

Any ideas? Any help would be appreciated.

Cheers


Frank.

---

### Post by dustgrain on 2009-10-17
I get this too with a cruzer8gig and an ext hdd on Karmic I have too plug the drives in and out until they're recognized and sometimes I need to reboot.

---

### Post by go7Ul1ai on 2009-10-17
I get this too with a Sandisk Cruzer 16Gb Memory stick, a Maxell 4Gb Memory Stick and when trying to connect my Samsung Tocco with a cable.

---

### Post by gmc on 2009-10-18
I'm not sure if this is the same thing or not. I have 3 USB ports on my eeepc 1000he, 2 on the right, one on the left. Any device (Sanza Fuze, Sony Ebook 505, Generic USB thumbdrives) plugged in the the left port gets recognized, but not if I try either of right ports. If I boot the system up in Jaunty, all three ports work as advertised.

Is this the same type of problem or something new?

G

---

### Post by zefew on 2009-10-19
I have two Sansa Clip multimedia players (8GB and 1GB).

Both devices were recognized on Ubuntu Gutsy without any problem,
but neither gets recognized on Karmic (beta).
I dist-upgrade every day but no progress so far. 

Karmic doesn't recognize my CD/DVD drive as well (which Gutsy did).
I find it fascinating that an Ubuntu two years ago does a much better
job in recognizing devices than the newest Ubuntu.

Maybe being "beta" gives us an excuse, but I hope the dev team will recover
the Ubuntu quality there had been before the official Karmic release.

---

### Post by Abdullahnz on 2009-10-26
Hi Frank,

My MF626 works just fine under Karmic. It is plug n play every time.

To achieve this I reconfigured the modem to load directly as a 'real modem', skipping the CD autorun.

I wrote a brief guide here:

[http://ubuntuforums.org/showthread.php?t=1302235](http://ubuntuforums.org/showthread.php?t=1302235)

---

### Post by eschvoca on 2009-10-27
Hi,

I had the same problem and tracked down the issue with "git bisect" to this [commit]("http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.30.y.git;a=commitdiff;h=b79e83bdd961ec9b862191c0df51aaeb3cb85664"):

> diff --git a/drivers/input/input.c b/drivers/input/input.c
index 913392f..a79c833 100644 (file)
--- a/drivers/input/input.c
+++ b/drivers/input/input.c
@@ -1551,7 +1551,6 @@ int input_register_handle(struct input_handle *handle)
                return error;
        list_add_tail_rcu(&handle->d_node, &dev->h_list);
        mutex_unlock(&dev->mutex);
-       synchronize_rcu();
 
        /*
         * Since we are supposed to be called from ->connect()


If I put "synchronize_rcu();" back into drivers/input/input.c and recompile the kernel then it works for me.

I'm currently working with the developers so they can get a high quality fix.  It seems that some other part of the system is missing the call and while my fix above works it is not optimal because it slows down boot-up.  

Please find a guide of how to download the kernel sources and add the line back to the file and install the kernel.  After making the fix and appending ".fix" to the EXTRAVERSION number in Makefile, I ran:

> $> make-kpkg clean && CONCURRENCY_LEVEL=4 time nice fakeroot make-kpkg --initrd --revision=custom.1.0 kernel_image && dpkg -i ../*.deb

Please report if the fix works for you.

Thanks.

---

### Post by eschvoca on 2009-10-27
Hi,

BTW, my usb2PS2 keyboard adapter and USB bluetooth dongle would fail to be recognized on about 70% of my boot-ups.

Thanks.

---

