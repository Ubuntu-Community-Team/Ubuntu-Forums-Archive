---
title: "Upgrading BIOS on a Samsung NC10"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by mintlars on 2009-12-19
Hi all

I've using linux (mainly kubuntu) since dapper, so I'm quite comfortable with it by now. However, now I ran into a problem which is pretty alien to me, so I could use some help.

I'm using Ubuntu Karmic on my Samsung NC10 netbook and need to upgrade my BIOS to be able to change brightness (at least according to the [wiki-page]("https://help.ubuntu.com/community/NC10#Karmic%209.10%20%28in%20development%29")). Unfortunately there seem to be a lack of guidance here on the forums on how to do it. The best way I've found so far is to use FreeDOS, that is, making a bootable usb drive and make the upgrade through that.

The part where I'm failing is how to make freedos boot on a usb drive. Here's what I've tried so far and failed:
Using Unetbootin to create a bootable freedos. Results in an invalid opcode error and halts.
Following [this guide]("http://wiki.fdos.org/Installation/BootDiskCreateUSB") at least boots into a DOS-prompt, but lacks the function to run the exe-file needed to upgrade.

This is what I've been trying so far and failed. I still haven't found a good guide on how to do this kind of thing so I'm suggesting that a solution to this thread should go into the ubuntu nc10 wiki so others can find it easily.

Note 1: I'm perfectly aware of the risks involved in upgrading the BIOS, but considering the situations I use my netbook in, I really need to be able to save battery life. Alas, the pros outweigh the cons for me here.

Note 2: The file I'm supposed to use to upgrade can be found [here]("http://www.samsungpc.com/08/products/nc10/firmware.html#firmware"). The 11CA for DOS.

---

### Post by darkod on 2009-12-19
Don't risk your NC10 with BIOS flash. Look in post number #1 here how to add this repository for NC10 and install the package nc10-backlight.
[http://www.voria.org/forum/viewtopic.php?f=3&t=41&sid=b777d3c3db077a656be08722616e3142](http://www.voria.org/forum/viewtopic.php?f=3&t=41&sid=b777d3c3db077a656be08722616e3142)

That will sort out the brightness problem.

---

### Post by cywhale on 2009-12-19
Upgraded my NC10 with Vorias' USB-Updater ([http://www.voria.org/forum/viewtopic.php?f=3&t=248](http://www.voria.org/forum/viewtopic.php?f=3&t=248)) a few weeks ago - worked fine for me.

---

### Post by mintlars on 2009-12-19
> **darkod said:**
> Don't risk your NC10 with BIOS flash. Look in post number #1 here how to add this repository for NC10 and install the package nc10-backlight.
[http://www.voria.org/forum/viewtopic.php?f=3&t=41&sid=b777d3c3db077a656be08722616e3142](http://www.voria.org/forum/viewtopic.php?f=3&t=41&sid=b777d3c3db077a656be08722616e3142)

That will sort out the brightness problem.

That should really go into the wiki. As it is now, it seems like you have to upgrade the BIOS to make brightness control work, which it shouldn't if there's another solution as well.

[quote=cywhale]Upgraded my NC10 with Vorias' USB-Updater ([http://www.voria.org/forum/viewtopic.php?f=3&t=248](http://www.voria.org/forum/viewtopic.php?f=3&t=248)) a few weeks ago - worked fine for me[/quote]

Thanks a bunch. I'll see if I think it's necessary now.

---

### Post by darkod on 2009-12-19
> **mintlars said:**
> That should really go into the wiki. As it is now, it seems like you have to upgrade the BIOS to make brightness control work, which it shouldn't if there's another solution as well.



Thanks a bunch. I'll see if I think it's necessary now.

Yes, you have both options. Personally I chose not to risk my NC10 with flashing the BIOS and went for the nc10-backlight route. That website of Voria is very good for Linux and NC10.

---

### Post by whych on 2010-01-05
I found that the new samsung nc10 bios gives me incorrect display setting for my ubuntu live usb. Plan to go back to the old version.
Samsung aren't renowned for being linux-friendly.

---

### Post by R_U_Q_R_U on 2010-04-30
The easiest way to update the NC10 BIOS is to use a bootable USB drive with FREEDOS. To do this is use UNetbootin to create a bootable USB drive.

HOW TO

1. Download UNetbootin here: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
2. Using UNetbootin, create a bootable USB drive with the FREEDOS option.
3. Get the BIOS DOS updater from Samsung website
4. Copy BIOS DOS uptater to ROOT of you USB drive
5. Boot NC10 using USB drive
6. Change to C:\ drive on your USB drive to see DOS updater file
7.  Execute the DOS BIOS update tool

---

