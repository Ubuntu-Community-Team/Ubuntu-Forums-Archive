---
title: "Mouse won't work in 686 Kernel but will on 386 Kernel"
date: 2006-07-09
forum: Installation &amp; Upgrades
---

### Post by dicecca112 on 2006-07-09
Liek that title says.  The only way the mouse will work is with a 386 kernel.  What can I do to fix this?  Sometimes it will work on the 686 kernel.

---

### Post by Cannaregio on 2006-10-28
Same problem. USB logitech vanilla mouse. Dies on 686 dapper. Works on 386 dapper.
Searching around, this seems to be a debian kernel problem.

---

### Post by dicecca112 on 2006-10-28
which build of Ubuntu are you using?  If its the newest 6.10, I'm just gonna delete the Iso and install Fedora.  I haven't used Ubuntu because of this since Edgy was still in Alpha stage

---

### Post by Cannaregio on 2006-10-28
Found solution: just use a normal USB port and take the <a href="http://www.ramelectronics.net/assets/images/000-USB-PS2MS1.jpg">PS/2 to USB mouse converter</a> off.

I'm using the last dapper.

---

### Post by Cannaregio on 2006-10-28
:D  Definitely. 
Mouse's perfect with USB port, does not work if you use a PS/2 (green exit) converter.
Without converter everything is fine.
I'm using kernel 2.6.15-27-686, and the only thing that annoys me is that it seems to load more slowly than 386. Is that your impression as well? MAybe I should switch to Edgy?

---

### Post by Cannaregio on 2006-11-26
This was true in Dapper, BUT NOT IN EDGY (since it uses a 386 kernel).
I have upgraded one box (the desktop) to edgy and now the mouse works again with the green converter.
So that was a 686 specific kernel problem, I guess.

New developments (february 2007):
On my edgy machine, the ps2 mouse STOPPED working when I updated from kernel 386 to generic
and BEGAN WORKING AGAIN when I updated generic to  2.6.17-11-generic from  2.6.17-10-generic (february 2007)

Now everything is fine, which is IMPORTANT, since thattaway we don't block with the mouse an USB port for nothing.

Note that this problem was true for ps2 keyboards as well.

---

### Post by xynapz on 2007-03-11
im using edgy 64bit and i just installed it and first time rebooting the mouse doesnt work. my mouse has worked on every other distro ive ever used. i have an logitech mx510 usb mouse.

linux for human beings? i dont think so...back to centos i think (because it works)

---

### Post by Drenhead on 2007-03-11
I had this problem also.  I fixed it by changing an entry in my BIOS.  I can't remember exactly, but it was something like the USB Emulation setting.

Hope this helps.

---

