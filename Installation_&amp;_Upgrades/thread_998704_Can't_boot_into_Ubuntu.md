---
title: "Can't boot into Ubuntu"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by NautiusMaximus on 2008-12-01
Hi All

I think I've managed to install Ubuntu 8.10. It wasn't easy, but eventually I managed to get into Live CD mode and then ran the install from there (replacing Windows, not setting up as dual boot).

On rebooting the computer, supposedly into Ubuntu, I got as far as a message saying that the Grub loader was running, and then a screen that said "Starting up...". It got stuck at that stage for about half an hour (am I being impatient or is that too long?)

I tried booting into recovery mode, and there it gives lots of output showing that it seems to be starting up. It gets as far as a line that says:

[    0.372023] Booting processor 1/1 ip 6000

and then it hangs. 

Any ideas what I can try next?

Hardware: Fujitsu Siemens Scaleo P, Pentium 4 3.2 GHz processor, 1 GB RAM, 250 GB HDD, NVIDIA GeForce 6200 TurboCache graphics card, Asus motherboard.

Thanks
NM

---

### Post by ndefontenay on 2008-12-01
Does it do that every single time?

Tried re installing?

My first install failed supposedly because my computer couldn't read from the CD.

After a 2nd trial it worked really well since then.

---

### Post by NautiusMaximus on 2008-12-01
It's done it a few times. I haven't tried reinstalling yet.

Given that the install did nothing in an hour or so but finally managed to boot into the Live CD overnight, I'm wondering whether I should try leaving it overnight to see if it's really hanging or if it's just being slow. It seems reasonable that it might take a while the first time it starts up.

Failing that, a fresh install seems like the next thing to try: perhaps from the Alternate CD?

Or is there anything else I could try?

---

### Post by caljohnsmith on 2008-12-01
> **NautiusMaximus said:**
> It's done it a few times. I haven't tried reinstalling yet.

Given that the install did nothing in an hour or so but finally managed to boot into the Live CD overnight, I'm wondering whether I should try leaving it overnight to see if it's really hanging or if it's just being slow. It seems reasonable that it might take a while the first time it starts up.

Failing that, a fresh install seems like the next thing to try: perhaps from the Alternate CD?

Or is there anything else I could try?
I think it's safe to say that Ubuntu should definitely not be taking half an hour or longer to load, even for the first time. :) One thing you could try is adding some different options to the kernel line in the Ubuntu Grub menu entry, and see if that works. When you start up and get the Grub menu, just select the first Ubuntu entry, press "e" to edit it, select the "kernel" line, press "e" to edit it, and at the end of the kernel line add one of these options:
```
noapic
nolapic
acpi=off
```
Press return to save the change, and then "b" to boot. Try each of those options one at a time and see if they make any difference. Let me know how that goes.

---

### Post by NautiusMaximus on 2008-12-01
Thanks for the suggestions.

noapic made no difference (I didn't leave it for half an hour, but nothing happened in the time it took to make a cup of tea)

nolapic brought up some error messages, namely:
[  0.336064] BIOS bug,  local APIC #0 not detected!...
[  0.336104] ... forcing use of dummy APIC emulation.(tell your hw vendor)

and then it just hung the same as before

acpi=off actually worked! The system booted into Ubuntu!

Thanks so much!

So, next question: am I going to have to do that editing every time I start the computer, or is there something I can do to fix it once I'm in Ubuntu?

---

### Post by caljohnsmith on 2008-12-01
I'm glad to hear the "acpi=off" worked; to make that change permanent, when you are in Ubuntu open a terminal (Applications > Accessories > Terminal) and do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the "# defoptions=quiet splash" line to include the new option:
```
# defoptions=quiet splash [COLOR="Blue"]acpi=off[/COLOR]
```
Note the line should still have a pound sign in front of it, so don't delete that. After you save that change, do:
```
sudo update-grub
```
And if you look at your menu.lst again, you should see that all your Ubuntu entries now have the "acpi=off" at the end of their kernel lines. Let me know how it goes or if you run into problems. :)

---

### Post by NautiusMaximus on 2008-12-02
caljohnsmith, you are an extremely helpful person and an absolute star. =D> I hope something good happens to you today, or, failing that, at least that something amusingly unpleasant happens to someone you don't like.

It all boots just fine now, and I'm typing this from my Ubuntu computer. :) No doubt I shall have other problems as I learn to use a Linux system for the first time, but it's great to know there are such helpful people out there for when I do.

Just one final question on this thread: it seems to me that what I have done is to type a magic incantation into my computer to get it to work. :confused: Is there a simple explanation that a Linux newbie like me could understand that would explain what I've just done and why it's fixed my computer?

Thanks again
NM

---

### Post by caljohnsmith on 2008-12-02
> **NautiusMaximus said:**
> 
Just one final question on this thread: it seems to me that what I have done is to type a magic incantation into my computer to get it to work. :confused: Is there a simple explanation that a Linux newbie like me could understand that would explain what I've just done and why it's fixed my computer?

Thanks again
NM
Yes, I agree, that "acpi=off" trick might look a little like Linux voodoo or something, but there actually is some real science behind it and not pure necromancy or black magic. :) "ACPI" is an acronym for "Advanced Configuration and Power Interface", and as I understand it, it basically has to do with power management functions on the computer like hibernating, suspending, etc. Unfortunately, it turns out that ACPI is often a problem for the linux kernel on some computers, so the easy solution is to just pass that "acpi=off" parameter to the kernel on boot time, and then the kernel does not use ACPI functions. The downside though is you unfortunately won't have any hibernate/suspend to RAM functionality. But at least you can boot into Ubuntu now, that's better than not being able to use Ubuntu at all I think. Anyway, cheers and have fun with your new Ubuntu install. :)

---

