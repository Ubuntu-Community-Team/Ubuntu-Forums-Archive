---
title: "Jaunty Instability"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hartz on 2009-04-12
Is it just me or is x.org unstable?

Actually, I assume it is the X server.  I've had a few cases of "partial freezing".  When this problem occur, I find that the mouse buttons become un-responsive.  Some keyboard combinations also do not work, eg Alt-TAB.

Others continue to work (eg Alt-2)

If I start a terminal (eg via Alt-2) I can enter commands in it and these work as expected.  The system appears to be "mostly functional"... The missing mouse burron functionality as well as some key combinations stopping appears to be the main symptom of this effect.

Has anybody else seen this?

For what it is worth, I wiped my old Ubuntu 8.04 install, doing a fresh install of Jaunty Beta.  The problem has so far happened maybe three or four times with exactly the same symptoms, over the past 2 weeks.

I have disabled Compiz for my main account and I think that has helped - I just had a recurrence a few minutes ago when I logged in under a different user name with a blank profile, so I suspect the default settings on that account had Compiz effects enabled.

---

### Post by coffeecat on 2009-04-12
Without knowing what your graphics card is and what video driver you're using, it's impossible to comment. I'm posting from Jaunty Beta from my 4-year old laptop with the old Intel 915G graphics and only 512 GB RAM, and everything's fine. Wobbly windows, rotating cubes and all. Ditto my desktop with nvidia card.

Have you looked in the Jaunty subforum? -

[http://ubuntuforums.org/forumdisplay.php?f=352](http://ubuntuforums.org/forumdisplay.php?f=352)

You might want to ask a moderator to move this thread there where you're more likely to find forum members with experience of Jaunty.

---

### Post by hartz on 2009-04-12
My Graphics is the excuse for a graphics accelerator Toshiba put into the Tecra M5 notebook.

01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M] (rev a1)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb


Regardless, I find it unlikely that the graphics chip is related to X ignoring (becoming blind to) specific mouse and keyboard events.

---

