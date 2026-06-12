---
title: "The curious case of the 1701mb Swap partition. After 15.04, 14.04 freezes."
date: 2015-10-12
forum: Installation &amp; Upgrades
---

### Post by hey2 on 2015-10-12
I'm really sorry if this will sound really weird.

Yesterday a tried 15.04 to confirm if a problem that I’m having was also happening in this version.

Like always i deleted my swap and / partition and created new ones.

This time i have chosen 1701mb to Swap and the rest to /. I never tried this Swap size before.

It worked, but since the problem was also present in 15.04 and i found it to be a little buggy on my system i wanted to install 14.04 again.

I did the same thing and chose 1701mb to Swap and the rest to /.

This time 14.04 would not boot. It froze on the black screen before the completely purple one and would not pass that. When i left the pen connected, it would bip like an alarm.

First i thought that i ruined the computer, but i tried installing with another swap size and it worked.

After this happened, i tried three times that amount, always with the same result.

What could possible have happened?

Was this cause by 15.04 or did i won some kind of lottery?

---

### Post by sudodus on 2015-10-13
What size of swap works?

What is the size of your root partition (in each case)?

Are you running standard Ubuntu? If not, which flavour of Ubuntu are you running (Kubuntu, Lubuntu ..., Xubuntu)?

What computer is it? Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

When we know these things we can give better advice.

---

### Post by hey2 on 2015-10-13
> **sudodus said:**
> What size of swap works?

What is the size of your root partition (in each case)?

Are you running standard Ubuntu? If not, which flavour of Ubuntu are you running (Kubuntu, Lubuntu ..., Xubuntu)?

What computer is it? Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

When we know these things we can give better advice.

Hi.

Thank you very much for your time.

The Distro is Ubuntu 14.04.

I tried before 2100, 3650 and 3700, and all worked.

When i tried 15.04 i tried 3701 so that when i press ok it would appear 3700 instead of 3699 on the installation menu. OCD, yeah i know...

Like always everything worked. 

When i tried to reinstall 14.04, i did the same thing, but Ubuntu would not work after that. 

I can't give you an exact amount of the root partition, but the space that i have available to crate a swap and a root is 151.7gb.

Cpu: Pentium 4
Ram: 4GB (3.4 detected by Ubuntu)
Graphics: HD3450

This not so much a issue, but more of me being curious.

I don't see why this would happen. I think is too much of a coincidence that i found a Swap value that is making 14.04 not work.

The only thing i could think of is that 15.04 did something. But what?

Thanks.

---

### Post by sudodus on 2015-10-13
With around 150 GB total amount of disk space I see no reason why you should have problems with 1701MB or 3701MB unless you do something that needs a huge amount of memory, so that you run out of memory (RAM + swap). Would that be the case? You did not mention anything like that.

And you did not mention hibernating. If you hibernate the computer, you need as much swap (in Mibibytes, binary) as RAM, to be able to copy the current content of the RAM to the swap area. But then the limit should be 4 Gibibytes ~ 4.3 Gigabytes (decimal).

There might be problems with some bad memory cell in the RAM or some bad block in the swap partition, and that bad unit might be used in the particular case of a certain size of swap. Or there might be a bug in some software.

---

### Post by hey2 on 2015-10-13
> **sudodus said:**
> With around 150 GB total amount of disk space I see no reason why you should have problems with 1701MB or 3701MB unless you do something that needs a huge amount of memory, so that you run out of memory (RAM + swap). Would that be the case? You did not mention anything like that.

And you did not mention hibernating. If you hibernate the computer, you need as much swap (in Mibibytes, binary) as RAM, to be able to copy the current content of the RAM to the swap area. But then the limit should be 4 Gibibytes ~ 4.3 Gigabytes (decimal).

There might be problems with some bad memory cell in the RAM or some bad block in the swap partition, and that bad unit might be used in the particular case of a certain size of swap. Or there might be a bug in some software.

Hi.

Thanks for response.

Yeah i don't have a clue.

If it worked in 15.04 it should be the same with 14.04.

Since you mention hibernating, I can't get my computer to suspend. When i run the "free" command i have more swap than ram, but i don't know why, when i try to suspend, the computer screen just turns off but then nothing happens. I press the power button and it doesn't turn on.

Maybe i need even more swap, i don't know.

I will will try to create a new partition table when i have some time to see if that (1701mb swap) happens again.

Once again thank you very much.

---

