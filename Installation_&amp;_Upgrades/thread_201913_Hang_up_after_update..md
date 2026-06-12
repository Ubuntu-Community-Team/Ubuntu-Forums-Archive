---
title: "Hang up after update."
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by KooT on 2006-06-22
have instaled kubuntu 6.06 on my laptop (IBM T20). Its was all ok. But after upgrading into new kernel, its now hang up just before it try to run X.
All i can see then its non-blinking cursor in the top left corner...

Any idea how to find and fix this problem?

---

### Post by user1397 on 2006-06-22
[quote=KooT]have instaled kubuntu 6.06 on my laptop (IBM T20). Its was all ok. But after upgrading into new kernel, its now hang up just before it try to run X.
All i can see then its non-blinking cursor in the top left corner...

Any idea how to find and fix this problem?[/quote]what new kernel did u install, and what processor do you have?

---

### Post by KooT on 2006-06-22
2.6.15-25-386 #1 PREEMPT
Pentium III Coppermine 700Mhz

I will try install diffrent kernel...

eh...

---

### Post by KooT on 2006-06-22
[QUOTE=KooT]2.6.15-25-386 #1 PREEMPT
Pentium III Coppermine 700Mhz
I will try install diffrent kernel...
eh...[/QUOTE]

the same with 2.6.15-25-606
and 2.6.15.23-386... maybe kernel is not the problem... but how can i find why its
stop? :(

---

### Post by user1397 on 2006-06-22
[quote=KooT]the same with 2.6.15-25-606
and 2.6.15.23-386... maybe kernel is not the problem... but how can i find why its
stop? :([/quote]kernel 2.6.15.25-386 is fine, your problem might have to do with X.  try pressing CTRL+ALT+F1 which will take you to a command-line.  then type: ```
sudo dpkg-reconfigure xserver-xorg
```and choose all of the default ones if you're not sure, but for graphics try the vesa driver, if it doesn't work, try a different one.

---

### Post by KooT on 2006-06-22
[QUOTE=erik1397]kernel 2.6.15.25-386 is fine, your problem might have to do with X.  try pressing CTRL+ALT+F1 which will take you to a command-line.  then type: ```
sudo dpkg-reconfigure xserver-xorg
```and choose all of the default ones if you're not sure, but for graphics try the vesa driver, if it doesn't work, try a different one.[/QUOTE]

I cant switch to command line, its totaly hang up... but in recovery mode i reconfigured xorg... but still the same... ;(

---

### Post by user1397 on 2006-06-22
[quote=KooT]I cant switch to command line, its totaly hang up... but in recovery mode i reconfigured xorg... but still the same... ;([/quote]can you go into grub at startup?  you would press escape (default time delay is 3 seconds so you gotta be quick) and try to boot into the 2.6.15.23-386 kernel.  if it works, then it's just that the -25 kernel doesn't work, and i dont know how to fix that, sorry

---

### Post by KooT on 2006-06-23
Ok, thank You for all Your replay! ;)

---

### Post by FredB on 2006-06-23
[QUOTE=KooT]have instaled kubuntu 6.06 on my laptop (IBM T20). Its was all ok. But after upgrading into new kernel, its now hang up just before it try to run X.
All i can see then its non-blinking cursor in the top left corner...

Any idea how to find and fix this problem?[/QUOTE]

Besides the answer which were given here, I want to ask you : what is the video chipset ?

ATI ? Nvidia ?

Did you install any 3D accelerated server for your chipset ? It could be an answer for your booting problem.

If so, try - using synaptic - to add the restricted module version compatible with the "faulty" kernel.

Just an idea, of course ;)

---

### Post by KooT on 2006-06-27
[QUOTE=FredB]Besides the answer which were given here, I want to ask you : what is the video chipset ?

ATI ? Nvidia ?
[/QUOTE]

Its quite old laptop with S3 savage video card, i changed driver into "vesa", and its working...

---

