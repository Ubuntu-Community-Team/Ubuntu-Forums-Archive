---
title: "How to enter BIOS on a mini PC with AMD processor?"
date: 2021-07-28
forum: Installation &amp; Upgrades
---

### Post by tahitiwibble on 2021-07-28
Greetings one and all.

It seemed like a good idea but now I'm having regrets.

I couldn't afford to replace my laptop with a new one so went for a "TOPTON Mini PC AMD Ryzen R5 3550H R7 2700U Vega 10 Graphic 2*DDR4 M.2 NVMe" and asked that the store install Ubuntu for me. Well they did, but now they can't remember the password that they used when they created the 'USER' account so I can't do a thing. Neither can they explain to me how to enter the BIOS so that I be able to reinstall Ubuntu on my own.

Can anyone PLEASE help me with how to enter the BIOS?

Many, many thanks in advance!

All the best, Martin

---

### Post by coffeecat on 2021-07-28
Duplicate of [https://ubuntuforums.org/showthread.php?t=2465291](https://ubuntuforums.org/showthread.php?t=2465291)

Thread closed.

---

### Post by ajgreeny on 2021-07-28
Do you see a grub menu at boot or does it boot straight to Ubuntu?
You should be able to get to the grub menu if it does not appear by default, but how you do that will depend on whether the computer uses legacy BIOS or UEFI.

If BIOS you need to hold Shift just after pressing the power button, if UEFI, which is much more likely, you need to continually tap Esc also at the same time, just after pressing the power button.

If, or maybe I should say when the grub menu appears select the Advanced section with cursor button and from that choose Recovery mode.
Once in recovery mode follow the instructions at [https://www.psychocats.net/ubuntu/resetpassword](https://www.psychocats.net/ubuntu/resetpassword) very carefully and you should be able to reset your user password.

---

