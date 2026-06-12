---
title: "Boot failure after memory upgrade - best practices when upgrading memory?"
date: 2016-09-28
forum: Installation &amp; Upgrades
---

### Post by pdesjardins on 2016-09-28
I'm using Ubuntu 16.04 on a Lenovo T450S laptop. I need to upgrade the memory and I want to make sure I'm doing it the right way.

I started at my current company with an identical laptop that had only the built in memory, no additional card. I installed 16.04 and it was working without problems. After installing an additional 4GB memory chip in the expansion slot, Ubuntu would not boot. It hung at the screen with the dots, no boot selection screen or any other screen ever appeared. So I took a laptop with that had the 4GB card already installed and I installed 16.04 on that (it's working fine right now).

It turns out that I still don't have enough memory and I need to upgrade the card. I think I should be able to switch the expansion memory cards without causing a problem for the OS. But since the memory installation caused problems before, I'm a little concerned.

Has anyone else seen boot problems after upgrading a memory card?

Are there any precautions I can take to make sure 16.04 is prepared to encounter more memory?

Thanks!

Peter

---

### Post by him610 on 2016-09-28
Does your memory meet these specs:
Technology DDR3L SDRAM
Speed 1600 MHz / PC3L-12800
Form Factor SO-DIMM 204-pin
Slots Qty 1
[https://www.cnet.com/products/lenovo-thinkpad-t450s/specs/]("https://www.cnet.com/products/lenovo-thinkpad-t450s/specs/")

---

### Post by pdesjardins on 2016-09-28
Thanks for the help! I ordered the new chip from Crucial, using their compatibility check. The specs of the new chip match what you found on CNET. I think it should be a match.

Peter

---

### Post by pdesjardins on 2016-09-29
Result: I upgraded the memory and there were no problems. I have no idea why the first memory upgrade (different laptop and different memory card) broke the boot process. This time there was no problem.

The only theories that I have are that the first memory card was faulty or that the first time I was adding a memory card to an empty expansion slot and this time I installed Ubuntu on a system that already had a card in the expansion slot.

Thanks for the help!

Peter

---

