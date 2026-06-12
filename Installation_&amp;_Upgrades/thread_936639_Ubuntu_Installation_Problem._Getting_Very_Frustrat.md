---
title: "Ubuntu Installation Problem. Getting Very Frustrated"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by daGeneral on 2008-10-03
Here's the thing. I want to do dual boot with vista on my laptop. I downloaded 32-bit version 8.04 Desktop, did checksum, burned to disk and booted from cd. I try to use livecd, and it goes to command line and gives a bunch of errors:

[92.435152] ata2.00: revalidation falied (errno=-5);
[92.530816] ata2: COMRESET failed (errno=-16);
[92.563881] ata2: exception Emask 0x1 SAct SErr 0x0 action 0x0 t4;
[92.563933] ata2: irq_stat 0x40000008;

I try to install, same errors. I have 3 seperate install cds,  both 32bit and 64bit and I get the same errors no matter wat I do (livecd, install, check cd for error)...with 64bit i was able to get to livecd the first time i booted from ubuntu cd. when i reboot same errors ever since.

And the funnything is I can install it as vista app (which is not how i want it)

My laptop config is:
Intel Core2Duo 2.53GHz (T9400)
2GB 1066Mhz Ram
nVidia 9800M GT 512MB

Its a clevo M57 based laptop

---

### Post by melojo on 2008-10-03
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206635](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206635)

Here is a link, don't know if this will help you.

---

### Post by melojo on 2008-10-03
[http://ubuntuforums.org/showthread.php?t=936638](http://ubuntuforums.org/showthread.php?t=936638)
another link that is recent.

---

### Post by daGeneral on 2008-10-03
did what the last link said:
all_generic_ide
acpi=off

old errors+new ones come up

---

### Post by melojo on 2008-10-03
> **daGeneral said:**
> did what the last link said:
all_generic_ide
acpi=off

old errors+new ones come up

Can you post the new errors?

---

### Post by daGeneral on 2008-10-03
i get a long list of errors...so i just installed as a windows app.

now it starts but cant get wifi to work and so cant download the nvidia drivers. Thanx all for the help but this is too much of a hassle. spent the last 5 hours switching between windows n ubuntu tryin to get the wireless (and hence internet workin)

Thanx all u guys for the input though. much appreciated.

I think i'll go back to windows and forget abt linux.

---

### Post by Just_Bri_Thanks on 2008-10-04
I am having the same problem, but I am not quite ready to give up yet.

Installing via windows app isn't an option for me, as the install ap doesn't show the HDD partition I have set aside for Linux.  This is probably due to it being ext3.

The Live CD will start, but it took 15 or so tries to get past the menu where it asks if you want to install or Demo the OS.

Selecting either of those options usually leads me to a busybox command prompt OR a cycling error message that is five lines of text, mostly numbers.

No matter what option I try, so far I have only been able to get into the Demo twice from the live CD, and I haven't successfully booted linux from my HDD at all.

---

### Post by xen-uno on 2008-10-04
Have you guys tried the Alternate CD yet? I couldn't get 7.x Live to install or run on this machine (tried both 32 and 64 bit versions). Went with x64 Alternate and had no serious probs. For 8.x x64, I tried the on-line upgrade but had weird problems after a (apparently) successful installation. With a clean install of the 8.04 x64 Alternate disk, she's been behaving very well.

---

### Post by Just_Bri_Thanks on 2008-10-04
I will try that shortly, next I boot into windows and download it.

Edit:  I just finished a reinstall while I was first making this post (from the live CD) and it seems to have works.  *crosses fingers*

Any idea why the installer is so fickle?

---

