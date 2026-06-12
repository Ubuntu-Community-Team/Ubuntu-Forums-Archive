---
title: "Can't install on my laptop yet again"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by JulienPDX on 2007-10-18
Dear Ubuntu users

I have a Compaq Presario V6107US notebook computer that I purchased last year.  I have had luck installing a few other linux distributions on it but have never gotten Ubuntu to work.

Can someone help me figure this out?  Basically the computer boots into the Live CD and allows me to see its "progress" and then just locks up.

I have tried starting up unbuntu in safe graphics mode and it gets as far as it does when I try a normal startup and then just locks up.  Anyone know of any issues?


and then just freezes.  What can I do to resolve this?  

Thanks

J

---

### Post by 1337455 10534 on 2007-10-18
ok, boot into a working OS
pop in the CD
reboot
boot to CD (the whole BIOS thing)
- at the boot options screen (install, check for defects etc:
press escape, and OK
enter:
```

live acpi = off

```
in the boot line
and press enter,,
working?? It helped my Feisty... But I am Gutsy now.

---

### Post by JulienPDX on 2007-10-18
I'm afraid this did nothing to fix the problem, the computer simply will lock up with a complete optical-drive spin-down ..and be "stuck" with a black screen.

is there a way to do a more thorough start-up that would allow me to pin-point from where the problem is originating?  :confused:

---

### Post by sands on 2007-10-18
I had the same problem. My laptop model is V6101US.  I was able to install by using noapic irqpoll

Follow these instr

Press F6

then at the end enter
noapic irqpoll

Press enter and it will work..

---

### Post by sands on 2007-10-18
If the prob still exists add noirqdebug too at the end.

---

### Post by sands on 2007-10-18
By the way, could someone tell what noapic & irqpoll means. I found this long back somewhere in the internet but dont know what that means.

Will there be any performance decrease if these arguments are used?

---

### Post by JulienPDX on 2007-10-18
sorry to post so late, those options work and i can install with no issues, now i'm struggling to get my broadcom wireless to work but ...i'm trying to follow instructions on finding on many different sites.

---

### Post by blackrim on 2007-10-18
which options worked (can't seem to get the options i see here to work)

---

### Post by sands on 2007-10-18
Well, mine is broadcom wireless card.  

I just installed Gusty. 

I went to System->administration->Restric drivers

There I enabled Broadcom..

Thats it. I got it..

---

### Post by JulienPDX on 2007-10-18
the optoins i used were 

noapic irqpoll noirqdebug vga=792


i added that vga line in there b/c i kept having a dotted display problem when i'd try to boot in (no video)

Also, all the "broadcom" nightmare scenarios expect you to have a working ethernet connection.  I don't.  I'm at school and the mac addresses have to be authorized to plug into an ethernet port and even then they run some program that configures the pc's with a bunch of advanced network settings that i can't seem to "imitate" on my installation so i am restricted to trying to solve this w/o a current net connection

:confused:

---

### Post by JulienPDX on 2007-10-18
aka "sneaker net" (downloading stuff onto a jump drive on this working internet connection (other computer))

---

### Post by sands on 2007-10-18
[https://wiki.ubuntu.com/LaptopTestingTeam/CompaqPresarioV6107AU](https://wiki.ubuntu.com/LaptopTestingTeam/CompaqPresarioV6107AU)

This might be helpful.

---

