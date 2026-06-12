---
title: "Three errors when installing 7.04"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by JonasW on 2008-02-17
Hi. First of all, I'm sorry about this: Don't like having my first action being a thread, especially not asking for help, but I really do need it.

Anyway, on with the problem: My Windows went completely dead on me last week after I replaced my CPU cooler. I said to myself "I am not pleased" and decided to go find my Ubuntu 7.04 x86 disc I got a while ago to try out, but never got to work. Now that I try to install it, I get the following three errors:

> [Large number] Buffer I/O error on device fd0, logical block 0
[Other large number] ata7.01: Failed to set xfermode (err_mask=0x4)
[Another large number] hub 5-0: 1.0: connect-debounce failed, port 7 disabled

The first one is floppy, as far as I've gathered. The solutions I've found and tried unsuccesfully are typing lsmod| grep floppy and removing floppy from boot priority. I do not have a floppy drive. I get this one 2-3 times.

The second one I've barely found anything on, and both of those are in a language I do not speak. I get this one 2-3 times.

The third one I have cleverly deducted indicates that port 7 is disabled, but I haven't found a solution for it. I get hundreds of this one.

Each repition of each error is of course with a different large number in front of it. There are so many I just couldn't keep up with them.

I have read that waiting sometimes make them go away and lets the disc go on anyway, but for me they just continue until they clear and there's a black screen. I got these same errors last time I tried installing it as well.

If this should be in the x86 forum, I apologize.

---

