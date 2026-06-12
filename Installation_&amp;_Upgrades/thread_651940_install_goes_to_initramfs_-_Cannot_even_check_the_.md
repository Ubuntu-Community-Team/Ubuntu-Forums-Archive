---
title: "install goes to initramfs - Cannot even check the CD"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by FFMG on 2007-12-28
Hi, 

When I run the install I go straight to the initramfs prompt after the splash screen.
When I remove the quiet option everything seem to run ok until I get the prompt.

I get some errors 

```

ide0cd: 0x5a timed out
hdc: lost interrupt
end_request: I/O error, dev fd0, sector 0
...

```

and if I don't touch the prompt then every 10-20 seconds a new message is displayed.

```

hdc: lost interrupt
hdc: ATAPI 24X CD-RIM drive, 128kB Cache, UDMA(33)
...

```

I have checked on another machine and the CD check runs fine with no errors.
I tried a few advices on this forum but nothing seems to work.

Any ideas as to what the problem could be?

What other information do you need?

Thanks

FFMG

---

### Post by FFMG on 2007-12-28
It is an acer travelmate 200.

[http://www.acersupport.com/notebook/html/tm200.html](http://www.acersupport.com/notebook/html/tm200.html)

I am running xubuntu btw, but the system does not start the install so I doubt it matters.

FFMG

---

### Post by Craigus on 2007-12-28
It may be a hardware fault in the CD drive - as a test, what happens if you try a different distro, like antix :

[http://antix.mepis.org/index.php/Main_Page]("http://antix.mepis.org/index.php/Main_Page")

or PCFluxboxOS:

[http://pcfluxboxos.wikidot.com/]("http://pcfluxboxos.wikidot.com/")

---

### Post by FFMG on 2007-12-28
> **Craigus said:**
> It may be a hardware fault in the CD drive - as a test, what happens if you try a different distro, like antix :

[http://antix.mepis.org/index.php/Main_Page]("http://antix.mepis.org/index.php/Main_Page")

or PCFluxboxOS:

[http://pcfluxboxos.wikidot.com/]("http://pcfluxboxos.wikidot.com/")

Thanks, I'll give it a try.

But I don't know if it is worth it, I thought that (x)Ubuntu would be a nice new OS, but it does not seem more stable than MS.

F.

---

### Post by steve_d on 2008-01-03
I had that initramfs problem on my first install, I had been using a USB key, and the 'windows installer' to install. I got some CD's the next day, and installed it from the disk as bootable instead of trying through the windows program and never had the problem again.

If you were using the windows installer , this may be the problem.

-Steve

---

### Post by FFMG on 2008-01-04
> **steve_d said:**
> I had that initramfs problem on my first install, I had been using a USB key, and the 'windows installer' to install. I got some CD's the next day, and installed it from the disk as bootable instead of trying through the windows program and never had the problem again.

If you were using the windows installer , this may be the problem.

-Steve

Not sure what the problem was.
In the end I installed xUbuntu Alternate and that did not give me any problems.

I had to use the 'irqpoll' install option, (as suggested in the install), maybe that would have worked with the default xUbuntu install as well.

FFMG

---

