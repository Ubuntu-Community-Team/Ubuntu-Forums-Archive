---
title: "Keeps turning computer off at worst times"
date: 2009-09-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by voncloft on 2009-09-24
I installed ubuntu 9.1 alpha, yes i know it is still a beta, however it shuts my computer off instantly.

My computer specs are as follows:
ASUS Motherboard a8n5x socket 939
amd 64 processor
4 gb of ram
over 3 tb of hard drive space
geforce 8600 GT video card
soundblaster soundcard

I will be doing something as simple as formatting a hard drive, or playing a game and the computer will shut off in a blink of an eye any idea how i can find the problem in the logs, or terminal.  I have been a proud user of linux for 2 years never had any probs like this.

---

### Post by kestal on 2009-09-24
> **voncloft said:**
> I installed ubuntu 9.1 alpha, yes i know it is still a beta, however it shuts my computer off instantly.

My computer specs are as follows:
ASUS Motherboard a8n5x socket 939
amd 64 processor
4 gb of ram
over 3 tb of hard drive space
geforce 8600 GT video card
soundblaster soundcard

I will be doing something as simple as formatting a hard drive, or playing a game and the computer will shut off in a blink of an eye any idea how i can find the problem in the logs, or terminal.  I have been a proud user of linux for 2 years never had any probs like this.

Maybe a little random... but that almost sounds like an overheating issue when a computer reaches a temperature threshold. Does it just turn off or does it go through the shut down process?  Possibly also a power supply issue, maybe?

Edit: I assume just turn off after re-reading. Anyone else?

---

### Post by Podex on 2009-09-24
This definitely sounds like a hardware problem to me too. I had this happening years ago (random instant shutdowns) and it turned out to be my hard disk which was broken beyond repair. But I think it can be any number of hardware problems: motherboard, cpu, graphics card etc.

---

### Post by Nickedynick on 2009-09-24
I had this on my laptop fairly recently. Turned out to be the CPU overheating, causing the machine to power off in an attempt to protect itself. Not that the manufacturer agreed - I had to return it about 5 times...

But yeah, if you're any good with conky you can set it up to monitor temperatures, loads etc. That way you can see if there's a common factor.

---

### Post by voncloft on 2009-09-25
> **kestal said:**
> Maybe a little random... but that almost sounds like an overheating issue when a computer reaches a temperature threshold. Does it just turn off or does it go through the shut down process?  Possibly also a power supply issue, maybe?

Edit: I assume just turn off after re-reading. Anyone else?

It just shuts off no boot off screen its as if the power went out during an electrical storm.  It never happened in Ubuntu 9.04 the video card is slightly in the yellow on the temperature monitor.  My CPU runs at about 104 degrees Fahrenheit and is clocked at 2.2 GHz it has a big fan on it, takes a lot of space up for being in an ATX Armor full case.

---

### Post by voncloft on 2009-09-26
This seems to be a recurring theme that it keeps shutting down.

I had the pc taken into a shop all checks out no problems found in hardware woohoo.. anyway can anyone direct me to the logs that would be causing this the only thing I can think of is everything in computer is about 3 years old and the new versions of Linux are becoming incompatible with my computer i don't know please help.

---

### Post by voncloft on 2009-09-26
My temperatures for computer in Fahrenheit are:

CPU 104
Hard drives range from 93-95
GPU: 145 - a bit high but never caused a problem before.
core0 temp is 97

---

### Post by hikaricore on 2009-09-26
You may want to consider opening your case up and taking a can of compressed air to it (gently).
I had an overheating issue years back and it ended up that the underside of the fan was just clogged full of dust and grime.
So basically the heatsync was just sitting there being hot and the air had nowhere to go.
If you're overclocking ANY of your hardware you may want to consider disabling such modifications and see if stability returns.
This is almost 100% hardware related.

---

### Post by kestal on 2009-09-26
> **voncloft said:**
> My temperatures for computer in Fahrenheit are:

CPU 104
Hard drives range from 93-95
GPU: 145 - a bit high but never caused a problem before.
core0 temp is 97

To be on the safe side (I know, basic question time). Could you check to see and verify if your CPU fan is properly seated over the CPU? I know you also said you also had a big fan.. is it located at the back of your tower or side? Is it intake or outtake? Also, if you get a chance to open the side of your tower and turn it on, just to check if it looks like the CPU fan is functioning properly? Can you check and open the side of your tower and see if, once you get proper ventilation, to see whether or not the problem persists?

_Edited for my mistakes:_ Indeed. I was pretty tired and forgot to account for that (silly me). If those are in Fahrenheit (which would totally make sense) then they are not that bad, when compared to mine. I've had a PC fail teetering at about 90-100c which is why I brought that up without looking further into that. (faulty fans). lol

This may bring me back to.... what kind of a power supply do you have? I've had some computers just 'power down' without damaging anything if the PSU couldn't keep up. Judging by your specs, I'd assume you have a pretty big PSU? O_o;

---

### Post by hikaricore on 2009-09-27
The OP is listing his temeratures in farenheight.

> **voncloft said:**
> My temperatures for computer in Fahrenheit are:

CPU 104 **(40c)**
Hard drives range from 93-95 **(33.8c-35c)**
GPU: 145 **(62.7c)** - a bit high but never caused a problem before.
core0 temp is 97

None of these temperatures save for the video card are too high, I still think they need to air out the case.  :p
There's also the posibility that the OP's temperatures are actually celcius and they don't know the difference.
In this case they are very very bad.

---

### Post by Gina on 2009-09-27
I don't think there's a lot I can add.  Dust can build up amazingly quickly even in what seems a clean environment.  A little while back I have a fan on a graphics card that had become totally clogged up with dust and actually dropped off!!  I'd opened up the case to see why my video was a bit erratic.  A new fan was needed.  I also found the CPU cooler airways blocked up.  That was after about two years from new.  Now I clean out annually or more often.

I have have similar problems with a friend's laptop - ran for a while and then just shut off power.  Dust again plus a poorly seated CPU heat sink.  Cleaning and fresh heat conducting compound between heat sink and CPU fixed it.

Many years ago I had a similar problem caused by a fault in the PSU.  Also, another time I found a loose CPU fan connector - it was intermittent.

I agree that there is a possibility that the OP was getting Celcius readings rather than Fahrenheit.

To conclude, I would certainly suggest opening the case and having a good look round.  Both switched off and then powered up.  Check for dust - there's bound to be plenty in my experience - and clean it out, being careful not to touch component parts.  Check for loose connections.

---

### Post by voncloft on 2009-09-28
> 

I agree that there is a possibility that the OP was getting Celcius readings rather than Fahrenheit.


I configured the program to display temperatures in Fahrenheit since I have grown accustomed to Fahrenheit never understood why computers displayed temperatures in Celsius. I reinstalled the OS and haven't had any problems It could be chance that its not turning off computer has been on for three days the GPU on the program says 147 Fahrenheit but my NVIDIA X server settings say the card is running at 63 degrees Celsius.  I'll let the computer run for a few more days to confirm all is well. I will for good measure clean out the case of dust because the computer is 3 years old and has never been dusted out.

---

### Post by 3rdalbum on 2009-09-28
If the computer is 3 years old, then it's a real possibility that the power supply isn't as powerful as it used to be, and that it is flaking out.

If the problem comes back, then try putting in a new power supply of a brand name (Antec, Corsair, Thermaltake or the like) with a higher power rating than the old one.

---

