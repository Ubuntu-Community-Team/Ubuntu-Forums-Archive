---
title: "Wont boot-help"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by police512 on 2008-11-22
Hi there, i am still having the problem that ubuntu wnt boot on my computers!. can someone help plz cuz this is annoying since i have always liked ubuntu. it gets stuck on the boot when that bar goes across the screen. 

[SIZE="7"]please help lol[/SIZE]

---

### Post by VastOne on 2008-11-22
From what little you have given, it is hard to trouble shoot, but, it sounds to me like the pci issues i had where I had to add pci=nomsi to my boot parameters

Before you boot, at the grub screen, hit e to edit the boot line and add at the end, pci=nomsi and see if you can boot.  If it works, you will need to add that line to your grub boot parameters...let us know if that works first



> **police512 said:**
> Hi there, i am still having the problem that ubuntu wnt boot on my computers!. can someone help plz cuz this is annoying since i have always liked ubuntu. it gets stuck on the boot when that bar goes across the screen. 

[SIZE="7"]please help lol[/SIZE]

---

### Post by police512 on 2008-11-23
ok now it boots everyime when i put in the dvd and boot, byt before it got stuck, but now it gets past that bar and then it goes to a black screen when it starts up everything. and now ( I STILL ENTERED THAT CODE AND DID A BOOT WHERE I DIDNT) AND IT GETS STUCK ON STARTING THE BLUETOOTH, it gets past that bar and goes to a black screen where it starts everything, i have entered that code bit into the boot but it still gets stuck on starting the bluetooth!. help

---

### Post by FaWzY86 on 2008-12-03
I have the exact same problem, here's a shot a took by my phone of the screen where it gets stuck

[IMG]http://i38.tinypic.com/ae8iv7.jpg[/IMG]

And it actually takes a LONG time to reach that screen, like 10 mins or so, and it does that whether when I'm trying to run the demo or when I'm trying to install it, it just stays like that

My PC is Pentium 4 3.2 GHz with 1.5GB RAM, so it's not a slow PC by any means...

I really don't understand what's wrong, and yes, I've added that term to the boot line, and nothing changed at all!

---

### Post by FaWzY86 on 2008-12-04
Okay, problem solved...

All I had to do was unplug ALL my USB devices :D

---

