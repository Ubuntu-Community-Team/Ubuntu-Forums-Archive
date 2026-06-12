---
title: "Istall ubunto on a barebone machine, no cd, no boot usb..."
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by highkftj on 2009-11-27
Hello to everyone,

I am new to linux and I want to move to this system after bad experiences with windows.
I have also a particular problem. An old laptop is probably able to handle just ubuntu at this point of its life.

The cdrom is gone, the bios doesn't have usb boot support, so I was wondering what other way I can have to install linux on a barebone hd (nothing on it). I thought about pxe and network, but that bios doesn't even support this.

so the only Idea I had was to copy some files on the hd via a ide cable adapter, connecting the laptop hd to the mobo of a desktop. I did the same in the past to install xp: I used msdos 7 to boot the machine and then launch the xp setup from withing the hd (copied before the installation files).

So my question is, can I do the same with linux? in such case, of course I will have a hd formatted with fat32 to boot in msdos, and what files should I copy on this partition and launch for the installation?

If this is not the best path to follow and some guru here can advise me a better way I am looking for his helps. I look on the net but everywhere at least they require a previous operative system on it or some kind of boot support (usb, cdrom, floppy...)

Thanks again :)

---

### Post by highkftj on 2009-11-28
So I did the installation connecting the hd via a usb adapter to my desktop.
Basically I installed instead of my desktop hds sda and sdb, on this third hd sdc. I also told lilo to be installed on the third hd. Then I put back my hd on the laptop.

Everything looked fine, except that during the installation I got a message that I probably should have rerun the lilo configuration once rebooted.

Anyway back the hd in the laptop, lilo seems to start loading linux but what's happen is that the root device cannot be found: after a while the process gave up and return to a shell...

As error I got the following:

"ALERT! /dev/sdc1 does not exist. Dropping to a shell!"

now I checkd under /dev and I have only sda, since in my notebook this is the first hd, while lilo was configured to run on a third hd (sdc)

So how can I edit lilo and where I can find lilo.conf to change the hd name? probably just substituting any sdc with sda.

 this should be easier now for any linux guru :)

---

