---
title: "Hanging during install"
date: 2006-07-18
forum: Installation &amp; Upgrades
---

### Post by 09amw on 2006-07-18
I have just recieved a livecd from shipit (because the bandwith sucks so much at home).  However, when trying to install on our old Compaq Presario 7970, the boot sequence hangs during the "creating new live user" stage of the checklist.  Briefly, earlier, I managed to get it to boot through to the running live version, but it hung and crashed when i clicked on the "install" link.

Any ideas?  Thanks a lot.

---

### Post by ferebee on 2006-07-18
If you can manage it, try the alternate install cd (can be downloaded from the main [ubuntu]("http://www.ubuntu.com") page.

Or if downloading isn't an option you could play around with the booting options until you find a combination that works for you.
Other users have found adding noapic nolapic to the boot parameters helped. you can add these by pressing f6 at boot.

I had to boot with **Start Ubuntu in Safe Graphics Mode** and
boot with noapic nolapic acpi=off, and reconfigure xserver-xorg afterwards, but it did work in the end!

---

### Post by 09amw on 2006-08-03
Well, I seem to have totally screwed this up.

So, I couldn't get ubuntu to boot with any boot modifications.  Every single time, it hung at that same "adding live user" step, forever, and then blacked back to the "Uncompressing Linux.... Ok, loading the kernel" blackscreen that preceeded the ubuntu checklist.  So I figure, ah the computer doesn't have enough RAM to properly run the ubuntu installer, so it probably wouldn't run ubuntu well either, okay I'll just download xubuntu.  Fine.

So, I download xubuntu, burn the image to a cd, pop it in, and start the boot sequence.  Which works.  Perfectly.  Until the last step, when I'm supposed to get xfce goodness, I get a blue screen with a functional mouse, and nothing else.  I can move the mouse, and that's it.  (Well, I could bang on the keyboard to no avail, but that's another story.)

I figure, well, just a minor boot error, I'll try again with my noapic nolapic debian-installer/framebuffer=false mishmash again.  And now, instead of booting to random blank blue screen, it freezes the EXACT same way that it did for the ubuntu install, at the add live user step.  And then flashes back to the blackscreen.

What the heck is wrong?  Why did it boot something (although not something useful) before, and now not boot at all?  Have I corrupted something?  Nothing's fried, I'm sure.  I checked, and besides, the stupid thing still turns on.  The harddrive is blank; I've previously erased everything.

I pretty much give up, and/or need serious help.  If I haven't supplied enough information for y'all to figure out what I've messed up, just mention the specific lacking details and I'll fill them in.

I would really rather get linux running than revert to the hell known as Win98 on this computer.

Thanks for all your help.

---

### Post by 09amw on 2006-08-05
can anyone help?  please?

---

