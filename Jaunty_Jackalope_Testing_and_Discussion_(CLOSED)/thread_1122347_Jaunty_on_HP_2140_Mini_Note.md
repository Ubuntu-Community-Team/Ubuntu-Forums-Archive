---
title: "Jaunty on HP 2140 Mini Note"
date: 2009-04-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by thyrcson on 2009-04-11
Just a short story of success.

Yesterday I installed the Jaunty beta on my new HP 2140 Mini-Note, and almost everything worked right out-of-the-box! Sound and wireless work flawlessly (I haven't tested the microphone jack, yet...)

But I couldn't get the Mini to shutdown, suspend or hibernate properly.

The machine would halt but not power down.

Today I found the culprit I wanted to share my - or actually splux' findings - from the Neptun Forum (at [https://forum.neptun.ethz.ch/read.php?42,540,1210](https://forum.neptun.ethz.ch/read.php?42,540,1210))

Be sure to disable the "Fan always on when on AC" option the BIOS and delete the acpi=off switch in the grub boot options.

There you go.

---

### Post by dichro on 2009-04-18
Huh. I received my brand new 2140 a couple of days ago and did a USB install of Jaunty last night. Observations:

* Had to use acpi=off to get usb netboot image to boot
* Had to add irqpoll to get installed kernel to boot
* Playing sound would rapidly hang the machine (mostly during greeter startup sound, once got far enough to start listening to login sound)

I'll try your suggestions, and will hope for the best!

---

### Post by dichro on 2009-04-18
Alas, still not straightforward. I disabled the fan-always-on BIOS setting you mentioned, but taking out acpi=off leads to instant oops on boot at the bottom of a cpu_idle trace. Booting with nosmp seems to avoid this, however, and it seems to work without irqpoll as well. Sound is still disabled, but I have S3 suspend available now, so will try that at some point.

---

### Post by thyrcson on 2009-04-20
@dichro
I had the same problem during install.

I did boot the liveCD (actually liveUSB) with the acpi=off noapic nolapic irqpoll options. Did a full install and updated the box. 

A small note:
I ran into some problems during install. For some reason Ubuntu rebooted bofore the install was finished (I remember reading something about that in a few threads, but I will have to look it up later...). I started again from USB in 'Save mode'(?, some thing like that) and repaired dpkg when promted. Again, I will have to give a detailed explanation later, sorry.

After that I could boot into my fresh Ubuntu system.
Ich changed the grub menu.lst (deleted the acpi=off noapic nolapic irqpoll entries) and it worked.

So right 'out-of-the-box' might be a little too enthusiastic a term. But it worked.

Sound works (even with Skype, but I had to change the sound device). And again: Details follow. 

Sorry for the delay, but right now I'm quite busy.

nosmp doesn't seem to be the way to go, though... just a thought.

---

### Post by dixon on 2009-04-20
Try to disable dual cpu support in bios. [It works for me](http://ubuntuforums.org/showthread.php?t=1115691) ;)

---

### Post by thyrcson on 2009-04-20
You're absolutely right!

The N270 **is** a single core processor. It is, isn't it? :o I will try this later this evening.

Thanks!

---

### Post by dichro on 2009-04-23
@dixon you're absolutely right :) I guess other OSes count the number of processors and just throw out the multi-processor ACPI directions :P

Laptop now working fine without any extra kernel command line flags (haven't tried suspend/resume since this last change, but S3 and S4 were both working before, so I expect them to keep doing so!)

Thanks!

---

### Post by dixon on 2009-04-23
Glad I could help ;) Suspend and hibernation works fine, but internal mic isn't working and closing the lid also does nothing. If you figure out how to solve these 2 things please post :)

---

