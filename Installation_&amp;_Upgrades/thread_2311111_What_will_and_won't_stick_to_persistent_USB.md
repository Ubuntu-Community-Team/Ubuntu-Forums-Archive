---
title: "What will and won't stick to persistent USB?"
date: 2016-01-24
forum: Installation &amp; Upgrades
---

### Post by t0p on 2016-01-24
My HP15 laptop does not have working wifi drivers out of the box.  I haven't been able to install Ubuntu to the laptop so I've been playing with live usb.  I found that if I use unetbootin to make a persistent live usb of 14.04.3, then install the wifi driver (sudo apt-get install bcmwl-kernel-source) the software installs but is not persistent.  If, however, I use the Pendrivelinux utility, and then run the command to install the wifi driver, the command does not complete in the terminal, ending in CRYPT SETUP errors; but the driver *does* install, and what is more, it is persistent - shut down, start up again, and the live usb has wifi working.

Also, Firefox extensions seem to be persistent: I installed a youtube-downloading add-on, which remains after shutdown.

I'm wondering if anyone else has experimented with this, and what other types of items will stick to a live usb?  For instance, ubuntu-restricted-extras and dvd-decryption?  Non-default applications?  And what parts of the file system are, or are not, persistent.  I'll do more experimentation myself, and I'll report my results; but my internet access is via a tethered phone, which means I have limited, relatively costly data allowance (basically paying per GB).  If anyone with conventional broadband has any info, I'd love to know.  Also, is there anywhere on the net where this info might be found?  I've looked, but not an in-depth search yet - like I said, every byte costs.

Cheers.

---

### Post by mastablasta on 2016-01-25
how about this.: [http://askubuntu.com/questions/295701/what-would-be-the-differences-between-a-persistent-usb-live-session-and-a-instal](http://askubuntu.com/questions/295701/what-would-be-the-differences-between-a-persistent-usb-live-session-and-a-instal)

it saves a couple fo settings and drivers should be saved (kept on reboot) as well.

you can install drivers on PC maybe with a .deb file. that might solve the issue.

---

### Post by C.S.Cameron on 2016-01-25
You can not easily update the kernel of a persistent drive, I have not had success making video drivers persistent since 8.04.

---

### Post by sudodus on 2016-01-25
You can store files and install 'regular' program packages in ***persistent live*** drives. You can save tweaks (which are often stored as hidden files in the home directory). But you cannot [easily] update the kernel because the kernel from the live system will be started and used before the system is ready to read the persistent data (from the casper-rw file or partition). To be clear: I don't know how to get the kernel updated except by getting a new iso file.

But it is possible to run an ***installed system*** from a USB drive. Maybe you can try according to the following links. If you want a pendrive with a live **and** an installed system, that works in UEFI and BIOS mode, you can try

[A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode]("http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506") and

[Compressed image file with a live Ubuntu 14.04.2 and an installed Ubuntu 15.10](http://ubuntuforums.org/showthread.php?t=2213631&page=4&p=13426191#post13426191)

The installed system can be updated/dist-upgraded 'as usual' with linux operating systems, but you must take special care with the booting in UEFI mode - do some manual editing, which is also described [in this post (and adjacent posts #63-66)](http://ubuntuforums.org/showthread.php?t=2259682&page=4&p=13426213#post13426213).

***Edit:*** Unfortunately this implies a big download if you want to use my compressed image file, but you can also create the system (or a similar system) yourself from an iso file, that you have already.

---

### Post by t0p on 2016-01-25
> **C.S.Cameron said:**
> You can not easily update the kernel of a persistent drive, I have not had success making video drivers persistent since 8.04.
Indeed that's what i found using unetbootin (i installed wifi driver to the kernel but it wasn't persistent), but with pendrivelinux the driver installation did NOT complete successfully, but the command DID put the driver in, and it has remained persistent.  Different results with different tools.  I'm intrigued, but my puny internet connection thwarts my wish for further play time.  Hence my request from ubuntunauts who own a space elevator rather than my costly solid-fuel rocket.  :)

Thanks for the link to your guide to making a portable ubuntu.  That might be the answer to my inability to install ubuntu to my evil HP UEFI monster.  Yes, a big download, but I think maybe I can let the public library pick up the tab?

I have given the guide only a cursory look so far, and it seems scary.  I'm not afraid of rolling up my sleeves and getting into a terminal, but many of the tools you mention are unfamiliar to me.  But at least (it looks like) I won't run the risk of bricking my evil yet necessary laptop...

> **mastablasta said:**
> how about this.: [http://askubuntu.com/questions/295701/what-would-be-the-differences-between-a-persistent-usb-live-session-and-a-instal](http://askubuntu.com/questions/295701/what-would-be-the-differences-between-a-persistent-usb-live-session-and-a-instal)

it saves a couple fo settings and drivers should be saved (kept on reboot) as well.

you can install drivers on PC maybe with a .deb file. that might solve the issue.

A question: when creating a persistent usb, how much space can be allocated as persistent?  Or, to make the question less nonsensical (ie "how long is a piece of string?" is not a sensible question I think): how much of the drive does ubuntu require that is *not*&#8203; persistent?  So, for example, if I'm using a 32GB stick... how much can I make persistent, and how much must be left non-persistent?  I'm assuming you can't make the whole thing persistent.  Or can you?  As readers of this thread may have noticed by now, I am very new to this persistence lark.

---

### Post by sudodus on 2016-01-25
Good idea to go to the library and download the image file there!

You are welcome to ask, if you need help :-)

---

### Post by sudodus on 2016-01-25
> **t0p said:**
> A question: when creating a persistent usb, how much space can be allocated as persistent?  Or, to make the question less nonsensical (ie "how long is a piece of string?" is not a sensible question I think): how much of the drive does ubuntu require that is *not*&#8203; persistent?  So, for example, if I'm using a 32GB stick... how much can I make persistent, and how much must be left non-persistent?  I'm assuming you can't make the whole thing persistent.  Or can you?  As readers of this thread may have noticed by now, I am very new to this persistence lark.

If you use a casper-rw ***partition*** (and not a file), you can use as much as you want. (I have tested with a 4 TB HDD ;-)) The image of the iso file needs about 1 GB (a bit more or less depending on the version and flavour). Lubuntu is smallest of the Ubuntu flavours and needs around 800 MB. mkusb can create persistent live drives with a casper-rw partition automatically. See [this link](https://help.ubuntu.com/community/mkusb/persistent).

---

