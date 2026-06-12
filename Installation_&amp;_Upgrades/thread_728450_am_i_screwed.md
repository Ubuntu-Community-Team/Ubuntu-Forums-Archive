---
title: "am i screwed?"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by rspear on 2008-03-18
My laptop recently got a virus and was running slow. I backed up my files and ran my Microsoft Windows XP disc to reformat. It turns out that i didn't have some sort of service pack for it and now it is stuck half way through the set up.

I have decided to try a new operating system as windows is too expensive to have these ongoing issues. That it why i am here. I am currently downloading the latest version of Ubuntu and plan to write it to disk.

Can someone tell me if i put the disk in my laptop and turn the power on if it will work or not? I don't think I can get to the boot configuration from the point that it seems to be starting up at.

Any suggestions would be greatly appreciated.

---

### Post by Pumalite on 2008-03-18
If you can boot a Live CD, install using Guided>Use Entire Disk. If not, Use the Alternate CD. Here is an installation guide with the Alternate:
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by jimv on 2008-03-19
I'm not entirely sure what you're asking.  Are you asking how to boot from the CD?  If it's a laptop, it should boot automatically from the CD.  If not, try pressing F10 or F12 to bring up a boot menu that will let you choose what disk to boot from.

---

### Post by feynmandiagram on 2008-03-19
Sometimes you can change the boot priority in the BIOS itself. Press F2 or ESC (sometimes other Key-combos) to get into the bios and set the CD-ROM in front of your harddisc to "try" to boot from cd-rom first. If there is no cd in the rom, it'll just boot the way you are used to it.

Regards and good luck!

---

### Post by rspear on 2008-03-19
the alternative cd seems to working.

I'm also concerned about my drivers needed (wireless card, sound card, etc.)

How do these get installed? I have the drivers on disk but i assume they are for windows only.

Any insight or any other problems i may run into after installation?

---

### Post by Pumalite on 2008-03-19
The installation takes care of most of it. We'll review it after you are set.

---

### Post by rspear on 2008-03-19
Ok, so it booted up from the hard disk fine, asked for username and password and now it just sitting at a brown screen. I did hear sound at the splash screen.

what next?

---

### Post by rspear on 2008-03-19
uh oh, i shut the computer off and restarted and it stops at a dos type of screen with a bunch of code on it.

now am i screwed?

---

### Post by rspear on 2008-03-19
i noticed it said 'scaling frequency not supported..." just before it goes to code.

if that helps at all.

---

### Post by tangibleorange on 2008-03-19
> **rspear said:**
> uh oh, i shut the computer off and restarted and it stops at a dos type of screen with a bunch of code on it.

now am i screwed?

What does the code say?

---

### Post by sowelie on 2008-03-19
Can you post the exact output, also what are your system specs.  I am thinking you may be having a video issue.  In that case you just need to get the right video driver installed.

---

### Post by Wobedraggled on 2008-03-19
Yes, just give as much detail as possible, and system specs.

---

### Post by NullHead on 2008-03-19
That shouldn't bother the operation of the system. Mine says the same thing and it works just fine.

When you get back into Ubuntu open a terminal window. Go through the menu system to find it Applications>Accessories>Terminal and type in this little bit of code into the terminal. ```
lspci
```it should spit out a whole bunch more code (thats good) copy and past it into a post here and we'll be able to tell what hardware you have and how to get it working :)

---

### Post by Pumalite on 2008-03-19
Try this:
Ctrl+Alt+F1 to get command line:
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose vesa as the drive, stick to 1024x768 for the moment, then: startx

---

### Post by rspear on 2008-03-19
it scrolls through alot of code at once but the screen i am seeing now shows:

[        49.900000] Call Trace:
[        49.900000] [<c0189185>] may_open+0x65/0X270
[        49.900000] [<c019b0ef>] seq_open+0x6f/0X90

etc.

etc.



[        49.900000] Code: 89 c3 fa 90 8d b4 26 00 00 00 00 90 64 etc.

[        49.900000] EIP: [<c017cc7c>] kmem_cache_alloc+0X4c/0X90

"the screen goes blank after about 10min."

I am using a ACER Travelmate 2312 120GB HD, 700MB of RAM, Celeron M processor.

---

### Post by rspear on 2008-03-19
> **Pumalite said:**
> Try this:
Ctrl+Alt+F1 to get command line:
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose vesa as the drive, stick to 1024x768 for the moment, then: startx

sudo dpkg.... took me back to the code screen.

should i just try to boot from disk again?

---

### Post by Pumalite on 2008-03-19
You might have to use some boot parameters. Here is a guide and some collections:
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)

Use the most common first; alone or in different combinations:
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317 vga=791

---

