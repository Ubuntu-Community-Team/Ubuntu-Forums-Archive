---
title: "I may have to return to M$"
date: 2005-03-16
forum: Installation &amp; Upgrades
---

### Post by jkeck55 on 2005-03-16
I have been trying to install Ubuntu and cannot get it to install.  I keep getting a kernel panic on initial install.  Here is the screen output.

EIP is at 0x20000
eax:  d77d060   ebx:  00000000   ecx:  00000000   edx:  00020000
esi:   d77ef260   edi:  d77d1000   ebp: 000000001  esp:  c0307f14
ds:  007b   es:  007b   ss0068
Process Swapper (pid: 0, thread info=c0306000 task=c0287a40)
Stack:  c0134024 d77d1060 d77ef260 00000001 d77d1000 d77ef260 d77d1000- c0306000
            c0134596 d77ef260 d77d1000 00000001 d77ef260 

Call Trace:
[c0133fd1>]alloc_slabmgt+0x20/0x47
[<c013457c>] kmem_cache_alloc_mode+0x65/0xfd
[<c01336a8>] alloc_arraycache+0x29/0x60
[<c0134760>] do_tune_cpucache+0x29/0x119
[<c01348a1>] enable_cpucache+0x51/0x6e
[<c03144da>] kmem_cache_init+0x1f6/0x229
[<x03085ca>] start_kernel+0x110/0x197
Code:  8b 44 82 10 eb 0c ff 74 24 0c 51 e8 ff fc ff ff 59 5a 53 9d 
 <0> Kernel panic:  Attempted to kill the idle task!
in idle task - not synching

 If I let it sit  it will continue and give a different error.  

Code:  8b 72 04 89 4a ha 03 00 00 00 89 71 04 89 0e b9 01 00 00
<0> kernel Panic:  Fatal exception in interupt
In interupt handler - not synching

I am installing this on a Compaq Presario 5460 system.  I have had Linux on the PC in the past.  It was Madrake 7.1  and it worked just fine.  I removed it because I needed M$ for work and it was too bloated for dual boot on my 8.0 gig harddrive.  

Here are the rest of the specifics
AMD/K6II 475 Mhz
Gigabyte MMS5 motherboard.
8.0 gig Harddrive
384MB memory
a new Liteon - it CD RW
a Linksys NIC
and another NIC unsure of type.
an old 56k modem again unsure of type.

Is there any other info you might need.

Please help I am dreading going back to Windows.

---

### Post by telmo on 2005-03-16
Are you trying to install Hoary or Warty? Live cd or install disk?
The live cd also gives a kernel panic.

BTW, i also have old stinky bastard M$ installed.
If you choose to install M$, don't forget to install Ubuntu after.

Let me just tell you, that despite of some minor problems, my Ubuntu Hoary is much faster and stable than my Window$.

---

### Post by jkeck55 on 2005-03-16
I am using the Warty install CD that I ordered from easylinux cds  I have the live CD iso but have been unsuccessful at getting it burned on properly.

---

### Post by jkeck55 on 2005-03-16
I am very excited.  I am installing right now.  It was the modem.  It is the last thing I could think of so I just pulled it out and now it appears to be working.

---

### Post by az on 2005-03-16
Boot with expert and scroll to the bottom of the list to the check cd integrity item.  Check the cds integrity.

If that does not work

Boot with
linux apci=off
or try other options offered to you in the F2 F3 F4 F5 and so on help screens.

---

### Post by jkeck55 on 2005-03-16
New problem  won't partition the hard drive gets to 59% and then just hangs.  If I can't figure this on my own I will start new thread.

---

### Post by Adrenal on 2005-03-16
Don't start a new thread, it can be solved in here.
Use partition magic or similiar and do it in windows, then go to install Ubuntu

---

### Post by bored2k on 2005-03-16
[QUOTE=Adrenal]Don't start a new thread, it can be solved in here.
Use partition magic or similiar and do it in windows, then go to install Ubuntu[/QUOTE]
 Or ultimate boot cd [google it] .

---

### Post by az on 2005-03-17
[QUOTE=jkeck55]New problem  won't partition the hard drive gets to 59% and then just hangs.  If I can't figure this on my own I will start new thread.[/QUOTE]

YOU HAVE A BAD CD!


Sorry for shouting.

---

### Post by jkeck55 on 2005-03-17
I have MD5 checked my iso file and I just burned a new copy of both the i386 install and i386 live on the lowest speed(4x).  We'll see how it works tonight.

---

### Post by nocturn on 2005-03-18
[QUOTE=jkeck55]I have MD5 checked my iso file and I just burned a new copy of both the i386 install and i386 live on the lowest speed(4x).  We'll see how it works tonight.[/QUOTE]

Try checking the MD5 of the CD too (md5sum /dev/cdrom)
Even at such a low speed, things can go wrong.

---

### Post by jkeck55 on 2005-03-18
I may have stumbled across something that could be causing problems.  If I reboot with no CD or Floppy it attempts to boot a failed Mandrake 10.1 install.  If I boot to DOS and Fdsik and reformat will that wipe this out?

---

### Post by nocturn on 2005-03-18
[QUOTE=jkeck55]I may have stumbled across something that could be causing problems.  If I reboot with no CD or Floppy it attempts to boot a failed Mandrake 10.1 install.  If I boot to DOS and Fdsik and reformat will that wipe this out?[/QUOTE]

This should not matter, I think Azz is right, there is a problem with your CD.

---

### Post by ebrowne on 2005-03-18
Hey,
I've seen this problem before with other distros before we decalre the cd a failure you could check that you Hd is pluged into the correct ide device on the Mobo one of my friends had this probelm and it turned out he had his hd connected to the ide-raid controller once we moved it to the regular ide channel the installed went smoothly.
Windows didn't seem to care that it was on a different channel either and it work fine on either or.

---

### Post by jkeck55 on 2005-03-18
I got it to work.  The problem was memory.  I had a chenk of bad memory.  Once I got it removed it installed no problem.  Now I just need to get out of the console and into Gnome.

---

### Post by jkeck55 on 2005-03-19
I am now up and running.  For some reason it didn/t install Gnome.  I had to go into base-config and bring it in.

---

