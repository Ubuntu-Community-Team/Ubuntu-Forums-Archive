---
title: "A most annoying problem"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by Iviesaur on 2010-04-28
I'm trying to install Ubuntu 9.10 on my computer i have a cd. Yes it does work i've tried it on another computer. I'm using a Compaq Presario with a pentium 4. I've gone into the BIOS placed CDR on the top for the boot order yet i can not get it to the installation screen. Does anyone have any ideas as to why this won't work? Also i am now just thinking of dual booting (even though i don't want to cause i heard it uses alot of memory) :// so if anyone has any good ideas or thoughts please let me know. I'll be happy to try anything. Thank you.

---

### Post by sxmaxchine on 2010-04-28
if you have windows already installed you can insert the disk and try using the wubi.exe program.

---

### Post by Iviesaur on 2010-04-28
Yes but that leaves windows on my computer i'd like to just only have Ubuntu cause from what i understand dual booting takes up alot of memory

---

### Post by sxmaxchine on 2010-04-28
are you able to boot from the cd if so does it give you an error message.

---

### Post by Iviesaur on 2010-04-28
> **sxmaxchine said:**
> are you able to boot from the cd if so does it give you an error message.
no i can't get to the installation screen at all. it just goes straight to XP like it doesn't read the cd at all

---

### Post by quadproc on 2010-04-28
> **Iviesaur said:**
> I'm trying to install Ubuntu 9.10 on my computer i have a cd. Yes it does work i've tried it on another computer. I'm using a Compaq Presario with a pentium 4. I've gone into the BIOS placed CDR on the top for the boot order yet i can not get it to the installation screen. Does anyone have any ideas as to why this won't work? Also i am now just thinking of dual booting (even though i don't want to cause i heard it uses alot of memory) :// so if anyone has any good ideas or thoughts please let me know. I'll be happy to try anything. Thank you.
Your BIOS may be somewhat buggy: I know that mine is (although I'm sure it isn't the same as yours).

Try getting the attention of the BIOS at boot time by pressing one of the following keys: F2, F8, F10, F12 (try this one first), ESC.  Hopefully one of those will bring up a BIOS screen which will allow you to choose what to boot from.

quadproc

---

### Post by sxmaxchine on 2010-04-29
there is a way to fix that using wubi.

1. open wubi and click demo and full instalation
2. then select hel me boot from cd then click finish
3. then click install and now you should be able to boot from cd

hope this helps

---

### Post by Gbeattie on 2010-04-29
do you have 2 cd/dvd drives?.. it may be trying to read from the wrong drive, try the disk in the other drive

---

### Post by Mark Phelps on 2010-04-29
> **Iviesaur said:**
> Yes but that leaves windows on my computer i'd like to just only have Ubuntu cause from what i understand dual booting takes up alot of memory

That's not correct.  You are confusing dual-booting with virtualization.  It's the latter that uses more memory, not the former.

With dual-booting, you are given a choice of which OS to boot.  Once that happens, you are using no more memory than if you just had that one OS installed.

---

