---
title: "Trying to install ubuntu or any linux period"
date: 2007-07-23
forum: Installation &amp; Upgrades
---

### Post by igoclimbingnaked on 2007-07-23
Alright everytime i install a form of linux it will never load when i try to boot it. Also i cant ever get it to succesfully boot from a live cd. 

The mother board is a Mitac with a Intel 845 (brookdale) Chipset
My processor is an intel pentium 4 with 2.0 ghz
My graphics card is an Nvidea GeForce4 MX 4000
I have roughly 750mb of ram
My hardrive is a 40 gb ata

any ideas if i can actually possibly run linux on my system

---

### Post by ddrichardson on 2007-07-23
You should be OK, is this a built system, or an off the shelf - if so model number?

What errors are you seeing and to what point do you fail loading Ubuntu live cd.

---

### Post by igoclimbingnaked on 2007-07-23
Its kind of a combo....its a dell dimension 2350 but ive added the graphics card and the harddrive. 
When i boot from the live cd it crashes after the loading bar finishes. The command prompt style text stuff starts running and then just stops and never moves again.

---

### Post by ddrichardson on 2007-07-23
Does the same thing happen with other distros?

---

### Post by igoclimbingnaked on 2007-07-23
I tryed redhat and it did the same type thing yes....they all never completely boot...its really confusing

---

### Post by ddrichardson on 2007-07-23
Have you got windows installed without any problems?

Excellent nickname by the way...

---

### Post by igoclimbingnaked on 2007-07-23
lol thanks....yah windows is installed perfectly fine.

---

### Post by ddrichardson on 2007-07-23
the most likely candidates are power management or your graphics adapter.

Try the alternate cd with acpi turned off. There's a thread[ here]("http://ubuntuforums.org/showthread.php?t=257912") about it.

---

### Post by MrHippocampus on 2007-07-23
It may also be bad RAM, you could try running the memory test on the install cd for a while and see if it comes up with anything.

---

### Post by igoclimbingnaked on 2007-07-23
well as for the no acpi thing.....i got it to do something different off the live cd....but it just froze at the same point that it did when i actually had it installed..it would load to the third bar on the loading bar and stop.

---

### Post by ddrichardson on 2007-07-23
If, when you're at the point where it stops, can you do <CTRL><ALT><F2> and see if there are any error messages displayed.

---

### Post by igoclimbingnaked on 2007-07-23
It wont let me <ctrl> <alt> <f2> its like my keyboard is off. And the mem test came up with no problems.....

If i let it run normally theres a few visable error messages

something along the lines of Unable to handle kernal paging request at adress ffff(something)

and the theres the fatal exception in interupt or something

---

### Post by markusf21 on 2007-07-23
the only thing I can think of is a bad cd/burn

---

### Post by igoclimbingnaked on 2007-07-23
Ive burned like 8 diffrent cds......all do the same thing....well there on dvds but that wouldnt matter.

---

### Post by Pumalite on 2007-07-23
Don't forget to do md5sum on your iso. Burn at 4x. Check your CD for corruption before install.

---

### Post by igoclimbingnaked on 2007-07-23
what is md5sum and if i already checked it for corruption should the burning speed matter

---

### Post by Pumalite on 2007-07-23
It all matters. Your md5sum on your iso is fundamental before you burn. [http://www.etree.org/md5com.html](http://www.etree.org/md5com.html). Burning at 4x avoids CD corruption.

---

### Post by igoclimbingnaked on 2007-07-23
well now im sure the cd is not corrupted so yah still stuck

---

### Post by ddrichardson on 2007-07-24
This is just a thought, given that these errors point towards a bad burn, have you another cd device you can try - the drive itself may be faulty.

---

### Post by igoclimbingnaked on 2007-07-26
i guess thats what it is cuz i tryed to boot the dvd from a laptop and it wouldnt boot it wouldnt even show the ubuntu screen...but my pc did...which kinda raises more questions but oh well....Ill prolly just go buy some blank cds and burn it onto that from a diffrent pc.

---

### Post by ddrichardson on 2007-07-26
Have you tried removing the cd drive, cleaning out the contacts (use air) and refitting it?

---

