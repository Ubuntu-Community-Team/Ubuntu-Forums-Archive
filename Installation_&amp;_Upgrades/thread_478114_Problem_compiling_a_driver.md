---
title: "Problem compiling a driver"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by TrackSprinter on 2007-06-19
I've got a new installation of 7.04, I've installed build-essential and linux-headers.

I've also torn out most of my hair.

When I try to make the driver for my ethernet card, I get this error message:

rt18139.c:91:26: error: linux/config.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.20.15/include/asm/thread_info.h:16,
                        from /usr/src/linux-headers-2.6.20.15/include/linux/thread_info.h:21,
.........

and it all goes pear-shaped from there.

It's been a long time since I did any serious C coding, so maybe I'm misreading this error, but it seems strange to me that asm/thread_info.h has ABSOLUTELY NO MENTION of linux/config.h, on line 16 or any other line.  I tried searching for other thread_info.h files, in case I was looking at the wrong one, but that's the only one in an 'asm' directory.

I'm sure that there's something simple that I'm missing, but I'm all out of ideas.

---

### Post by zanglang on 2007-06-19
linux/config.h has been removed since 2.6.19, that's why it doesn't work. You can either edit the offending source file and comment out:
```
#include <linux/config.h>
```
Or just do:
> sudo touch /usr/src/linux/include/linux/config.h
to create it yourself.

---

### Post by TrackSprinter on 2007-06-19
Right, but, see, that's the problem:  the "offending source file" seems to be (according to the error message) asm/thread_info.h at line 16, but that files doesn't contain a line 
#include <linux/config.h>
either on line 16 or anywhere else.  The asm directory is sym-linked (as it should be, I imagine) to asm-i386, but I can't find any thread_info.h in any of the asm-* directories that contains the offending line.

Am I mis-reading the error message?  There are a lot of following errors about undefined constants and division by zero, I originally assumed those were caused by the missing include.  But maybe not?  (I'm at work right now, can't see the machine to give more details about the further errors.  I'll try your 'touch' idea when I get home, but I'm skeptical, since I seem to be dealing with the wrong includes entirely, or something like that.)

---

