---
title: "can't get into new installation... grub messed"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by banda on 2007-06-10
i just installed ubuntu 7.04 but i can't run it..
in the grub menu none of the options are working.. also it has some how detected vista which i had deleted long ago from my system and does not show my xp :(

when i choose ubuntu from grub it says cannot boot from hd (something)
i m on the live cd now.. can i fix it from here??

---

### Post by OzzyFrank on 2007-06-10
Hi. First of all, always write down any messages you get, coz the first thing people will ask when you say you had an error is "What was it?". Now, I'm just having a guess here it was something like an Error 17, and that the partition couldn't be found. You can use the Live CD to get to a command prompt, and you should just be able to access GRUB commands by typing **grub** at the prompt (I usually use the Super GRUB Disk). Once you have a prompt that looks like** grub>** you can then determine where your GRUB files reside:

**find /boot/grub/stage1**

It will say something like **(hd0,0)**, and note that Linux and GRUB vary on how they call drives: **/dev/hda1** in Linux is** (hd0,0)** in GRUB. If you have Ubuntu on a second drive, it will probably be **(hd1,0)**, which I'll use for the next commands:

**root (hd1,0)**

**setup (hd1)**     {to put it in the mbr of the whole drive}
or
**setup (hd1,0) **  {to put it on the actual partition of Ubuntu}

As you see, when you use the **setup** command to finish it off, you can choose to do it in the mbr or on the partition. I suppose if it is the mbr, you can also choose to put it on the first drive, the Windows drive in most cases, as that is the actual default for an Ubuntu install. Personally, I put it on the partition, as my 1st drive is the Windows one, and I have a great bootloader (Acronis OS Selector) to handle them all. And I think that if you have a bootloader that can handle it, putting GRUB in on the partition is less messy if you want to try a couple other OSes on the same drive.

Anyway, that works for me, and when I click on Ubuntu and get to GRUB and realise I meant to go into Windows (rarer and rarer these days!), I can still choose to boot into Windows. If you just have the one drive, then using GRUB as the menu to choose between Windows and Ubuntu is just fine.

As for GRUB naming your Windows wrong, that could mean nothing (Acronis doesn't know about XP so called it Millennium Edition).

So if you need to reset GRUB, those are the commands to do it, and they have saved me grief a couple times when some thing or another messed it up for me. You just have to work out where to **setup** to, as mbr isn't always the best option.

Hope this is of some help.

---

