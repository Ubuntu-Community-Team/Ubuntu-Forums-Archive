---
title: "The 133-P19700-18 problem."
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by frmlt on 2008-04-24
Hi.

I've had terrible problems getting Ubuntu working on this machine.
The story is as follows:

The machine belongs to a friend who had a spyware ridden and almost
totally broken version of XP on it. We decided to put Ubuntu on it.
Attempting to boot from a Ubuntu CD simply resulted in a blank
console with '133-P19700-18' printed in the top left hand corner.
The machine isn't "frozen" as such as I can still ctrl-alt-delete
to restart.

We eventually managed to coax the machine to boot off a Ubuntu CD
by installing the small boot loader program in XP (I forget
what it's called, it's included on the CD and has a graphical
installer). Basically I had to start the machine up with no CD
in there, wait for the Ubuntu progress bar to appear and then
put the CD in the drive. This appeared to be the only way to
avoid stalling on this mysterious '133-P19700-18' screen.

After the install had completed, the machine booted into Ubuntu
from the hard disk without issue.

I updated to 8.04 today using the software update utility and now
I can't even boot from a hard disk. The BIOS logo displays, the
GRUB boot loader counts down, I get a flash of 'Starting up...' in
the top left hand corner for a split second and then this screen
with only '133-P19700-18' written on it.

I tried booting from a FreeBSD 6.3 CD and it worked properly. At
this point I'm suspicious of the graphics card as it seems the
problem occurs when Ubuntu changes the console to a higher
resolution (where as FreeBSD just leaves the console in generic
80x25 mode).

Does anybody have any idea how I can fix this, or at least paper
over the problem?

The graphics card is an ATI Radeon, for the record.

---

### Post by Peter09 on 2008-04-24
Have you tried using the alternate CD, it has a text based installation method so does not get caught up with the graphics card.

PC

---

### Post by frmlt on 2008-04-24
> **Peter09 said:**
> Have you tried using the alternate CD, it has a text based installation method so does not get caught up with the graphics card.

PC

Well, the problem isn't the install, now. The problem now is that I
can't boot from a hard disk with an (apparently) working, upgraded
install.

I will keep the other CD in mind for future reference, though.

---

### Post by Peter09 on 2008-04-24
Are you confident that your install went ok, you suggest that you had a lot of trouble, could it have resulted in a corrupt installation.

PC

---

### Post by frmlt on 2008-04-24
> **Peter09 said:**
> Are you confident that your install went ok, you suggest that you had a lot of trouble, could it have resulted in a corrupt installation.

PC

The original install went OK when we actually managed to get into the
installer. I've been using the installed copy for about two weeks with
no instability or problems.

---

### Post by frmlt on 2008-04-24
The upgrade apparently went flawlessly as well, before you ask...

---

### Post by Peter09 on 2008-04-24
an you boot into recovery mode, if so when you get to the command prompt type

```
startx
```

and see what happens.

PC

---

### Post by frmlt on 2008-04-24
I can't boot into recovery mode. I did however discover
this:

```

Ubuntu 8.04, kernel 2.6.24-16-generic
Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
Ubuntu 8.04, kernel 2.6.24-14-generic
Ubuntu 8.04, kernel 2.6.24-14-generic (recovery mode)

```

2.6.24-14 does actually boot but still doesn't appear to
be exactly correct - something selects a video mode that
my monitor can't cope with ("out of range") for the duration
of the console startup before starting X.

After X starts, everything appears to be OK.

This is very frustrating though. Am I running the kernel
from 7.10?

---

### Post by Peter09 on 2008-04-24
Not sure why you cannot get to recovery mode.

Are you saying that you can get to the GUI interface now?

PC

---

### Post by frmlt on 2008-04-24
> **Peter09 said:**
> Not sure why you cannot get to recovery mode.

Are you saying that you can get to the GUI interface now?

PC

At the GRUB boot loader menu, I get these options:

```

Ubuntu 8.04, kernel 2.6.24-16-generic
Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
Ubuntu 8.04, kernel 2.6.24-14-generic
Ubuntu 8.04, kernel 2.6.24-14-generic (recovery mode)

```

If I choose either of the 2.6.24-16 options, I simply get a blank
screen with "133-P19700-18" on it. Booting halts at that point and
the only thing I can do is ctrl-alt-delete to reboot.

If I choose either of the 2.6.24-14 options, I can boot (almost)
without issue (everything starts up, I get a graphical login, etc).

---

### Post by Peter09 on 2008-04-24
are you seeing a command prompt (is there a $ sign after the 18?)

if so try typing startx

PC

---

### Post by frmlt on 2008-04-24
> **Peter09 said:**
> are you seeing a command prompt (is there a $ sign after the 18?)

if so try typing startx

PC

The number that appears onscreen is not a command prompt. This message
is appearing before the kernel has even had a chance to load.

---

### Post by frmlt on 2008-04-25
Nobody knows then?

---

