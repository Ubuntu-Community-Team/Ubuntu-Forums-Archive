---
title: "[SOLVED] Fatal exception in interrupt"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by The Phoenix on 2008-08-15
Hi. For the past week I have been trying to install xubuntu on my old Win 98 computer. No matter what I try I can't get it to work. I have gotten many different errors but 9 times out of 10 its "Kernel Panic - not syncing: Fatal exception in interrrupt"
[INDENT]I have tried everything I can think of xubuntu helper install, alternate install disc, no cd install, update bios, etc. But I still keep getting this error. Here are my specs:[/INDENT]
[LIST]
[*]CPU:Pentium III 500mhz
[*]Motherboard: ABIT BE6
[*]RAM: 256
[*]HDD: 20 GB
[/LIST]

Can anyone help me with this?

---

### Post by Partyboi2 on 2008-08-15
What happens if you try this boot option ```
linux ide=nodma
``` Press F6 at the main menu and add it to the end, then press enter.

---

### Post by The Phoenix on 2008-08-16
Thanks for your help. I tried it 3 times so far. The first time I typed linux ide=nodma after "boot" in the boot line(I have that grub helper thing installed) and it got past the first error and then got hung up on "Checking 'hlt' instruction" (I've gotten this before too). The second time I typed "linux ide=nodma linux no-hlt" after boot but I got the same error that I posted. The third time I just typed "linux ide=nodma" again and got "Code: Bad EIP value." Then "EIP:" with what looks to me like a bunch of hexadecimial numbers, and then "Kernel panic - not syncing: Fatal exception in interrupt" again.

---

### Post by The Phoenix on 2008-08-16
Ok. Just tried it with the Live boot instead of the installer and got "Kernel panic - not syncing: Attempted to kill the idle task!"

---

### Post by Partyboi2 on 2008-08-16
Have you done a memory test to make sure its not a problem with your ram? You can choose the memory test at the main menu of the live cd.

---

### Post by The Phoenix on 2008-08-16
Yes I have. Almost 24 hrs. and no errors. Plus Win 98 runs fine.

---

### Post by The Phoenix on 2008-08-16
Well I found out that I didn't really update the BIOS when I thought I did, so I did that but it didn't seem to help. The screen from the disc shows up now but as soon as I boot it it goes to a black screen with a blinking cursor but I can't type. So then I did safe graphics mode and got the same kernel panic.

---

### Post by Partyboi2 on 2008-08-16
You could try adding noapci as a boot option as well.  Have you tried using these boot options with the alternate cd? Another thing you could try is to install [[COLOR=Blue]feisty [/COLOR]]("http://cdimage.ubuntu.com/releases/feisty/release/")or  [[COLOR=Blue]gusty [/COLOR]]("http://cdimage.ubuntu.com/releases/gutsy/release/")as it uses a older kernel and see what happens.

---

### Post by The Phoenix on 2008-08-16
Ok, I tried xubuntu 6.06.1 Dapper Drake and got the same kernel panic, Fatal exception error.

---

### Post by Partyboi2 on 2008-08-16
I am all out of ideas, I would suggest trying some more boot options like:
idle=poll
acpi=force irqpoll
pci=off
Maybe try another distro to see if its not just ubuntu that's having problems to install. Or maybe someone else might know.

---

### Post by The Phoenix on 2008-08-17
Ok. I'll try those options. As for the other distros, I tried DSL and it seems to load but then freezes on what I assume is their splash screen. I might try some more distros, but thanks for the help!

---

### Post by The Phoenix on 2008-08-17
Thanks for your help!!! I was able to get xubuntu load with your last suggestion. Now I just have to get it to recognize my hardrive. Thanks alot!

---

### Post by Partyboi2 on 2008-08-18
Good to hear you got over the first hurdle.

---

### Post by The Phoenix on 2008-08-18
Ok. So now that thats done, how do we mark this as solved and how do I thank you?

---

### Post by Partyboi2 on 2008-08-18
this will explain how to mark your thread as solved.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by The Phoenix on 2008-08-21
Ok. I got it completely installed and it is running fine. Just for the record.

---

