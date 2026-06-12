---
title: "Ubuntu bricked my computer :-)"
date: 2010-09-28
forum: Installation &amp; Upgrades
---

### Post by octm8 on 2010-09-28
I intend this as a cautionary tale, rather than a direct request for help. I'm afraid the situation is beyond help now.

I installed Ubuntu on a somewhat older (2007) HP Pavilion notebook. Although it did not detect the wireless settings, it worked fine with the DSL cable plugged in. For two days, that is. This morning, as I was scrolling the software list to download some programs, the mouse cursor suddenly turned into a one-inch square composed entirely of vertical lines. The unit was frozen – nothing could be successfully clicked on, no keystroke would work. There was no alternative but a hard shutdown of the computer.

Upon restarting the machine, the pretty purple Ubuntu background came up. The music played sweetly. But the entire screen now consisted of patches of vertical lines, with a little one-inch square in the middle, where the mouse cursor should be. That's all. No desktop, no nothing. Hard shutdown. So I put in the install CD, thinking to try a clean reinstall. After some preliminary noises from the CD player, the pretty purple Ubuntu screen came up once again. The music played. The vertical lines came up. Hard shutdown.

I reasoned that since the Ubuntu screen initially displayed intact, the computer itself must be okay and therefore I might be able to reload Windows, blank the disc that way, and then try Ubuntu once again. Masochist. But I was not to have my chance. When I put in the Windows CD, the CD player shifted around a while, the sweet music of Ubuntu wafted in the background (no pretty purple screen this time). Then the vertical lines came up once again.

The computer is a brick.

This is an older computer I don't care about that much. But if it can happen to a three-year-old HP Pavilion... it might happen to you. So beware :-)

---

### Post by nothingspecial on 2010-09-28
Try doing a minimal install then install the lubuntu-desktop package.

Ubuntu needs a certain amount of ram to run and ever more to install, lubuntu works well on older machines.

---

### Post by Peter09 on 2010-09-28
This is almost certainly a graphics card issue. Can you tell us what the graphics card is.
 
If you hold down shift while booting you can get to the grub menu - from there select recovery mode. As a start when the menu appears select the reconfigure graphics option.

---

### Post by octm8 on 2010-09-28
Hi, thanks for your good offices gentlemen, but I'm afraid it's still a no-go. Holding down shift does nothing – the screen just stays blank. The issue seems to have entered a new phase: now, nothing happens whatsoever after turning on the power switch. The machine turns on but nothing boots, there doesn't seem to be any way to get into bios, etc.

Maybe it was just this machine's time and the problem started with the graphics card. The timing seems mysterious, but then again if coincidences didn't seem full of meaning, there wouldn't be astrologers :-)

Thanks for trying.

---

### Post by nothingspecial on 2010-09-28
You could try booting from usb

---

### Post by coffee412 on 2010-09-28
> **octm8 said:**
> Hi, thanks for your good offices gentlemen, but I'm afraid it's still a no-go. Holding down shift does nothing – the screen just stays blank. The issue seems to have entered a new phase: now, nothing happens whatsoever after turning on the power switch. The machine turns on but nothing boots, there doesn't seem to be any way to get into bios, etc.

Maybe it was just this machine's time and the problem started with the graphics card. The timing seems mysterious, but then again if coincidences didn't seem full of meaning, there wouldn't be astrologers :-)

Thanks for trying.

I was just reading your thread and wanted to add some input. 

I repair these things for a living and I have found that HP laptops are really having problems with overheating video cards that burn up the motherboard and thus ruin the laptop. These mostly happen with the nvidia chipsets models. The Laptops last for about a year/ year and a half and then die a wierd death. 

HP has recalled some laptops and extended the warranty on some others but the problem is that they are replacing the motherboards in the laptops with the same defective ones. Therefore in a year or so they die again. Poor Engineering.

Im very sorry to hear about your laptop. :(

---

### Post by octm8 on 2010-09-28
Thanks, coffee412, I'm pretty sure you hit it right on the head, then. This HP Pavilion was never a good computer – the drive died within a month and it had to be sent back to the shop. And for the whole time I've owned it afterwards, it's operated hot – hotter and hotter, I'd say. And the fan, as a result of that, would become unbelievably loud.

I'm no tech but the scenario I experienced – first, the video going bye-bye and then the whole machine becoming unresponsive – seems to fit well with what you're saying. I've been having a weird time with Linux distributions on three different computers. Ubuntu ran well until the HP decided to self-immolate. But I had also tried Jolicloud on my netbook and it was horrible. Repeated strange errors and hugely slow. And 'andLinux' on my tower computer but it wouldn't install – although there was 130 GB of RAM available, it complained there wasn't enough room to install the virtual machine it needed. Just weird errors. So I was skeptical about Linux functionality, and when Ubuntu blew up on the HP, in spite of owning the whole disk – I figured enough was enough.

But maybe in this case, it was just a bad choice of machine. Now if I could just find another one to do a further test :-)

Thanks for your input.

---

### Post by julio_cortez on 2010-09-28
The same happened to me in Windows last year, and it was the video card.
*First it hanged during games, then it hanged during normal operation (with little pretty nasty artifacts here and there), then the whole screen in normal mode was full of artifacts to the extent I couldn't use it. Strangely, in recovery mode artifacts were there, but at least I managed to save my most needed files (to be used with my old "backup" system) before the graphic card eventually left for good.*

But I agree it's hardly Ubuntu's fault.. Looks like a hardware failure to me :)

---

