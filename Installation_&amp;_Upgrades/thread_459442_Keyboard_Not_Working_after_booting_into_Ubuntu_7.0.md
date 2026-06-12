---
title: "Keyboard Not Working after booting into Ubuntu 7.04 install disk"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by sme445 on 2007-05-30
Hi
I'm new to Linux and have decided after years of Windows that I'm going to install Ubuntu in a dual booting system (WXP & Ubuntu, PIV processor, 512MB RAM, ). I obtained Ubuntu Desktop 7.04 and booted into the demo version. After playing around with it I decided to install, but when it gets to the stage that I have to type in info (e.g. passwords for imported windows accounts), my keyboard doesn't work. It is an old style PS2 connection keyboard (my USB mouse works fine). Is there any obvious reason anyone can think of why I lose my keyboard after selecting to boot into Ubuntu demo/install?
Thanks

---

### Post by QwUo173Hy on 2007-05-30
I had the same problem. I highlighted the "start ubuntu in safe graphics mode" and pressed F6.
I then typed
> vga=771 noacpi noapic nolapic
By the way, that's an L in the last option, not a 'one' as I thought.

---

### Post by sme445 on 2007-06-01
Thanks for the suggestion. I tried this, but the end result was the same. Should I delete the startup parameter that are already there before typing in **vga=771 noacpi noapic nolapic**? What does this command do anyway? Is the last parameter no**L**apic or something else?

I've deactivated USB keyboard support in the BIOS, a suggestion I saw somewhere else but this did not help either.

:(

Bummer, I was expecting this to go without a hitch.

---

### Post by QwUo173Hy on 2007-06-01
I appended those options to the existing ones. no**L**apic is correct. I don't know what the options do, I found them on this site and they did the trick for me.

I did not disable USB and had not problems, but I had a USB keyboard.

Can you continue to use your system with the mouse? For example, could you load a music player and play a few songs with it? My system was not responsive at all. Sometimes I could move the mouse arrow, but the desktop wouldn't react.

The only other thing I can think of trying at the moment is adding
> pci=assign_busses
at the end of those options I gave you. Or  instead of them since they dont seem to work for you.

---

### Post by sme445 on 2007-06-03
Thanks for advice. In the end I just got hold of a USB keyboard and I was away! Only now the keyboard doesn't work with my WXP OS! Feel pretty sure I will be dumping that anyway as so far I have been very impressed by Ubuntu's feature set.

---

### Post by QwUo173Hy on 2007-06-03
Glad you got it going. Good luck with it. I've just installed XP on Ubuntu using [these simple instructions]("https://help.ubuntu.com/community/KVM") exactly. I don't know how practical it's going to work out. I was going to use it for Photoshop, but the GIMP is actually a lot better than I had realized so I might not need it.

---

