---
title: "Can I replace mobo/chip/ram without Ubuntu re-install?"
date: 2011-07-28
forum: Installation &amp; Upgrades
---

### Post by mfearby on 2011-07-28
I have 10.04 LTS installed onto an SSD and have a spinning disk for crud, and my brother wants to give me his old GA-PH67A-UD3 and 8GB of RAM if I buy an i7 2600 to put in it. The thing is, I'm happy with my GA-965P-DS3 with Q6600, so I don't actually need an upgrade.

So, can I get away with replacing the mobo, chip, and RAM and putting the SSD in the equivalent SATA port on the new mobo (/dev/sda), and will it cope? Will the kernel detect a new board and chip and carry on accordingly?

I'll have to remount my crud drive to the same mount point it expects, and if my user account as the same UID as the old system, I'm hoping that might cope, too.

Of course, I might be suggesting complete evil, and if this was Windows, I wouldn't even dare think about it, but I have a sneaking suspicion that Linux might cope with this kind of change where Windows would fall over in a heap.

Thanks.

---

### Post by An Sanct on 2011-07-28
From my experience it will work, unless you would force a 32bit CPU on a 64bit OS (q6600 and i7 are both 64bit)

I would still go at it with a great deal of caution... The first step would be to uninstall ANY third party drivers, even if they are going to be used afterwards, this means (mainly) GPU and any other drivers visible via System>Administration>Additional Drivers.

Also as you noted, putting the disks in the same/equivalent SATA ports will be a thing to do.

Another good way to do this would be to back up your home folder and all the installed software and just drop them into the new setup. (There where a lot of threads about this ...)

:) Thats my 5 cents ... Note, that altho I did go through a similar situation, I cannot say 100% for sure, that it will work for you too.

PS. A great example of (crazy) switching amongst various hardware setups is the "Live" session version :)

---

### Post by mfearby on 2011-07-31
Thanks for the advice. I may as well just back everything up and do a fresh install, but re-mount my user drive after a clean OS install, so I get most of my application settings back (such as compiz, bash, gnome, etc). I'm just lazy and wanted to avoid the repeated visits to Synaptic as I realise X or Y package needs to be installed.

It would be nice to somehow generate a list of packages I've actually installed myself since I first installed 10.04 over a year ago. Then I could just install them all in one visit to the package manager.

---

### Post by Hakunka-Matata on 2011-07-31
there is a command to write a list of all your installed applications out to a disk file.  It is also possible to write that list and feed it back into a new installation automatically.  I've done it, it's sweet.

I can't tell you how at the moment, but a search will probably find it for you.  It's late, I'm off to sleep, I'll check in tomorrow

---

### Post by Hakunka-Matata on 2011-07-31
here ya go:
[http://www.smartietips.com/2011/05/16/reinstall-your-ubuntu-apps-after-a-fresh-reinstall/]("http://www.ubuntugeek.com/howto-reinstall-all-of-currently-installed-packages-in-fresh-ubuntu-install.html")

---

### Post by mfearby on 2011-07-31
> **Hakunka-Matata said:**
> here ya go:
[http://www.smartietips.com/2011/05/16/reinstall-your-ubuntu-apps-after-a-fresh-reinstall/]("http://www.ubuntugeek.com/howto-reinstall-all-of-currently-installed-packages-in-fresh-ubuntu-install.html")

Thanks. That is so awesome :D My new chip hasn't arrived yet but the thought of switching mobo/chip/ram is no longer something even a lazy sod like me can whine about.

*begin sarcasm* What? No bloated XML output? Just a simple text file listing of package names followed by a space and the word "install"??? My .NET friends would be very disappointed at the lack of padding :-)

---

### Post by mfearby on 2011-08-03
Well, I've replaced the motherboard, CPU, and memory. Booted up and thought "I might just let the OS boot and see what it thinks" and, apart from booting faster than before, it let me log in, everything is fine, not a single complaint. The only visible difference is gkrellm showing 8 little graphs instead of 4.

I'm thinking of not even bothering with a fresh re-install. I've been using Linux for several years now so I don't even feel "dirty" like I would if I had done this with Windows. Not a single sign of there being even a tincture of a problem.

Kudos to Linux and to Ubuntu 10.04 :-)

---

