---
title: "Dual boot safe and easy"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by tomexx on 2007-04-19
Hi,
I'm very new to Ubuntu and I do like it. However coming from Windows world I still need to run XP for some things so I started looking into dual booting Ubuntu and XP. After reading lots of posts it became clear that it's not as easy as I'd hoped. Apparently it can even be dangerous since you can override your Windows MBR and lose your stuff. I didn't like that. I also wanted both OS to be completely independent of each other with no ties whatsoever (no GRUB installed on my windows etc.)

So here it is, nice & easy:

My setup:
- 3 years old motherboard & Sempron 2500+ (1.4Ghz), 512 RAM
- 2 hard drives, (one has XP installed, the other one is empty)
=========================================

1. Download and burn Ubuntu LIveCD
2. Turn power OFF
3. Unplug power cable from hard drive that has windows installed
4. Connect the second (empty) hard drive to another channel. This will be your Ubuntu drive
5. Turn power ON and boot from LiveCD (you might have to change boot sequence in BIOS)
6. Double-click the install icon on your Ubuntu desktop to install it to the newly connected drive
7. After Ubuntu is installed, remove LiveCD and turn power OFF
8. Reconnect power cable to your windows hard drive
9. Turn computer ON
10. As the computer starts hit F11 for boot menu. A small menu will appear with all your drives. Select to boot from the drive that you installed Ubuntu on.

[B]A)Now I'm assuming that your motherboard will have a boot menu option like mine using F11. Since my motherboard is pretty old and has it, chances are that yours will too. Might not be F11 but some other key so check your documentation.

B)If you can't find the boot menu, go to manufacturer's website and ask the support stuff if there's one OR if you can flash your bios with a newer one that has that option. 

C)Two hard drives setup is really nice since you can format eighter one without affecting the other[/b]


Hope it works for you.

---

