---
title: "Ubuntu 8.04 (x86) : Can't boot &quot;Undefined video mode&quot; problem"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by u00000000 on 2008-05-26
I recently installed Ubunutu 8.04 on a couple of PC's (Core 2 Duo, very similar configs). The first one I got running and no problem.
The 2nd machine, I also got running, but after 2 days of usage, I came back from the weekend to find that it would not boot. I get the following error:
========================
Starting up ...
Undefined video mode number: f7f7
Press <ENTER> to see video modes available, <SPACE> to continue or wait 30 sec
========================
If I press enter, I get a list like:
=============================================
Mode:    COLSxROWS:
0  0F00   80x25   VGA
1  0F01   80x50   VGA
2  0F02   80x43   VGA
3  0F03   80x28   VGA
4  0F05   80x30   VGA
5  0F06   80x34   VGA
6  0F07   80x60   VGA
Enter a video mode or "scan" to scan for additional modes:
=============================================
If I tell it to scan or enter any other video mode, most of them just lock up (even NumLock / Caps Lock doesn't toggle on my keyboard). A couple of the modes changes the text display first and then lock up.
I cannot boot to "recovery mode" from GRUB, it gives me the same message.

It shouldn't be hardware failure, I plug in the old WinXP drive and it boots fine.

I found a bunch of posts pointing to "lilo.conf" problems, but i) how could this work for a few days and change? and ii) I can't log in to edit this anyways!

Motherboard is some standard (actually Intel brand) Intel 945 chipset board with nVidia 7500 ASUS card (we have a ton of these around the office, they're all working fine).

Any tips?
I'm loathe to re-install since we just had this thing configured with all sorts of development tools and source code to get ready to develop (same as the other machine).


Thanks,
Isaac

---

### Post by Vegetarianrage on 2008-06-12
I had this same problem when i reinstalled my nvidia drivers and started fiddling around with /etc/X11/xorg.conf.

You can't simply select one of the choices? for example just push 4 and press enter. It doesn't work? Mine boots fine if i just pick one of them, any one of them works. I'm still searching for how to adjust it so that it isn't an invalid setting by default. Let me know if you find the actual file.

---

### Post by Vegetarianrage on 2008-06-12
I had this same problem when i reinstalled my nvidia drivers and started fiddling around with /etc/X11/xorg.conf.

You can't simply select one of the choices? for example just push 4 and press enter. It doesn't work? Mine boots fine if i just pick one of them, any one of them works. I'm still searching for how to adjust it so that it isn't an invalid setting by default. Let me know if you find the actual file.

---

### Post by Corazon912 on 2008-08-24
I have this same type of video mode error but my pc won't react whether I press enter or space.  I simply wait it out and it starts normally.  I still would like to eliminate this error.  If I found out how I'll stop by here again.

---

### Post by zphowells on 2008-09-02
same problem after fiddling with ati drivers "undefined video mode number:318 the only option that doesnt seriously corrupt the screen is "space bar" i would also like to resolve this i expect its a line or two in xorg.conf but i dont know which of the hundreds of xorg's im booting with i have so many and at least 20 flgrx's !

any help would be greatly appreciated

regrds
si
sorry im running 64bit

---

### Post by Corazon912 on 2008-09-07
Well I think I fixed this problem.  I don't know if it works for everyone, but on my first re-boot things went fine.

I opened my Startup Manager (in Administration menu) and changed the Display Resolution to 1024x768.  No video mode error on reboot.

If the error appears again I'll let you know, but as of right now I'm video mode error free.

---

