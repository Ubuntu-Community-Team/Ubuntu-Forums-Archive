---
title: "Text console resolution problem"
date: 2005-06-08
forum: Installation &amp; Upgrades
---

### Post by plcdfa on 2005-06-08
I was unsure where to post it, as I'm not sure of the type of the problem either. It might be very trivial, though  I couldn't find anything about it with google - if it is, please don't flame me, I'm relatively new to Linux. Oh, and sorry if I make grammar mistakes -  I'm not a native speaker.

So the problem is if I pass a vga=something parameter to the kernel at boot (cos I'm using Splashy) my text mode ttys become completely unusable. During the boot process they look just normal if I press F2, but after X starts and I switch to them they're in a very unreasonable resolution - one character occupies quarter of the screen. Needless to say it's completely impossible to use them that way. And at shutdown it also shows some crap instead of the Splashy screen. Strange is that the problem didn't started when I installed Splashy - I remember it working perfectly, but then something went wrong, and now I can't fix it, no matter what resolution I give with the vga= parameter. The only thing I can think of is that I installed the nvidia driver for my geforce fx not long ago - but i'm not sure if it's got anything to do with my problem, and even if so what would be the workaround. I'd really appreciate any help.

---

### Post by alastair on 2005-06-08
What's "Splashy"? Maybe that's the problem? Might be worth uninstalling and seeing it it helps.

I use "vga=791", no "Splashy" and things are fine.

---

### Post by plcdfa on 2005-06-09
Splashy is a boot-splash program, it displays a nice picture and progressbar during the boot process instead of the text. I might uninstall it, but in fact it's the only reason I use the vga parameter at all. I don't have any problem with the default resolution, but Splashy only works this way.
Besides my kernel doesn't accept the 791 number after vga= It says "undefined video mode" or something like that. I don't know if it's the resolution or the format, as i gives it the parameter in hexa format instead of decimal.

---

