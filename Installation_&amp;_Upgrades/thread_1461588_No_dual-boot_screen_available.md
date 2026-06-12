---
title: "No dual-boot screen available"
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by PyroFX on 2010-04-24
I am completely new to Ubuntu and recently installed Ubuntu 9.10 using the live CD.  I allowed the set-up to install Ubuntu next to Windows XP and to let me choose which OS boots at start-up.  Upon restarting my computer after installation, however, there is no boot-screen and my computer goes straight to WinXP.

I have done some reading and it seems like I need to install GRUB, but I'm really not sure if this is really the case or if I am missing something else entirely.

---

### Post by ingramproductions on 2010-04-24
Add xp to the grub boot menu (grub is already installed, and it should have added xp automatically). It's in the /boot folder. I think it's called list.menu or boot.menu or something like that.

---

### Post by plus2plus on 2010-04-24
I figured it out! It was my hard drive boot priority in my bios.  It had  my raid array with windows Vista as first boot device so I switched it  to my single HD that I installed XP on first.  Now it loads the dual  boot menu for XP and Vista without needing a windows system CD in the  drive.  Kudos to Rick P. aka raph on the howtogeek forums for pointing  me in the right direction. Hopefully if nothing else this thread will  help others having the same problem with their gaming rigs. :confused:

---

### Post by PyroFX on 2010-04-24
> **ingramproductions said:**
> Add xp to the grub boot menu (grub is already installed, and it should have added xp automatically). It's in the /boot folder. I think it's called list.menu or boot.menu or something like that.

Well, I found /boot/grub, but the only thing in it is "grubenv" which is a text file saying "# GRUB Environment Block" followed by a long line of more pound symbols

---

### Post by PyroFX on 2010-04-24
Also, if I go into the terminal and type "sudo grub" (which was suggested on one site) I am told that the command was not found. If  I type "grub" I am told that: "The program 'grub' is currently not installed. You can install it by typing: sudo apt-get install grub"

Is that what I should be doing?

---

### Post by wilee-nilee on 2010-04-24
> **PyroFX said:**
> Also, if I go into the terminal and type "sudo grub" (which was suggested on one site) I am told that the command was not found. If  I type "grub" I am told that: "The program 'grub' is currently not installed. You can install it by typing: sudo apt-get install grub"

Is that what I should be doing?

So it is sudo update-grub from a Ubuntu terminal if you have it booted. This will look for XP. I would post this boot script though it will get you the help you need.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by PyroFX on 2010-04-24
> **wilee-nilee said:**
> So it is sudo update-grub from a Ubuntu terminal if you have it booted. This will look for XP. I would post this boot script though it will get you the help you need.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

The results are attached.__

---

### Post by wilee-nilee on 2010-04-24
I'm not the one that will be able to help you with this, you might consider pasting the script in code tags so that it is a easy read. I do see 2 HD with  both having boot flags, and the Ubuntu install in sdb and the grub boot loader in sda. It may be only that you need to change the boot order of the bios to look at one or the other 1st, I am not sure if any of this is correct. There are several people on the forums that are very good at diagnosing, and your on at the right time of day, they are probably around or will be soon.

---

### Post by PyroFX on 2010-04-24
Actually, that worked! I had to change the boot order.  I have never really messed with setting computer to dual-boot and this is the first computer I've had with two hard drives, so I didn't really think that it could be the bios.

Thanks

---

### Post by wilee-nilee on 2010-04-24
> **PyroFX said:**
> Actually, that worked! I had to change the boot order.  I have never really messed with setting computer to dual-boot and this is the first computer I've had with two hard drives, so I didn't really think that it could be the bios.

Thanks

That is great, like I said I am hesitant to advise in this area, but once in a while I am lucky. I check out the answers from the people I know who are really good at this and the scripts people post.

---

