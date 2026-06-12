---
title: "Just built a new computer, Ubuntu not working."
date: 2014-06-10
forum: Installation &amp; Upgrades
---

### Post by boss86741 on 2014-06-10
Hi,
I just built a new commuter (I will list the specs below). I installed Ubuntu 14.04 onto a fresh SSD (using unetbootin) to plug into the computer, and when I try to boot up, the monitor says that there is no video feed coming in. The wire is plugged in, and I know the computer works because the fans are turning on.
Thanks

Specs (I built an economy computer, so don't complain that the parts are el cheapo):
Processor = AMD A-Series A4-4000 3.0GHz Dual-core.
Motherboard = ASRock FM2A55M-VG3+
RAM = AData 4GB DDR3-1600MHz PC3-12800
Drive = AData SP600 64GB SSD
Case = Rosewill FBM-01 w/built in power supply

---

### Post by SuperFreak on 2014-06-10
When you boot the computer does the BIOS post onscreen(ie see image)

---

### Post by boss86741 on 2014-06-11
No, the monitor says "Attention: no video feed". Nothing is outputting.

---

### Post by SuperFreak on 2014-06-11
Sounds like a hardware problem not Ubuntu. Bad RAM possibly? Check to make sure the RAM is seated correctly on the motherboard. Are the fans of th computer working ? CPU fan, case fans?

---

### Post by boss86741 on 2014-06-11
The fans are all working fine and the RAM is in correctly.

---

### Post by rahul4557 on 2014-06-11
As SuperFreak suggested seems hardware problem,
connect the motherboard buzzer for beep codes
check RAM
check APU
check cables for loose connections
and also try resetting the CMOS

---

### Post by boss86741 on 2014-06-11
I tried all of your suggestions and none of these are a problem. I also reset the CMOS and that didn't work.

---

### Post by rahul4557 on 2014-06-11
if no display on monitor than either RAM, CPU or Motherboard is failing in your system.

There is no problem with the Ubuntu in this case..

**Get your System Checked**

---

### Post by mastablasta on 2014-06-11
any chance of getting a GPU card to see if it would work? maybe the CPU is bad?

---

### Post by grumblebum2 on 2014-06-11
This may or may not help you.
A couple of days ago my screen just went blank.
Computer was still running but there was no output to the monitor.
I could not shutdown by holding the power button like I had done previously for a hard reset.
Turned the power off at wall then restarted.
Computer would turn on with fans working but doesn't post to BIOS and no beeps are heard.
The mouse and keyboard also failed to light up.

Swapped out, in turn the RAM,monitor and gfx card with some old spares but same result.

Was due for an upgrade so purchased new CPU, motherboard and ram.
Installed new components tonight but didn't fix.
Off to buy a new PSU tomorrow.
With the symptoms I thought it was the motherboard but looks like it's the power supply.

So if you have same symptoms I would be looking at the PSU.
I have built a few PC's and have found the PSU to be the flakiest component having to replace 3 or 4.

---

### Post by SuperFreak on 2014-06-11
The power supply is often the most neglected component on new builds, but is also one of the most important components. It is worth spending a bit more money and getting a bronze certified or if you can afford it a gold certified power supply. That being said it is still not clear if that is the source of the problem.

This from NewEgg feedback on your case:> Cons: Would it kill them to drill some SSD holes in the hard drive cage? Also, if you are buying this because it has a power supply installed, you should reconsider. **_The Power Supply is DOA. Of the 4 Rosewill cases I purchased that had Power Supplies, this is the second one that was DOA._**
[http://www.newegg.ca/Product/Product.aspx?Item=N82E16811147168]("http://www.newegg.ca/Product/Product.aspx?Item=N82E16811147168")

---

### Post by boss86741 on 2014-06-11
> [COLOR=#000000]if no display on monitor than either RAM, CPU or Motherboard is failing in your system.[/COLOR]

[COLOR=#000000]There is no problem with the Ubuntu in this case..[/COLOR]

**Get your System Checked**
I don't think that the RAM is failing. The CPU seems fine as does the motherboard, but there could be something wrong with them.

> [COLOR=#000000]any chance of getting a GPU card to see if it would work? maybe the CPU is bad?[/COLOR]
I don't really want to get a dedicated GPU for it because as you can see, I am trying to make this computer a cheap one. The CPU might be defective, I am not sure.

> [COLOR=#000000]This may or may not help you.[/COLOR]
[COLOR=#000000]A couple of days ago my screen just went blank.[/COLOR]
[COLOR=#000000]Computer was still running but there was no output to the monitor.[/COLOR]
[COLOR=#000000]I could not shutdown by holding the power button like I had done previously for a hard reset.[/COLOR]
[COLOR=#000000]Turned the power off at wall then restarted.[/COLOR]
[COLOR=#000000]Computer would turn on with fans working but doesn't post to BIOS and no beeps are heard.[/COLOR]
[COLOR=#000000]The mouse and keyboard also failed to light up.[/COLOR]

[COLOR=#000000]Swapped out, in turn the RAM,monitor and gfx card with some old spares but same result.[/COLOR]

[COLOR=#000000]Was due for an upgrade so purchased new CPU, motherboard and ram.[/COLOR]
[COLOR=#000000]Installed new components tonight but didn't fix.[/COLOR]
[COLOR=#000000]Off to buy a new PSU tomorrow.[/COLOR]
[COLOR=#000000]With the symptoms I thought it was the motherboard but looks like it's the power supply.[/COLOR]

[COLOR=#000000]So if you have same symptoms I would be looking at the PSU.[/COLOR]
[COLOR=#000000]I have built a few PC's and have found the PSU to be the flakiest component having to replace 3 or 4.[/COLOR]
The power supply seems fine.

---

### Post by grumblebum2 on 2014-06-11
> **boss86741 said:**
> 


The power supply seems fine.

How did you determine this?

---

### Post by SuperFreak on 2014-06-11
If possible run memtest on the RAM

---

### Post by LastDino on 2014-06-11
Please check your cable by attaching it to different monitor/system. Generally it is either that or loose RAM.

---

### Post by Vladlenin5000 on 2014-06-11
To all the possible causes you systematically replied "I think it's fine" or "It seems fine". Obviously something isn't and you actually haven't determined those components were fine. It's just your opinion, feeling, whatever, certainly not facts.
The only way to determine whether a component is failing or not is to test with a different known good component. FYI, this is called troubleshooting and you need to do that. Otherwise this is just a fruitless exercise in speculation and a waste of your time (and other people's).

---

### Post by LastDino on 2014-06-11
And by the way, OS of any sort, Ubuntu in this particular case, hasn't even came into picture as you're not even getting to booting screen. An empty/no drive will still get you there and ask of you to put something to boot off. 

Therefore, this is definitely a hardware problem. Even the best sometime fail and it is not a bad idea to check those components rather than blaming it on something irrelevant.

---

