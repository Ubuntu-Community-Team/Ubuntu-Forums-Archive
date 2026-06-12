---
title: "Gets to login screen, clears, plays sound, then nothing"
date: 2005-09-23
forum: Installation &amp; Upgrades
---

### Post by ivanjs on 2005-09-23
Hey-
Just installed ubuntu (heard about it at digg.com). 

Sounds exciting. Just installed it, installation went incredibly well, rebooted, got to login screen logged in, screen cleared, heard some soothing sounds, nothing happened. cursor just sits there (though I can move it around).

No menus or icons, just a sort of gold/green screen with a white cursor that I can move around.

Suggestions?

Installer CD came from download, then ISO image burned to disc. No errors during installation.

here's my system specs:

Gigabyte 8i915 motherboard
Intel P4 3.0ghz cpu
1 gig of DDR400 ram (2 512 sticks)
GeForce 6200 graphics card
ViewSonic GS771 monitor
Lite-On 48x CD Rom
36 gig Maxtor hard drive, partitioned and formatted during installation.

Thanks.
ivanjs

---

### Post by ivanjs on 2005-09-25
[QUOTE=ivanjs]Suggestions?
[/QUOTE]
 Anyone?

---

### Post by greenway on 2005-09-27
Hi, 

I am experiencing exactly the same problems. Both with the regular installation as well with the live CD. No solution found yet, the only thing I know is that's probably not kernel related. Did you fixed this problem already? If I find out anything, I'll post it again.

-greenway

---

### Post by jakeofnote on 2005-09-28
well i have the same graphics & memory and a gigabyte 8i915 motherb, but my only problem is sound... I'll say more when i know more...

---

### Post by brentoboy on 2005-09-28
this is probably the 5th time I have heard this same post.  the 6200 nvidia chip (which happens to also be in my PC) seems to be the culprit.  I had this same issue a few weeks back when I got my new pc and put ubuntu on it.

The initial fix is to change the xorg.conf file to use the vesa driver instead of the "nv". to do that, restart, and use grub to boot to recovery mode.

from the command line, edit the xorg.conf
nano /etc/X11/xorg.conf

find the line that specifies to use:
Driver "nv"
change it ot Driver "vesa"

(this is the "widely compatible but no optimizations" driver that works in most scenarios)

save the file, exit nano and reboot the pc.

the desktop will work.

from there, surf the foumns on getting the latest driver from nvidia installed.  (which you only need to do if you are a gamer or need the opengl stuff to work)

---

### Post by ivanjs on 2005-10-14
[QUOTE=brentoboy]from the command line, edit the xorg.conf
nano /etc/X11/xorg.conf[/QUOTE]

But if I can't even get into ubuntu (cause it hangs right when it starts getting to it), how can I edit a file from the command line...

---

### Post by kvidell on 2005-10-14
[QUOTE=ivanjs]But if I can't even get into ubuntu (cause it hangs right when it starts getting to it), how can I edit a file from the command line...[/QUOTE]
Ctrl+Alt+F1 to drop to a VTerm. Login, make happiness.
- Kev

---

### Post by ivanjs on 2005-10-14
[QUOTE=kvidell]Ctrl+Alt+F1 to drop to a VTerm. Login, make happiness.
- Kev[/QUOTE]
Thanks, I'll give that a try.

---

