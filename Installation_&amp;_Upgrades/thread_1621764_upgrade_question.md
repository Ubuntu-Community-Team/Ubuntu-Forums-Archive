---
title: "upgrade question"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by mitchmcc on 2010-11-14
I had previously created an install disk (quite a while ago) for 8.4. I had installed it on an old Compaq (since deceased) and now wanted to install it on a Dell Inspiron 5160.

Truth be told, I tried to install 10.4 and had the same problem many others have reported, so I gave up on it.

So my 8.4 installed fine, but when I tried to install some other software packages, I was told "these are not available for your hardware".  After some investigation, I realized that somehow my original disk had been created for i686, not i386!  It seems to run fine, but obviously I need to get on the correct hardware so I can install other software packages.

I tried to use the update manager, and it successfully updated my installation to 9.04, but it did not change the hardware type.

When I try to boot off my 10.04 disk, it doesn't boot it (despite my having changed the Bios setting to always boot first from CD-ROM drive.. this being the way I got Ubuntu on in the first place).

So I am obviously missing something basic.  How can I get to *any* version of Ubuntu that is i386.  I would prefer to be on 10.4, but it seems to hang the way many people have reported.

Oh, and I don't have 100 hours to figure it out, as one person online reported.

If anyone has any suggestions, I would appreciate it.  On my Dell, if you press F2 at boot, it goes to the Bios, but I cannot seem to get Ubuntu to actually boot that disk and try to install it (yes, it is the i386 version of 10.4).

Thanks,

mitch

---

### Post by TBABill on 2010-11-14
I believe ALL 32 bit desktop versions of Ubuntu are i386. Aren't the server versions i686 (32 it server version)? Please post the output of ```
uname -a
``` from a terminal.

---

### Post by mitchmcc on 2010-11-14
I am going to have to wait a while.  I just tried the online update to 9.10, and now it won't boot at all.

Something happened between 8.04 and 9.10 that will not boot on my Dell Inspiron 5160.

I don't know what I am going to do, and this is only a weekend project for me.

Thanks!

Mitch

---

### Post by TBABill on 2010-11-14
I would never trust upgrading all the way from the version you started on to a current version. Way too much room for error. Simple way is to burn a LiveCD and verify it works properly and then backup the entire home directory, then install fresh. Otherwise you are open to many glitches and failures, plus the wasted time upgrading (takes WAY longer than installing fresh). Just my suggestion :)

---

### Post by mitchmcc on 2010-11-14
> **TBABill said:**
> I believe ALL 32 bit desktop versions of Ubuntu are i386. Aren't the server versions i686 (32 it server version)? Please post the output of ```
uname -a
``` from a terminal.
I re-installed.

Here is the output:

uname -a

Linux godog 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux

---

### Post by mitchmcc on 2010-11-14
Remember, that was my first attempt, to install 10.04 via LiveCD, but that version does not boot.  It starts to, then hangs with a dark screen.  Many others have reported this exact same behavior with 10.4, so it's not "just me".

---

### Post by TBABill on 2010-11-15
Will it run from the LiveCD you installed from without any problems? Or does it hang trying to boot from that as well?

---

### Post by mitchmcc on 2010-11-15
> **TBABill said:**
> Will it run from the LiveCD you installed from without any problems? Or does it hang trying to boot from that as well?
Yes, it will run from that CD

---

### Post by TBABill on 2010-11-15
At what point does it fail and go to a black screen? Can you get to Grub2 and select safe mode?
 
Edit: I am wondering if you can boot using the VESA driver with low grade graphics until you can get your driver sorted (if it's a video issue causing the problem, still unknown).

---

