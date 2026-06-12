---
title: "My Boot Experience. (please help)"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kestal on 2009-10-06
**My Hardware:**
- Dell new studio 14z (T6400 @ 2.0ghz)
- Nvidia 9400m-g
- 320gb hardrive - Partition 1: Windows 7, Parition 2: ubuntu (40gb), Partition 3: Swap (4mb), Partition 4: Extra EXT4 (Blank).

**Software**
- Beta (fully updated as of now), 2.6.31-11-generic, nvidia 190.36 beta drivers

**Problem:**
I am having some problems with my Karmic Beta boot. on previous versions it has been fine (and pretty quick), but currently on Karmic something is wrong. It takes a minute for me to fully boot. my Live iso took less time to boot, sadly enough.

I see text during my startup and shutdown process. On startup, I have a blinking cursor for about 12 seconds then text which flashes on the screen. A few seconds pause, Nvidia Beta splash, few seconds pause, Xsplash.

Once xsplash hits, its seems fine and that runs its course. Then Desktop.

On shutdown, I do not see anything graphical, but text on my screen during the shutdown. Any help on this would be appreciated, even if its to understand what the problem is.

I provided the bootchart png, if anyone needs any other information I will gladly give that.

---

### Post by VMC on 2009-10-06
> **kestal said:**
> **My Hardware:**
- Dell new studio 14z (T6400 @ 2.0ghz)
- Nvidia 9400m-g
- 320gb hardrive - Partition 1: Windows 7, Parition 2: ubuntu (40gb), Partition 3: Swap (4mb), Partition 4: Extra EXT4 (Blank).

**Software**
- Beta (fully updated as of now), 2.6.31-11-generic, nvidia 190.36 beta drivers

**Problem:**
I am having some problems with my Karmic Beta boot. on previous versions it has been fine (and pretty quick), but currently on Karmic something is wrong. It takes a minute for me to fully boot. my Live iso took less time to boot, sadly enough.

I see text during my startup and shutdown process. On startup, I have a blinking cursor for about 12 seconds then text which flashes on the screen. A few seconds pause, Nvidia Beta splash, few seconds pause, Xsplash.

Once xsplash hits, its seems fine and that runs its course. Then Desktop.

On shutdown, I do not see anything graphical, but text on my screen during the shutdown. Any help on this would be appreciated, even if its to understand what the problem is.

I provided the bootchart png, if anyone needs any other information I will gladly give that.

I recall there is a fix on that long boot and nVidia. Maybe a search will find an answer. Unless someone comes here with the fix, if I find it I will come back with the link.

---

### Post by kestal on 2009-10-06
> **VMC said:**
> I recall there is a fix on that long boot and nVidia. Maybe a search will find an answer. Unless someone comes here with the fix, if I find it I will come back with the link.

Still not sure what to do about this problem. I am not sure whats causing the problem. Which is why I post in the forum to begin with..

---

### Post by ttoms on 2009-10-06
I'm afraid that it is exactly the same for me with a Lenovo X61, intel graphics. Same messages at the start, and quicker to boot from a live usb. I had assumed the speed would improve with each update but sadly not yet.

The laptop boots faster with Arch linux running a full KDE 4.3 environment.

---

### Post by laborg on 2009-10-06
count me in with a lenovo t500 (2,53ghz) current boottime: 1:16 :-(

---

### Post by hexsel on 2009-10-06
Your boot ends at 40s or so, I think I read another thread saying they changed the way bootchart is behaving, includes getting to the full Gnome desktop.  On my box with auto-login, it includes stuff like waiting for my password before connecting to mission-control.  

Which is a much bigger issue for me... (no, I don't give a **** if anyone would steal my MSN password when they have access to my machine, just make them plain-text or scramble them... also don't freaking lock the desktop when auto-login is turned on!  DUH!!!!)

---

### Post by kestal on 2009-10-06
Though I understand it doesn't take a full minute for me to get into the Ubuntu Desktop and actually do things, its just that there are gaps of time that occur before the xsplash even shows up (not to mention the random text I see - shouldn't that be 'inside' xsplash?). 

Not to mention I do not have any kind of shut down graphic but, oh, more text. I understand its beta, but I did not have this problem on my desktop. Its a noticeable difference (not only because its longer, but because of the overall experience). My live USB (though yes, it was slow), did not have a 12 second gap with just a non-blinking cursor.

---

