---
title: "Installation of Ubuntu 18.04 taking hours on &quot;Configuring Hardware&quot; stage"
date: 2018-06-12
forum: Installation &amp; Upgrades
---

### Post by deutne on 2018-06-12
Hello, 

I have been using Ubuntu for many years on a variety of machines, but I have not been particularly active on the forums or in bug reporting. 

I am currently trying to install the following ISO (ubuntu-18.04-desktop-amd64.iso) on an HP 250 G6 laptop. I previously had no success installing 17.10 on the same machine, but I was hoping that whatever wasn't compatible with my very new machine would be fixed by the time the 18.04 version was released. 

The installation of 18.04 has been "Configuring Hardware" for about 10 hours now. It is still providing new output messages, but it is proceeding at a snail's pace, and I am very sceptical that a stable, well-running installation is going to come out of this. I unfortunately do not know how to save a log file of the messages or access such a file that may be automatically saving. The output messages include many about lowering kernel performance (for example, ubuntu kernel:  [15061.058108] perf: interrupt took too long (6302 > 6280), lowering kernel.perf_event_max_sample_rate to 31500... {cut off}). There are also lots of messages that say "Started Run anacron jobs." I am attaching some photos of the screen.

I would love some help in figuring out how to get a working version of Ubuntu onto this computer.

---

### Post by ajgreeny on 2018-06-12
I wonder if you've come a cropper on the HP problem of their UEFI machines only booting bootloader files that are from, or are renamed to give the impression that they are from a Windows OS.

There is a great deal of info on such problems, along with several other machine makes, and workarounds for those problems, in the long but very detailed thread at [https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295).

---

### Post by deutne on 2018-06-12
Good grief! That looks annoying. I will have to slog through that one and see if it applies.

---

