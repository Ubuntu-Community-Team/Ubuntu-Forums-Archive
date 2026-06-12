---
title: "Processor too much good 4 motherboard?"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by meisenshi on 2008-01-22
Recently there was a power failure at my place. After that my computer (which had Ubuntu installed, working out-of-the-box) wouldn't boot anymore... I tried to solve it but eventually I couldn't, so I asked a friend to check it out, and he realised my processor was *dead*.

He got for me a new processor, a "Pentium 4 3GHz". I tried to install Ubuntu back. However, after the first menu in the LiveCd appears (Install, check for errors, etc.), the cd booting process was *so painfully slow* it became impossible to install! On the other hand, Windows XP was flawlessly installed.

As I wanted to know more about my new processor, I used CPU-Z utility. I was intrigued when I saw this:

[[IMG]http://img257.imageshack.us/img257/1992/cpuztl7.th.jpg[/IMG]](http://img257.imageshack.us/my.php?image=cpuztl7.jpg)

According to Intel Processor Spec Finder ([http://processorfinder.intel.com/](http://processorfinder.intel.com/)) my new processor has FSB 800.

However, my motherboard (FIC VC19) only suports processors FSB 400 / 533.

So, I suspect that my new processor is too much good for my motherboard =P


Here's what I've already tried:

# Tried both Gutsy and Feisty - they load **veryyy** slowly, pratically unusable;

# MD5Checksum - the cd's are alright, they boot properly on other PC's;

# Memory check - it runned all night and no errors were detected;

# Boot parameters - tried _noapic_, _noacpi_, removed _quiet_ and _[U]splash_[/U], and none of them works;

# Alternate CD - tried that (Gutsy) and it took **5 hours** to install :S when booting from HD, it is just as slow as a LiveCD! And it doesn't have Internet and graphic driver properly configured out-of-the-box (as it always did on my PC).

# Lubi - tried that one but it doesn't work, too (same thing as Alternate CD).


When my older processor was *alive*, everything was running just fine... please help me!

---

### Post by Carl H on 2008-01-22
I'm afraid  your friend has wasted your cash. You can't just buy any processor and fit it, you have to get one that matches your mobo. Mismatches in bus speeds will make it unstable. 

At best, the CPU will run at a lower speed so the mobo can cope, which means you're not getting the best performance out of it and you might as well have bought a cheaper one.

---

### Post by meisenshi on 2008-01-22
> **Carl H said:**
> I'm afraid  your friend has wasted your cash. You can't just buy any processor and fit it, you have to get one that matches your mobo. Mismatches in bus speeds will make it unstable. 

At best, the CPU will run at a lower speed so the mobo can cope, which means you're not getting the best performance out of it and you might as well have bought a cheaper one.

Yes, it is actually running at a lower speed... But I just can't understand why Windows XP is running without any problem, and Linux can't be installed!!! :S

Is there any way to install it?

---

### Post by wolfen69 on 2008-01-22
> **Carl H said:**
> I'm afraid  your friend has wasted your cash. You can't just buy any processor and fit it, you have to get one that matches your mobo. Mismatches in bus speeds will make it unstable. 


not quite right. (i fix computers for a living) just because the cpu will support a higher bus speed than the mobo does not mean it will become unstable. it will just default to the highest speed the mobo can handle, without loss of performance. (compared to old cpu)

one of the motherboard components could be damaged. i realize xp is working well, but they are 2 different OS's and are made to interact differently with computer components. for some reason, ubuntu does not like a "change" that was made to the computer.

without getting my hands on it, that's the best i can do.

---

### Post by Carl H on 2008-01-24
Fair points about the CPU slowing down to match the mobo. I was going off my experiences of a 3/4 years ago, when I put a few systems together based on some old parts that I had lying around. Sounds like more modern CPUs and mobos don't need to be quite so closely matched. 

Although I still think that buying a CPU with an 800 FSB and fitting it to a 400 FSB mobo is a waste of money.

---

### Post by meisenshi on 2008-01-26
Well,you're right... I've trusted on my friend to get me a new processor and... :(

But for  €30 (approx. $44) I think I didn't waste much money!

I'm considering to buy a new motherboard, one that's cheap and supports well my processor. Does anyone have good suggestions?

---

### Post by JonUK76 on 2008-01-26
Not sure on suggestions - they don't sell many 478 socket boards now so you might have to get secondhand. Probably something from a well known make (Asus, Gigabyte etc) with an Intel 865PE or 875 chipset would be a safe bet, and will support 800mhz FSB. Asus P4P800SE would be an example.

Just a note but it looks like you are running that on a 400mhz FSB. You should be able to bump up the speed a bit by adjusting the FSB speed in the BIOS settings.

---

### Post by meisenshi on 2008-01-26
> **JonUK76 said:**
> Not sure on suggestions - they don't sell many 478 socket boards now so you might have to get secondhand. Probably something from a well known make (Asus, Gigabyte etc) with an Intel 865PE or 875 chipset would be a safe bet, and will support 800mhz FSB. Asus P4P800SE would be an example.

Just a note but it looks like you are running that on a 400mhz FSB. You should be able to bump up the speed a bit by adjusting the FSB speed in the BIOS settings.

Actually, I've already adjusted it, and the maximum is 1.95GHz. However, when I do that, sound doesn't work on Windows, and I can't still install Ubuntu.

And thanks for the tip, I will search for secondhand  motherboards.

---

