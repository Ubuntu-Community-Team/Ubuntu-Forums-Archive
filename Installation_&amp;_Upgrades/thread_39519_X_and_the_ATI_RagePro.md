---
title: "X and the ATI RagePro"
date: 2005-06-05
forum: Installation &amp; Upgrades
---

### Post by FatherDale on 2005-06-05
OK, I'm in full head-scratching mode. Ubuntu worked just fine on this old box, a 500mhz Celeron Compaq Presario 3550, with digital flat panel and an unusual connector -- as far as I know, only ATI ever made a video card for this thing, a RagePro with 8mb of RAM. Otherwise you have to use the on-board graphics, which, frankly, stink.
I managed to find one of these cards and installed it on the old box, and ubuntu stopped working. I get a black screen. Found a set of linux drivers for it and reran X setup, no joy. Here's the odd part -- Mandrake 10.1 works fine with this thing, but I don't like it now that I've used ubuntu. Knoppix 3.6 works fine, but runs too slow with this coal-fired 4x CDRW drive. What do I have to do to ubuntu to make it work? X is largely a mystery to me, which sort of leaves me in the position of having to run a lesser O/S or using crappy graphics. Whimper.
Thanks in advance. Please have a terrific day.

dale

---

### Post by mingus on 2005-06-05
So you are getting through the boot sequence up to display of the login screen?

---

### Post by FatherDale on 2005-06-05
No, after GRUB, I get squat. Blank screen. I booted in 'rescue' mode and fiddled with X a bit and got nothing. I pulled the cable off the ATI, rebooted, and now I have odd, but usable video on the i810 stuff. Is there an ubuntu counterpart to Mandrake's GUI x configurator, or do I need to fix this at the command line?

thanks,
Dale

---

### Post by mingus on 2005-06-05
X is not the immediate problem, although it may be a secondary one.  X is loaded by gdm (the graphical login manager), you lose video before that.

Before researching that particular video card, try this quick & dirty:

At the grub menu ('escape' will show it if it is not displayed), edit (press 'e') the kernel options.  Remove any "vga" command and add at the end "vga=normal" and then press 'b' to boot.

Do you get the screen now?

---

### Post by mingus on 2005-06-05
I forgot . . .

after doing the above (whether it works or not) then use the above procedure but instead of "vga=normal" use "vga=ask"

the kernel will ask you if you want help with the video mode, hit enter . . .
a table should be displayed with a video drive name (e.g., "vesa vga), note this . . .
you can choose from this table or type in "scan", do the scan
the table now will probably be different, more entries
try selecting an entry with a higher column number

what you are testing here is whether the vesa framebuffer can properly detect your video card.

---

### Post by FatherDale on 2005-06-05
Excellent. Thanks for giving me a starting point. In the meantime, I managed to mung it thorougly, including the windoze partition (got fdisk-happy), so I said "Like I have something better to do this afternoon?" and blew the whole drive away and started over. Right now, it's happily updating packages. Everything works as long as I don't try the Evil Video Card. Not being all that bright, I'll give it another shot later. :-)
Thanks,
Dale

---

