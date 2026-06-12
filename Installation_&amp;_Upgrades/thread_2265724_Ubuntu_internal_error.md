---
title: "Ubuntu internal error"
date: 2015-02-17
forum: Installation &amp; Upgrades
---

### Post by andrew201 on 2015-02-17
Upon the initial boot of Ubuntu I received a message "Sorry, Ubuntu 14.04 experienced an internal error."  Some screen shots of the error output are below.

---

### Post by v3.xx on 2015-02-17
This is apport.  It can be disabled if your getting a false report.

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

But first you can try resetting it by removing the crash reports in /var/crash/.

---

### Post by andrew201 on 2015-02-17
It didn't seem like a false report.  The computer was not usable and I was lucky to get access to the pictures above.  The mouse moved on the screen with a delay of 10's of seconds.  There was something in an error that mentioned a core of the CPU was maxed out, which  is exactly what it seemed like was happening.  I posted the pictures because I wasn't sure I would be able to do anything else with the machine.  Thanks very much for the reply.

---

### Post by v3.xx on 2015-02-17
Ok, looks like you got kerneloops going on.
[https://wiki.ubuntu.com/DebuggingKernelOops](https://wiki.ubuntu.com/DebuggingKernelOops)

This also looks like a fresh install, so better to start there.

How did you install?  Did you do a checksum on the download?  Did you burn the dvd at low speed?

And for reference, what are your computer specs (ram, cpu, video)?

edit
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=how+to+checksum&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=how+to+checksum&sa=Search&cof=FORID:9)

---

### Post by andrew201 on 2015-02-17
I installed with a DVD.  I tried to use a USB and it hung.  I don't know if I did a checksum download or not.  I suspect that not knowing is enough to mean that I didn't.  :)  I also didn't fiddle with the burn speed on the DVD burner.  The computer is an old Dell tower.  The processor is an AMD Athlon dual core 4400+.  There are 2 gb or ram and I am using the on board video controller.  I did have an external PCI-e video card in the computer at time of install, but I had the bios set to look on the mother board.  I am using a 40 gb Intel SSD.  Oh, and it is a fresh install.  The pictures I posted are after rebooting a couple of times because it locked up but essentially immediately after a fresh install.  After crashing the computer did want to run through a memory check.  It went for quite a while and I got sick of it and stopped it about 1/2 way.  There were no errors.  I should also say that this machine was previously a windows XP machine and worked find up until yesterday when I switched it to Ubuntu.  (That sounds like I am blaming Ubuntu which I am not.  I am only saying that the hardware, although old, should be fine.)

Thanks.

---

### Post by v3.xx on 2015-02-17
Have you tried the option to run ubuntu from the dvd before installing?

Also ubuntu is graphics demanding and your on board video controller probably can't handle it.

Try running a live session.  You may have to go with a desktop that is easier on your resources.

---

