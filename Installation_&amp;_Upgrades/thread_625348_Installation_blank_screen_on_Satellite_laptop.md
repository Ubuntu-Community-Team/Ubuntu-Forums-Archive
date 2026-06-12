---
title: "Installation blank screen on Satellite laptop"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by Elpoca on 2007-11-27
Hello:

I am trying to install 7.10 on an old Toshiba Satellite 1800-S200 laptop (specifically, [this one]("http://www.toshiba.ca/web/product.grp?lg=en&section=1&group=223&product=6"), but with 384MB of memory).  However, everything I do eventually leads to a flashing cursor.   With the normal installation disk/live CD I've tried:
[LIST]
[*]The default installation process
[*]Graphics safe mode
[*]Changing the resolution (VGA to 1024x768, etc)
[*]Various boot options: nofb, vga=771, noapci, nolacpi
[/LIST]
Nothing seems to work.  The live CD booting always stops following the squashfs message.

I've also tried the alternate CD, but that also ended with a flashing cursor.

I'm at my wits end.  Any suggestions, or is installing ubuntu on this laptop simply not an option?

Elpoca

---

### Post by x64Jimbo on 2007-11-28
On a system with that little memory, I would recommend running a lighter weight version of Ubuntu like Xubuntu. My guess is that the system just runs out of memory and gets hung up on all the extra stuff that Ubuntu has added over the years. Xubuntu is about as raw as it gets for a graphically enabled desktop. It runs on very little hardware, and it absolutely screams on beefier hardware.

---

### Post by Elpoca on 2007-11-28
Nope, Xubuntu didn't work either.  It gets to the squashfs message, but ends on a blank screen after that.  Any other suggestions?

Elpoca

---

### Post by Bllz on 2007-11-28
No live-cd is going to work with that little memory.

I have a slightly more recent Toshiba Satellite, and ubuntu installed without a hitch--use the alternate install CD.

With that little memory, consider using Xubuntu or Fluxbuntu.

---

### Post by gams on 2008-03-15
I have the exact same issue.  I have installed kubuntu on my laptop and desktop, but couldn't get xubuntu, ubuntu, or kubuntu installed on my old Toshiba Satellite....Piece of junk! :D  Same black screen.

It used to run XP.

Any suggested would be great.

Thanks,

Gams.

---

### Post by Peter09 on 2008-03-15
As suggested use the Alternate CD which you can download. It does not need very much memory to do the installation. Once done the O/S will run fine.

PC

---

### Post by gams on 2008-03-15
I'll give it a try.  I'm downloading the ubuntu 7.10 alternate CD now, I'll report back how it goes

Thanks,

Gams.

---

### Post by Elpoca on 2008-03-15
The 7.10 alternate CD didn't work for me.  Eventually, the way I got it installed was to use the 7.04 Xubuntu alternate.  I suspect, however, that any 7.04 version might have worked (i.e., it was a 7.10 issue preventing installation, not a resources issue).

---

### Post by gams on 2008-03-24
Thanks.  The 7.04 alternate CD worked.  I accidentanly upgraded the OS to 7.10 and then it didn't work anymore, but at least I know what to do now to get it back to a working state.

Thanks,

Gams.

---

