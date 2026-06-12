---
title: "No video -- monitor OK, new video card not working :S"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by altonbr on 2008-04-04
Oddest problem I've ever seen.

I'm trying to fix a clients computer because after I installed Ubuntu and she took it home, her video stopped working. I figured she just couldn't hook it up properly but when she brought in her monitor and computer, I knew it was more serious.

I plugged in her monitor and hooked it up to the computer but no video was displayed. I used that same monitor on another computer and it worked.

Not the monitor.

I figured it was either a bad connection for her VGA female end or her integrated Intel i910 video chip and those, both I can't fix. So I figured she needed a nice, cheap, PCI-E video card. (Luckily she had a PCI-E slot). Bought that, plugged it in, tried it on two different montiors and no video.

When I say no video, I mean even the BIOS/POST output doesn't show.

There is no beeping from POST either and this eMachines (Canada) computer has no debugging lights.

Her CPU seems to be running at full-tilt and so does her new video card fan... Her power supply is fine as far as I can tell...

Has anyone ran into this before? What can I do?

---

### Post by Pumalite on 2008-04-04
Did the video work after you finished installing Ubuntu?

---

### Post by 22flames on 2008-04-04
mother board to internal graphics card error what is her graphics chipset

---

### Post by prshah on 2008-04-04
> **altonbr said:**
> 
I figured it was either a bad connection for her VGA female end or her integrated Intel i910 video chip
 

Intel boards tend to go "dead" when the cmos battery has lost power. Same symptoms as you describe here. Typically she would be having troubles with date and time being maintained across extended periods of the machine being off.

i910 tells me it's an old motherboard. I would suggest removing and checking the CMOS battery (typicaly CR2032) voltage (should be around 3v for a good one) using a digital multimeter. If it is low, just replace it and clear CMOS. On some boards there is a jumper, and on some, you have to keep "F" or "J" pressed on your keyboard before and while starting the machine.

---

### Post by 22flames on 2008-04-04
yah i figuerd it might have gone dead as well

---

### Post by altonbr on 2008-04-04
First off, thank you everyone for your quick replies!

> **Pumalite said:**
> Did the video work after you finished installing Ubuntu?

Yes, that is why I'm so perplexed. I believe they are heavy smokers (as per the yellow dust in her tower), so I also suspect it could be due to corrosion.

> **prshah said:**
> Intel boards tend to go "dead" when the cmos battery has lost power. Same symptoms as you describe here. Typically she would be having troubles with date and time being maintained across extended periods of the machine being off.

Odd that POST wouldn't be beeping, isn't it?

> **prshah said:**
> i910 tells me it's an old motherboard. I would suggest removing and checking the CMOS battery (typicaly CR2032) voltage (should be around 3v for a good one) using a digital multimeter. If it is low, just replace it and clear CMOS. On some boards there is a jumper, and on some, you have to keep "F" or "J" pressed on your keyboard before and while starting the machine.

I'll give that shot, thank you.

> **22flames said:**
> mother board to internal graphics card error what is her graphics chipset

I believe it's Intel i910 as per `dpkg-reconfigure xserver-xorg`... there is a chip that says VIA in there, but I also bought a nVidia 8400, so it's not her video. Probably chipset... :S

---

### Post by altonbr on 2008-04-04
I reset the CMOS, replaced the CMOS battery and can confirm again that both monitors work.

What is not working is either the motherboard or both the brand-new nVideo 8400 card and the integrated Intel i910 VGA outputs...

What do you think?

Any text book manual I have simply says "check your monitor, check your cables"... not very helpful.

---

### Post by altonbr on 2008-04-04
I tested the CR2032, 3V CMOS Lithium battery and it is still working, so is the one I used to replace it...

Are we looking at the motherboard now? Still no beeping from POST

---

### Post by Pumalite on 2008-04-04
Get into your BIOS and make sure that whatever card you have installed is well configured.

---

### Post by altonbr on 2008-04-04
> **Pumalite said:**
> Get into your BIOS and make sure that whatever card you have installed is well configured.

I have no video output ;)

NOTE: I just booted up the machine WITHOUT RAM and WITHOUT a hard drive, and there were no beeps from POST... assuming POST has a speaker to use to make that beep on an error.

Can we safely say it's the motherboard?

---

### Post by Pumalite on 2008-04-04
Sorry, you are right.

---

