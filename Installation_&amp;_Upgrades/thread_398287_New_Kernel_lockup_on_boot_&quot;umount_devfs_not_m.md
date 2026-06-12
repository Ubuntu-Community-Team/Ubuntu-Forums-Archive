---
title: "New Kernel lockup on boot: &quot;umount: devfs: not mounted&quot;"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by benutne on 2007-03-31
I'll admit right now, I probably don't know enough about linux to be compiling my own kernel, but I've decided to try.  I'm not sure what I've done (or not done) to break this thing, but I'll start at the beginning.  

1.  Got the source (2.6.20.4) from kernel.org
2.  (and I think this is where I'm screwing up) Set up the config file using "make xconfig"
3.  Once I got the config I wanted, did a make "bzImage && make modules && make modules_install"
4.  Copied the newly compiled image to the /boot directory and then made a initrd image.
5.  Copied the existing GRUB entry and changed the image name and the initrd name to reflect my new stuff so I could boot back into a working system in case I screwed up.  

Everything seemed to be going great, until the system locked after displaying the message "umount: devfs: not mounted"

I can go into detail on any of the steps above if need be, or even post my config file (or parts of it).  I'd really like to get this thing up and running so I don't feel stupid.

---

### Post by benutne on 2007-04-01
bump

---

