---
title: "Quadrapassel does not run"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by atlee on 2010-04-08
I installed Ubuntu 10.04 Beta 2 Netbook edition on my old laptop, installed perfectly, boots perfectly, no crash errors.

I Click Games, AisleRiot runs, Mahjongg runs, Sudoku runs but I cannot get Quadrapassel to run, it says Loading then nothing, Anyone else can re-make this issue or is it only related to myself?

Can anyone else reproduce this, Is it only attached to Netbook edition or all editions?

---

### Post by Mr. Picklesworth on 2010-04-08
Could you please try Nibbles, Lights Off or Swell Foop? (Or try running it in a terminal). It's probably because your driver doesn't support GLX, which is now needed for Quadrapassel since it has started using the Clutter library. Could be a temporary hitch; seems to break every now and then for the Intel drivers :b

---

### Post by atlee on 2010-04-08
failed to create drawable
Failed to initialise clutter: Unable to select the newly created GLX context

So does this mean it will not run on 2D cards that don't support any 3D rendering whatsoever or can it run on 2D cards?

---

### Post by Mr. Picklesworth on 2010-04-08
> **atlee said:**
> failed to create drawable
Failed to initialise clutter: Unable to select the newly created GLX context

So does this mean it will not run on 2D cards that don't support any 3D rendering whatsoever or can it run on 2D cards?

Sorry, it won't run on older cards. That does mean it's *very* cool on newer cards :)

(And yah, would be nice if it had some kind of error handling. *Sigh*...)

---

### Post by atlee on 2010-04-08
Well Nibbles runs but does not start a new game, Lights off and Swell floop i'm assuming terminal will show same GLX error message, It's a SiS S3 Unichrome chipset, i do have my desktop but for it to still run on my laptop would of been nice too oh well.

---

