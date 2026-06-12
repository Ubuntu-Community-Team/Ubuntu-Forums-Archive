---
title: "Installing Windows After Ubuntu?"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by cmillican on 2007-07-09
I have Ubuntu on my desktop, and I'd like to be able to sync my Zune, and since there seems to be no way for that yet in Linux, I think I'll just install Windows XP on a small partition and use my external hard drive for the media. I read a little bit a while back about installing Windows after Ubuntu...I just remember they said something about not being able to boot into Ubuntu without reinstalling GRUB (that may be wrong...I don't remember much about what was said)...anyways, I was wondering if anyone could advise me on this.

Installing WinXP fresh and THEN installing Ubuntu would be nice, but I already have Ubuntu kinda situated how I want it (programs, games, preferences, etc....), so if I could it would be nice to just be able to install Windows.

Thanks,
Chris

---

### Post by merlinus on 2007-07-09
You will have to reinstall grub after installing windows.  You can do it from the live cd.

-merlin

---

### Post by cmillican on 2007-07-09
I have several Live CD's here to give to friends and all...how would I tell it to install GRUB?

---

### Post by merlinus on 2007-07-09
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_restore_GRUB_menu_after_Windows_installation](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_restore_GRUB_menu_after_Windows_installation)

-merlin

---

### Post by gauravp55 on 2007-07-09
> **cmillican said:**
> I have several Live CD's here to give to friends and all...how would I tell it to install GRUB?

Boot from the LiveCD and wait till you get to the Terminal Window.. After that you need to do the following:

1> Open the terminal and type Sudo fdisk -l. This should give you all the partitions on your hard disk so that you could locate Ubuntu's root partition.

2> type sudo grub
3> You'll get the grub prompt: grub> and then u gotta proceed as follows:
4>  grub> root (hda,x) (a is ur hd no. and x is the partition no... This has to be Ubuntu's root partition)
5> grub> setup (hda)
6> grub> quit

And your done.. Restart and you'll see GRUB showing up.

---

### Post by cmillican on 2007-07-09
Thanks a bunch guys.

---

