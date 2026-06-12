---
title: "Can only boot 64bit version"
date: 2008-07-12
forum: Installation &amp; Upgrades
---

### Post by chidge on 2008-07-12
I have a problem in that I can't install 32bit debian or ubuntu. I get lots of 'Kernel panic bad EIP value' errors unless I'm using a 64bit iso.
I can however get 32bit fedora to install which makes me think it must be something specific to the kernel on the disc?

Some programs I use don't have 64bit versions so I really need to be using a 32bit OS. I have an Asrock 2Core1333-2.66G motherboard - the same as the person in _[this thread]("http://ubuntuforums.org/showthread.php?t=629973")_ in the archives. They had the same problem but no resolution other than going for 64bit :confused:

Can anyone help?

---

### Post by Vivaldi Gloria on 2008-07-12
Have you tried the 32bit alternative cd?

---

### Post by chidge on 2008-07-12
Thank you for the quick reply - I'm downloading it now
Will report back if it works or not :)

---

### Post by chidge on 2008-07-13
Unfortunately the alternative disk gives the same error :(
This is all of the message I can see before it hangs

printing eip: 31c00f01 *pde = 00000000
Oops: 0000 [#1] SMP
Modules linked in:

Pid: 1, comm: swapper Not tainted (2.6.24.19-generic #1)
EIP: 0060:[<31c00f01>] EFLAGS: 00010002 CPU: 1
EIP is at 0x31c00f01
EAX: 680000b1 EBX: 000f0000 ECX: 00010000 EDX: 49430150
ESI: 0000ff01 EDO: c0400000 EBP: 000f0031 ESP: f7c65f33
 DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
Process swapper (pid: 1, ti=f7c64000 task=f7c62000 task.ti=f7c64000)
Stack: 0f040600 740000c0 00500072 d7b10100 49c00f00 02c00f00 444d8200 000060c0
[INDENT]132aa900 000000c0 00028600 00000100 c8a0c000 000286f7 00020200 00000100[/INDENT]
[INDENT]00000000 00000000 46affc00 444c16c0 444714c0 000000c0 42155600 3a2618c0[/INDENT]
Call Trace:
=======================
Code: Bad EIP value.
EIP: [<31c00f01>] 0x31c00f01 SS:ESP 0068:f7c65f33
---[ end trace ca143223eefdc828 ]---
Kernel panic - not synching: Attempted to kill init!

---

### Post by Kevbert on 2008-07-13
It's probably worth raising a bug report for this on [[COLOR="Red"]launchpad[/COLOR]]("https://bugs.launchpad.net/")
I've just had a quick look and can't see any reported bugs on this problem.  Please include the specs of your PC and as much info as possible.

---

### Post by Vivaldi Gloria on 2008-07-13
> **Kevbert said:**
> It's probably worth raising a bug report for this on [[COLOR="Red"]launchpad[/COLOR]]("https://bugs.launchpad.net/")


Yes, that's a good idea.

Also try: download minimal cd from here:

[https://help.ubuntu.com/community/In...tion/MinimalCD](https://help.ubuntu.com/community/In...tion/MinimalCD)

This is just a 10 MB cd which downloads everything from the net during install. So you can use it if you have a decent net connection. Use it to install a command line only system. (You can install ubuntu-desktop afterwards).

I have seen minamal cd work in some sytems where the other cds failed. So give it a try. I think that minimal cd will also fail in your system to be honest, but since it is just a 10 MB download there is no reason not to try it.

Whether this works or not, report a bug at launchpad.

---

### Post by chidge on 2008-07-13
Minimal CD gives the same error - and I tried allot of boot arguments but still no luck :(
re. posting a launchpad bug I've just done a search and [this one exists]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/173797") presumably created by the person who had the problem in [this post]("http://ubuntuforums.org/showthread.php?t=629973"). Looking at the comments there nothing seems to have been resolved.
Our hardware is the same so should I add a comment to that?

thanks

---

### Post by Vivaldi Gloria on 2008-07-13
> **chidge said:**
> I've just done a search and [this one exists]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/173797/+viewstatus") presumably created by the person who had the problem in [this post]("http://ubuntuforums.org/showthread.php?t=629973"). Our hardware is the same so I'll add a comment to that?

Don't forget to write that the problem continues with 8.04.

---

### Post by ukripper on 2008-07-14
> **chidge said:**
> I have a problem in that I can't install 32bit debian or ubuntu. I get lots of 'Kernel panic bad EIP value' errors unless I'm using a 64bit iso.
I can however get 32bit fedora to install which makes me think it must be something specific to the kernel on the disc?

Some programs I use don't have 64bit versions so I really need to be using a 32bit OS. I have an Asrock 2Core1333-2.66G motherboard - the same as the person in _[this thread]("http://ubuntuforums.org/showthread.php?t=629973")_ in the archives. They had the same problem but no resolution other than going for 64bit :confused:

Can anyone help?

Just seen your private message. I am surprised 32bit Fedora worked on this motherboard.  Looks like you might want to compile and install your own kernel (which is not difficult if you use Kernelcheck app which is very simple).

With kernelcheck you can compile and install the latest custom kernel by just following steps, it may take couple of hours depending upon your machine. Here is the link - [http://ubuntuforums.org/showthread.php?t=618563](http://ubuntuforums.org/showthread.php?t=618563) 

Alternatively, you can try Intrepid Ibex 32bit alpha 2 [http://cdimage.ubuntu.com/releases/intrepid/alpha-2/](http://cdimage.ubuntu.com/releases/intrepid/alpha-2/). if that works then you can use its kernel for Hardy.

If I were you I would give Ibex alpha 2 a try if that worked I then use its kernel for Hardy.

---

