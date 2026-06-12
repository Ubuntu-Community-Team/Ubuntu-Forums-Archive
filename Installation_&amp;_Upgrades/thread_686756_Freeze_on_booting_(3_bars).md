---
title: "Freeze on booting (3 bars)"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by joeleeg on 2008-02-03
[IMG]http://www.dsl.sk/images/articles/2007-05-06-ubuntu-1.png[/IMG]

that is a picture of someone else's screen, mine is similar. the problem with mine is it stops at 3 blocks. anyone know what is wrong?

ubuntu 7.10 gusty gibon.

i had a problem similar to this with some live cds as it ended with the same results. to install ubuntu i used the alternate cd distribution.

computer is an HP Pavilion a705w desktop.
modified with
128 meg geforce graphics card
1.25 gig ram


------------------------------------------------


Alright so I edited the way Ubuntu boots by removing quite splash. The booting sequence simply ends with a screen that prints the following information to the screen:


[  133.312319]   [<c011fbbc>]  kmap_atomic_prot+0xbc/0xc0
[  133.312419]   [<c01282b3>] __call_console_drivers+0x53/0x60
[  133.312542]   [<c01286f7>]  release_console_sem+0x1c7/0x1f0
[  133.312657]   [<c02f4292>]  error_code+0x72/0x80
[  133.312768]   [<c011fbbc>]  kmap_atomic_prot+0xbc/0xc0
[  133.312880]   [<c016b46c>]  unmap_vmas+0x1ac/0c5d0
[  133.312993]   [<c016efe8>]  exit_mmap+0x78/0xf0
[  133.313105]   [<c01260c8>]  mmput+0x38/0xa0
[  133.313214]   [<c012b5ff>]  do_exit+0x10f/0x810
[  133.313327]   [<c0105edf>]  die+0x25f/0x260
[  133.313437]   [<c0106200>]  do_invalid_op+0x0/0x90
[  133.313547]   [<c0106281>]  do_invalid_of+0x81/0x90
[  133.313659]   [<c011fbbc>]  kmap_atomic_prot+0xbc/0xc0
[  133.313772]   [<c02f4292>]  error_code+0x72/0x80
[  133.313883]   [<c011fbbc>]  kmap_atomic_prot+0xbc/0xc0
[  133.313995]   [<c016cc0c>]  __handle_mm_fault_0x7c/0xb00
[  133.314109]   [<c02f5b36>]  do_page_fault+0x126/0x690
[  133.314222]   [<c02f5a10>]  do_page_fault+0x0/0x690
[  133.314333]   [<c02f4292>]  error_code+0x72/0x80
[  133.314444]   [<c01fe852>]  __put_user_4+0x12/0x20
[  133.314556]   [<c01248a9>]  schedule_tail+0x69/0xa0
[  133.314667]   [<c01040f6>]  ret_from_fork+0x6/0x20
[  133.314778]   [<c02f0000>]  clip_ioctl+0x500/0x510
[  133.314889]   =======================

You people got any thoughts?

---

### Post by orange2k on 2008-02-03
Maybe you need to give it some time. 
Are you booting from the CD or from hard drive?
Because when you boot from hard drive the first time, Ubuntu does a disk check, and this can take some time...

---

### Post by joeleeg on 2008-02-03
I am booting from my hard drive. I have given it some time before when booting with the live CD and I just left it there for a few hours but there is no guarantee that those were not corrupted because i possibly burned them in an incorrect way.

In the meantime while I let my machine sit here, anyone got any ideas?

---

### Post by orange2k on 2008-02-03
The last line you posted looked to me like a progress bar, just like the one you see when disk check is running...
> [ 133.314889] ======================= 
:confused:

---

### Post by joeleeg on 2008-02-03
23 equal signs that don't move. It took me an hour or so to actually make this post and over the hour I left that screen there so I could copy the data to this thread.

---

### Post by jou770d on 2008-03-03
I'm just gonna bump this thread instead of making a new one.
I'm having the same problem as the thread started but the only difference is that I'm trying to boot from a live CD.
This is definitely not caused by a bad CD cause I'm using a CD I ordered from ship-it and I've already used is to install ubuntu on my laptop and those of two of my friends (we decided to learn using linux together).
These are my desktop's specs:
Biostar 865GV Micro 775
Pentium 4 3.00GHz (2 CPUs)
512 RAM
Nvidia GeForce 4 MX 4000 / 128 RAM (rather old)
Creative SB Live! 5.1
Creative Modem Blaster
LifeView FlyTV Prime 34

There are also the built-in video/audio cards (both disabled from the bios).

I've looked around the net but I couldn't get any working solution beside installing from the alternate cd. I'm gonna try that when I get a chance to download it (can't do that from home) but I would really like a fix cause I was planning to install from a live DVD that I remastered from the updated and somewhat customized installation on my laptop.

---

### Post by jou770d on 2008-03-04
I'm gonna give this one last bump before I admit that XP can do something better than Ubuntu: It actually installs on my desktop.
I've tried all that I found on the net but nothing worked...

---

