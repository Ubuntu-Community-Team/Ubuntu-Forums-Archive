---
title: "How to install in &quot;live mode&quot; (OS on HDD but no changes on reboot)"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by edgar83 on 2010-02-14
Hello everybody!

Some time ago I read that it's possible to install ubuntu in a sort of "live mode", so that when you reboot the machine, no change has been written to the disk.


Anyone knows how to do that?

Thanks a lot and excuse my bad English! :redface:

---

### Post by darkod on 2010-02-14
It's not installing it, and that's why it doesn't write anything to the hdd. Download the Desktop 32bit or 64bit ISO and burn a cd at low speed, not more than 8x. When you boot with that cd the first option in the menu should be Try Ubuntu without changes to your computer.
If you select that it will load the so called live desktop, ubuntu running from the cd. You can see how it works, even browse the internet on a wired and sometimes wireless connection (depending if it can recognize your card). After you shut down there are no changes to your hdd.
You could also create live usb from the ISO if you need to use that instead of cd.

---

### Post by edgar83 on 2010-02-14
Thanks for the answer, I now that I can boot from a LIVE cd, but I'm asking for a method to boot from the hard disk, a real ubuntu installation AS IF it was a live cd, some time ago I read about it on internet...

---

### Post by darkod on 2010-02-14
I don't know what you mean "as if it was a live cd".
You can have a bootable live usb, in fact the same as cd but on usb stick which will be able to boot the live desktop and which you can also use to install ubuntu.
You can also have full installation made to a usb hdd (or large enough stick) that you can also boot, and it runs the same like int hdd install, you can install software, make updates, etc. Is that what you meant?
Take a look here also, I just explained how to install it and to watch out where grbu2 goes:
[http://ubuntuforums.org/showthread.php?t=1406599](http://ubuntuforums.org/showthread.php?t=1406599)

---

### Post by edgar83 on 2010-02-14
Ok let me explain...

What I want is an hdd installation, with customized programs, configuration etc. that after a setup stage, work like a LIVE cd, so if for example I create a text file on my desktop, or change the screen resolution, and then reboot the system, I will not find the file created, and the changed resolution.


I know it can be done, I read about it, in a thread talking of a way to speed up an ubuntu system on a netbook with very slow ssd. The problem is that I can't find anymore that thread :(

Bye!

---

### Post by darkod on 2010-02-14
OK, I don't know how to do that. :(

---

### Post by snowpine on 2010-02-14
The simplest way is using [Unetbootin]("http://unetbootin.sourceforge.net").

I am not sure it will speed up your netbook though. I've always found running from a Live CD to be slower than once Ubuntu is installed because the filesystem is compressed and must be uncompressed "on the fly."

---

### Post by Mark Phelps on 2010-02-14
I think you must have misunderstood the thread you read because EVERY Ubuntu installation needs to write files somewhere.

In the case of a LiveCD, it creates a RAMDISK (a virtual drive using system memory), and write its files there.

In the case of installing to a USB stick, it writes the files there.

In the case of installing to your hard drive, it writes the files there.

So, what you're asking -- install Ubuntu to hard drive but not write any files there -- is not possible.

---

### Post by edgar83 on 2010-02-14
Thanks for the answers!

The only solution I can find at this point, is to use a LIVE iso image on the hard disk, right?

In this case is there a way to customize the LIVE iso? (default user, application, system settings)

---

### Post by C.S.Cameron on 2010-02-14
If you use Windows UNetbootin for Windows to install to C drive, it writes sort of a virtual "Live CD" that you can boot from. this is usefull for installing Uvuntu if you have no CD drive or pendrive.
You can delete it next time you boot Windows.

UNetbootin is a free download for either Windows or Linux. It can also be used to install a "Live CD" to pendrive.

---

