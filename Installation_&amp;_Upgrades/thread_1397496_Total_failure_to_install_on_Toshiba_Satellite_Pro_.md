---
title: "Total failure to install on Toshiba Satellite Pro 4600"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by isonomia on 2010-02-03
I installed Ubuntu on another Toshiba Satellite and decided to upgrade my old Satellite with some new memory and a bigger (40gb) disk. 

I've tried 9.10, desktop, server and alternative CD, I've tried 8.0.4.4 server (32bit) and desktop, I even tried the mini.disk version 6.

Since about the 12th attempt, I've been using bit-torrent I've checked the data with bit-torrent and checked the CD on the final PC. I thought I had cracked the problem when I did a memory test and found a couple of errors - but replacing the offending items and retesting still failed to load.

The error I seem to be getting is a failure to install the kernel, and then a failure to install either grub of lilo (is that the name)

The final (relevant) message is a "try apt-get -f install" with no packages (or specify a solution". 

But trying apt-get doesn't work because it isn't there!

I did manage to install puppy linux & even dos  onto the PC with the same 40g disk, so it does seem to be a Ubuntu which is at fault.

.. whilst I'm not a "newby", my linux experience really doesn't extend much beyond copying a few files to tidy up directories on the basic "server" (fsg). So I need some fairly detailed instructions to get me out of this mess and e.g.  I wouldn't understand "install this or that", because even if its on the disk, even if I knew the command, I'd still struggle to mount the CD.


CAN ANYONE HELP (a gun/sledge hammar?)

My intended use is for a webserver that will run PHP5, for a bit more file storage and as a spare machine which I can use to read emails and surf the net when all the better PCs are being used and I want it to have Ubuntu because Vista is such a pig, and I'd like them all to have one operating system etc.

---

### Post by pkm4o93 on 2010-02-03
I would get debian net-install) and compare. Also do MD5 to be absolutely sure the media is not at fault.  [   ] debian-504-i386-netinst.iso        01-Feb-2010 17:46  150M   Its good you treid a memtest. Perhaps some other hardware is flaky - such as hard drive.

---

