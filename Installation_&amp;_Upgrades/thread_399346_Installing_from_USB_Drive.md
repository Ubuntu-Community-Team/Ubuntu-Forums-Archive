---
title: "Installing from USB Drive"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by Majorix on 2007-04-02
Is there like a compact version of Ubuntu that can be loaded on a USB drive and then installed from there using net-install? And if there is how is the procedure? If not, where can I suggest it?

Yeah I have used Debian and I want to see that feature in Ubuntu too, because I have used it often and liked it.

---

### Post by Majorix on 2007-04-02
No USB drive versions?

---

### Post by Aro on 2007-04-02
I wanted to do this yesterday so I figured it out.

I have Xubuntu 6.10 running off a 1 gb usb flash drive. And while I am having a lot of problems, they're mostly because I don't know what I'm doing in Linux ;-)

This is the article I followed, enjoy:

[http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610]("Xubuntu Flash Pen Drive")

---

### Post by Majorix on 2007-04-02
No I don't want to run Ubuntu off flash drive. I want to install Ubuntu on my harddrive using the data on the flash disk.

So any ideas?

---

### Post by me2000r on 2007-04-05
I, too, wish to be able to do this. I have done lots of searching; I've found nothing so far. I found a site about how to create a bootable USB drive using the Windows utility for formatting a floppy drive and MKBT, a utility to copy the boot sector from a floppy to a .bin file and then onto your flash drive. However, that doesn't seem to work with the Ubuntu setup disc.

---

### Post by juice99 on 2007-04-07
*bump*

---

### Post by Aro on 2007-04-08
When I ran xubuntu live off my flash disk it was nothing more than a live CD that I put onto the flash drive...

You can run linux off it just like you can run linux off a live cd...

AND you have the option of installing linux...
just like from live cd's.


So, that IS how you do it :)

---

### Post by me2000r on 2007-04-08
Ideally, though, Linux would be *installed* on that USB drive; instead of having a live cd copied to it, install to the drive and have most (if not all) of the filesystem contained within that device. Unless, and I don't know how Ubuntu live works exactly, one could use Ubuntu Live on a USB drive like I'm suggesting (i.e., save session data automatically/install applications/etc. to the drive just as if it were installed).

---

### Post by Majorix on 2007-04-08
Guys I have found the answer to this. Straight from the official docs:
[https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/boot-usb-files.html)

Just make sure to replace the part of the link for the all-in-one-file (if you choose the easy way) where it says "edgy" with whichever version you want to use.

---

### Post by Aro on 2007-04-09
Keep in mind that flash drives have a limited number of times they can be written to before they go kaput. The number is pretty high, like 10,000 - 100,000 depending on the type of write but...

If you were running your linux off a flash drive for more than just the occasional use (like a live cd), you might find that you'll destroy your flash drives now and again.

Also, when I was running linux off that flash drive (with the live cd copied to it), i could save changes to my settings and they would remain the next time I booted up.

---

### Post by juice99 on 2007-04-10
> **Aro said:**
> Keep in mind that flash drives have a limited number of times they can be written to before they go kaput. The number is pretty high, like 10,000 - 100,000 depending on the type of write but...

If you were running your linux off a flash drive for more than just the occasional use (like a live cd), you might find that you'll destroy your flash drives now and again.

Also, when I was running linux off that flash drive (with the live cd copied to it), i could save changes to my settings and they would remain the next time I booted up.

he is not talking about running Linux from USB, but only installing it...
and thanks for the link Majorix

---

