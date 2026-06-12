---
title: "[SOLVED] First time boot, all good until expected login screen, which does not appear"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by shamar on 2008-08-12
Hi Forum,

Have just installed Hardy 8.04.1 32-bit on the following new PC:

P5E3 WS Pro
Intel Core 2 Quad
2 x 2GB Corsair DDR3
2 x Seagate 73GB SCSI
Adaptec 29320A-R SCSI controller
Asus 8500GT 512MB
Acer 22" Wide monitor
Logitech Cordless Desktop LX 710/US Laser

Install from Live CD was flawless however when it boots up the first time, the Ubuntu splash appears, the progress bar completes then the monitor flashes a bit and goes black and hangs.

No combination of keys except ALT-CTRL-DEL (which reboots) has any affect.

Cannot bring up other terminals, no text login, etc.

Recovery mode reveals all commands executing correctly up until running rc.local (from memory).

Have read a few other threads with similar problems, unfortunately everything I've tried does not seem to work.

btw, the Live CD works perfect (when in 'Live Session User' mode) and displays in 1680 x 1050 resolution.

Am sure I'm not the first one with this issue, if someone can point me to the right thread (if it exists), would much appreciate it.

Thanks.

---

### Post by shamar on 2008-08-14
For what it's worth, have attached the Xorg.0.log showing the back trace:

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x7e) [0x80c780e]
1: [0xb7f9b420]
2: /usr/bin/X(AddResource+0x52) [0x8076692]
3: /usr/bin/X(PictureInit+0x1e4) [0x815caf4]
4: /usr/bin/X(miPictureInit+0x2c) [0x815714c]
5: /usr/lib/xorg/modules//libfb.so(fbPictureInit+0x2c) [0xa69d2e2c]
6: /usr/lib/xorg/modules/drivers//nv_drv.so [0xb7b75801]
7: /usr/bin/X(AddScreen+0x1fc) [0x8073d9c]
8: /usr/bin/X(InitOutput+0x21e) [0x80a9c4e]
9: /usr/bin/X(main+0x296) [0x8074526]
10: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d35450]
11: /usr/bin/X(FontFileCompleteXLFD+0x201) [0x8073a91]

Fatal server error:
Caught signal 11.  Server aborting

---

### Post by S.A.A on 2008-08-14
Hey, in the grub menu press "e" then in the line which begins with "kernel" add this:
    
   "vga=normal"

then press "b" to boot...

---

### Post by shamar on 2008-08-17
Hey, thanks for replying.

Tried your suggestion, unfortunately same result with same log output (see attached).

Since my first post, have tried installing the linux-restricted... drivers, have tried installing the drivers direct from Nvidia and have tried using envyng, all to no avail.

The only difference is the monitor flickers on & off 3 times (attempting to set the correct resolution or something I assume) and then eventually  returns to the text console.

Am at my wits end trying to figure this one out and very tempted to go to Vista right about now.

The other thing I noticed was that 'dpkg-reconfigure xserver-xorg' in the text console has never worked for me, it always hangs and never actually updates xorg.conf. And that during the envyng install it mentioned something about /../../../dpkg being 'locked'??? Could be related....?? 

Could it be something to do with my scsi drives / controller? I noticed during boot up (in recovery mode) it mentioned something about updating the sd driver...will try that next.

Any more advice / assistance would be much appreciated.

Cheers.

---

### Post by shamar on 2008-08-18
All good, was my SCSI.

Removed card and started again and all works.

---

