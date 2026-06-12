---
title: "How to change default OS in new grub version"
date: 2010-04-26
forum: Installation &amp; Upgrades
---

### Post by kwalters on 2010-04-26
I have just installed Ubuntu 9.10 on a laptop previously running 8.10

I am unable to change the default OS in Grub from Ubuntu 9.10 as I cannot find /boot/grub/menu.lst.

How do you change the default OS in this newer version of Grub, please?

Thanks

---

### Post by quadproc on 2010-04-26
> **kwalters said:**
> I have just installed Ubuntu 9.10 on a laptop previously running 8.10

I am unable to change the default OS in Grub from Ubuntu 9.10 as I cannot find /boot/grub/menu.lst.

How do you change the default OS in this newer version of Grub, please?

Thanks
You apparently are now using grub2, aka grub-pc.  The bootloader has changed a lot.

The file which contains the list of things to boot is now called grub.cfg and you will find the default entry in it.  The old menu file is not used with grub2.

quadproc

---

### Post by CLEARviewF on 2010-04-26
Look at the web for tutorials about "editing or customizing Grub2 in Ubuntu"
Even better: look at the Ubuntu Documentation for that matter.

like [this one]("https://wiki.ubuntu.com/Grub2")

And this [exactly what you want]("https://wiki.ubuntu.com/Grub2#grub (/etc/default/grub)")

And take your time to read, then you will find what you want.

good luck!

---

### Post by null_pointer_us on 2010-04-26
Lots of info here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Apparently, the two commands you want are:

```
grep menuentry /boot/grub/grub.cfg
```

...which will give you a list of menu entries, and...

```
sudo grub-set-default X
```

...to see the default to menu entry number X.

NOTE: Menu entry numbers start at zero, not at one.

---

### Post by Dayofswords on 2010-04-26
is it me or was grub 1 better in some ways...

---

### Post by wilee-nilee on 2010-04-26
If this is a dual boot or multi boot startup manager is the easiest way to make a OS default, it is in synaptic.

---

### Post by plus2plus on 2010-04-26
OK This is what you have to do -> Open a terminal window and type:
> cd ..
cd ..
cd /etc/default
sudo gedit grub
The GEdit window will pop-up and the only line you have to change is this one:
> GRUB_DEFAULT=0
Change the 0 to whatever number your windows OS is located at when your computer starts (remember that the list is zero-based) so if your Windows is number 7, you should change it for this:
> GRUB_DEFAULT=6
Then you click on save, close GEdit and type this:
> sudo update-grub
And that’s it!!! Now every time you start your machine or reboot it, it will default to Windows, or whatever OS you want it to go by default for that matter… Hope it helps.

---

### Post by wilee-nilee on 2010-04-26
> **plus2plus said:**
> OK This is what you have to do -> Open a terminal window and type:

The GEdit window will pop-up and the only line you have to change is this one:

Change the 0 to whatever number your windows OS is located at when your computer starts (remember that the list is zero-based) so if your Windows is number 7, you should change it for this:

Then you click on save, close GEdit and type this:

And that’s it!!! Now every time you start your machine or reboot it, it will default to Windows, or whatever OS you want it to go by default for that matter… Hope it helps.

Your not supposed to edit grub2 without backing up the original GO AWAY.

---

### Post by kwalters on 2010-04-29
Many thanks for all of the replies.  As President of the "I hate using a terminal window when a GUI is available" Society of Great Britain, I leave you to guess which of the suggestions I went to first

Like one of the respondents, I actually prefer Grub 1; I cannot see anything it does that version 1 did not do

Thanks again

KW

---

### Post by uncleV on 2010-04-29
Then take a look at "sbm" in Synaptic and may be install it?

> Smart Boot Manager (SBM) is a full-featured boot manager

Smart Boot Manager (SBM) is an OS independent and full-featured boot
manager with an easy-to-use user interface.

The main goals of SBM are to be absolutely OS independent, flexible
and full-featured. It has all of the features needed to boot a variety
of OSes from several kinds of media, while keeping its size no more
than 30K bytes. In another words, SBM does NOT touch any of your
partitions, it totally fits into the first track (the hidden track)
of your hard disk!

Main features:
  * Automatically searches drivers and partitions
  * Powerful Boot Schedule
  * Booting from CD-ROM
  * Swapping driver ID
  * Auto Delay Boot
  * Sending keystrokes to the operating system
  * Easy Customized Theme file
  * Password protection
  * Y2k bug work-around for old BIOSes

Canonical does not provide updates for sbm. Some updates may be provided by the Ubuntu community.

---

