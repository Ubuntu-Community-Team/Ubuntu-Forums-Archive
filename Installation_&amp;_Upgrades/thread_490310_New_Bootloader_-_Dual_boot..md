---
title: "New Bootloader - Dual boot."
date: 2007-07-02
forum: Installation &amp; Upgrades
---

### Post by cmgannon26 on 2007-07-02
Hello all.

I'm not quite sure this is the appropriate forum, but it sounded the best due to the whole bootloader installation portion of my question.

My system is configured as follows:

/dev/sda = Hard Drive 1 = Ubuntu 7.04
/dev/sdb = Hard Drive 2 = Win XP

The system was not set up for dual boot. As an alternative, I have been unplugging/plugging in the alternate drives to boot to the other OS. (Windows was added as an afterthought and I've only been doing this for a few days now.)

For obvious reasons, I'd like to install a modified GRUB bootloader to select which OS to boot upon booting. Right now, it boots to windows (installed last) when both drives are installed.

Any help would be appreciated.

---

### Post by LaRoza on 2007-07-02
Easy, type:

```

sudo mv /boot/grub/menu.lst /boot/grub/menu.bk

```
This backs up your grub settings.

Now you will need to edit grub to add the second hard disk to the grub menu at start up.

```

gksudo gedit /boot/grub/menu.lst

```

You will see in this file a lot of lines that begin with #. Those are comments. You will also see a section at the bottom that is not commented out, it will probably have three sections, with the word Ubuntu in them and a memtest. These are what are in the grub menu.

Find the commented out section, that has the words "Windows in it". Copy that to the end of the list, get rid of the comments in the copy. Change the first "0" in the "hdd(0,0) to a "1". (That is the number one)

You can change the description also.

Sorry I can give you the exact setting so you can just copy and paste, I am away from Ubuntu at the moment.

There is also a "hiddenmenu" setting, if that is comments out, delete the # so you can see the menu without pressing esc.

---

### Post by cmgannon26 on 2007-07-02
Okay... I've swapped my drives around a bit so the Ubuntu one is the first in order to boot. It loads grub fine and I'm able to boot Ubuntu. Unfortunately when I go to boot XP, it hangs at "Starting up ..."

Any ideas for a working loader?

It's set to hd(1,0) by the way in menu.lst.

---

### Post by logos34 on 2007-07-02
Add mapping (and savedefault) options:

> [B]title		Windows XP
root		(hd1,0)
map            (hd0) (hd1)
map            (hd1) (hd0)
makeactive
savedefault
chainloader	+1[/B]

Then change /boot/grub/device.map to look like this:

> [B](hd0) /dev/sda
(hd1) /dev/sdb[/B]

edit: you need the map lines because you're using grub to boot windows on a non-first hard drive (i.e. second in Bios order)

---

