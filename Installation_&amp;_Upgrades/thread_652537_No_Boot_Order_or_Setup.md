---
title: "No Boot Order or Setup"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by mattwinsatlife on 2007-12-28
I know I'm supposed to try to hit DEL for the setup menu before Windows loads, but my Windows XP isn't giving me that option. When I turn on the computer, it goes from a blank screen, to the screen for my Intel board, then the Windows XP loading bar.

Therefore, I can't even get the computer to boot from the Ubuntu Live CD...

Suggestions? O_o

---

### Post by Pumalite on 2007-12-28
What computer and what BIOS do you have?

---

### Post by mattwinsatlife on 2007-12-28
Well that's kind of the problem. It's not showing me anything.

I have a self-built PC. Pretty average Intel board, P4 processor 2.4GHz, 1Gb RAM, about 4 years old now

---

### Post by oldos2er on 2007-12-28
I believe the "screen for your Intel board" is what you're looking for.

---

### Post by halw on 2007-12-28
Sounds like you need to set the boot order in your bios.

Find out what bios you have and go to that web site to find out what keys you press to enter the bios setup. From there change the boot order to look at your optical drive first.

---

### Post by Partyboi2 on 2007-12-29
If its a intel motherboard you should be able to access the bios pressing "del" like you have been doing. As soon as you  turn the pc on just keep pressing the del button. Sometimes its all about the timing. :)
If that does not work then you could try one of these instead to see if that works.[LIST]
[*]                   F1
[*]                   F2
[*]                   [ESC]("http://www.computerhope.com/jargon/e/esc.htm")
[*]                   F10[/LIST]

---

### Post by alexandroid on 2007-12-29
During booting or restart monitor gets turned off and on, so it may not be quick enough to show you the BIOS screen with a hint to press DEL button (or whatever button it uses).

You should try pressing the button repeatedly (not too fast =), like 3-4 times per sec) as soon as your screen goes blank and until you either get into BIOS or see Windows loading bar. If you see Win bar, then you missed it, or the key was wrong. =)

Another way you could try -- pressing "pause" key when the screen goes blank, but I am not sure it works during the power-on-self-test. Pause can freeze the boot so monitor can catch up and you can see the screen. To un-pause press space (but you will have to press DEL-or-whatever-key-your-bios-wants anyway to enter the BIOS right after you unpause).

---

