---
title: "Ubuntu on bi-processor server"
date: 2024-02-24
forum: Installation &amp; Upgrades
---

### Post by maredentro on 2024-02-24
Hi at all, sorry for my bad english.

I want to buy a  fujitsu primergy rx300 s7 with two processors Xeon E5-2630.

Is possible to install ubuntu?

I want to create a desktop computer with thisachine.

I download .iso installer and create a usb key for normal install?


Thanks for reading
Alberto

---

### Post by TheFu on 2024-02-24
The passmark on a Xeon E5-2630 is only 6000 and it is likely to use much more power than a newer computer that costs less, say a Ryzen 2600 which is 4+ yrs old.

Some advice. Things often seem like a good idea, but aren't.  Acquiring a "server' for use at home, especially an older server, just transfers a "_boat anchor_" to you.  You are better off on price,  parts, power, noise, and reliability to get 2 desktop systems if you want server redundancy. A Ryzen 2600 passmark is 13000+.

Right now, a Ryzen 5500 ($85) is the best "value" for performance in the CPU market with over 19000 passmarks.  Plus cheap AM4 motherboards are available for $75 and RAM is cheap too.  The Ryzen 5500 is hexacore - so 6 cores, but 12 threads.  It lacks a iGPU, so you'll want a cheap GPU. Use an old one or get a cheap AMD. Avoid nvidia to stay away from the nvidia driver problems.  For less than $200, you can have a pretty awesome computer that is nearly 2x faster than your Xeon.  I saw a nice LSI SAS HBA for $60 today, so you can have fantastic HDD performance if that's your goal too, but most AM4 motherboards have 1-2 NVMe m.2 slots, so that would be where I'd go for 2TB or less NVMe storage.

I know you won't listen.  We all go through the "need-a-server" phase.  Then we learn and have to find the next idiot to buy/give our _boat anchor_ to.  Sigh.  Nobody ever listens.

---

### Post by maredentro on 2024-02-25
Thanks TheFu for your accurate explanation.

Given what you write, I won't take it.

I confess that the temptation is strong but I will make an evaluation based on your advice. 

Thanks Alberto

---

### Post by TheFu on 2024-02-25
If you need some sort of a GPU and want around 19000 passmarks, the Ryzen 5600G isn't bad.  Just look for a deal around $130.  The iGPU on the Ryzen 5600G is worth about $70.  I have 2 systems with it and have been pretty happy.  It will even transcode/encode to either h.264 or h.265 video in hardware using the iGPU.  

There may be better deals right now.  Intel Core i5s are often very competitive with their iGPUs as well.  If you keep a CPU+motherboard+RAM setup for over a decade, Intel vs AMD CPUs don't really matter.  

If you plan to upgrade performance by getting faster CPUs as they become less and less expensive, the AMD is better with their socket for the entire line that supports multiple generations of CPUs, speeds, and total performance from 8K passmarks to over 30K passmarks.  If you do plan to upgrade CPUs over time, spend more on the motherboard and avoid the cheap lines.  Get at least a B550. These are usually $120-$180, so much more than the cheap ones.

Don't forget that older CPUs and lower-end CPUs will be worth less and less, so if you are always at the last-in-line position, you won't be able to sell your old CPU when it is time to upgrade to a faster one.  For example, I sold a Ryzen 2600 with some unused DDR4 RAM for $85 when I was upgrading to a Ryzen 5600G.  Because these were slot compatible and the 5600G was only $119, I got a 40% performance increase + iGPU for $35. The same motherboard and RAM that were already in the older system was used. It was purely a CPU swap.

I have a bunch of older motherboard+cpu+ram groups here that nobody wants.  On the really low end, the only people will to take them want a complete computer.  Nerds know they are old CPUs with lower performance and won't touch them.  Sorta like your Xeon CPU.  Definitely avoid really old hardware that won't have any resale or give away value.

Of course, nobody really knows the future. These are all educated guesses.

---

