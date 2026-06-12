---
title: "cant install ubuntu 6.10"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by grojam on 2007-03-08
i received some cds of ubuntu linux and i tried to install it  on my pc. i try to run the live cd so i can install it but it wont load up at all it stops at the black screen with the loading bar and a title saying ubuntu if anyone has any ideas how to fix it.   my sys specs are below.


2.4ghz intel solo pentium 4
1gb DDR2 ram
40gb hard drive
quick note there is no operating system on the hard drive

---

### Post by wpshooter on 2007-03-08
Did you check the integrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

---

### Post by grojam on 2007-03-09
i just tried  that but it still dident work

---

### Post by zvacet on 2007-03-09
Does is it looks like this
[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")
If it does maybe you shoud try alternate CD.
[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by rsambuca on 2007-03-09
Try adding some different boot options (F6 if I recall correctly).  You can try adding these instructions to the end of the line (before the -- at the end):
```
ide=nodma
```
or if that doesn't work, try adding all of this:
```
irqpoll pci=noacpi noapic nolapic acpi=off
```

---

### Post by grojam on 2007-03-09
thanks zvacet the loading screen for the live cd looks simular but the logo has the proper logo on it instead of it just beeing yellow and it tottally freezes and i have to do a hard reset. the copy i have it 6.10

---

### Post by wpshooter on 2007-03-09
> **grojam said:**
> i just tried  that but it still dident work

Do you mean that it still did not install or that it did NOT pass the integrity test ?

---

### Post by grojam on 2007-03-09
it passed the integrity test but it crashes wen it starts installing

---

### Post by wpshooter on 2007-03-09
Have you tried booting with the safe video mode parameter ?

---

### Post by grojam on 2007-03-10
i havnt tried the safe wideo mode parameter i will post back if it makes it work or not

---

### Post by grojam on 2007-03-10
the safe video parameter still doesent help it still freeses at the same place.

---

### Post by rsambuca on 2007-03-10
Did you try adding the boot parameters from post #5?

---

### Post by patlew on 2007-03-10
I had the same problem. Let fall all noapi integrity....
You are loosing your time. It will not be possible to install.
Only 7.04 can be installed on some computers.

---

### Post by grojam on 2007-03-10
oh well i will just have to go back to my windows pc and suffer lol i proberly got a faulty cd cuz it wouldent install on my mates computer either and he desperatly needs a os but cant find one so i will use the cd as a frisby lol

---

