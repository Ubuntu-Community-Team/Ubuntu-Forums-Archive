---
title: "windows issues"
date: 2010-01-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by SeePU on 2010-01-23
I can't believe no one has posted yet on the bugs regarding having a window open, any Nautilus window or even Synaptic's window.   There is no resizing, moving it or minimizing it or shutting it down via 'windows style' 'x.'

It also hangs sometimes.

This is a major bug and I'm wondering if it has been reported or documented yet.

---

### Post by BackwardsDown on 2010-01-23
> **SeePU said:**
> I can't believe no one has posted yet on the bugs regarding having a window open, any Nautilus window or even Synaptic's window.   There is no resizing, moving it or minimizing it or shutting it down via 'windows style' 'x.'

It also hangs sometimes.

This is a major bug and I'm wondering if it has been reported or documented yet.

No problems here.

---

### Post by SeePU on 2010-01-23
it doesn't reboot properly either.

init: ureadahead-other main process (1370) terminated with status 4
init: ureadahead-other main process (1371) terminated with status 4
* Starting init crypto disks...

WTH?

---

### Post by kansasnoob on 2010-01-23
> I can't believe no one has posted yet on the bugs regarding having a window open, any Nautilus window or even Synaptic's window. There is no resizing, moving it or minimizing it or shutting it down via 'windows style' 'x.'


I haven't seen that behavior here.

> It also hangs sometimes.

What do you mean by "hangs"? Does it lock up completely? Need a much better explanation :)

> it doesn't reboot properly either.

init: ureadahead-other main process (1370) terminated with status 4
init: ureadahead-other main process (1371) terminated with status 4
* Starting init crypto disks...

Yes, the "quiet" isn't quiet yet.

> WTH?

This is an Alpha 2. It's under heavy development. As it says at the top of this forum category:

**Ubuntu Lucid Lynx is in development, use only for testing purposes!!!**

---

### Post by VMC on 2010-01-23
> **SeePU said:**
> I can't believe no one has posted yet on the bugs regarding having a window open, any Nautilus window or even Synaptic's window.   There is no resizing, moving it or minimizing it or shutting it down via 'windows style' 'x.'

It also hangs sometimes.

This is a major bug and I'm wondering if it has been reported or documented yet.

Same behavior using the LiveCD or just the installed one?
List your hardware specs.

---

### Post by SeePU on 2010-01-23
> **VMC said:**
> Same behavior using the LiveCD or just the installed one?
List your hardware specs.
LiveCD.

I don't know if it would happen with the Live CD.  I was thinking of trying the install to just test.  But, if it is still really buggy, how do I recover the bootloader since Grub 2 would be installed to the MBR?

I have another Linux OS installed and XP also.

My specs (for my laptop):
IBM Thinkpad T41, Radeon Mobility 9000 FireGL graphics card, Intel 2200bg wifi card, Intel Pentium M 1.6GHz CPU, 1,5 GB RAM, 160GB PATA (IDE) Samsung HDD - current partition setup - 30GB NTFS-XP, 15GB NTFS, rest of it consists of extended partion and I don't mind partitioning it in any way with Linux (Ubuntu or whatever distro... I prefer Ubuntu, Fedora, Mandriva, Mepis and would like to install each)

---

### Post by xebian on 2010-01-23
> **SeePU said:**
> LiveCD.

I don't know if it would happen with the Live CD.  I was thinking of trying the install to just test.  But, if it is still really buggy, how do I recover the bootloader since Grub 2 would be installed to the MBR?

I have another Linux OS installed and XP also.

My specs (for my laptop):
IBM Thinkpad T41, Radeon Mobility 9000 FireGL graphics card, Intel 2200bg wifi card, Intel Pentium M 1.6GHz CPU, 1,5 GB RAM, 160GB PATA (IDE) Samsung HDD - current partition setup - 30GB NTFS-XP, 15GB NTFS, rest of it consists of extended partion and I don't mind partitioning it in any way with Linux (Ubuntu or whatever distro... I prefer Ubuntu, Fedora, Mandriva, Mepis and would like to install each)

Simply don't install a bootloader.

Or you can install one and then boot to your desired bootloader and then reinstall the bootloader.

---

### Post by Seventh Reign on 2010-01-23
I havent noticed any problems with Windows, but I did see a massive regression in boot times since yesterday.  from 57 sec to 1:55.  Nothing unusual tho for an Alpha .. it usually goes up and down over the course of 6 months.

---

### Post by ranch hand on 2010-01-23
I take that this is an upgrade.  Fresh installs work better most of the time.

This is grub2 it should work fine even if you can't boot to it.  If this is a second Ubuntu on the drive then you can boot to it and run;
```

sudo grub-install /dev/sda

```
editing "sda" to meet the needs of your box.

That will put the grub from that install onto the MBR.

See link in my sig for simple over view of grub2.  See second link in that post for the best in depth info on grub2 you are going to find.

---

### Post by moviemaniac on 2010-01-24
> **SeePU said:**
> I can't believe no one has posted yet on the bugs regarding having a window open, any Nautilus window or even Synaptic's window.   There is no resizing, moving it or minimizing it or shutting it down via 'windows style' 'x.'

Try enabling or disabling desktop effects (compiz). I remember the same thing happening to me on Karmic when I wanted to enable Gnome shell - all the buttons disappeared but reappeared when I switched back to metacity.

---

### Post by SeePU on 2010-01-24
moviemaniac, I haven't seen the problem recently.  Weird.

I notice you have a T40?  With a Radeon card?

Btw, how come Ubuntu 10.04 LiveCD doesn't 'shut down' or 'reboot' properly?  It just crashes.  They gotta fix that! ;-)   'Can't be that hard to have it reboot?

---

### Post by moviemaniac on 2010-01-24
Yeah, my T40 has a Radeon Mobility 7500 - old, but I can play Morrowind in wine with it :D But my T40 still runs Karmic - I need it for university and in case my lucid testing install on my main machine goes bananas :D

---

### Post by SeePU on 2010-01-24
> **moviemaniac said:**
> Yeah, my T40 has a Radeon Mobility 7500 - old, but I can play Morrowind in wine with it :D But my T40 still runs Karmic - I need it for university and in case my lucid testing install on my main machine goes bananas :D
Oh yeah?

With your T40, did you have any initial probs with booting up and/or having 3D / Desktop Effects enabled?   Any issues like mine such as the lockups or crashes?   I had problems with 9.10 Karmic as you may have read from my experience?

---

### Post by moviemaniac on 2010-01-25
Nope, sorry, my machine's running like a charm ever since I isntalled karmic.

---

### Post by kansasnoob on 2010-01-25
Have you tried running the Live CD in safe graphics mode?

I think that option pops up if you press F4, maybe F6, can't remember for sure.

---

### Post by seeker5528 on 2010-01-25
> **SeePU said:**
> I can't believe no one has posted yet on the bugs regarding having a window open, any Nautilus window or even Synaptic's window.   There is no resizing, moving it or minimizing it or shutting it down via 'windows style' 'x.'

If the window manager isn't running, you get no window management functions.

What happens if you open a terminal window and type...

```
metacity --replace
```

Later, Seeker

---

